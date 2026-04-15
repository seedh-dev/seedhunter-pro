# Frequently Asked Questions

## General

**What is SeedHunter Pro?**

SeedHunter Pro is a cryptocurrency wallet recovery tool. It generates BIP39
seed phrases, derives addresses across 10 blockchains, and checks their
balances in real time against live blockchain data.

**Is this legal?**

SeedHunter Pro is a security research tool. Using it to recover your own
wallets or for authorized security testing is legal in most jurisdictions.
Users are responsible for compliance with their local laws.

**How does it work?**

The tool generates random 12-word BIP39 mnemonic phrases from the standard
2048-word English wordlist. Each phrase maps to a deterministic set of
private keys and wallet addresses via BIP32/BIP44 hierarchical derivation.
The tool then queries blockchain APIs to check if those addresses hold funds.

**What are the odds of finding a funded wallet?**

Statistically, the probability is extremely low for any single seed phrase.
The BIP39 12-word space contains 2^128 possible combinations (~3.4 × 10^38).
However, SeedHunter Pro can check thousands of seeds per minute across
10 chains simultaneously, which improves throughput significantly over
manual methods.

## Licensing

**What's the difference between Trial and Pro?**

| Feature | Trial | Pro |
|---------|-------|-----|
| Scan rate | ~50 seeds/min | Unlimited (network-bound) |
| Chains | All 10 | All 10 |
| Balance checking | ✅ | ✅ |
| Hit logging | ✅ | ✅ |
| Scheduled scanning | ❌ | ✅ |
| Stealth mode | ❌ | ✅ |
| Priority support | ❌ | ✅ |

**How do I buy a license?**

Contact [@seedhunter_support](https://t.me/seedhunter_support) on Telegram.
Payment accepted in BTC, ETH, XMR, and USDT. Key delivered within 1 hour
of confirmed payment.

**Is the license a one-time purchase?**

Yes. One key, one device, no subscription. Lifetime updates for the current
major version (v3.x). Major version upgrades (v4.0) may require a new key
at a discounted rate.

**Can I use one license on multiple devices?**

Each license key is tied to a single device. Contact support for multi-device
pricing.

## Privacy

**Does SeedHunter Pro collect any data?**

No. Zero telemetry. Zero analytics. The only network requests the app makes
are: (1) balance checks against public blockchain APIs, (2) price updates
from CoinGecko, (3) optional license verification and update check.

**Can I use it with Tor?**

Yes. Configure a SOCKS5 proxy in Settings → Network → enter `127.0.0.1:9050`.
All traffic (including balance checks and price updates) will route through
Tor.

**Are my found seeds stored securely?**

Yes. All hit logs are encrypted with AES-256-GCM using a key derived from
your machine's hardware ID. Logs are stored locally and auto-purged after
7 days (configurable). No data ever leaves your machine.

## Technical

**Why Electron?**

Cross-platform support (macOS + Windows) with a single codebase, native
networking, and fast UI updates for the real-time dashboard. The performance
bottleneck is network I/O, not CPU, so Electron's overhead is negligible.

**Why isn't the source code public?**

The scanning engine contains proprietary optimizations for balance checking
throughput and provider rotation. Publishing the source would enable trivial
cloning and undercut the licensing model. Source is available for audit upon
request to verified security researchers.

**Does it actually check live blockchain balances?**

Yes. Every generated address is checked against real blockchain nodes and
APIs (mempool.space, Blockstream, public RPC endpoints). The network status
panel shows live connection data.

**How fast is it?**

Depends on network conditions and the number of chains selected:

| Chains Selected | Approx. Rate (Pro) |
|---|---|
| 1 | 300-500 seeds/min |
| 3 | 200-350 seeds/min |
| 5 | 150-250 seeds/min |
| 10 | 80-150 seeds/min |

Rate scales inversely with chain count because each seed requires a separate
API call per chain.

**Does it support 24-word seeds?**

Not currently. 12-word (128-bit entropy) is the default. 24-word support
is planned for v4.0.
