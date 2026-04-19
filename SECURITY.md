# Security Policy

## Repository

> **Note**: This repository was renamed from `n8n-workflows` → `automation-workflows`

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 1.0.x   | :white_check_mark: |

## Reporting a Vulnerability

If you discover a security vulnerability, please report it responsibly:

1. **Do NOT** create a public GitHub issue
2. Email directly to: dhyan.work.2815@gmail.com
3. Include detailed reproduction steps
4. Expect acknowledgment within 48 hours

## Security Best Practices

- All workflows use environment variables for credentials
- No hardcoded secrets in workflow exports
- CI/CD includes auto-redaction for sensitive data
- Review `.github/workflows/secrets-scanner.yml` for scanning automation