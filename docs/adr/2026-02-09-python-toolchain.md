# ADR-0002: Python Toolchain Selection

**Status**: Accepted
**Date**: 2026-02-09
**Deciders**: Strict Guardian, User

## Context and Problem Statement
Python's dynamic nature makes large codebases prone to runtime errors. We need a strict static analysis toolchain to bring "Strict Guardian" safety to Python development.

## Decision
We have decided to use the following stack:
1.  **Type Checking**: Mypy
2.  **Linting**: Ruff
3.  **Formatting**: Black
4.  **Testing**: Pytest

## Rationale
### Mypy
- **Why**: The reference implementation of Python static typing. Most mature ecosystem support.
- **Alternatives**: Pyright (Rejected: Mypy is more standard for CI/CD pipelines, though Pyright is great for editors).

### Ruff
- **Why**: Written in Rust. Extremely fast (10-100x faster than competitors). Replaces Flake8, Isort, and Pylint in one tool.
- **Alternatives**: Flake8 (Rejected: Too slow), Pylint (Rejected: Too slow and noisy).

### Black
- **Why**: Deterministic formatting. "The Uncompromising Code Formatter". Ensures identical output regardless of who writes the code.
- **Alternatives**: YAPF, Autopep8 (Rejected: Too configurable, leads to debates).

### Pytest
- **Why**: Standard testing framework. Functional style (fixtures) is superior to class-based `unittest` for integration testing.
- **Alternatives**: Unittest (Rejected: Java-style verbosity).

## Consequences
- **Positive**: Python code becomes as reliable as TypeScript code. Fast feedback loop due to Ruff.
- **Negative**: Requires strict discipline with Type Hints (`typing` module).
