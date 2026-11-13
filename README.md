# Algorithm Battle: Which Data Structure Wins?

Student record search (by Student ID) comparing three data structures in C++:
**Binary Search Tree (BST)**, **AVL Tree**, and a **Hash Table with Linear Probing**.

- Course: 21CS201J - Data Structures and Algorithms (CLA-2, Task 3)
- Institution: SRM Institute of Science and Technology, Tiruchirappalli
- Author (per source header): Syed Saalim, RA2511026050149

## Overview

All three structures are built from the same 40-record dataset, inserted in the
same order. The program then measures how many key comparisons (or slots
examined) each one needs for searching and inserting, so the structures can be
compared fairly.

Each record is a `Book` struct holding `id` (Student ID), `title` (student name)
and `author` (department).

## Implementations

| Structure | Key details |
|-----------|-------------|
| BST | Plain unbalanced insert/search, can degrade towards a linked list |
| AVL | Self-balancing via LL, RR, LR and RL rotations; rotations are counted |
| Hash table | Size 61 (prime), `hash(id) = id % 61`, linear probing, collisions tracked |

## What the Program Does

1. Builds the BST, AVL tree and hash table from the 40 records.
2. Prints inorder, preorder and postorder traversals of the BST and AVL tree.
3. Runs experiments:
   - Successful search: every stored key (average and max comparisons)
   - Unsuccessful search: 10 keys not in the dataset
   - Insertion cost: the initial 40 records, then 5 extra keys
     (3004, 3016, 3052, 3070, 3095)
4. Prints a comparison table (Part C - Observations) with:
   - Average and max comparisons for each experiment
   - Tree heights after the initial build and after the extra inserts
   - AVL rotation counts (build / total)
   - Hash collisions (total extra probes and insertions that collided)
5. Prints the theoretical reference (log2(40) ~ 5.3 levels) and the final hash
   load factor.
6. Starts **Technical Defense Mode**: enter a Student ID to see, for each
   structure, whether it was found and how many comparisons or probes it took.
   Enter `0` to exit.

## Build and Run

Requires a C++11 (or newer) compiler.

```bash
g++ -std=c++11 -o algorithm_battle main.cpp
./algorithm_battle
