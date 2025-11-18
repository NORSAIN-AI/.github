# Security Policy

## Reporting Security Vulnerabilities

At NORSAIN-AI, we take security seriously. We appreciate your efforts to responsibly disclose your findings and will make every effort to acknowledge your contributions.

### 🔒 How to Report a Vulnerability

**Please do NOT report security vulnerabilities through public GitHub issues.**

Instead, please report security vulnerabilities by:

1. **Using GitHub Security Advisories** (Preferred):
   - Navigate to the repository's Security tab
   - Click "Report a vulnerability"
   - Fill out the form with details

2. **Email** (Alternative):
   - Send details to: <security@norsain.ai>
   - Include "SECURITY" in the subject line

### What to Include

Please include the following information in your report:

- **Type of vulnerability** (e.g., SQL injection, XSS, authentication bypass)
- **Full paths** of source file(s) related to the vulnerability
- **Location** of the affected source code (tag/branch/commit or direct URL)
- **Step-by-step instructions** to reproduce the issue
- **Proof-of-concept or exploit code** (if possible)
- **Impact** of the vulnerability and potential attack scenarios
- **Any suggested fixes** or mitigations

### What to Expect

1. **Acknowledgment**: We'll acknowledge receipt of your report within 48 hours
2. **Initial Assessment**: We'll provide an initial assessment within 5 business days
3. **Updates**: We'll keep you informed about our progress
4. **Resolution**: We'll work to resolve confirmed vulnerabilities as quickly as possible
5. **Disclosure**: We'll coordinate public disclosure timing with you

### Our Commitment

- We will not pursue legal action against security researchers who:
  - Act in good faith
  - Follow responsible disclosure practices
  - Don't access or modify user data beyond what's necessary
  - Don't degrade our services
  - Don't disclose the issue publicly before we've had time to fix it

## Supported Versions

We provide security updates for the following versions:

| Version | Supported          |
| ------- | ------------------ |
| Latest  | :white_check_mark: |
| < Latest| :x:                |

We recommend always using the latest version to ensure you have the most recent security patches.

## Security Best Practices

### For Users

1. **Keep Software Updated**: Always use the latest version
2. **Use Strong Authentication**: Enable 2FA where available
3. **Review Permissions**: Only grant necessary permissions
4. **Monitor Activity**: Watch for suspicious activity
5. **Report Issues**: Report security concerns immediately

### For Contributors

1. **Never Commit Secrets**: Don't commit API keys, passwords, or tokens
2. **Use Secret Scanning**: Enable secret scanning in your repositories
3. **Review Dependencies**: Keep dependencies updated and scan for vulnerabilities
4. **Follow Secure Coding**: Follow OWASP guidelines and secure coding practices
5. **Test Security**: Include security tests in your contributions

## Security Features

### Automated Security Scanning

We use several automated tools to maintain security:

- **CodeQL**: Semantic code analysis for security vulnerabilities
- **Dependabot**: Automated dependency updates and vulnerability alerts
- **Trivy**: Container and filesystem vulnerability scanning
- **Grype**: Additional vulnerability scanning
- **Secret Scanning**: Detect committed secrets and credentials

### Security Workflows

- Code scanning on every push and PR
- Dependency updates and vulnerability alerts
- Container security scanning
- Regular security audits

## Security Updates

Security updates are released as soon as possible after a vulnerability is confirmed. Updates are announced through:

- GitHub Security Advisories
- Release notes
- Email notifications (for critical issues)

## Third-Party Dependencies

We actively monitor our dependencies for security vulnerabilities using:

- Dependabot alerts
- Automated security updates
- Regular dependency audits

When a vulnerability is discovered in a dependency:

1. We assess the impact on our projects
2. We update or patch as quickly as possible
3. We release a new version if needed
4. We notify users of critical updates

## Compliance

We strive to comply with:

- OWASP Top 10 security guidelines
- CWE (Common Weakness Enumeration) standards
- Industry best practices for secure software development

## Bug Bounty Program

We currently do not have a formal bug bounty program, but we:

- Acknowledge security researchers in our release notes
- Provide credit for responsible disclosure
- Consider implementing a bug bounty program in the future

## Security Hall of Fame

We'd like to thank the following security researchers for responsibly disclosing vulnerabilities:

<!-- List will be populated as vulnerabilities are reported and fixed -->

_No vulnerabilities have been reported yet._

## Additional Resources

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [CWE Top 25](https://cwe.mitre.org/top25/)
- [GitHub Security Best Practices](https://docs.github.com/en/code-security)
- [Security Checklist](https://github.com/OWASP/CheatSheetSeries)

## Questions?

If you have questions about this security policy, please contact us at:

- Email: <security@norsain.ai>
- GitHub Discussions: [NORSAIN-AI Discussions](https://github.com/orgs/NORSAIN-AI/discussions)

---

Last Updated: 2025-01-27

Thank you for helping keep NORSAIN-AI secure! 🔒
