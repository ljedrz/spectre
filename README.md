# Spectre

[![crates.io](https://img.shields.io/crates/v/spectre)](https://crates.io/crates/spectre)
[![docs.rs](https://docs.rs/spectre/badge.svg)](https://docs.rs/spectre)

In French, the spectrum of a matrix is called "spectre".

This micro-library contains a small toolkit helpful in analysing network topologies. Namely:
- Degree, adjacency and Laplacian matrices for a graph.
- Various centrality measures for a graph.
- The algebraic connectivity of a graph (Fiedler).

## Basic usage

The library is centered around the [`Graph`](graph::Graph) structure which can be constructed
from one or more [`Edge`](edge::Edge) instances. Once constructed, various measurements and
matrix representations of the graph can be computed.

```rust
use spectre::edge::Edge;
use spectre::graph::Graph;

// Construct the graph instance.
let mut graph = Graph::new();

// Insert some edges, note the IDs can be any type that is `Copy + Eq + Hash + Ord`.
graph.insert(Edge::new("a", "b"));
graph.insert(Edge::new("a", "c"));

// Compute some metrics on that state of the graph.
let density = graph.density();
let degree_centrality_delta = graph.degree_centrality_delta();

// Matrices can be pretty printed...
println!("{}", graph.laplacian_matrix());
// ...outputs:
//
//  ┌          ┐
//  │  2 -1 -1 │
//  │ -1  1  0 │
//  │ -1  0  1 │
//  └          ┘
```
