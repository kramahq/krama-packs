---
name: security-review
description: Deep security-focused review for changes involving auth, data handling, or APIs.
allowedTools:
  - bitbucket
  - sonar
  - terminal
---

# Security Review

## Purpose

Perform a deep security-focused review when changes involve authentication, authorization, data handling, or external API integrations.

## When to Use

Activate this skill when the PR touches:
- Authentication or authorization logic
- User input handling or validation
- Database queries (especially dynamic ones)
- External API calls or webhook handlers
- File upload/download functionality
- Encryption or hashing
- Session management
- CORS or CSP configuration

## Security Checklist

### Injection
- [ ] All database queries use parameterized statements
- [ ] No string concatenation in SQL/NoSQL queries
- [ ] HTML output is properly escaped (XSS prevention)
- [ ] Command execution uses safe APIs (no shell interpolation)

### Authentication & Authorization
- [ ] Auth checks on all protected endpoints
- [ ] Token validation is complete (expiry, signature, issuer)
- [ ] No privilege escalation paths
- [ ] Session invalidation on logout/password change

### Data Protection
- [ ] Sensitive data not logged (passwords, tokens, PII)
- [ ] Error messages don't leak internal details
- [ ] Proper encryption for data at rest and in transit
- [ ] PII handling complies with data retention policies

### Input Validation
- [ ] All external inputs validated (type, length, format)
- [ ] File uploads validated (type, size, content)
- [ ] Rate limiting on sensitive endpoints
- [ ] Request size limits configured

## Output

Security findings flagged as BLOCKING — they must be resolved before approval. Each finding includes the vulnerability type, affected file/line, and recommended fix.
