# Looking to the future of Haskell and JavaScript for Plutus
### **Smart contracts use the GHCJS cross-compiler to translate off-chain code**
![](img/2020-06-04-looking-to-the-future-of-haskell-and-javascript-for-plutus.002.png) 4 June 2020![](img/2020-06-04-looking-to-the-future-of-haskell-and-javascript-for-plutus.002.png)[ Luite Stegeman](tmp//en/blog/authors/luite-stegeman/page-1/)![](img/2020-06-04-looking-to-the-future-of-haskell-and-javascript-for-plutus.003.png) 8 mins read

![Luite Stegeman](img/2020-06-04-looking-to-the-future-of-haskell-and-javascript-for-plutus.004.png)[](tmp//en/blog/authors/luite-stegeman/page-1/)
### [**Luite Stegeman**](tmp//en/blog/authors/luite-stegeman/page-1/)
Software Engineer

Engineering

- ![](img/2020-06-04-looking-to-the-future-of-haskell-and-javascript-for-plutus.005.png)[](mailto:luite.stegeman@iohk.io "Email")
- ![](img/2020-06-04-looking-to-the-future-of-haskell-and-javascript-for-plutus.006.png)[](https://github.com/luite "GitHub")

![Looking to the future of Haskell and JavaScript for Plutus](img/2020-06-04-looking-to-the-future-of-haskell-and-javascript-for-plutus.007.jpeg)

*This is the second of the Developer Deep Dive technical posts from our Haskell team. This occasional series offers a candid glimpse into the core elements of the Cardano platform and protocols, and gives insights into the engineering choices that have been made. Here, we outline some of the work that has been going on to improve the libraries and developer tools for Plutus, Cardanoâ€™s smart contract platform.*
## **Introduction**
At IOHK we are developing the Plutus smart contract platform for the Cardano blockchain. A Plutus contract is a Haskell program that is partly compiled to on-chain Plutus Core code and partly to off-chain code. On-chain code is run by Cardano network nodes using the interpreter for Plutus Core, the smart contract language embedded in the Cardano ledger. This is how the network verifies transactions. Off-chain code is for tasks such as setting up the contract and for user interaction. It runs inside the wallet of each user of the contract, on a node.js runtime.

Compiling the off-chain part of a Plutus contract therefore involves translating the off-chain code to JavaScript. To accomplish this, we use GHCJS, the Glasgow Haskell to JavaScript cross-compiler.

In the past year, we haven't made many changes in the GHCJS code generator. Instead, we did some restructuring to make compiling things with GHCJS more reliable and predictable as well as adding support for Windows and making use of the most recent Cabal features. This post gives an overview of what has happened, and a brief look at what's in store for this year.
## **Cabal support**
When installing a package with GHCJS, you probably use the --ghcjs command line flag or include compiler: ghcjs in your configuration file. This activates the [ghcjs compiler flavor](https://hackage.haskell.org/package/Cabal-3.0.0.0/docs/Distribution-Simple-GHCJS.html) in Cabal. The ghcjs flavor is based on the ghc flavor and adds features such as support for running set-up scripts built by GHCJS, and for adding JavaScript sources.

Cabal has introduced many features in recent years, including support for backpack, Nix-style local builds, multiple (named) libraries per package, and per-component build plans. Unfortunately, the new features resulted in many changes to the code base, and maintenance for the ghcjs flavor fell behind for some time. We have brought GHCJS support up to date again in version 3.0. If you want to use the new-style build features, make sure that you use [cabal-install](https://hackage.haskell.org/package/cabal-install) version 3 or later.

The differences between the ghcjs and ghc compiler flavors are minor, and cross-compilation support in Cabal has been improving. Therefore, we hope that eventually we will be able to drop the ghcjs compiler flavor altogether. The extensions would instead be added as platform-specific behaviour in the ghc flavor.
## **Compiler plug-ins**
GHC allows the compiler to be extended with [plug-ins](https://downloads.haskell.org/ghc/8.8.1/docs/html/users_guide/extending_ghc.html#compiler-plugins), which can change aspects of the compilation pipeline. For example, plug-ins can introduce new optimization features or extend the typechecker.

Unlike Template Haskell, which is separated from the compiler through the [Quasi typeclass](https://hackage.haskell.org/package/template-haskell-2.12.0.0/docs/Language-Haskell-TH-Syntax.html#t:Quasi) abstraction, plug-ins can directly use the whole GHC API. This makes the â€˜[external interpreter](https://gitlab.haskell.org/ghc/ghc/wikis/commentary/compiler/external-interpreter)â€™ approach that GHCJS introduced for running Template Haskell in a cross-compiler unsuitable for compiler plug-ins. Instead, plug-ins need to be built for the build platform (that runs GHC).

In 2016, GHCJS introduced experimental support for compiler plug-ins. This relied on looking up the plug-in in the GHCJS package database and then trying to find a close match for the plug-in package and module in the GHC package database. We have now [added a new flag](https://github.com/ghcjs/ghc/commit/21aee8d3e6ff3991cf17b59b0992829de1565265) to point GHCJS to packages runnable on the build system. This makes plug-ins usable again with new-style builds and other â€˜exoticâ€™ package database configurations.

In principle, our new flag can make plug-ins work on any GHC cross-compiler, but the requirement to also build the plug-in with the cross-compiler is quite ugly. We are working on removing this requirement followed by merging plug-in support for cross-compilers into upstream GHC (see [ticket 14335](https://gitlab.haskell.org/ghc/ghc/issues/14335) and [ticket 17957](https://gitlab.haskell.org/ghc/ghc/issues/17957)).
## **Emscripten toolchain**
Long, long ago, GHCJS worked on Windows. One or two brave souls might have actually used it! Its boot packages (the packages built by ghcjs-boot) would include the Win32 package on the Windows build platform. The reason for this was the Cabal configuration with GHCJS. Cabalâ€™s os(win32) flag would be set if the build platform was Windows. At the time it was easiest to just patch the package to build without errors with GHCJS, and include it in the boot packages. However, the Win32 package didn't really work, and keeping it up to date was a maintenance burden. At some point it fell behind and GHCJS didn't work on Windows any more.

The boot packages having to include Win32 on Windows was indicative of poor separation between the build platform (which runs the compiler) and the host platform (which runs the executable produced by the compiler). This was caused by the lack of a complete C toolchain for GHCJS. Many packages don't just have Haskell code, but also have files produced by a C toolchain, for example via an [Autotools configure](https://www.gnu.org/software/autoconf/) script or [hsc2hs](https://hackage.haskell.org/package/hsc2hs).

The GHCJS approach was to include some pre-generated files, and use the build platform C toolchain (the same that GHC would use) for everything else, hoping that it wouldn't break. If it did break, we would patch the package.

In recent years, the web browser as a compilation target has steadily been gaining more traction. Emscripten has been providing a C toolchain for many years, and has recently switched from its own compiler backend to the Clang compiler with the standard LLVM backend.

Clang has been supported by GHC as a C toolchain for a while. It can output asm.js and WebAssembly code that can run directly in the browser. Unfortunately, users of the compiler cannot yet directly interact with compiled C code through the C FFI (foreign import ccall) in GHCJS. But having a C toolchain allows packages that depend on configure scripts or hsc2hs to compile much more reliably. This fixes some [long-standing build problems](https://github.com/ghcjs/ghcjs/issues/702) and allows us to support Windows again. We thought this is already worth the additional dependency.

A variant of GHCJS 8.6 using the Emscripten toolchain is available in the ghc-8.6-emscripten branch, which can be installed on Windows. This time around, the set of boot packages is the same on every build platform. Emscripten is planned to be the standard toolchain in GHCJS 8.8 onwards.
## **Code organization**
At some point in the early days, GHCJS was implemented as a patch to GHC. It generated JavaScript from the STG intermediate code that a regular GHC installation produced. This made it easy to install packages with GHCJS. Just install normally and get JavaScript for free. Even Template Haskell worked!

The downside of this approach was that the build platform very much affected the generated code. If you build on a 64-bit Linux machine, all platform constants would come from the Linux platform. And the code would be built with the assumption that Int is 64-bit. That is not very efficient to implement in JavaScript. And Cabal would not be aware that JavaScript was being generated at all.

Later, we switched to using ghc as a library, introducing [Hooks](https://gitlab.haskell.org/ghc/ghc/blob/ghc-8.8/compiler/main/Hooks.hs) to change the compilation pipeline where needed. This made it possible to make the GHCJS platform word size independent of the build platform, introduce the JavaScriptFFI extension and run Template Haskell in a separate process with node.js.

Unfortunately, it turned out to be hard to keep up with changes in the upstream ghc library. In addition, modifying the existing ghc through Hooks encouraged engineers to work around issues instead of directly fixing them upstream.

In early 2018, we decided to build a custom ghc library for GHCJS, installed as ghc-api-ghcjs, allowing us to work around serious issues before they were merged upstream. Recently, we dropped the separate library, and built both the GHC and GHCJS source code in one library: ghcjs.

Although we cannot build GHCJS with the GHC build system yet, we are using the upstream GHC source tree much more directly again. Are we going back to the past? Perhaps, but this time we have our own platform with a toolchain and build tools, avoiding the pitfalls that made this approach so problematic the first time.
# **Outlook**
In 2019, we saw improvements to make Cabal work again, to bring back Windows support and to improve the C toolchain. We hope that the underlying changes in the GHCJS code base will make it easier to merge more upstream and to make libraries compatible with fewer changes. By continuing this path of turning GHCJS into a proper cross-compiler with a proper toolchain, as well as reducing its custom tools, we intend to further align and eventually merge GHCJS with GHC. While there will always be platform-specific libraries that simply cannot be cross-compiled, our ultimate goal is to provide GHC with a JavaScript target, alongside its x86\_64, Arm, AArch64, and other code generation targets.
