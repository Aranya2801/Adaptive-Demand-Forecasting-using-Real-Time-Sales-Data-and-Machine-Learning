# Security Policy

## Supported Versions

| Version | Supported |
|---|---|
| 1.x (latest) | ✅ |
| < 1.0 | ❌ |

## Reporting a Vulnerability

**Please do NOT open a public GitHub issue for security vulnerabilities.**

Report security issues privately:

1. Email: `security@your-domain.com` (replace with your contact)
2. Use GitHub's private vulnerability reporting:
   **Security → Report a vulnerability** in this repository

Include:
- Description of the vulnerability
- Steps to reproduce
- Potential impact assessment
- Any suggested fixes

We will acknowledge receipt within 48 hours and aim to patch critical
vulnerabilities within 7 days.

## Security Practices

This project follows these security practices:

- **JWT authentication** for all API endpoints (configurable enforcement)
- **Environment variables** for all secrets (no hardcoded credentials)
- **Rate limiting** (100 requests/minute per IP by default via `slowapi`)
- **Dependency scanning** via GitHub Actions (Trivy + Dependabot)
- **Static analysis** via Bandit in CI pipeline
- **No `eval()` or dynamic code execution** of user input
- **Input validation** via Pydantic schemas on all endpoints
- **Non-root Docker containers** in production Dockerfiles

## Security Checklist for Deployment

- [ ] Change `JWT_SECRET_KEY` from default to a cryptographically random value
- [ ] Set `REQUIRE_AUTH=true` in production
- [ ] Use managed secrets (AWS Secrets Manager, Azure Key Vault, GCP Secret Manager)
- [ ] Enable HTTPS via load balancer / reverse proxy (Nginx, Traefik)
- [ ] Restrict PostgreSQL and Redis to private VPC network
- [ ] Configure `CORS` allowed origins to your specific frontend domain
- [ ] Enable Postgres SSL connections (`sslmode=require`)
