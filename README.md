# Catalogue of Formal Verification Tools

This is a catalogue of the various existing formal methods (formal verification) tools, with an eye towards apply them to software verification in an industrial setting.
We use the catalogue at DFINITY to inform ourselves about tools and evaluate them for our needs.
If a tool you know is not in the list, or has insufficient/wrong information, please send a PR!

We list the following information for every tool:

* **Modeling language**: verifying a system requires modeling both the system and its specification in the tool. 
  Different tools provide different languages for specifying systems and specifications (often the same language is used for both, but not always). 
  The languages can range from very general mathematical languages (e.g., some form of logic) to languages specialized for a specific domain 
  (e.g., cryptographic protocols, or process calculi). 
  The language may influence the difficulty of modeling particular systems (or their interesting aspects), but also the analysis effort (i.e., automation)

* **Domain**: some tools are geared towards specific domains, e.g., security protocols.

* **Model analysis & automation**: ultimately, the goal of the tool is to analyze a model of the system.
  The analysis can be fully automated, or can require a lot of manual input, or lie somewhere in between. 
  Furthermore, there’s a number of standard analysis approaches: interactive tactic-based reasoning, SAT/SMT solving (often with some preprocessing), exhaustive finite state model checking, symbolic model checking, etc. 
  If the tool uses such an approach, we note it here.

* **Success stories**: notable verification efforts successfully completed using the tool.
  While subjective, we want to focus on verification of software and algorithms that have had real-world usage.
  
* **UX: UI, documentation, community, tooling**: all things that influence the ergonomics of working with the tool.

* **More details**: anything significant that wasn't covered by the previous points, including comparisons to related tools.

* **URL**: where to find more information

Other resources that compare different tools:

* [SOK: Computer-Aided Cryptography (2019)][1]
* [Seventeen Provers of the World (2006)][2]

[1]: <https://eprint.iacr.org/2019/1393.pdf> "SOK: Computer-Aided Cryptography"
[2]: <http://www.cs.ru.nl/~freek/comparison/comparison.pdf> "Seventeen Provers of the World"


## Agda

* **Modeling language**: dependently-typed lambda calculus 
* **Domain**: general, geared towards verified functional programs
* **Analysis mechanisms & automation**: Interactive theorem proving
* **Success stories**:
* **UX: UI, documentation, community, tooling**:
* **More details**:
* **URL**: https://wiki.portal.chalmers.se/agda/pmwiki.php

## Alloy

* **Modeling language**: First-order relational logic (no function symbols) with a transitive closure operator.
* **Domain**: general, focus on "lightweight analysis" (high-level system/algorithm descriptions)
* **Analysis mechanisms & automation**: Fully automated, SAT-based model finder (KodKod) for models of user-defined sizes.
* **Success stories**:
    * Pamela Zave used it to find problems in Chords (an influential distributed hash table algorithm)
* **UX (UI, documentation, community, tooling)**:
  * Multi-platform Java-based IDE for specifying and analyzing models
  * Docs: online tutorials and references, as well as a book
  * StackOverflow community (~500 questions as of Sep 2021)
* **More details**:
* **URL**: https://alloytools.org/

## Coq

* **Modeling language**: dependently-typed lambda calculus
* **Domain**: general
* **Analysis mechanisms & automation**: 
    * interactive theorem proving with user-definable tactics
    * QuickCheck for finding counterexamples
* **Success stories**: 
  * CompCert, a formally verified optimizing C compiler (~100k lines of Coq code)
  * CertiKOS, a concurrent microkernel/hypervisor (~6500 lines of C and x86
    assembly)
  * FSCQ, a simple FUSE file system verified to be safe in the presence of crashes (~30k lines of Coq, extracted Haskell code)
* **UX (UI, documentation, community, tooling)**: 
    * Built-in IDE, and also integrations for VSCode, Emacs, and Vim
    * Several free books & courses available 
* **More details**: supports code extraction to OCaml, Haskell and Scheme. Likely the best-known theorem prover.
* **URL**: https://coq.inria.fr/

## CryptoVerif

* **Modeling language**: 
* **Domain**: crypto protocols in a computational model
* **Analysis mechanisms & automation**: automated?
* **Success stories**: has been used to analyze protocol models of TLS 1.3,
  Signal, WireGuard
* **UX (UI, documentation, community, tooling)**:  
* **More details**: has a notion of private channels.
* **URL**: https://prosecco.gforge.inria.fr/personal/bblanche/cryptoverif/

## CT-Wasm

* **Modeling language**: 
* **Domain**: enforcing constant-time behavior of Wasm programs
* **Analysis mechanisms & automation**:
* **Success stories**: 
* **UX (UI, documentation, community, tooling)**:  
* **More details**: available in the [crypto SoK][1]
* **URL**: https://github.com/PLSysSec/ct-wasm

## EasyCrypt

* **Modeling language**: cryptographic games
* **Domain**: crypto protocols in a computational model
* **Analysis mechanisms & automation**:  automated?
* **Success stories**: 
* **UX (UI, documentation, community, tooling)**:  
* **More details**: close to pen-and-paper crypto proofs
* **URL**: https://www.easycrypt.info/

## F*

* **Modeling language**: dependently-typed lambda calculus (refinement types)
  with monadic effects
* **Domain**: general, geared towards verified funcitonal programs
* **Analysis mechanisms & automation**: a combination of manual and SMT-based
  proofs; does the user get feedback on proof progress/failed proofs?
* **Success stories**: 
  * miTLS, a verified implementation of TLS 1.3
  * LibSignal*, a verified implementation of the Signal protocol that compiles down to WebAssembly
* **UX (UI, documentation, community, tooling)**:  
* **More details**: Supports program extraction to F#, OCaml, C, WASM and assembly.
* **URL**: https://www.fstar-lang.org/
  
## Idris

* **Modeling language**: dependently-typed lambda calculus
* **Domain**: general, geared towards verified functional programs
* **Analysis mechanisms & automation**: interactive (with tactics)
* **Success stories**: 
* **UX (UI, documentation, community, tooling)**:  
* **More details**:
* **URL**: https://www.idris-lang.org/

## Isabelle/HOL

* **Modeling language**: HOL (higher-order logic) with typeclasses
* **Domain**: general
* **Analysis mechanisms & automation**: 
  * interactive (with tactics)
  * Sledgehammer tool for automated proof generation using different backend
    solvers (e.g., Z3), Nitpick tool for counter-example search
* **Success stories**: 
  * seL4 microkernel verification (~10 kLoC of C code), verified information
    flow and other properties down to the binary code, initial formalization
    effort estimated at 30 person-years)
  * CoCon, a secure (against an information flow policy with declassification)
    scientific conference management system used for ITP 2016, code generated
    from a verified developmen
* **UX (UI, documentation, community, tooling)**:
  * IDEs for jEdit and VSCode (less functional than jEdit), with code completion/navigation on-par with most mainstream programming languages
  * Tutorials and books freely available
  * CLI tools for building theories, supporting caching and parallel proof checking
  * A large collection of existing developments: https://www.isa-afp.org/ 
  * An active mailing list, Stackoverflow
* **More details**: supports code generation into OCaml, Haskell SML, and Scala.
  The structured proof language Isar makes maintenance of proofs easier compared
  to proofs based on just a sequence of tactic applications.
* **URL**: https://isabelle.in.tum.de/

## K-framework

* **Modeling language**: a term-rewriting system
* **Domain**: programming language semantics
* **Analysis mechanisms & automation**:
  * Automatically defines interpreters for a specified language
* **Success stories**: semantics for C, Java 1.4, EVM
* **UX (UI, documentation, community, tooling)**:
* **More details**:
* **URL**: https://kframework.org/

## Lean Prover

* **Modeling language**: dependently-typed lambda calculus
* **Domain**: general
* **Analysis mechanisms & automation**: interactive, with strong emphasis on programmable tactics backed by Z3
* **Success stories**:
* **UX (UI, documentation, community, tooling)**:
* **More details**:
* **URL**: https://leanprover.github.io/


## Move prover
* **Modeling language**: 
* **Domain**: smart contracts for the Libra blockchain
* **Analysis mechanisms & automation**: 
   * automation?
   * bytecode verifier that does semantics checks on the bytecode, uses boogie and Z3 in background
* **Success stories**:
* **UX (UI, documentation, community, tooling)**:
* **More details**:
* **URL**: https://research.fb.com/publications/the-move-prover/

## ProVerif

* **Modeling language**: applied Pi calculus
* **Domain**: security protocols in the symbolic (Dolev-Yao) model
* **Analysis mechanisms & automation**: 
   * protocols translated to Horn clauses with automated proof search
* **Success stories**: models of the Signal protocol, TLS 1.3 draft, parts of the Belenios voting system
* **UX (UI, documentation, community, tooling)**:
* **More details**:
* **URL**: https://prosecco.gforge.inria.fr/personal/bblanche/proverif/

* 
## PVS

* **Modeling language**: 
* **Domain**: 
* **Analysis mechanisms & automation**: 
* **Success stories**: 
* **UX (UI, documentation, community, tooling)**:
* **More details**:
* **URL**: https://pvs.csl.sri.com/

## Tamarin

* **Modeling language**: Rewrite rules to model the protocol, equational
  theories for specifying properties of primitives, trace-based execution and
  FOL to express properties
* **Domain**: security protocols in the symbolic (Dolev-Yao) model
* **Analysis mechanisms & automation**: 
   * a built-in Dolev-Yao adversary model
   * automated proof search with 
   * interactive proof search also supported
* **Success stories**: TLS 1.3 and Signal protocols
* **UX (UI, documentation, community, tooling)**:
  * a Web-based interface for proof search/construction
  * a manual is available
* **More details**:
* **URL**: http://tamarin-prover.github.io/

## TLA+

* **Modeling language**: First-order logic to define transition systems, LTL formulas to specify properties
* **Domain**: general (state machines), geared towards analysis of high-level designs
* **Analysis mechanisms & automation**: 
   * finite state model checker for restricted-size domains
   - TLA proof system for interactive proofs; proofs can also be done in Isabelle/HOL
* **Success stories**: 
   * the Paxos consensus protocol and its many variations
   * Amazon used it to check designs of their protocol
* **UX (UI, documentation, community, tooling)**:
  * there's a Java-based IDE that feels somewhat dated, and also a VSCode plugin is available (albeit with less functionality)
  * a free book is available, also a video course
* **More details**:
* **URL**: https://lamport.azurewebsites.net/tla/tla.html

## Viper

* **Modeling language**: 
* **Domain**:
* **Analysis mechanisms & automation**: 
* **Success stories**: 
* **UX (UI, documentation, community, tooling)**:
* **More details**:
* **URL**: https://www.pm.inf.ethz.ch/research/viper.html

## Z3 and new-Z/max-Z

* **Modeling language**: SMT with a number of theories (arithmetic, bit-vector, arrays)
* **Domain**: general
* **Analysis mechanisms & automation**: automated model finding
* **Success stories**: 
* **UX (UI, documentation, community, tooling)**:
* **More details**: often used as a background solver for many other tools
* **URL**: https://lamport.azurewebsites.net/tla/tla.html
