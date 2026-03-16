# Midterm Lab 2 - Brief Report

## Overview
This project implements a shortest-path route visualizer for a small directed road network using Python. The application supports three optimization metrics:
- distance
- time
- fuel

It provides both:
- GUI mode (default)
- CLI mode (`--cli`)

## Algorithm Approach
The core pathfinding method is Dijkstra's algorithm.

### 1. Graph Representation
- The graph is stored as an adjacency list.
- Each directed edge contains three weights:
  - `D` for distance
  - `T` for time
  - `F` for fuel
- Input one-way edge rows are expanded into bidirectional edges with the same values.

### 2. Metric-Based Optimization
- The selected metric from the dropdown (or CLI argument) decides the primary objective:
  - `distance -> D`
  - `time -> T`
  - `fuel -> F`

### 3. Deterministic Tie-Breaking
When multiple candidate paths have equal primary metric totals, a deterministic rank tuple is used:
1. selected metric total
2. secondary totals in fixed order
3. fewer hops
4. lexicographically smaller path

This makes outputs stable and repeatable across runs.

### 4. Result Aggregation
After the shortest path is selected:
- Total distance, time, and fuel are computed along the chosen path.
- The GUI highlights the route and can animate traversal.
- A popup can show a detailed route summary.

## Time and Space Notes
For a graph with `V` nodes and `E` edges, Dijkstra with a binary heap runs in approximately:
- Time: `O((V + E) log V)`
- Space: `O(V + E)`

## Challenges Faced During Assignment

• Correct visulization of nodes in the node path showing overlaps or unclean paths
• UI Layout of the program increasing efficiency
• Tons of unecessary buttons reducing effiency and clarity