# ADR-0001: TypeScript Toolchain Selection

**Status**: Accepted
**Date**: 2026-02-09
**Deciders**: Strict Guardian, User

## Context and Problem Statement
We need a standardized, strict, and performant toolchain for JavaScript/TypeScript development to ensure code quality, consistency, and reliability across all projects.

## Decision
We have decided to use the following stack:
1.  **Language**: TypeScript (Strict Mode)
2.  **Linting**: ESLint
3.  **Formatting**: Prettier
4.  **Testing**: Vitest + Testing Library

## Rationale
### TypeScript
- **Why**: Provides static typing, which is our "First Line of Defense" in the Testing Trophy. Captures bugs at compile time.
- **Alternatives**: JavaScript (Rejected: Too error-prone), JSDoc (Rejected: Less ergonomic validation).

### ESLint
- **Why**: The industry standard for static analysis. Its ecosystem of plugins (especially `@typescript-eslint`) allows us to enforce correctness (e.g., specific hook usage in React) that compilers miss.
- **Alternatives**: Biome (Rejected: Ecosystem not yet mature enough for our strict needs).

### Prettier
- **Why**: "An opinionated code formatter". We value consistency over debate. It removes all mental overhead regarding style.
- **Alternatives**: ESLint formatting rules (Rejected: Slower, conflicts with logic rules).

### Vitest
- **Why**: Native Vite support, faster than Jest, ESM-first.
- **Alternatives**: Jest (Rejected: Configuration overhead for modern TS/ESM is too high).

## Consequences
- **Positive**: Zero configuration debates for new projects. Logic errors caught early.
- **Negative**: Initial setup complexity (mitigated by `new-project` workflow).
