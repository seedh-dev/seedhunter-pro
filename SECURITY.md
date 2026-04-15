# Security Policy

## Supported Versions

| Version | Status |
|---------|--------|
| 3.2.x | ✅ Actively supported |
| 3.1.x | ✅ Security fixes only |
| 3.0.x | ⚠️ End of life — upgrade recommended |
| < 3.0 | ❌ Unsupported |

## Reporting a Vulnerability

We take security seriously. If you've found a vulnerability in SeedHunter Pro, we appreciate your help in disclosing it responsibly.

### How to Report

1. **Do not** open a public GitHub issue — this exposes the vulnerability to everyone
2. **Email:** seedhunter.code@proton.me
3. **Telegram DM:** [@seedhunter_support](https://t.me/seedhunter_support)

### What to Include

- SeedHunter Pro version
- Operating system and version
- Step-by-step reproduction instructions
- Impact assessment (what an attacker could do)
- Proof of concept (if applicable)

### What to Expect

- **Acknowledgment** within 48 hours
- **Assessment** within 5 business days
- **Fix timeline** communicated once the issue is triaged
- **Credit** in the changelog (unless you prefer anonymity)

### Scope

The following are in scope:
- Seed phrase generation weaknesses (predictability, bias)
- Key derivation errors producing incorrect addresses
- Network traffic leaking sensitive data (seeds, private keys)
- Local storage encryption weaknesses
- Privilege escalation via the Electron shell

The following are **out of scope:**
- Social engineering attacks against users
- Issues requiring physical access to the machine
- Denial of service against third-party API endpoints
- Issues in the Electron framework itself (report upstream)

### Hall of Fame

We recognize researchers who help improve SeedHunter Pro's security:

*No reports yet — be the first.*
