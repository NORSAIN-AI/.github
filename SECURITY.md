# Security Policy

## Reporting Security Vulnerabilities

We take security seriously at NORSAIN-AI. If you discover a security vulnerability, please report it responsibly.

### Private Reporting Channel

**DO NOT** open a public issue for security vulnerabilities. Instead, please use GitHub's private security advisory feature:

1. Go to the repository's Security tab
2. Click "Report a vulnerability"
3. Fill out the security advisory form with details about the vulnerability

Alternatively, you can report security issues to our security team directly through our private reporting channel:

- **GitHub Security Advisories**: [Report a vulnerability](https://github.com/NORSAIN-AI/.github/security/advisories/new)

### What to Include in Your Report

When reporting a security vulnerability, please include:

- Description of the vulnerability
- Steps to reproduce the issue
- Potential impact of the vulnerability
- Any suggested fixes or mitigations
- Your contact information for follow-up

### Response Timeline

- We will acknowledge receipt of your vulnerability report within 48 hours
- We will provide an initial assessment within 5 business days
- We will keep you informed of progress toward a fix
- We will notify you when the vulnerability has been fixed

## Supported Versions

We provide security updates for the following versions. Supported versions are determined by our release strategy and published releases.

| Version | Supported          |
| ------- | ------------------ |
| Latest  | :white_check_mark: |

**Note**: Supported versions are based on our official releases. Please check the [Releases page](https://github.com/NORSAIN-AI/.github/releases) for the latest stable version.

For repositories using this `.github` repository, security support follows the same pattern:
- Latest release versions receive security updates
- Older versions may receive critical security patches on a case-by-case basis

## Zero-Day Vulnerabilities

For zero-day vulnerabilities or actively exploited security issues:

1. **DO NOT** create a public issue or pull request
2. **DO NOT** discuss the vulnerability in public forums
3. **DO** report immediately through our private reporting channel
4. **DO** allow us time to develop and deploy a fix before public disclosure

We follow responsible disclosure practices and will coordinate with you on the timeline for public disclosure.

## Security Best Practices

When contributing to NORSAIN-AI projects, please follow these security best practices:

- Never commit secrets, API keys, passwords, or credentials to the repository
- Use environment variables for sensitive configuration
- Keep dependencies up to date to avoid known vulnerabilities
- Follow the principle of least privilege
- Validate and sanitize all user input
- Use secure communication protocols (HTTPS, SSH)
- Review security scanning results in CI/CD pipelines

## Security Scanning

Our repositories include automated security scanning:

- **Dependency scanning**: Automated checks for vulnerable dependencies
- **Code scanning**: Static analysis for security issues (CodeQL)
- **Container scanning**: Vulnerability scanning for container images (Trivy)
- **Secret scanning**: Detection of accidentally committed secrets

Please ensure all security checks pass before submitting a pull request.

## Contact

For general security questions or concerns, please contact:

- Security Team: Use GitHub Security Advisories for sensitive issues
- Platform Team: @NORSAIN-AI/platform-team (for non-sensitive security discussions)

Thank you for helping keep NORSAIN-AI secure! 🔒
