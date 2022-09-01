# Being lazy without getting bloated
### **Haskell nothunks library goes a long way towards making memory leaks a thing of the past**
![](img/2020-09-24-being-lazy-without-getting-bloated.002.png) 24 September 2020![](img/2020-09-24-being-lazy-without-getting-bloated.002.png)[ Edsko de Vries](tmp//en/blog/authors/edsko-de-vries/page-1/)![](img/2020-09-24-being-lazy-without-getting-bloated.003.png) 25 mins read

![Edsko de Vries](img/2020-09-24-being-lazy-without-getting-bloated.004.png)[](tmp//en/blog/authors/edsko-de-vries/page-1/)
### [**Edsko de Vries**](tmp//en/blog/authors/edsko-de-vries/page-1/)
Software Engineer

Well-Typed

- ![](img/2020-09-24-being-lazy-without-getting-bloated.005.png)[](http://www.linkedin.com/in/edsko-de-vries-04126b31 "LinkedIn")
- ![](img/2020-09-24-being-lazy-without-getting-bloated.006.png)[](https://twitter.com/EdskoDeVries "Twitter")
- ![](img/2020-09-24-being-lazy-without-getting-bloated.007.png)[](https://github.com/edsko "GitHub")

![Being lazy without getting bloated](img/2020-09-24-being-lazy-without-getting-bloated.008.jpeg)

*In our Developer Deep Dive series of occasional technical blogs, we invite IOHKâ€™s engineers to discuss their latest work and insights.*

Haskell is a lazy language. The importance of laziness has been widely discussed elsewhere: [Why Functional Programming Matters](http://www.cse.chalmers.se/~rjmh/Papers/whyfp.html) is one of the classic papers on the topic, and [A History of Haskell: Being Lazy with Class](http://citeseer.ist.psu.edu/viewdoc/download;jsessionid=1DD00353B72F4318D0FE3D41668AB13A?doi=10.1.1.168.4008&rep=rep1&type=pdf) discusses it at length as well. For the purposes of this blog we will take it for granted that laziness is something we want. But laziness comes at a cost, and one of the disadvantages is that laziness can lead to memory leaks that are sometimes difficult to find. In this post we introduce a new library called [nothunks](http://hackage.haskell.org/package/nothunks) aimed at discovering a large class of such leaks early, and helping to debug them. This library was developed for our work on the Cardano blockchain, but we believe it will be widely applicable in other projects too.
## **A motivating example**
Consider the tiny application below, which processes incoming characters and reports how many characters there are in total, in addition to some per-character statistics:

import qualified Data.Map.Strict as Map

data AppState = AppState {

`      `total :: !Int

`    `, indiv :: !(Map Char Stats)

`    `}

`  `deriving (Show)

type Stats = Int

update :: AppState -> Char -> AppState

update st c = st {

`      `total = total st + 1

`    `, indiv = Map.alter (Just . aux) c (indiv st)

`    `}

`  `where

`    `aux :: Maybe Stats -> Stats

`    `aux Nothing  = 1

`    `aux (Just n) = n + 1

initAppState :: AppState

initAppState = AppState {

`      `total = 0

`    `, indiv = Map.empty

`    `}

main :: IO ()

main = interact $ show . foldl' update initAppState

In this version of the code, the per-character statistics are simply how often we have seen each character. If we feed this code â€˜aabbbâ€™, it will tell us that it saw 5 characters, 2 of which were the letter â€˜aâ€™ and 3 of which were â€˜bâ€™:

\# echo -n aabbb | cabal run example1

AppState {

`    `total = 5

`  `, indiv = fromList [('a',2),('b',3)]

`  `}

Moreover, if we feed the application a ton of data and construct a memory profile,

dd if=/dev/zero bs=1M count=10 | cabal run --enable-profiling example1 -- +RTS -hy

we see from Figure 1 that the application runs in constant space.

![Figure 1. Memory profile for the first example](img/2020-09-24-being-lazy-without-getting-bloated.009.png)

**Figure 1. Memory profile for the first example**

So far so good. But now suppose we make an innocuous-looking change. Suppose, in addition to reporting how *often* every character occurs, we also want to know the *offset* of the last time that the character occurs in the file:

type Stats = (Int, Int)

update :: AppState -> Char -> AppState

update st c = -- .. as before

`  `where

`    `aux :: Maybe Stats -> Stats

`    `aux Nothing       = (1     , total st)

`    `aux (Just (n, \_)) = (n + 1 , total st)

The application works as expected:

\# echo -n aabbb | cabal run example2

AppState {

`    `total = 5

`  `, indiv = fromList [('a',(2,1)),('b',(3,4))]

`  `}

and so the change is accepted in GitHub's PR code review and gets merged. However, although the code still *works*, it is now a lot slower.

\# time (dd if=/dev/zero bs=1M count=100 | cabal run example1)

(..)

real    0m2,312s

\# time (dd if=/dev/zero bs=1M count=100 | cabal run example2)

(..)

real    0m15,692s

We have a slowdown of almost an order of magnitude, although we are barely doing more work. Clearly, something has gone wrong, and indeed, we have introduced a memory leak (Figure 2).

![Figure 2. Memory profile for example 2](img/2020-09-24-being-lazy-without-getting-bloated.009.png)

**Figure 2. Memory profile for example 2**

Unfortunately, tracing a profile like this to the actual problem in the code can be very difficult indeed. Whatâ€™s worse, although our change introduced a regression, the application still worked fine and so the test suite probably wouldnâ€™t have failed. Such memory leaks tend to be discovered only when they get so bad in production that things start to break (for example, servers running out of memory), at which point you have an emergency on your hands.

In the remainder of this post we will describe how nothunks can help both with spotting such problems much earlier, and debugging them.
## **Instrumenting the code**
Letâ€™s first see what usage of nothunks looks like in our example. We modify our code and derive a new class instance for our AppState:

data AppState = AppState {

`      `total :: !Int

`    `, indiv :: !(Map Char Stats)

`    `}

`  `deriving (Show, Generic, NoThunks)

The NoThunks class is defined in the nothunks library, as we will see in detail later. Additionally, we will replace foldl' with a new function:

repeatedly :: forall a b. (NoThunks b, HasCallStack)

`           `=> (b -> a -> b) -> (b -> [a] -> b)

repeatedly f = ..

We will see how to define repeatedly later, but, for now, think of it as 'foldl' with some magic sprinkled on topâ€™. If we run the code again, the application will throw an exception almost immediately:

\# dd if=/dev/zero bs=1M count=100 | cabal run example3

(..)

example3: Unexpected thunk with context

`  `["Int","(,)","Map","AppState"]

CallStack (from HasCallStack):

`  `error, called at shared/Util.hs:22:38 in Util

`  `repeatedly, called at app3/Main.hs:38:26 in main:Main

The essence of the nothunks library is that we can check if a particular value contains any thunks we werenâ€™t expecting, and this is what repeatedly is using to make sure weâ€™re not inadvertently introducing any thunks in the AppState; itâ€™s this check that is failing and causing the exception. We get a HasCallStack backtrace telling us where we introduced that thunk, and â€“ even more importantly â€“ the exception gives us a helpful clue about where the thunk was:

["Int","(,)","Map","AppState"]

This context tells us that we have an AppState containing a Map containing tuples, all of which were in weak head normal form (not thunks), *but* the tuple contained an Int which *was not* in weak head normal form: a thunk.

From a context like this it is obvious what went wrong: although we are using a strict map, we have instantiated the map at a lazy pair type, and so although the map is forcing the *pairs*, itâ€™s not forcing the *elements* of those pairs. Moreover, we get an exception the *moment* we introduce the thunk, which means that we can catch such regressions in our test suite. We can even construct minimal counter-examples that result in thunks, as we will see later.
## **Using nothunks**
Before we look at how the library works, letâ€™s first see how itâ€™s used. In the previous section we were using a magical function repeatedly, but didnâ€™t see how we could define it. Letâ€™s now look at this function:

repeatedly :: forall a b. (NoThunks b, HasCallStack)

`           `=> (b -> a -> b) -> (b -> [a] -> b)

repeatedly f = go

`  `where

`    `go :: b -> [a] -> b

`    `go !b []     = b

`    `go !b (a:as) =

`        `let !b' = f b a

`        `in case unsafeNoThunks b' of

`              `Nothing    -> go b' as

`              `Just thunk -> error . concat $ [

`                  `"Unexpected thunk with context "

`                `, show (thunkContext thunk)

`                `]

The only difference between repeatedly and foldl' is the call to unsafeNoThunks, which is the function that checks if a given value contains any unexpected thunks. The function is marked as â€˜unsafeâ€™ because whether or not a value is a thunk is not normally observable in Haskell; making it observable breaks equational reasoning, and so this should only be used for debugging or in assertions. Each time repeatedly applies the provided function f to update the accumulator, it verifies that the resulting value doesnâ€™t contain any unexpected thunks; if it does, it errors out (in real code such a check would only be enabled in test suites and not in production).

One point worth emphasizing is that repeatedly reduces the value to weak head normal form (WHNF) *before* calling unsafeNoThunks. This is, of course, what makes a strict fold-left *strict*, and so repeatedly must do this to be a good substitute for foldl'. However, it is important to realize that if repeatedly *did not* do that, the call to unsafeNoThunks would trivially and immediately report a thunk; after all, we have just created the f b a thunk! Generally speaking, it is not useful to call unsafeNoThunks (or its IO cousin noThunks) on values that arenâ€™t already in WHNF.

In general, long-lived application state should never contain any unexpected thunks, and so we can apply the same kind of pattern in other scenarios. For example, suppose we have a server that is a thin IO layer on top of a mostly pure code base, storing the application state in an IORef. Here, too, we might want to make sure that that IORef never points to a value containing unexpected thunks:

newtype StrictIORef a = StrictIORef (IORef a)

readIORef :: StrictIORef a -> IO a

readIORef (StrictIORef v) = Lazy.readIORef v

writeIORef :: (NoThunks a, HasCallStack)

`           `=> StrictIORef a -> a -> IO ()

writeIORef (StrictIORef v) !x = do

`    `check x

`    `Lazy.writeIORef v x

check :: (NoThunks a, HasCallStack) => a -> IO ()

check x = do

`    `mThunk <- noThunks [] x

`    `case mThunk of

`      `Nothing -> return ()

`      `Just thunk ->

`        `throw $ ThunkException

`                  `(thunkContext thunk)

`                  `callStack

Since check already lives in IO, it can use noThunks directly, instead of using the unsafe pure wrapper; but otherwise this code follows a very similar pattern: the moment we might introduce a thunk, we instead throw an exception. One could imagine doing a very similar thing for, say, StateT, checking for thunks in put:

newtype StrictStateT s m a = StrictStateT (StateT s m a)

`  `deriving (Functor, Applicative, Monad)

instance (Monad m, NoThunks s)

`      `=> MonadState s (StrictStateT s m) where

`  `get    = StrictStateT $ get

`  `put !s = StrictStateT $

`      `case unsafeNoThunks s of

`        `Nothing -> put s

`        `Just thunk -> error . concat $ [

`            `"Unexpected thunk with context "

`          `, show (thunkContext thunk)

`          `]
## **Minimal counter-examples**
In some applications, there can be complicated interactions between the input to the program and the thunks it may or may not create. We will study this through a somewhat convoluted but, hopefully, easy-to-understand example. Suppose we have a server that is processing two types of events, A and B:

data Event = A | B

`  `deriving (Show)

type State = (Int, Int)

initState :: State

initState = (0, 0)

update :: Event -> State -> State

update A (a, b)    = let !a' = a + 1 in (a', b)

update B (a, b)

`  `| a < 1 || b < 1 = let !b' = b + 1 in (a, b')

`  `| otherwise      = let  b' = b + 2 in (a, b')

The serverâ€™s internal state consists of two counters, a and b. Each time we see an A event, we just increment the first counter. When we see a B event, however, we increment b by 1 only if a and b havenâ€™t reached 1 yet, and by 2 otherwise. Unfortunately, the code contains a bug: in one of these cases, part of the serverâ€™s state is not forced and we introduce a thunk. (Disclaimer: the code snippets in this blog post are not intended to be good examples of coding, but to make it obvious where memory leaks are introduced. Typically, memory leaks should be avoided by using appropriate *data types*, not by modifying *code*.)

A minimal counter-example that will demonstrate the bug would therefore involve two events A and B, in any order, followed by another B event. Since we get an exception the *moment* we introduce an exception, we can then use a framework such as quickcheck-state-machine to find bugs like this and construct such minimal counter-examples.

Hereâ€™s how we might set up our test. Explaining how quickcheck-state-machine (QSM) works is well outside the scope of this blog post; if youâ€™re interested, a good starting point might be [An in-depth look at quickcheck-state-machine](http://www.well-typed.com/blog/2019/01/qsm-in-depth/). For this post, it is enough to know that in QSM we are comparing a real implementation against some kind of model, firing off â€˜commandsâ€™ against both, and then checking that the responses match. Here, both the server and the model will use the update function, but the â€˜realâ€™ implementation will use the StrictIORef type we introduced above, and the mock implementation will just use the pure code, with no thunks check. Thus, when we compare the real implementation against the model, the responses will diverge whenever the real implementation throws an exception (caused by a thunk):

data T

type instance MockState   T = State

type instance RealMonad   T = IO

type instance RealHandles T = '[]

data instance Cmd T f hs where

`  `Cmd :: Event -> Cmd T f '[]

data instance Resp T f hs where

`  `-- We record any exceptions that occurred

`  `Resp :: Maybe String -> Resp T f '[]

deriving instance Eq   (Resp T f hs)

deriving instance Show (Resp T f hs)

deriving instance Show (Cmd  T f hs)

instance NTraversable (Resp T) where

`  `nctraverse \_ \_ (Resp ok) = pure (Resp ok)

instance NTraversable (Cmd T) where

`  `nctraverse \_ \_ (Cmd e) = pure (Cmd e)

**This document was truncated here because it was created in the Evaluation Mode.**
