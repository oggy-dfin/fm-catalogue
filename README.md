# Catalogue of Formal Verification Tools

This is a catalogue of various existing formal methods (formal verification) tools, with an eye towards applying them to software verification in an industrial setting.
We aim to use this catalogue at DFINITY to inform ourselves about tools and evaluate them for our needs.
We invite others to also use this list for reference and ask experts in the different tools to help us improve it.
If a tool you know is not in the list, or has insufficient/wrong information, please send a PR!

As we are driven by industrial applications, we are interested not only in the scientific, but also the engineering and community aspects of a tool. 
We thus aim to collect the following information for every tool:

* **Short description**: How would you describe the tool in one sentence?
* **URL**: The official (or as official as possible) tool URL
* **License**:
* **Modeling language**: Verifying a system requires modeling both the system
  and its specification in the tool. Different tools provide different languages
  for specifying systems and specifications (often the same language is used for
  both, but not always). The languages can range from very general mathematical
  languages (e.g., some form of logic) to languages specialized for a specific
  domain (e.g., cryptographic protocols, or process calculi). The language may
  influence the difficulty of modeling particular systems (or their interesting
  aspects), but also the analysis effort (i.e., automation)
* **Domain**: Some tools are geared towards specific domains, e.g., security
  protocols, while others can be applied to any domain.
* **Abstraction level of models**: Some tools specialize in high-level
  descriptions of systems (protocols, designs and algorithms). Others specialize
  in verifying code, while yet others can handle arbitrary models.
* **Supported languages**: If the tool supports code verification and/or generation, what languages does it support? How complete is the support (i.e., does it cover all the features)?
* **Analysis mechanisms & automation**: Ultimately, the goal of the tool is to
  analyze a model of the system. The analysis can be fully automated, or can
  require a lot of manual input, or lie somewhere in between. Furthermore,
  there’s a number of standard analysis approaches: interactive tactic-based
  reasoning, SAT/SMT solving (often with some preprocessing), exhaustive finite
  state model checking, symbolic model checking, etc. If the tool uses such an
  approach, we note it here.
* **UX (UI, tooling, libraries)**: All things that influence the ergonomics of working with the tool, both in direct interaction and in processes such as CI.
* **Scalability**: How good is the tool at using additional available hardware (more cores, multiple machines)?
* **Stability**: How backwards-compatible is the tool? E.g., are existing proofs likely to break with a new version? Does it have good changelogs?
* **Documentation and learning resources**: Where do I find documentation? Are there books, tutorials, courses etc. available?
* **Support**: What are the main channels to get support? Mailing lists? Chat? Stackoverflow? How active are these? Does the tool receive regular bugfixes/improvements?
* **Success stories**: Notable verification efforts successfully completed using the tool, ideally with links to them.
  While subjective, we want to focus on verification of software and algorithms that have had real-world usage.
  What was verified: code, high-level models? Is there any information on how large the code/model was? How long did the modeling and verification take?
* **Community**: How many projects are using it (e.g., on Github)? Where does one find them? Are there active projects using it? Are there conferences devoted to the tool, or where work done in the tool regularly features?
* **Related tools and comparison**: Which tools are similar to this one? How do they compare? While comparisons 
  are always somewhat subjective, they are very helpful and we encourage you to post them if you are familiar
  with multiple similar tools. Links to comparison papers/blog posts/other resources are also welcome!
* **Limitations**: Does the tool have notable limitations relevant to its domain?
* **Future prospects**: Are there any notable features on the way?
* **More details**: Anything relevant that's not covered by the above.

Also, we collect here other resources that compare different tools:

* [SOK: Computer-Aided Cryptography (2019)][1]
* [Seventeen Provers of the World (2006)][2]
* [QED at Large: A Survey of Engineering of Formally Verified Software (2020)][9]
* [A Survey on Theorem Provers in Formal Methods (2019)][10]

## ACL2

* **Short description**: Interactive theorem prover
* **URL**: https://www.cs.utexas.edu/users/moore/acl2/
* **License**: MIT-like
* **Modeling language**: First-order, computational, applicative subset of
  common lisp. Dynamically typed.
* **Domain**: program analysis
* **Abstraction level of models**:
* **Supported languages**:
* **Analysis mechanisms & automation**: https://www.cs.utexas.edu/users/moore/acl2/
* **UX (UI, tooling, libraries)**: Emacs mode
* **Scalability**: As proof structures grow larger and more complex, typically
  needs guiding "hints" to get proofs through in a reasonable length of time.
* **Stability**: Very stable, project releases are infrequent.
* **Documentation and learning resources**: An extensive online manual exists
  at
  https://www.cs.utexas.edu/users/moore/acl2/current/combined-manual/index.html.
* **Support**: Mailing list.
* **Success stories**: AMD microcode, used in microprocessor industry
* **Community**:
* **Related tools and comparison**: PVS
* **Limitations**: Problems must be expressible in first-order logic, without
  dependent types, and all terms must be computable. Note that relations can
  be used, since a theorem can simply be a series of computable asserts.
* **Future prospects**:
* **More details**:

## Agda

* **Short description**: Dependently typed programming language
* **URL**: https://wiki.portal.chalmers.se/agda/pmwiki.php
* **License**: BSD-like
* **Modeling language**: Dependently-typed lambda calculus with or without
  Axiom K. Also optionally supports cubical type theory, though without an
  accompanying standard library.
* **Domain**: General, geared towards verified functional programs. Makes it
  relatively convenient to write "proof-carrying code" using dependent type
  indices, so that algoritms are correct-by-construction.
* **Abstraction level of models**: Support any level of abstraction.
* **Supported languages**: Integrates with Haskell.
* **Analysis mechanisms & automation**: Has very limited support for proof
  refinements, though support here is growing. Emacs mode allows for easy
  exploration of available theorems and terms, sometimes making proof
  construction somewhat magical. Does not offer extensive proof term search,
  however, only what is obvious from the environment.
* **UX (UI, tooling, libraries)**: Relies heavily on the Emacs mode for its
  UX.
* **Scalability**: Scales relatively well by having good support for modules.
* **Stability**: Very stable, releases are infrequent.
* **Documentation and learning resources**: Weaker than other dependently
  typed languages but growing. There is now PLFA, Programming Language
  Foundation in Agda, to help with learning the language and its approach to
  proof term construction.
* **Support**: Zulip, GitHub.
* **Success stories**:
* **Community**: Has a relatively strong but small community.
* **Related tools and comparison**: Similar in some ways to Coq, Lean and
  Idris. More "proofs as programs" focused than the others.
* **Limitations**: No severe limitations over similar such provers. "Fixing
  proofs" after code refactoring remains a difficult problem for all provers
  in this category.
* **Future prospects**: Gaining better support for HoTT, which could make
  setoid reasoning more natural.
* **More details**:

## Alloy

* **Short description**: Automated analyzer of high-level models
* **URL**: https://alloytools.org/
* **License**: MIT
* **Modeling language**: First-order relational logic (no function symbols) with a transitive closure operator.
* **Domain**: general
* **Abstraction level of models**: "lightweight analysis" (high-level system/algorithm descriptions)
* **Supported languages**: N/A
* **Analysis mechanisms & automation**: Fully automated, SAT-based model finder (KodKod) for models of user-defined sizes.
* **UX (UI, tooling, libraries)**:
  * Multi-platform Java-based IDE for specifying and analyzing models
* **Scalability**:
* **Stability**:
* **Documentation and learning resources**: online tutorials and references, as well as a book
* **Support**: StackOverflow community (~500 questions as of Sep 2021)
* **Success stories**:
    * [Found problems in Chord][3] (an influential distributed hash table algorithm)
* **Community**:
* **Related tools and comparison**:
  * B, OCL, VDM and Z ([comparison][4])
  * TLA+ ([comparison][8] from 2016)
* **Limitations**:
* **Future prospects**:
* **More details**:


## Coq

* **Short description**: Interactive theorem prover
* **URL**: https://coq.inria.fr/
* **License**: LGPL 2.1
* **Modeling language**: Dependently-typed lambda calculus.
* **Domain**: General.
* **Abstraction level of models**: Any.
* **Supported languages**: OCaml, Haskell, Scheme.
* **Analysis mechanisms & automation**: 
    * Interactive theorem proving with user-definable tactics (Ltac language to define tactics).
    * QuickChick for finding counterexamples.
* **UX (UI, tooling, libraries)**:
    * Built-in IDE, and also integrations for VSCode, Emacs, and Vim
* **Scalability**: Has an excellent module system, so scales well through modularity. There is a Coq-IDE support for resolving goals in parallel, but not in the coqc - it's currently mainly a single core environment.
* **Stability**: Relatively stable; releases are regular (several point
  releases each year), but sometimes break earlier proof developments,
  depending on how heavily one makes use of automated capabilities.
* **Documentation and learning resources**:
    * Several free books & courses available
    * Excellent multi-part Software Foundations course for new learners
* **Support**:
    * Coq has an active bug tracker on GitHub, team is quite responsive.
* **Success stories**: 
  * CompCert, a formally verified optimizing C compiler (~100k lines of Coq code)
  * CertiKOS, a concurrent microkernel/hypervisor (~6500 lines of C and x86
    assembly)
  * FSCQ, a simple FUSE file system verified to be safe in the presence of
    crashes (~30k lines of Coq, extracted Haskell code)
  * Fiat, Bedrock, Kami, a complete system developed by MIT for correct
    construction of hardware and software platforms.
* **Community**:
    * Zulip gives access to all the primary developers
    * IRC, mailing list, GitHub
* **Related tools and comparison**: Isabelle, Agda, Idris, Lean
* **Limitations**: Not very good at dependently-typed programming, definitely
  focused on interactive proof construction using tactics. Thus, it is more
  common to use data with associated proofs, than dependently-typed data that
  is proof-carrying.
* **Future prospects**:
* **More details**: supports code extraction to OCaml, Haskell and Scheme. Likely the best-known theorem prover.


## Creusot

* **Short description**: A deductive verifier for Rust code based on Why3
* **URL**: https://github.com/xldenis/creusot
* **License**: LGPL
* **Modeling language**: Rust for the model, Pearlite for specifications. Pearlite consists of the pure subset of Rust, together with quantifiers and special operators for mutable borrows.
* **Domain**: Verification of safe Rust code
* **Abstraction level of models**: Code
* **Supported languages**: Rust
* **Analysis mechanisms & automation**: The key trick is the representation of mutable borrows, based on the prophecy variables of RustHorn, which avoids using separation logic. This simplifies the reasoning and the proof obligations, but limits the applicability. The verification is otherwise based on annotations and a weakest pre-condition calculus. The resulting proof obligations are then translated to Why3 (the MLCFG language), and can be discharged using any of the Why3 backends. This includes SMT solvers but also interactive theorem provers (Isabelle).
* **UX (UI, tooling, libraries)**:
* **Scalability**: Multiple backend solvers can (and usually are) run in parallel. It's unclear if there is any parallelism beyond that.
* **Stability**: Progress over stability is currently an explicit tenant of the tool.
* **Documentation and learning resources**:
* **Support**:
* **Success stories**:
* **Community**:
* **Related tools and comparison**:
    - Prusti is a deductive verifier for Rust based on separation logic.
    - Verus is a deductive verifier also focused on the safe subset of Rust
    - Stainless-Rust is a deductive verifier for the safe subset of Rust, focused on issuing decidable SMT queries
* **Limitations**: No support for unsafe subset of Rust or the "interior mutability" Rust pattern.
* **Future prospects**:
* **More details**:


## CryptoVerif

* **Short description**: Cryptographic protocol analyzer
* **URL**: https://prosecco.gforge.inria.fr/personal/bblanche/cryptoverif/
* **License**:
* **Modeling language**:
* **Domain**: crypto protocols in a computational model
* **Abstraction level of models**:
* **Supported languages**: N/A
* **Analysis mechanisms & automation**: automated?
* **UX (UI, tooling, libraries)**:
* **Scalability**:
* **Stability**:
* **Documentation and learning resources**:
* **Support**:
* **Success stories**: has been used to analyze protocol models of TLS 1.3,
  Signal, WireGuard
* **Community**:
* **Related tools and comparison**:
* **Limitations**:
* **Future prospects**:
* **More details**: has a notion of private channels.

## CT-Wasm

* **Short description**: Code analyzer
* **URL**: https://github.com/PLSysSec/ct-wasm
* **License**:
* **Modeling language**:
* **Domain**: enforcing constant-time behavior of Wasm programs
* **Abstraction level of models**:
* **Supported languages**: Wasm
* **Analysis mechanisms & automation**: 
* **UX (UI, tooling, libraries)**:
* **Scalability**:
* **Stability**:
* **Documentation and learning resources**:
* **Support**:
* **Success stories**:
* **Community**:
* **Related tools and comparison**:
* **Limitations**:
* **Future prospects**:
* **More details**: available in the [crypto SoK][1]

## EasyCrypt

* **Short description**: Cryptographic protocol analyzer
* **URL**: https://www.easycrypt.info/
* **License**:
* **Modeling language**: cryptographic games
* **Domain**: crypto protocols in a computational model
* **Abstraction level of models**:
* **Supported languages**:
* **Analysis mechanisms & automation**:  automated?
* **UX (UI, tooling, libraries)**:
* **Scalability**:
* **Stability**:
* **Documentation and learning resources**:
* **Support**:
* **Success stories**:
* **Community**:
* **Related tools and comparison**:
* **Limitations**:
* **Future prospects**:
* **More details**: close to pen-and-paper crypto proofs

## F*

* **Short description**: Dependently typed functional programming language
* **URL**: https://www.fstar-lang.org/
* **License**: Apache 2.0
* **Modeling language**: dependently-typed lambda calculus (refinement types)
  with monadic effects
* **Domain**: general, geared towards verified functional programs
* **Abstraction level of models**:
* **Supported languages**:
* **Analysis mechanisms & automation**: a combination of manual and SMT-based
  proofs; does the user get feedback on proof progress/failed proofs?
* **Scalability**:
* **Stability**:
* **UX (UI, tooling, libraries)**:
* **Success stories**: 
  * miTLS, a verified implementation of TLS 1.3
  * LibSignal*, a verified implementation of the Signal protocol that compiles down to WebAssembly
* **Community**:
* **Related tools and comparison**:
* **Limitations**:
* **Future prospects**:
* **More details**: Supports program extraction to F#, OCaml, C, WASM and assembly.
  
## Idris

* **Short description**: Dependently typed functional programming language
* **URL**: https://www.idris-lang.org/
* **License**:
* **Modeling language**: dependently-typed lambda calculus
* **Domain**: general, geared towards verified functional programs
* **Abstraction level of models**:
* **Supported languages**:
* **Analysis mechanisms & automation**: interactive (with tactics)
* **UX (UI, tooling, libraries)**:
* **Scalability**:
* **Stability**:
* **Documentation and learning resources**:
* **Support**:
* **Success stories**:
* **Community**:
* **Related tools and comparison**:
* **Limitations**:
* **Future prospects**:
* **More details**:

## Isabelle/HOL

* **Short description**: Interactive theorem prover
* **URL**: https://isabelle.in.tum.de/
* **License**: BSD
* **Modeling language**: HOL (higher-order logic) with typeclasses
* **Domain**: general
* **Abstraction level of models**: any
* **Supported languages**: 
  * Built-in code generation to Haskell, OCaml, Scala, and SML (SML has a [verified compilation path to CakeML](https://lars.hupel.info/pub/isabelle-cakeml.pdf)). 
  * [Autocorres](https://github.com/seL4/l4v/blob/master/tools/autocorres/README.md) library for parsing C code into Isabelle
  * Semantics of [x86_64](https://www.ssrg.ece.vt.edu/papers/cpp2019.pdf), [Wasm](https://www.isa-afp.org/entries/WebAssembly.html), [ARMv8, RISC-V and CHERI_MIPS](https://www.cl.cam.ac.uk/~pes20/sail/sail-popl2019.pdf)
* **Analysis mechanisms & automation**: 
  * interactive (with tactics, programmable in SML or using the Eisbach language)
  * Sledgehammer tool for automated proof generation using different backend
    solvers (e.g., Z3), Nitpick tool for counter-example search
* **UX (UI, tooling, libraries)**:
  * IDEs for jEdit and VSCode (less functional than jEdit), with code completion/navigation on-par with most mainstream programming languages
  * CLI tools for building theories, supporting caching and parallel proof checking
* **Scalability**: supports parallel proof checking (i.e., runs multi-core), also parallel proof search with multiple SMT solvers
* **Stability**: Detailed [changelogs](https://isabelle.in.tum.de/dist/Isabelle2021/doc/NEWS.html) for backwards-incompatible changes. Proofs will often break with new versions, less problematic if the structured proof language (Isar)  is used.
* **Documentation and learning resources**:
  * Bundled [tutorials and reference documentation](https://isabelle.in.tum.de/documentation.html)
  * Books freely available (e.g., [this](http://concrete-semantics.org/))
* **Support**: 
  * An active [mailing list](https://lists.cam.ac.uk/pipermail/cl-isabelle-users/), Stackoverflow (tag: isabelle)
* **Success stories**: 
  * [seL4 microkernel verification][5]: ~10 kLoC of C code), verified information
    flow and other properties down to the binary code, initial formalization
    effort estimated at 20 person-years with 200 kLoC of proofs, i.e., 20:1 ratio
  * [CoCon](https://link.springer.com/article/10.1007/s10817-020-09566-9), a secure (against an information flow policy with declassification)
    scientific conference management system used for ITP 2016, code generated
    from a verified development
* **Community**:
  * A large collection of existing developments: https://www.isa-afp.org/ 
* **Related tools and comparison**: 
  * Other provers: Coq, HOL4, HOL Light
  * [An older comparison][2] (2006) to 16 other provers, math focused
  * A more recent (2019) [comparison to Coq][7] (math focused)
* **Limitations**:
* **Future prospects**:
* **More details**: supports code generation into OCaml, Haskell SML, and Scala.
  The structured proof language Isar makes maintenance of proofs easier compared
  to proofs based on just a sequence of tactic applications.

## K-framework

* **Short description**: Framework for programming language semantics and analysis
* **URL**: https://kframework.org/
* **License**:
* **Modeling language**: a term-rewriting system
* **Domain**: programming language semantics
* **Abstraction level of models**:
* **Analysis mechanisms & automation**:
  * Automatically defines interpreters for a specified language
* **UX (UI, tooling, libraries)**:
* **Scalability**:
* **Stability**:
* **Documentation and learning resources**:
* **Support**:
* **Success stories**: semantics for C, Java 1.4, EVM
* **Community**:
* **Related tools and comparison**:
* **Limitations**:
* **Future prospects**:
* **More details**:

## Lean Prover

* **Short description**: Interactive theorem prover
* **URL**: https://leanprover.github.io/
* **License**: Apache 2.0
* **Modeling language**: dependently-typed lambda calculus
* **Domain**: general
* **Abstraction level of models**: any
* **Supported languages**:
* **Analysis mechanisms & automation**: interactive, with strong emphasis on programmable tactics backed by Z3
* **UX (UI, tooling, libraries)**:
* **Scalability**:
* **Stability**:
* **Documentation and learning resources**:
* **Support**:
* **Success stories**:
* **Community**:
* **Related tools and comparison**:
* **Limitations**:
* **Future prospects**:
* **More details**:

## Move prover

* **Short description**: Verifier for smart contracts
* **URL**: https://research.fb.com/publications/the-move-prover/
* **License**:
* **Modeling language**:
* **Domain**: smart contracts for the Libra blockchain
* **Abstraction level of models**:
* **Supported languages**:
* **Analysis mechanisms & automation**: 
   * automation?
   * bytecode verifier that does semantics checks on the bytecode, uses boogie and Z3 in background
* **UX (UI, tooling, libraries)**:
* **Scalability**:
* **Stability**:
* **Documentation and learning resources**:
* **Support**:
* **Success stories**:
* **Community**:
* **Related tools and comparison**:
* **Limitations**:
* **Future prospects**:
* **More details**:

## ProVerif

* **Short description**: Security protocol verifier
* **URL**: https://prosecco.gforge.inria.fr/personal/bblanche/proverif/
* **License**:
* **Modeling language**: applied Pi calculus
* **Domain**: security protocols in the symbolic (Dolev-Yao) model
* **Abstraction level of models**: high-level protocol descriptions
* **Supported languages**:
* **Analysis mechanisms & automation**: 
   * protocols translated to Horn clauses with automated proof search
* **UX (UI, tooling, libraries)**:
* **Scalability**:
* **Stability**:
* **Documentation and learning resources**:
* **Success stories**: models of the Signal protocol, TLS 1.3 draft, parts of the Belenios voting system
* **Community**:
* **Related tools and comparison**: Tamarin
* **Limitations**:
* **Future prospects**:
* **More details**:

## Prusti

* **Short description**: Prusti is a prototype verifier for Rust, built upon the Viper verification infrastructure. Prusti aims to reuse as much information as possible from the type system to reduce the annotation effort required from the user. Many other tools start from LLVM IR and they don't get information from the Rust type system.
* **URL**: http://prusti.org/
* **License**: Mozilla Public License Version 2.0
* **Modeling language**: Prusti supports first-order logic. The specifications can be written in a pure (i.e. deterministic, side-effect free, non-diverging) subset of Rust (including Rust functions marked as pure), plus some Rust-like syntax to express implications and quantifiers.
* **Domain**: Prusti is a general purpose verifier for Rust that allows proving functional correctness and absence of panics (e.g. absence of integer overflows).
* **Abstraction level of models**: Code-level verification against code-level contracts. The specification syntax builds on top of Rust syntax, adding operators such as ```==>``` or ```forall```.
* **Supported languages**: Prusti covers a large subset of safe Rust. There are still fragments of Rust which Prusti does not support. Unsafe Rust (which removes some of the memory safety guarantees) is a prime example that the Prusti developers are currently working on.
* **Analysis mechanisms & automation**: Prusti is an automated deductive verifier (like e.g. Dafny) that automatically extracts the necessary information from the Rust compiler and builds a Viper program, which is then verified by the Viper verification infrastructure. Viper uses the SMT solver Z3 under the hood.
* **UX (UI, tooling, libraries)**: Apart from the VS Code IDE extension [Prusti Assistant](https://marketplace.visualstudio.com/items?itemName=viper-admin.prusti-assistant), Prusti integrates with Rust's package manager (```cargo prusti```) to support the standard Rust developer experience. As a result, the Prusti UX feels very similar to the Rust UX, for example: verification errors are reported just like compilation errors.
* **Scalability**: The verification is modular in that every method is checked independently from the others. The bottleneck is usually the Viper verification, which already uses all available cores. The developers report no benefit in further parallelizing the tool in it's current implementation.
* **Stability**: Prusti is still a prototype and, therefore, stability guarantees are limited. The best way to be sure that a proof keeps working is to add it to the (extensive) test suite. 
* **Documentation and learning resources**: 
    * http://prusti.org/
    * https://viperproject.github.io/prusti-dev/
    * https://www.youtube.com/watch?v=C9TTioH5JUg
* **Support**: These channels are used by the team for regular communication:
    * https://github.com/viperproject/prusti-dev/issues
    * https://prusti.zulipchat.com/login/
* **Success stories**:
    * Prusti successfully executes on >60 of the most used Rust crates (packages).
* **Community**: Prusti has been used in various research projects. 
* **Related tools and comparison**: A nice survey is presented at https://alastairreid.github.io/automatic-rust-verification-tools-2021/
    * Creusot (built on top of Why3) is another automated verifier in development. 
    * RustBelt is a Coq-based alternative. 
* **Limitations**: Unsupported language features is the main practical limitation. 
* **Future prospects**: Support for unsafe code, closures, type invariants, interior mutability, concurrency, refinement, dependent types.
* **More details**: 


## PVS

* **Short description**: Interactive theorem prover
* **URL**: https://pvs.csl.sri.com/
* **License**:
* **Modeling language**: dependently-typed lambda calculus
* **Domain**: program analysis
* **Abstraction level of models**: any
* **Supported languages**:
* **Analysis mechanisms & automation**: Interactive with automation. Has a plugin system and built in tools for automating proofs.
* **UX (UI, tooling, libraries)**: Emacs mode, VS Code integration for more user-friendly interaction
* **Scalability**:
* **Stability**:
* **Documentation and learning resources**:
* **Support**:
* **Success stories**: byzantine fault tolerance, used by NASA in flight control systems
* **Community**:
* **Related tools and comparison**: Coq, Isabelle, Lean
* **Limitations**:
  - It seems to require processes to terminate in order to model them.
  - Types need to be well-founded.
  - The type system language is distinct and more limited than the object language. This is due to its focus on program analysis,
    rather than mathematics.
* **Future prospects**:
* **More details**:

## Tamarin

* **Short description**: Security protocol verifier
* **URL**: http://tamarin-prover.github.io/
* **License**:
* **Modeling language**: Rewrite rules to model the protocol, equational
  theories for specifying cryptographic primitives, trace-based execution and
  FOL to express properties
* **Domain**: security protocols in the symbolic (Dolev-Yao) model
* **Abstraction level of models**: Protocol logic
* **Supported languages**: N/A
* **Analysis mechanisms & automation**: 
   * a built-in Dolev-Yao adversary model
   * automated proof search (support to modify the search strategies by scripts called "oracles") 
   * interactive proof search also supported
* **UX (UI, tooling, libraries)**:
  * a Web-based interface for proof search/construction
* **Scalability**:
  * can be run on multiple cores to speed up the proves, but often using more than 12-14 cores does not provide additional improvement
  * can also use up a lot of memory for complicated proofs, so using a larger machine with more memory can help 
* **Stability**:
  * think there have been changes where it was not clear whether all proofs still go through (with the same stragegies), but I have never experienced incompatibility of old proofs   
* **Documentation and learning resources**:
  * a manual is available here: https://tamarin-prover.github.io/manual/book/001_introduction.html 
  * tutorials are available here: https://github.com/tamarin-prover/teaching
  * research papers, links to the above, etc can all be found here: https://tamarin-prover.github.io/
* **Support**:
  * I think the tool is still regularly updated / improved
  * if one has a problem it is probably best to write to the maintainers listed here: https://tamarin-prover.github.io/  
* **Success stories**: TLS 1.3 and Signal protocols
* **Community**:
  * developments of the tool as well as applications of the tool to protocols are regularly features in security conferences (e.g., CSF,...)
  * different research groups seem to regularly use the tool (CISPA, ETH Zurich, Loria/Inria) 
* **Related tools and comparison**:
  * ProVerif:
  * Scyther: Tamarin is more expressive. 
* **Limitations**: No support for arithmetic 
* **Future prospects**:
* **More details**: Support for observational-equivalence properties (e.g., privacy).


## TLA+

* **Short description**: Analyzer of high-level models
* **URL**: https://lamport.azurewebsites.net/tla/tla.html
* **License**: BSD
* **Modeling language**: First-order logic to define transition systems, LTL formulas to specify properties
* **Domain**: general (state machines)
* **Abstraction level of models**: high-level designs
* **Supported languages**: N/A
* **Analysis mechanisms & automation**: 
   * TLC, a finite explicit state model checker for restricted-size domains
   * Apalache, a bounded model checker based on SMT
   * TLA proof system (TLAPS) for interactive proofs; proofs can also be done in Isabelle/HOL
* **UX (UI, tooling, libraries)**:
  * there's a Java-based IDE that feels somewhat dated, and also a VSCode plugin is available (albeit with less functionality)
* **Scalability**: the model checker can run on multiple machines in parallel,  with built-in support for Azure and EC2 on AWS
* **Stability**:
  * Backwards incompatibilities seem rare
  * Detailed [Changelogs]()https://github.com/tlaplus/tlaplus/releases)
* **Documentation and learning resources**:
  * a free [book](https://lamport.azurewebsites.net/tla/book.html) is available, a [tutorial website](https://learntla.com/introduction/), and also a [video course)(https://lamport.azurewebsites.net/video/videos.html)
* **Support**:
* **Success stories**: 
   * the Paxos consensus protocol and its many variations
   * Amazon used it to check designs of their protocol
* **Community**:
* **Related tools and comparison**:
* **Limitations**:
* **Future prospects**:
* **More details**:

## Viper

* **Short description**: (V)erification (I)nfrastructure for (Pe)rmission-based (R)easoning
* **URL**: https://www.pm.inf.ethz.ch/research/viper.html
* **License**: Mozilla Public License 2.0
* **Modeling language**: The Viper intermediate language contains implementation and specification primitives. 
    * The implementation language is suitable for modeling potentially concurrent, stateful systems, e.g., statically typed, object-oriented programs. 
    * The specification language is Separation Logic with abstract predicates, state-dependent functions, iterated separating conjunction, magic wands, fractional permissions, state introspection. 
    * Built-in uninterpreted (partially axiomatized) types include Sets, Sequences, Multisets, and Maps. User-defined uninterpreted types and functions can be modeled in first-order logic. 
* **Domain**: Automated modular verification of potentially concurrent, stateful systems described in a statically typed, object-oriented language (e.g. Java). 
* **Abstraction level of models**: SMT-generated counterexample models to verification failures can be lifted to the level of Viper. There exists an [experimental debugger support](https://github.com/viperproject/lizard) for automatically visualizing heap configurations based on counterexample models. 
* **Supported languages**: Concurrent Java, OpenCL, C/OpenMI (via VerCors) Go (via Gobra); safe Rust (via Prusti); Python 3, statically typed using MyPy (via Nagini), the Vyper smart contract language (via 2vyper)
* **Analysis mechanisms & automation**: automated verification via the Z3 SMT solver. 
* **UX (UI, tooling, libraries)**: Viper IDE (based on VS Code) integrates all Viper-related tools.
* **Scalability**: yes, due to procedure-modular reasoning
* **Stability**: A fairly stable/ mature JVM-based project 
* **Documentation and learning resources**: http://viper.ethz.ch/tutorial/
* **Support**: https://stackoverflow.com/questions/tagged/viper-lang
* **Success stories**: Viper's frontend verifiers are used in production (e.g., [VerCors](https://vercors.ewi.utwente.nl/wiki#introduction), [VerifiedSCION](https://www.pm.inf.ethz.ch/research/verifiedscion.html)) as well as research (e.g., [Etherium smart contracts](https://www.pm.inf.ethz.ch/research/2vyper.html), [Prusti](https://www.pm.inf.ethz.ch/research/prusti.html)). Viper itself has been successfully used in [verification competitions](https://www.pm.inf.ethz.ch/research/verifythis.html) and teaching formal methods. 
* **Community**: 
    * The development of the core Viper project is between ETH Zurich and UBC. 
    * Active projects include [VerCors](https://vercors.ewi.utwente.nl/), [Nagini](https://www.pm.inf.ethz.ch/research/nagini.html), [Prusti](https://www.pm.inf.ethz.ch/research/prusti.html), [2vyper](https://www.pm.inf.ethz.ch/research/2vyper.html), [Gobra](https://www.pm.inf.ethz.ch/research/gobra.html)
* **Related tools and comparison**: 
    * Dafny: also modular language with implementation+specification ingrediants for heap-trasforming programs; does not support concurrency/ Separation Logic but can be compiled and run; supports only verification condition generation
    * VeriFast: also based on Separation Logic; heavily relies on user-defined lemmas; no automation for ISC; typically, more predictable verification times than in Viper; supports only symbolic execution
    * Boogie: only basic verification features (~first-order logic); used to encode more sophisticated techniques (including Viper and Dafny)
    * F*: arguably, Viper's functional alter-ego. More powerful type system than in Viper; limited support for heap verification and modeling stateful systems. 
* **Limitations**: Sometimes the SMT solver is a bottleneck. Verification performance debugging requires domain expertise in hard cases. 
* **Future prospects**: 
* **More details**: 

## Z3 and new-Z/max-Z

* **Short description**: SMT solver
* **URL**: https://lamport.azurewebsites.net/tla/tla.html
* **License**: MIT
* **Modeling language**: SMT with a number of theories (arithmetic, bit-vector, arrays)
* **Domain**: SMT formulas
* **Abstraction level of models**: SMT formulas
* **Supported languages**: N/A
* **Analysis mechanisms & automation**: automated model finding
* **UX (UI, documentation, community, tooling)**:
* **Scalability**:
* **Stability**:
* **Documentation and learning resources**:
* **Support**:
* **Success stories**: 
* **Community**:
* **Related tools and comparison**:
* **Limitations**:
* **Future prospects**:
* **More details**: used as a background solver for many other tools

## References

[1]: <https://eprint.iacr.org/2019/1393.pdf> "SOK: Computer-Aided Cryptography"
[2]: <http://www.cs.ru.nl/~freek/comparison/comparison.pdf> "Seventeen Provers of the World"
[3]: <http://cs.brown.edu/courses/cs195y/2020/pages/pdf/chord.pdf> "Using Lightweight Modeling To Understand Chord"
[4]: <https://alloytools.org/download/comparisons.pdf> "Alloy: Comparisons to Z, B, VDM and OCL"
[5]: <https://www.cs.columbia.edu/~junfeng/09fa-e6998/papers/sel4.pdf> "seL4: Formal Verification of an OS Kernel"
[6]: <https://link.springer.com/article/10.1007/s10817-020-09566-9> "CoCon: A Conference Management System with Formally Verified Document Confidentiality"
[7]: <https://arxiv.org/abs/1808.09701> "Comparison of Two Theorem Provers: Isabelle/HOL and Coq"
[8]: <https://arxiv.org/abs/1603.03599> "Alloy meets TLA+: An exploratory study"
[9]: <https://arxiv.org/pdf/2003.06458.pdf> "QED at Large: A Survey of Engineering of Formally Verified Software"
[10]: <https://arxiv.org/pdf/1912.03028v1.pdf> "A Survey on Theorem Provers in Formal Methods"

## Template

* **Short description**:
* **URL**:
* **License**:
* **Modeling language**:
* **Domain**:
* **Abstraction level of models**:
* **Supported languages**:
* **Analysis mechanisms & automation**: 
* **UX (UI, tooling, libraries)**:
* **Scalability**:
* **Stability**:
* **Documentation and learning resources**:
* **Support**:
* **Success stories**:
* **Community**:
* **Related tools and comparison**:
* **Limitations**:
* **Future prospects**:
* **More details**:
