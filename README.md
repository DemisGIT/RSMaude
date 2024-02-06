# Reactions Systems in Maude

Reaction Systems (RSs) are a computational framework inspired by the functioning of living cells and 
by biochemical reactions. Their constituents are a finite set of entities (a background set) and 
a finite set of reactions. Each reaction is a triple that consists of: 
1. a set of entities whose presence is needed to enable the reaction, called *reactants*;
2. a set of entities whose absence is needed to enable the reaction, called *inhibitors*;
3. a set of entities that are produced when the reaction takes place, called *products*.

All entities must be included in a fixed background set.
Applications of RSs are very general and range from the modeling of biological phenomena to molecular chemistry.
The classical behavior of RSs is defined as a rewriting system whose states are sets of entities (those produced at the previous step, possibly joined with others provided by an external context, thus modeling the interaction with the environment).

This repository includes an implementation of Reactions Systems in Maude that follows the approach described in the paper

> D. Ballis, L. Brodo, M. Falaschi - Modeling and Analyzing Reaction Systems in Maude

whose preliminary version can be found [here](https://users.dimi.uniud.it/~demis.ballis)

More specifically, it includes the following two Maude specificantions:

1. **RS-semantics.maude**: this specification provides an executable semantics for reaction systems that supports exploration and analysis of RSs.
2. **FWDslicer.maude**: this specification implements a forward slicing algorithm for RSs. Forward slicing is a powerful tool to detect (forward) causality and influence relations among the entities produced in a biological model. It shows how (parts of) an initial input affect the production of (parts of) the output and helps estimate which input data need to be modified to accomplish a change in the outcome.
Our methodology considers *closed* RSs, which are RSs where the environment provides a set of initial entities, and then proceeds with a computation which does not require further interactions with the environment. In our approach, the user must select a subset C0' of the initial state C0 of the RS, then our forward slicing algorithm produces a computation that encodes two reaction system processes that progress in parallel: the original process that stems from C0 and a secondary process (the sliced one) that originates from C0' ant that includes only the entities and reactions which are related to the partial input C0.
This way the two processes can be easily compared and some errors and/or causality patterns can be detected.

These Maude specifications can be executed either

- in the Maude system which can be downloaded at [https://maude.cs.illinois.edu/w/index.php/The_Maude_System](https://maude.cs.illinois.edu/w/index.php/The_Maude_System)

or

- in the ANIMA system ---a visual program explorer for Maude computations which is publicly available
at [https://safe-tools.dsic.upv.es/anima/](https://safe-tools.dsic.upv.es/anima/). In ANIMA, system biologists can stepwise explore the computation space
of a reaction system by expanding state transitions one at a time with a simple point-and-click interface, thereby producing an incremental visual representation
of the whole computation tree w.r.t. a given initial state. 
To reproduce the examples of a gene regulatory network and its forward slicing in ANIMA, please select
the preloaded examples GENE-REGULATION-RS and GENE-REGULATION-RS-FWD-SLICING, respectively. 
