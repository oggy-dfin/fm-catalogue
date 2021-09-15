# Catalogue of Formal Verification Tools

This is a catalogue of various existing formal methods (formal verification) tools, with an eye towards applying them to software verification in an industrial setting.
We aim to use this catalogue at DFINITY to inform ourselves about tools and evaluate them for our needs.
We invite others to also use this list for reference and ask experts of different tools to help us improve it.
If a tool you know is not in the list, or has insufficient/wrong information, please send a PR!

We aim to collect the following information for every tool:

* **Short description**: How would you describe the tool in one sentence?
* **URL**: The official (or as official as possible) tool URL
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
* **Analysis mechanisms & automation**: Ultimately, the goal of the tool is to
  analyze a model of the system. The analysis can be fully automated, or can
  require a lot of manual input, or lie somewhere in between. Furthermore,
  there’s a number of standard analysis approaches: interactive tactic-based
  reasoning, SAT/SMT solving (often with some preprocessing), exhaustive finite
  state model checking, symbolic model checking, etc. If the tool uses such an
  approach, we note it here.
* **Success stories**: Notable verification efforts successfully completed using the tool.
  While subjective, we want to focus on verification of software and algorithms that have had real-world usage.
* **UX (UI, documentation, community, tooling)**: All things that influence the ergonomics of working with the tool.
* **Related tools and comparison**: Which tools are similar to this one? How do they compare? While comparisons 
  are always somewhat subjective, they are very helpful and we encourage you to post them if you are familiar
  with multiple similar tools. Links to comparison papers/blog posts/other resources are also welcome!
* **Limitations**: Does the tool have notable limitations relevant to its domain?
* **More details**: Anything relevant that's not covered by the above.


Also, we collect here other resources that compare different tools:

* [SOK: Computer-Aided Cryptography (2019)][1]
* [Seventeen Provers of the World (2006)][2]
* [QED at Large: A Survey of Engineering of Formally Verified Software (2020)][9]

## Agda

* **Short description**: Dependently typed programming language
* **URL**: https://wiki.portal.chalmers.se/agda/pmwiki.php
* **Modeling language**: dependently-typed lambda calculus 
* **Domain**: general, geared towards verified functional programs.
* **Abstraction level of models**:
* **Analysis mechanisms & automation**: 
* **Success stories**:
* **UX (UI, documentation, community, tooling)**:
* **Related tools and comparison**:
* **Limitations**:
* **More details**:

## Alloy

* **Short description**: Automated analyzer of high-level models
* **URL**: https://alloytools.org/
* **Modeling language**: First-order relational logic (no function symbols) with a transitive closure operator.
* **Domain**: general
* **Abstraction level of models**: "lightweight analysis" (high-level system/algorithm descriptions)
* **Analysis mechanisms & automation**: Fully automated, SAT-based model finder (KodKod) for models of user-defined sizes.
* **Success stories**:
    * [Found problems in Chord][3] (an influential distributed hash table algorithm)
* **UX (UI, documentation, community, tooling)**:
  * Multi-platform Java-based IDE for specifying and analyzing models
  * Docs: online tutorials and references, as well as a book
  * StackOverflow community (~500 questions as of Sep 2021)
* **Related tools and comparison**:
  * B, OCL, VDM and Z ([comparison][4])
  * TLA+ ([comparison][8] from 2016)
* **Limitations**:
* **More details**:


## Coq

* **Short description**: Interactive theorem prover
* **URL**: https://coq.inria.fr/
* **Modeling language**: dependently-typed lambda calculus
* **Domain**: general
* **Abstraction level of models**: any
* **Analysis mechanisms & automation**: 
    * interactive theorem proving with user-definable tactics (Ltac language to define tactics)
    * QuickCheck for finding counterexamples
* **Success stories**: 
  * CompCert, a formally verified optimizing C compiler (~100k lines of Coq code)
  * CertiKOS, a concurrent microkernel/hypervisor (~6500 lines of C and x86
    assembly)
  * FSCQ, a simple FUSE file system verified to be safe in the presence of crashes (~30k lines of Coq, extracted Haskell code)
* **UX (UI, documentation, community, tooling)**: 
    * Built-in IDE, and also integrations for VSCode, Emacs, and Vim
    * Several free books & courses available 
* **Related tools and comparison**: Isabelle, Agda, Idris
* **Limitations**:
* **More details**: supports code extraction to OCaml, Haskell and Scheme. Likely the best-known theorem prover.

## CryptoVerif

* **Short description**: Cryptographic protocol analyzer
* **URL**: https://prosecco.gforge.inria.fr/personal/bblanche/cryptoverif/
* **Modeling language**:
* **Domain**: crypto protocols in a computational model
* **Abstraction level of models**:
* **Analysis mechanisms & automation**: automated?
* **Success stories**: has been used to analyze protocol models of TLS 1.3,
  Signal, WireGuard
* **UX (UI, documentation, community, tooling)**:
* **Related tools and comparison**:
* **Limitations**:
* **More details**: has a notion of private channels.

## CT-Wasm

* **Short description**: Code analyzer
* **URL**: https://github.com/PLSysSec/ct-wasm
* **Modeling language**:
* **Domain**: enforcing constant-time behavior of Wasm programs
* **Abstraction level of models**:
* **Analysis mechanisms & automation**: 
* **Success stories**:
* **UX (UI, documentation, community, tooling)**:
* **Related tools and comparison**:
* **Limitations**:
* **More details**: available in the [crypto SoK][1]

## EasyCrypt

* **Short description**: Cryptographic protocol analyzer
* **URL**: https://www.easycrypt.info/
* **Modeling language**: cryptographic games
* **Domain**: crypto protocols in a computational model
* **Abstraction level of models**:
* **Analysis mechanisms & automation**:  automated?
* **Success stories**:
* **UX (UI, documentation, community, tooling)**:
* **Related tools and comparison**:
* **Limitations**:
* **More details**: close to pen-and-paper crypto proofs

## F*

* **Short description**: Dependently typed functional programming language
* **URL**: https://www.fstar-lang.org/
* **Modeling language**: dependently-typed lambda calculus (refinement types)
  with monadic effects
* **Domain**: general, geared towards verified functional programs
* **Abstraction level of models**:
* **Analysis mechanisms & automation**: a combination of manual and SMT-based
  proofs; does the user get feedback on proof progress/failed proofs?
* **Success stories**: 
  * miTLS, a verified implementation of TLS 1.3
  * LibSignal*, a verified implementation of the Signal protocol that compiles down to WebAssembly
* **UX (UI, documentation, community, tooling)**:
* **Related tools and comparison**:
* **Limitations**:
* **More details**: Supports program extraction to F#, OCaml, C, WASM and assembly.
  
## Idris

* **Short description**: Dependently typed functional programming language
* **URL**: https://www.idris-lang.org/
* **Modeling language**: dependently-typed lambda calculus
* **Domain**: general, geared towards verified functional programs
* **Abstraction level of models**:
* **Analysis mechanisms & automation**: interactive (with tactics)
* **Success stories**:
* **UX (UI, documentation, community, tooling)**:
* **Related tools and comparison**:
* **Limitations**:
* **More details**:

## Isabelle/HOL

* **Short description**: Interactive theorem prover
* **URL**: https://isabelle.in.tum.de/
* **Modeling language**: HOL (higher-order logic) with typeclasses
* **Domain**: general
* **Abstraction level of models**: any
* **Analysis mechanisms & automation**: 
  * interactive (with tactics, programmable in SML or using the Eisbach language)
  * Sledgehammer tool for automated proof generation using different backend
    solvers (e.g., Z3), Nitpick tool for counter-example search
* **Success stories**: 
  * [seL4 microkernel verification][5] (~10 kLoC of C code), verified information
    flow and other properties down to the binary code, initial formalization
    effort estimated at 30 person-years with 200 kLoC of proofs)
  * CoCon, a secure (against an information flow policy with declassification)
    scientific conference management system used for ITP 2016, code generated
    from a verified development
* **UX (UI, documentation, community, tooling)**:
  * IDEs for jEdit and VSCode (less functional than jEdit), with code completion/navigation on-par with most mainstream programming languages
  * Tutorials and books freely available
  * CLI tools for building theories, supporting caching and parallel proof checking
  * A large collection of existing developments: https://www.isa-afp.org/ 
  * An active mailing list, Stackoverflow
* **Related tools and comparison**: 
  * Other provers: Coq, HOL4, HOL Light
  * [An older comparison][2] (2006) to 16 other provers, math focused
  * A more recent (2019) [comparison to Coq][7] (math focused)
* **Limitations**:
* **More details**: supports code generation into OCaml, Haskell SML, and Scala.
  The structured proof language Isar makes maintenance of proofs easier compared
  to proofs based on just a sequence of tactic applications.

## K-framework

* **Short description**: Framework for programming language semantics and analysis
* **URL**: https://kframework.org/
* **Modeling language**: a term-rewriting system
* **Domain**: programming language semantics
* **Abstraction level of models**:
* **Analysis mechanisms & automation**:
  * Automatically defines interpreters for a specified language
* **Success stories**: semantics for C, Java 1.4, EVM
* **UX (UI, documentation, community, tooling)**:
* **Related tools and comparison**:
* **Limitations**:
* **More details**:

## Lean Prover

* **Short description**: Interactive theorem prover
* **URL**: https://leanprover.github.io/
* **Modeling language**: dependently-typed lambda calculus
* **Domain**: general
* **Abstraction level of models**:
* **Analysis mechanisms & automation**: interactive, with strong emphasis on programmable tactics backed by Z3
* **Success stories**:
* **UX (UI, documentation, community, tooling)**:
* **Related tools and comparison**:
* **Limitations**:
* **More details**:

## Move prover

* **Short description**: Verifier for smart contracts
* **URL**: https://research.fb.com/publications/the-move-prover/
* **Modeling language**:
* **Domain**: smart contracts for the Libra blockchain
* **Abstraction level of models**:
* **Analysis mechanisms & automation**: 
   * automation?
   * bytecode verifier that does semantics checks on the bytecode, uses boogie and Z3 in background
* **Success stories**:
* **UX (UI, documentation, community, tooling)**:
* **Related tools and comparison**:
* **Limitations**:

## ProVerif

* **Short description**: Security protocol verifier
* **URL**: https://prosecco.gforge.inria.fr/personal/bblanche/proverif/
* **Modeling language**: applied Pi calculus
* **Domain**: security protocols in the symbolic (Dolev-Yao) model
* **Abstraction level of models**: high-level protocol descriptions
* **Analysis mechanisms & automation**: 
   * protocols translated to Horn clauses with automated proof search
* **Success stories**: models of the Signal protocol, TLS 1.3 draft, parts of the Belenios voting system
* **UX (UI, documentation, community, tooling)**:
* **Related tools and comparison**: Tamarin
* **Limitations**:
* **More details**:

## PVS

* **Short description**: Interactive theorem prover
* **URL**: https://pvs.csl.sri.com/
* **Modeling language**: dependently-typed lambda calculus
* **Domain**: program analysis
* **Abstraction level of models**: any
* **Analysis mechanisms & automation**: Interactive with automation. Has a plugin system and built in tools for automating proofs.
* **Success stories**: byzantine fault tolerance, used by NASA in flight control systems
* **UX (UI, documentation, community, tooling)**: Emacs mode, VS Code integration for more user-friendly interaction
* **Related tools and comparison**: Coq, Isabelle, Lean
* **Limitations**:
  - It seems to require processes to terminate in order to model them.
  - Types need to be well-founded.
  - The type system language is distinct and more limited than the object language. This is due to its focus on program analysis,
    rather than mathematics.

## ACL2

* **Short description**: Interactive theorem prover
* **URL**: https://www.cs.utexas.edu/users/moore/acl2/
* **Modeling language**: Applicative subset of common lisp. Dynamically typed.
* **Domain**: program analysis
* **Abstraction level of models**: any
* **Analysis mechanisms & automation**: https://www.cs.utexas.edu/users/moore/acl2/
* **Success stories**: AMD microcode, used in microprocessor industry
* **UX (UI, documentation, community, tooling)**: Emacs mode
* **Related tools and comparison**: PVS
* **Limitations**:

## Tamarin

* **Short description**: Security protocol verifier
* **URL**: http://tamarin-prover.github.io/
* **Modeling language**: Rewrite rules to model the protocol, equational
  theories for specifying cryptographic primitives, trace-based execution and
  FOL to express properties
* **Domain**: security protocols in the symbolic (Dolev-Yao) model
* **Abstraction level of models**: Protocol logic
* **Analysis mechanisms & automation**: 
   * a built-in Dolev-Yao adversary model
   * automated proof search with 
   * interactive proof search also supported
* **Success stories**: TLS 1.3 and Signal protocols
* **UX (UI, documentation, community, tooling)**:
  * a Web-based interface for proof search/construction
  * a manual is available
* **Related tools and comparison**:
  * ProVerif:
  * Scyther: Tamarin is more expressive. 
* **Limitations**: No support for arithmetic 
* **More details**: Support for observational-equivalence properties (e.g., privacy).


## TLA+

* **Short description**: Analyzer of high-level models
* **URL**: https://lamport.azurewebsites.net/tla/tla.html
* **Modeling language**: First-order logic to define transition systems, LTL formulas to specify properties
* **Domain**: general (state machines)
* **Abstraction level of models**: high-level designs
* **Analysis mechanisms & automation**: 
   * finite state model checker for restricted-size domains
   - TLA proof system for interactive proofs; proofs can also be done in Isabelle/HOL
* **Success stories**: 
   * the Paxos consensus protocol and its many variations
   * Amazon used it to check designs of their protocol
* **UX (UI, documentation, community, tooling)**:
  * there's a Java-based IDE that feels somewhat dated, and also a VSCode plugin is available (albeit with less functionality)
  * a free book is available, also a video course
* **Related tools and comparison**:
* **Limitations**:
* **More details**:

## Viper

* **Short description**:
* **URL**: https://www.pm.inf.ethz.ch/research/viper.html
* **Modeling language**:
* **Domain**:
* **Abstraction level of models**:
* **Analysis mechanisms & automation**: 
* **Success stories**:
* **UX (UI, documentation, community, tooling)**:
* **Related tools and comparison**:
* **Limitations**:
* **More details**:

## Z3 and new-Z/max-Z

* **Short description**: SMT solver
* **URL**: https://lamport.azurewebsites.net/tla/tla.html
* **Modeling language**: SMT with a number of theories (arithmetic, bit-vector, arrays)
* **Domain**: SMT formulas
* **Abstraction level of models**:
* **Analysis mechanisms & automation**: automated model finding
* **Success stories**: 
* **UX (UI, documentation, community, tooling)**:
* **Related tools and comparison**:
* **Limitations**:
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

## Template

* **Short description**:
* **URL**:
* **Modeling language**:
* **Domain**:
* **Abstraction level of models**:
* **Analysis mechanisms & automation**: 
* **Success stories**:
* **UX (UI, documentation, community, tooling)**:
* **Related tools and comparison**:
* **Limitations**:
* **More details**:

