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
Placeholder text.
# Detailed Code Examination
Placeholder text.
# Summary
Placeholder text.

