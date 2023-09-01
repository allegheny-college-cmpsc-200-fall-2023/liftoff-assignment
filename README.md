# CMPSC 200: Liftoff

| Date              |          |
|:------------------|:---------|
| 1 September 2023 | Assigned  |
| 4 September 2023 | Due       |
| Status           | [![GatorGrader](../../actions/workflows/main.yml/badge.svg)](../../actions/workflows/main.yml) |

## Introduction

We're on our way into the world of the stored-program computer through using our `cardiac`s to develop
some simple programs. Given only a few simple instructions -- even one so reduced as that of the `cardiac`,
we can develop some pretty surprising, if not rudimentary, stuff. In this brief assignment, we look to the
stars to descend further into the underlying systems we're interested in studying. 

With some basic paperware, let's participate in a pyrotechnics display and launch some rockets. Our mission
control, like many, uses a `10`-count to give adequate warning to everyone involved. Your program should do
this in as few instructions as possible (time, in the world of rockets, isn't cheap).

![Flowchart for liftoff program](https://raw.githubusercontent.com/allegheny-college-cmpsc-200-fall-2023/liftoff-assignment/media/img/CMPSC%20200%20-%20Launch%20diagram.png)

(**NB**: The program does not need to actually launch the rocket.)

### Space camp

In order to get us suited up, there are a couple of programs to run through to demonstrate both `JMP` (Unconditional Jump)
and `TAC` (Test Accumulator Contents). Both contain required instructions that our rocket launching program needs. To graduate
from Space Camp, you need to complete:

* `looping.cardiac`: revise the original program to make use of `JMP` (opcode `8`)
* `breaking.cardiac`: implement the `TAC` instruction (opcode `3`)

#### `looping.cardiac`

You've been given a program that has a significant draw back. You'll be asked to discuss what it is in this assignment's documentation,
but you might want to run through it at least once to understand the program's purpose and what its (not quite _fatal_) flaw is. Your
task is to remedy what you find!

#### `breaking.cardiac`

Continuing our work with `JMP` _and_ elaborating on our adding machine, we've created a _variable input_ adding machine which adds any
list of `n` numbers until the number entered is `-1`. But, IT'S BROKEN! Your job? Fix it because Mission Control is pretty lazy.

**Note**: For simulators: the `DECK` is the input card; click `LOAD` after you've entered your data, start the program counter at the 
memory location where you've begun entering instructions and simulate away!

## Learning objectives

* describe and use elements of a simple, stored-program computer
* develop a loop-based program to iterate `10` times and halt (after which it launches our rocket)
* demonstrate fluency with CARDIAC opcodes and data "words"

## Reminder of the CARDIAC ISA

|Opcode|"Mnemonic"|Operation|
|:-----|:---------|:---------|
|`0`     |`INP`        |Read input card entry into memory |
|`1`     |`CLA`	       |Clear accumulator and add from memory (load) |
|`2`     |`ADD`        |Add from memory to ACC |
|`3`     |`TAC`        |Test ACC and jump if negative |
|`5`     |`OUT`        |Write memory location to output card |
|`6`     |`STO`        |Store ACC to memory |
|`7`     |`SUB`        |Subtract memory from ACC |
|`8`     |`JMP`        |Jump and save PC |
|`9`     |`HALT`       |Halt and reset |

## Instructions

To recieve credit for this assignment, write your program in the [liftoff.cardiac](src/liftoff.cardiac) file
in the `src` folder. Be sure to follow the convention of listing relevant `ADDRESS` register for the instruction,
followed by the `OPCODE` and target `ADDRESS` register for the command.

For example:

```
ADDRESS CONTENTS    COMMENTS
17      034         Read "A"
```

**Note**: You will work in pairs, but you should submit _your own assignment_ (including "training" programs)

### Assignment "Hacks"

See the `Suggestion` below to challenge yourself to implement a Hack. As always, you are allowed to develop
your own Hack to satisfy this stretch goal. Place the code for the Hack inline with the code you write to 
create the liftoff sequence program (i.e. make it part of the program).

In order to recieve credit for the Hack, you must fill out the [hack.md](docs/hack.md) file located in the
`docs` folder.

#### Suggestion

Make the program print the word "LIFTOFF" using the decimal letter representations from the 
[ASCII Table](https://www.ascii-code.com/). This Hack is case-sensitive.

**HINT**: To do this _may_ involve "bootstrapping" (refer to our conversation about Memory Unit `00`); you _can_ 
pre-load data into the CARDIAC for later use during computation.

#### Make it your own

You are free to develop your own "Hack" for this assignment, provided that it elaborates on the liftoff
countdown counter we're developing this week.

### Working outside of class

To finish developing these programs, you may need to use the [CARDIAC simulator](https://www.cs.drexel.edu/~bls96/museum/cardsim.html).
This simulator works slightly differently than our physical CARDIAC unit, but follows the same opcodes, rules, and general principles.
Some notes about using the simulator:

* In the `CPU` section, the `PC` value simulates where you put the "bug" in the CARDIAC Memory Unit
* The buttons at the bottom allow you to `Run` or `Step` through the program; I suggest `Step` as it executes instruction-by-instruction
* `Reset` resets the current stored program; `Clear` erases programs stored in the `Memory` section

**Note**: The simulator is laid out differently than the CARDIAC and it does't have input strips (the `Deck` is a way to implement other
folks' programs relatively quickly from a list of instructions). As such, if you're developing outside of class, your solutions may be
different in at least one significant way: you'll have to pre-load (i.e. "bootstrap") the values you want to store somewhere in memory.
This means that you likely _won't use_ the `INP` instruction (opcode `0`) in simulated code.
