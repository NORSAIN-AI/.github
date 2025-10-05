# Contributing to NORSAIN Projects

Thank you for your interest in contributing to NORSAIN! This document provides guidelines and best practices for contributing to our repositories.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [How to Contribute](#how-to-contribute)
- [Development Workflow](#development-workflow)
- [Coding Standards](#coding-standards)
- [Commit Messages](#commit-messages)
- [Pull Request Process](#pull-request-process)
- [Reporting Bugs](#reporting-bugs)
- [Suggesting Features](#suggesting-features)

## Code of Conduct

This project adheres to the [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to the project maintainers.

## Getting Started

1. **Fork the repository** - Create your own fork of the repository
2. **Clone your fork** - `git clone https://github.com/YOUR_USERNAME/REPO_NAME.git`
3. **Create a branch** - `git checkout -b feature/your-feature-name`
4. **Set up the development environment** - Follow the README instructions

## How to Contribute

### Types of Contributions

We welcome various types of contributions:

- 🐛 **Bug fixes** - Fix issues in existing code
- ✨ **New features** - Add new functionality
- 📝 **Documentation** - Improve or add documentation
- ✅ **Tests** - Add or improve test coverage
- ♻️ **Refactoring** - Improve code quality and structure
- ⚡ **Performance** - Optimize performance

### Before You Start

- Check existing [issues](../../issues) and [pull requests](../../pulls) to avoid duplicates
- For major changes, open an issue first to discuss your proposal
- Make sure you understand the project's architecture and conventions

## Development Workflow

1. **Update your fork** regularly from the main repository:
   ```bash
   git remote add upstream https://github.com/NORSAIN-AI/REPO_NAME.git
   git fetch upstream
   git merge upstream/main
   ```

2. **Create a feature branch** from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Make your changes** following the coding standards

4. **Test your changes** thoroughly:
   - Run existing tests: Check repository-specific test commands
   - Add new tests for new functionality
   - Ensure all tests pass

5. **Commit your changes** with clear, descriptive messages

6. **Push to your fork**:
   ```bash
   git push origin feature/your-feature-name
   ```

7. **Open a Pull Request** using the provided template

## Coding Standards

### General Guidelines

- Write clean, readable, and maintainable code
- Follow the language-specific style guides
- Keep functions small and focused on a single responsibility
- Use meaningful variable and function names
- Add comments for complex logic
- Avoid duplication (DRY principle)

### Language-Specific Standards

- **Python**: Follow [PEP 8](https://pep8.org/)
- **JavaScript/TypeScript**: Follow [Airbnb Style Guide](https://github.com/airbnb/javascript)
- **Go**: Follow [Effective Go](https://golang.org/doc/effective_go.html)
- **Other languages**: Follow community-accepted standards

### Documentation

- Document all public APIs
- Include examples in documentation
- Keep README files up to date
- Add inline comments for complex algorithms

## Commit Messages

Write clear and meaningful commit messages following these guidelines:

### Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, missing semicolons, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks
- `perf`: Performance improvements
- `ci`: CI/CD changes

### Examples

```bash
feat(auth): add OAuth2 authentication support

Implement OAuth2 authentication flow with support for
multiple providers including Google and GitHub.

Fixes #123
```

```bash
fix(api): resolve null pointer exception in user service

Add null checks before accessing user properties to prevent
crashes when user data is incomplete.

Closes #456
```

## Pull Request Process

1. **Use the PR template** - Fill out all sections of the pull request template
2. **Link related issues** - Reference any related issues
3. **Ensure tests pass** - All CI checks must pass
4. **Request review** - Tag relevant maintainers for review
5. **Address feedback** - Respond to review comments and make necessary changes
6. **Keep it updated** - Rebase on main if needed to resolve conflicts
7. **Be patient** - Reviews may take time, especially for large changes

### PR Checklist

- [ ] Code follows project style guidelines
- [ ] Self-review completed
- [ ] Comments added for complex code
- [ ] Documentation updated
- [ ] Tests added/updated
- [ ] All tests pass
- [ ] No new warnings introduced

## Reporting Bugs

Use the [Bug Report template](../../issues/new?template=bug_report.yml) and include:

- Clear description of the bug
- Steps to reproduce
- Expected vs. actual behavior
- Environment details
- Relevant logs or screenshots

## Suggesting Features

Use the [Feature Request template](../../issues/new?template=feature_request.yml) and include:

- Problem statement
- Proposed solution
- Alternative approaches considered
- Benefits to users
- Any relevant examples or mockups

## Questions?

If you have questions about contributing, feel free to:

- Open a [discussion](https://github.com/orgs/NORSAIN-AI/discussions)
- Reach out to maintainers
- Check existing documentation

## License

By contributing, you agree that your contributions will be licensed under the same license as the project (see [LICENSE](LICENSE) file).

---

Thank you for contributing to NORSAIN! 🎉
