# ZK Whiteboard Sessions

This includes some notes I took from watching [ZK Whiteboard Sessions](https://www.youtube.com/playlist?list=PLj80z0cJm8QErn3akRcqvxUsyXWC81OGq) playlist. It is mainly a list of building blocks.



## My progress

- [x]  **Module 1: What is a SNARK? by Dan Boneh**

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

- Zero knowledge definition: (informally) is zk if verifier can generate (an indistinguishable) proof by itself. "by itself" = "using a simulator".


### [x] Module 2: Building a SNARK, pt 1 by Dan Boneh

- General paradigm for SNARK:
1. Functional commitment scheme (commit to a function: polynomial, multilinear, linear)
2. Interactive oracle proof (IOP)

#### PCS (Polynomial Commitment Scheme)

Commit to univeriate polynomial f -> (later) prove that v = f(u) for public u, v.

Examples:
- Ellipctic curves: Bulletproofs (verifier is linear in d)
- Bilinear groups: KZG10 (trusted setup), Dory20
- Groups of unknown order: Dark20
- Hash functions: based on FRI

##### KZG (Kate-Zaverucha-Goldberg 2010)

```
Setup:
- Sample alpha
- pp = {H0 = G, ...,Hd = alpha^d * G}, where G is the generator
- delete alpha (trusted setup)

Commit(pp, f) -> com_f := f(alpha) * G

Minute: 30
```

Note: Dory does not need trusted setup (transparent)


#### Polynomial IOP

Let C(x, w) be some arithmetic circuit. 

Poly-IOP: A proof system that proves that there exists w such that C(x,w)=0 in a very specific way:

- Verifier sends a bunch of random values r_i.
- Prover commits to a bunch of polynomials.
- Verifier checks polynomial evaluations at his choosing.

#### SNARK

(t, q) Poly-IOP: 

- t: nr polynomials committed during the interactive phase
- q: nr evaluation queries during the verification procedure at the end of the proof

Usually: t,q < 4

The Snark:
- Prover: sends t poly commitments
- During poly-IOP verify:run PCS eval protocol q times
- Use Fiat-Shamir to be non-interactive



### [x] Module 3: Building a SNARK, pt 2 by Dan Boneh

#### Polynomial IOP:

H = {1, w, w^2, ..., w^(k-1)} where w is a k-th root of unity 

- Proof gadgets:
1. Zero-test: f is identically zero on H
2. Sum-check: 

```math
\sum_{a\in H} f(a) = b
```
3. Prod-check:
```math
\Pi_{a\in H} f(a) = c
```

#### Plonk (poly-IOP for general circuit)

- Create a computation trace
- Encode the computation trace with PCS

Extensions: PLONKUP: handle circuits with more general gates than + and x (use lookup tables)


### [x] Module 4: SNARKs vs STARKs with Bobbin Threadbare


### [x] Module 5: PLONK and Custom Gates with Adrian Hamelink


### [x] Module 6: Lookup Tables for Performance Optimisation


### [x] Module 7: Zero Knowledge Virtual Machines (zkVM) with grjte






