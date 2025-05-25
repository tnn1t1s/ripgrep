# Ripgrep Code Structure Analysis

## Overview

**Ripgrep** is a fast line-oriented search tool written in Rust, organized as a workspace with multiple specialized crates.

## Core Architecture (9 main crates):

1. **`core`** - Main entry point (`main.rs`) containing CLI logic, flag parsing, and search orchestration
2. **`grep`** - High-level library facade that re-exports all the core searching components
3. **`searcher`** - Core search engine responsible for reading bytes, applying matchers, and managing search execution
4. **`matcher`** - Trait definitions for pattern matching (regex interface abstraction)
5. **`regex`** - Rust regex engine implementation of the matcher trait
6. **`pcre2`** - Optional PCRE2 regex engine implementation for advanced patterns
7. **`printer`** - Output formatting (JSON, standard grep-like output, colors, etc.)
8. **`ignore`** - Git/ignore file handling and directory traversal logic
9. **`globset`** - Efficient glob pattern matching for file filtering
10. **`cli`** - CLI utilities (decompression, escaping, process management)

## Key Design Patterns:

- **Trait-based architecture**: `Matcher` trait allows pluggable regex engines
- **Sink pattern**: `Sink` trait handles output formatting and result processing  
- **Builder pattern**: `SearcherBuilder` for configurable search setup
- **Performance-focused**: Memory mapping, SIMD optimizations, parallel directory walking

## Performance Features:
- Built on Rust's fast regex engine with finite automata
- Lock-free parallel directory iteration
- Automatic memory mapping vs buffered reading strategy
- RegexSet for efficient ignore pattern matching
- Optional jemalloc for MUSL builds

## Architecture Summary

The architecture cleanly separates concerns: file traversal (`ignore`), pattern matching (`matcher`/`regex`/`pcre2`), search execution (`searcher`), and output formatting (`printer`), making it highly modular and performant.