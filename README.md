# Haskell I/O Laziness Bug

This repository demonstrates a subtle bug in Haskell related to lazy evaluation and I/O operations.  The program may fail to print all output if interrupted before lazy I/O actions complete.

## Bug Description

The `bug.hs` file contains a Haskell program that reads user input and prints it back. It also includes a final `putStrLn` statement that might not be printed if the program is forcefully terminated. This is due to Haskell's lazy evaluation: the I/O action is only executed when its result is needed, and in the case of an interrupt, it might not be needed.

## Solution

The `bugSolution.hs` file provides a fix by using the `hFlush` function to force the output buffer to be flushed, ensuring that all pending output is printed before the program terminates.