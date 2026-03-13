Assignment 5
=========
# Team Members:
- Aarnav
- Colton 
# Expected Data Structures
A dictionary (hash table) would likely be the most important structure. It could map filenames to sets of executed line numbers. This allows quick lookup and updates while a program runs. For example, each time a line executes, the tester could add that line number to a set associated with the file.

A set would be useful for storing executed line numbers without duplicates. Since a line might execute many times in loops, using a set ensures each line is recorded only once.

A list or array might be used to store tokens or lines of code when analyzing a source file. This helps reconstruct the structure of the program.

Additionally, trees or graph-like structures might appear when analyzing Python’s abstract syntax tree (AST) to detect functions or code regions. These structures allow the coverage tool to understand code structure rather than just individual lines.

Together, these data structures help efficiently record, analyze, and report which parts of a program were executed.
# Initial Code Examination
The coverage.py project contains several directories including coverage, tests, doc, and ci. The coverage directory contains the main implementation of the coverage tool, while the tests directory contains automated tests that verify the tool’s correctness. The project also includes documentation files such as CHANGES.rst, CONTRIBUTORS.txt, and configuration files for development tools.

Using a line counting tool shows that the project is fairly large. The main implementation code in the coverage directory contains roughly 16,000 lines, while the tests directory contains about 28,000 lines of test code. This indicates that the project has a very large and thorough test suite.

We examined two test files:

test_templite.py :
This file tests the Templite class used by coverage.py. It verifies that template rendering works correctly and that errors such as syntax problems are properly detected.

tests/zipsrc/zip1/init.py :
This file is mostly empty and serves as part of a test package used to verify how coverage handles zipped Python modules.

We also examined five files from the coverage directory:

phystokens.py :
This file handles tokenizing Python source code. It wraps Python’s tokenizer to ensure physical tokens, including line continuations, are properly captured.

annotate.py :
This module generates annotated source files that display which lines were executed during testing.

files.py :
This module handles file path processing and normalization. It includes utilities for managing filenames and resolving relative paths.

regions.py :
This file analyzes Python source code using the AST to detect regions such as functions and classes.

pytracer.py :
This module implements the tracer that collects execution data as a program runs.

Overall, the code itself is generally more informative than comments, although comments help clarify complex parts of the implementation.
# Detailed Code Examination
One interesting file that uses data structures extensively is regions.py, which identifies functions and classes within Python source code.

The module uses Python’s AST (Abstract Syntax Tree) to analyze the structure of a program. The key class in this file is RegionFinder, which traverses the AST to identify code regions.

A central data structure used here is a list of regions, stored in self.regions. Each element represents a code region such as a function or class. These are stored using a CodeRegion object.

Another important data structure is the Context dataclass, which contains three fields:

name – the name of the function or class

kind – whether it is a function or class

lines – a set of line numbers belonging to that region

The lines field uses a set of integers to track which lines belong to that code region. Using a set ensures fast lookup and avoids duplicates.

The RegionFinder also maintains a stack-like list called context. This tracks the nested structure of code while the AST is being traversed. For example, when the visitor enters a function definition, a new context is pushed onto the list, and when leaving it, the context is popped. This behaves similarly to a stack and allows the program to keep track of nested scopes.

The flow of data is as follows:

Python source code is parsed into an AST.

RegionFinder walks the AST nodes.

As functions or classes are encountered, new contexts are created.

Line numbers are collected into sets.

Completed regions are stored in the regions list.

These data structures allow coverage.py to understand the structural organization of code so it can report coverage information for specific functions and classes.
# Summary
Overall, the code in coverage.py seems well organized and fairly readable, especially considering how large the project is. The code is split into different modules that each handle a specific task, which makes it easier to understand how the system works. For example, some modules focus on tracking which lines of code run during execution, while others deal with file handling or generating reports about coverage results.
Most of the functions also have clear and descriptive names, which makes the code easier to follow. The comments are mainly used to explain more complicated sections of the code instead of repeating what the code already says. This helps keep the files cleaner while still making the logic understandable.

Another thing we noticed is that the project has a very large test suite. There are actually more lines of testing code than implementation code. This suggests that the developers place a strong emphasis on making sure the software works correctly and continues to work as changes are made.

Compared to the kind of code we usually write in our own projects, this codebase is much more modular and structured. Different pieces of functionality are separated into helper modules and organized in a clear way. Even though some parts of the code are complicated, the overall structure makes it seem maintainable. With enough time to understand the project structure, we think it would be possible to work on or update this code without too much difficulty.
