# Security Policy

## Supported Versions

| Version | Supported          |
| ------- | ------------------ |
| 1.x.x   | :white_check_mark: |
| < 1.0   | :x:                |

## Reporting a Vulnerability

We take security seriously. If you discover a security vulnerability in AISDK, please report it responsibly.

### How to Report

**DO NOT** open a public GitHub issue for security vulnerabilities.

Instead, please report vulnerabilities via one of these methods:

1. **GitHub Security Advisories** (Preferred)
   - Go to the repository's Security tab
   - Click "Report a vulnerability"
   - Fill out the form with details

2. **Email**
   - Send details to: [YOUR_SECURITY_EMAIL]
   - Use subject: `[SECURITY] AISDK Vulnerability Report`

### What to Include

Please provide:

1. **Description** - What is the vulnerability?
2. **Impact** - What could an attacker do?
3. **Steps to reproduce** - How can we verify it?
4. **Affected versions** - Which versions are vulnerable?
5. **Suggested fix** - If you have one (optional)

### Response Timeline

| Action | Timeline |
|--------|----------|
| Initial response | Within 48 hours |
| Vulnerability confirmation | Within 1 week |
| Fix development | Depends on severity |
| Public disclosure | After fix is released |

### Severity Levels

| Level | Description | Response |
|-------|-------------|----------|
| **Critical** | Remote code execution, credential exposure | Immediate patch |
| **High** | Data leakage, authentication bypass | Patch within 7 days |
| **Medium** | Limited impact vulnerabilities | Patch in next release |
| **Low** | Minor issues | Scheduled fix |

## Security Best Practices for Users

When using AISDK:

### API Keys

```swift
// NEVER hardcode API keys
let provider = ClaudeProvider(apiKey: "sk-xxx") // BAD

// Use environment variables or secure storage
let provider = ClaudeProvider(apiKey: ProcessInfo.processInfo.environment["CLAUDE_API_KEY"]!) // BETTER

// Use Keychain for production apps
let provider = ClaudeProvider(apiKey: KeychainHelper.getAPIKey()) // BEST
```

### Sensitive Data

- Never log API keys or tokens
- Sanitize user input before sending to AI providers
- Don't include sensitive data in AI prompts unnecessarily

### Network Security

- AISDK uses HTTPS for all cloud API calls
- Verify you're using official API endpoints
- Be cautious with local AI (Ollama) network exposure

## Acknowledgments

We thank security researchers who help keep AISDK safe. Responsible disclosure contributors will be acknowledged (with permission) in our security hall of fame.

## Updates

This security policy may be updated. Check back for changes.

---

*Last updated: January 2026*
