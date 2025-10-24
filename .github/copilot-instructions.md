# AI Agent Instructions for setup-node

This document provides essential guidance for AI agents working with the setup-node GitHub Action codebase.

## Project Overview
- This is a GitHub Action that sets up Node.js environments in GitHub Actions workflows
- Primary functionality includes Node.js installation, dependency caching, and registry authentication
- Written in TypeScript, targeting Node.js 24+

## Key Architecture Points
1. Core Components:
   - Main action entry: `src/setup-node.ts`
   - Cache functionality: `src/cache-save.ts`
   - Uses `@actions/*` packages for core GitHub Actions functionality

2. Important Patterns:
   - Semantic versioning for Node.js version resolution (`semver` package)
   - Caching strategy using `@actions/cache` for package manager data
   - Registry authentication handling for npm, yarn, and pnpm

## Development Workflow
```bash
# Standard development commands
npm run build          # Builds the action using ncc
npm run test          # Runs jest tests
npm run pre-checkin   # Format, lint, build and test
```

## Critical Conventions
1. Versioning:
   - Follows semantic versioning strictly
   - Supports various version spec formats (e.g., `12.x`, `lts/*`, `latest`)

2. Caching:
   - Automatic caching for npm when package.json contains appropriate fields
   - Manual cache configuration required for yarn/pnpm
   - Uses `cache-dependency-path` for monorepo support

3. Testing:
   - Jest for unit tests
   - Use `jest-circus` as test runner
   - Mock `@actions/*` packages in tests

## Security Considerations
- Token handling for GitHub Enterprise Server
- Package manager authentication
- Rate limiting concerns for Node.js downloads

## Key Files
- `action.yml`: Action metadata and input definitions
- `src/setup-node.ts`: Core setup logic
- `src/cache-save.ts`: Package manager caching
- `__tests__/`: Test files demonstrating expected behavior

For detailed API documentation and examples, refer to README.md and docs/advanced-usage.md