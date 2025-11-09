# Contributing to NORSAIN-AI

Thank you for your interest in contributing to NORSAIN-AI! We welcome contributions from the community and are grateful for your support. 🙏

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [How to Contribute](#how-to-contribute)
- [Development Workflow](#development-workflow)
- [Coding Standards](#coding-standards)
- [Commit Convention](#commit-convention)
- [Pull Request Process](#pull-request-process)
- [Reporting Bugs](#reporting-bugs)
- [Feature Requests](#feature-requests)
- [Community](#community)

## Code of Conduct

By participating in this project, you agree to abide by our Code of Conduct. Please be respectful and considerate in all interactions.

## Getting Started

1. **Fork the repository** to your GitHub account
2. **Clone your fork** to your local machine:
   ```bash
   git clone https://github.com/YOUR-USERNAME/REPO-NAME.git
   cd REPO-NAME
   ```
3. **Add upstream remote**:
   ```bash
   git remote add upstream https://github.com/NORSAIN-AI/REPO-NAME.git
   ```
4. **Install dependencies** (varies by project):
   ```bash
   npm install  # for Node.js projects
   # or
   pip install -r requirements.txt  # for Python projects
   ```

## How to Contribute

### Types of Contributions

We appreciate all types of contributions:

- 🐛 **Bug fixes**
- ✨ **New features**
- 📝 **Documentation improvements**
- ✅ **Test coverage**
- 🔧 **Code refactoring**
- 🎨 **UI/UX improvements**
- 🌐 **Translations**

## Development Workflow

1. **Create a new branch** for your changes:
   ```bash
   git checkout -b feat/your-feature-name
   # or
   git checkout -b fix/your-bug-fix
   ```

2. **Make your changes** following our coding standards

3. **Test your changes**:
   ```bash
   npm test  # or appropriate test command
   ```

4. **Commit your changes** using conventional commits:
   ```bash
   git commit -m "feat: add new feature"
   ```

5. **Keep your branch up to date**:
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

6. **Push to your fork**:
   ```bash
   git push origin feat/your-feature-name
   ```

7. **Open a Pull Request** on GitHub

## Coding Standards

### General Guidelines

- Write clear, readable, and maintainable code
- Follow the existing code style in the project
- Add comments for complex logic
- Write meaningful variable and function names
- Keep functions small and focused
- Avoid unnecessary complexity

### Language-Specific Standards

#### JavaScript/TypeScript
- Use ESLint and Prettier configurations
- Prefer `const` and `let` over `var`
- Use async/await over callbacks
- Write TypeScript types for all public APIs

#### Python
- Follow PEP 8 style guide
- Use type hints where appropriate
- Write docstrings for all public functions
- Use `black` for code formatting

#### Go
- Follow effective Go guidelines
- Use `gofmt` and `golint`
- Write clear error messages
- Document exported functions

## Commit Convention

We use [Conventional Commits](https://www.conventionalcommits.org/) for clear and semantic commit messages:

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, missing semicolons, etc.)
- `refactor`: Code refactoring without changing functionality
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `build`: Changes to build system or dependencies
- `ci`: Changes to CI configuration
- `chore`: Other changes that don't modify src or test files
- `revert`: Revert a previous commit

### Examples

```bash
feat(auth): add OAuth2 authentication
fix(api): resolve null pointer exception
docs(readme): update installation instructions
test(user): add unit tests for user service
```

## Pull Request Process

1. **Fill out the PR template** completely
2. **Link related issues** using keywords (Closes #123)
3. **Ensure CI passes** - all tests and checks must pass
4. **Request review** from appropriate team members
5. **Address feedback** from reviewers
6. **Keep PR focused** - one feature/fix per PR
7. **Update documentation** if needed
8. **Add tests** for new functionality

### PR Checklist

Before submitting your PR, ensure:

- [ ] Code follows project style guidelines
- [ ] Self-reviewed the code
- [ ] Added comments for complex logic
- [ ] Updated documentation
- [ ] Added tests that prove the fix/feature works
- [ ] All tests pass locally
- [ ] No new warnings introduced
- [ ] Checked for security vulnerabilities
- [ ] Appropriate labels assigned
- [ ] Linked related issues

## Reporting Bugs

Use the [Bug Report](.github/ISSUE_TEMPLATE/bug_report.yml) template to report bugs. Include:

- Clear description of the bug
- Steps to reproduce
- Expected vs actual behavior
- Environment details
- Relevant logs or screenshots

## Feature Requests

Use the [Feature Request](.github/ISSUE_TEMPLATE/feature_request.yml) template to suggest features. Include:

- Problem statement
- Proposed solution
- Alternative solutions considered
- Benefits of the feature

## Community

### Getting Help

- 💬 [GitHub Discussions](https://github.com/orgs/NORSAIN-AI/discussions) - Ask questions and share ideas
- 📖 [Documentation](https://github.com/NORSAIN-AI) - Browse our guides and references
- 🐛 [Issues](https://github.com/NORSAIN-AI/.github/issues) - Report bugs or request features

### Stay Connected

- Follow us on GitHub
- Star repositories you find useful
- Share feedback and suggestions

## Recognition

We value all contributions! Contributors will be:

- Listed in release notes
- Credited in project documentation
- Invited to join our community discussions

## License

By contributing, you agree that your contributions will be licensed under the same license as the project (see LICENSE file).

---

Thank you for contributing to NORSAIN-AI! 🚀
