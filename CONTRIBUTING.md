# Contributing to AISDK

Thank you for your interest in contributing to AISDK! This document provides guidelines and instructions for contributing.

## Code of Conduct

By participating in this project, you agree to maintain a respectful and inclusive environment for everyone.

## How to Contribute

### Reporting Bugs

1. **Check existing issues** - Search [open issues](../../issues) to avoid duplicates
2. **Create a new issue** - Use the bug report template
3. **Provide details:**
   - SDK version
   - Swift version
   - macOS/iOS version
   - Steps to reproduce
   - Expected vs actual behavior
   - Code samples if applicable

### Suggesting Features

1. **Check existing requests** - Search issues with the `enhancement` label
2. **Create a feature request** - Use the feature request template
3. **Explain the use case** - Why would this benefit users?

### Contributing Code

#### First Time Contributors

1. Fork the repository
2. Clone your fork locally
3. Create a new branch from `main`

```bash
git clone https://github.com/YOUR_USERNAME/AISDK.git
cd AISDK
git checkout -b feature/your-feature-name
```

#### Development Setup

1. **Requirements:**
   - Xcode 15.0+
   - Swift 5.9+
   - macOS 13+

2. **Open the package:**
   ```bash
   open Package.swift
   ```

3. **Run tests:**
   ```bash
   swift test
   ```

#### Making Changes

1. **Follow Swift conventions:**
   - Use Swift API Design Guidelines
   - Keep code readable and documented
   - Add tests for new functionality

2. **Commit guidelines:**
   - Use clear, descriptive commit messages
   - Keep commits focused and atomic
   - Format: `type: short description`

   Types: `feat`, `fix`, `docs`, `test`, `refactor`, `chore`

   Examples:
   ```
   feat: add streaming support for Claude API
   fix: handle timeout errors in OllamaProvider
   docs: update README with usage examples
   ```

3. **Before submitting:**
   - Run all tests: `swift test`
   - Check for warnings
   - Update documentation if needed

#### Pull Request Process

1. **Create a PR** against the `main` branch
2. **Fill out the PR template** completely
3. **Wait for review** - maintainers will review within a few days
4. **Address feedback** - make requested changes
5. **Merge** - maintainers will merge once approved

### PR Requirements

- [ ] Tests pass locally
- [ ] New code has test coverage
- [ ] Documentation updated (if applicable)
- [ ] No breaking changes (or clearly documented)
- [ ] Follows existing code style

## Branching Strategy

| Branch | Purpose |
|--------|---------|
| `main` | Stable, release-ready code |
| `develop` | Integration branch for features |
| `feature/*` | New features |
| `fix/*` | Bug fixes |
| `release/*` | Release preparation |

## Testing

- Write unit tests for all new functionality
- Maintain existing test coverage
- Test with both cloud and local AI providers if applicable

```bash
# Run all tests
swift test

# Run specific test
swift test --filter AISDKTests.ClaudeProviderTests
```

## Documentation

- Add inline documentation for public APIs
- Update README.md for user-facing changes
- Include code examples where helpful

## Questions?

- Open a [Discussion](../../discussions) for questions
- Tag issues with `question` label

## Recognition

Contributors will be recognized in:
- Release notes
- Contributors list

Thank you for helping make AISDK better!
