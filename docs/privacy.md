# Privacy Policy

**Last updated:** April 2026

## The Short Version

SeedHunter Pro collects nothing. We have no servers receiving your data,
no analytics, no tracking, no user accounts. Everything runs locally on
your machine.

## What We Don't Collect

- Seed phrases (generated or found)
- Private keys
- Wallet addresses
- Scan results or statistics
- IP addresses
- Device identifiers
- Usage patterns
- Crash reports

## Network Requests

SeedHunter Pro makes the following outbound network requests during operation:

| Request | Destination | Purpose | Frequency |
|---------|-------------|---------|-----------|
| Balance check | Public blockchain APIs | Core functionality — checking if addresses hold funds | Per scan cycle |
| Price update | CoinGecko API | USD value conversion display | Every 15 min |
| License check | License server | Validating license key | On launch (once) |
| Update check | GitHub Releases API | Checking for new versions | On launch (once) |

All requests go to **public, free-tier API endpoints**. No API keys are used.
No authentication tokens are sent. The requests contain only the wallet
address being checked — no identifying information.

If you route traffic through a SOCKS5 proxy (Tor), all of the above requests
go through the proxy.

## Local Storage

SeedHunter Pro stores the following data locally:

| Data | Location | Encryption | Auto-Purge |
|------|----------|------------|------------|
| Configuration | config.json | No (non-sensitive) | No |
| Scan logs | logs/ | AES-256-GCM | 7 days (configurable) |
| Hit records | hits/ | AES-256-GCM | No (manual delete) |
| License key | config.json | Obfuscated | No |

All encrypted data uses a key derived from your machine's hardware fingerprint.
Moving the data files to another machine renders them unreadable.

## Third-Party Services

| Service | What we use | Their privacy policy |
|---------|-------------|---------------------|
| CoinGecko | Price data API | [coingecko.com/en/privacy](https://www.coingecko.com/en/privacy) |
| mempool.space | BTC balance/UTXO | [mempool.space/about](https://mempool.space/about) |
| Blockstream | BTC fallback | [blockstream.info](https://blockstream.info/) |
| Various public RPC | ETH/SOL/etc. balances | Public infrastructure, no accounts |

We have no data-sharing agreements with any third party. We send the minimum
data required (a wallet address) and receive the minimum data needed (a balance).

## Data Deletion

To remove all SeedHunter Pro data from your system:

**macOS:**
```bash
rm -rf ~/Library/Application\ Support/SeedHunter\ Pro
rm -rf /Applications/SeedHunter\ Pro.app
```

**Windows:**
1. Uninstall via Settings → Apps
2. Delete `%APPDATA%\SeedHunter Pro`

## Changes to This Policy

This policy may be updated with new releases. Changes will be noted in the
[Changelog](../CHANGELOG.md).

## Contact

Questions about privacy: seedhunter.code@proton.me
