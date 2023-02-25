# ZK Whiteboard Sessions

This includes some notes I took from watching [ZK Whiteboard Sessions](https://www.youtube.com/playlist?list=PLj80z0cJm8QErn3akRcqvxUsyXWC81OGq) playlist. It is mainly a list of building blocks.



## My progress

- [x]  ** Module 1: What is a SNARK? by Dan Boneh **

- SNARK: the proof is "short" (log(lenght of circuit)) and "fast" to verify
- Usecases: Zcash, Tornado cash, IronFish, Aleo (Private Dapps).
- Preprocessing: S(C,r) -> (Sp, Sv) for prover and verifier. Sv: short "summary" of circuit
- Types of preprocessing setup:
1. Trusted setup per circuit: in S(C,r), r must be kept from prover. (Groth16)
2. Trusted but universal (updatable) setup: r is independent of C. (Plonk/Marlin)
3. Transparent setup: S(C) does not use secret data (no trusted setup). (Bulletproofs, STARK, DARK) => higher proof size

DSL program:
- Circom
- ZoKrates
- Leo
- Zinc
- Cairo
- Noir

SNARK friendly format:
- R1CS
- AIR
- Plonk-CG
- PIL



### [x] Module 2: Building a SNARK, pt 1 by Dan Boneh


### [x] Module 3: Building a SNARK, pt 2 by Dan Boneh


### [x] Module 4: SNARKs vs STARKs with Bobbin Threadbare


### [x] Module 5: PLONK and Custom Gates with Adrian Hamelink


### [x] Module 6: Lookup Tables for Performance Optimisation


### [x] Module 7: Zero Knowledge Virtual Machines (zkVM) with grjte






