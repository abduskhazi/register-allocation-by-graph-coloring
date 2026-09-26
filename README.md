# Register Allocation by Graph Coloring

> A from-scratch **C implementation of register allocation using liveness analysis, interference graphs, graph coloring, and spilling**.

The project takes a high-level control-flow graph represented as basic blocks and quadruple instructions, determines which variables are simultaneously live, and uses that information to build a **register interference graph**.

```text
Instructions
     ↓
Control Flow Graph
     ↓
Liveness Analysis
     ↓
Interference Graph
     ↓
Graph Coloring
     ↓
Register Assignment
     ↓
Spilling (when required)
```

## Implementation

* Represents instructions as **quadruples** grouped into basic blocks.
* Propagates live variables through the control-flow graph.
* Builds a variable **interference matrix** from the liveness information.
* Uses a stack-based graph-coloring strategy to assign a limited number of registers.
* When coloring is insufficient, selects a variable for **spilling** and inserts `LOAD`/`STORE` operations, then repeats allocation.

## Files

```text
main.c                # Allocation pipeline
CFG.h                 # Control-flow / basic-block structures
algorithm.c            # Liveness and interference analysis
colour_allocation.c    # Graph coloring and register assignment
spilling.c             # Spill transformation
set.c / set.h          # Set implementation
input* / flow_matrix   # Example input
RIG.txt                # Generated interference graph
```

The project demonstrates the connection between **compiler data-flow analysis** and **graph algorithms**: variable lifetimes become graph constraints, and graph coloring turns those constraints into register assignments.
