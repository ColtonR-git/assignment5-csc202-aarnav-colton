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
Placeholder text.
# Summary
Placeholder text.

