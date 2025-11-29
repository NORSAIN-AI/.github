# NORSAIN-AI Security Policy

## Scope

This policy applies to all repositories under the NORSAIN-AI GitHub organization, including this `.github` governance repository. It sets minimum requirements for security reporting, review, and risk management for all NORSAIN-AI projects.

## Reporting Security Vulnerabilities

- **Do not report vulnerabilities via public GitHub issues.**
- Use GitHub Security Advisories (preferred) or email security@norsain.ai with "SECURITY" in the subject.
- Reports should include: vulnerability type, affected files/URLs, reproduction steps, impact, and suggested mitigations.

## Response Process

- Reports are triaged by designated maintainers or the Security Lead.
- We aim to acknowledge reports promptly, but cannot guarantee fixed response times.
- Confirmed vulnerabilities are tracked internally (ticketing/risk register) and prioritized by impact.
- Public disclosure is coordinated with the reporter when possible.

## Security Practices and Controls

- All NORSAIN-AI repos must:
  - Avoid committing secrets or credentials.
  - Use secret scanning and dependency scanning where supported.
  - Apply least-privilege permissions in workflows and automation.
  - Review all changes to workflows, templates, and permissions for security impact.
- Security tools (code scanning, dependency scanning, container scanning) are used where practical and maintained. See each repo’s workflows for details.
- All org-level workflow and permission changes require review by a designated maintainer.

## Compliance and Governance

- NORSAIN-AI strives to align with OWASP Top 10, CWE Top 25, and industry best practices where relevant.
- Secure coding, risk management, and incident response are governed by internal QMS/IMS procedures (reference internal documentation).
- All changes to `.github` workflows, templates, and policies must be auditable and reviewed for org-wide impact.

## Roles and Responsibilities

- Security Lead (or delegate) is responsible for triage, risk assessment, and coordination of vulnerability response.
- All maintainers are responsible for following this policy and ensuring security reviews for impactful changes.

## Limitations and Disclaimers

- NORSAIN-AI does not operate a formal bug bounty program.
- Security tools and processes may change over time; this document may not always reflect the current toolset.
- This policy does not guarantee specific response or resolution times.

## Questions and Contact

- Email: security@norsain.ai
- GitHub Security Advisories (preferred for confidential reports)
- For internal process details, refer to NORSAIN-AI QMS/IMS documentation.

---

_Last updated: 2025-11-29_
