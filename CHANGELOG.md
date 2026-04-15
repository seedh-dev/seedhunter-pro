# Changelog

All notable changes to SeedHunter Pro are documented here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## [3.2.1] — 2026-04-08

### Fixed
- Cardano address derivation edge case causing invalid addr1 prefixes
- Network panel latency display freezing above 200ms
- Memory leak in long-running sessions (>12h) due to uncapped log buffer

### Changed
- CoinGecko price refresh interval: 5min → 15min (rate limit compliance)

## [3.2.0] — 2026-03-15

### Added
- Multi-chain parallel scanning — check up to 10 chains per seed simultaneously
- Real-time USD conversion with live CoinGecko prices on the dashboard
- Network status panel: peer count, latency, block height, connection health
- Stealth mode: randomized scan intervals with configurable jitter range
- Activity chart with live scan rate visualization

### Changed
- Complete UI overhaul — new dark theme as default, refined layout
- Scan engine rewritten for 3x throughput improvement
- Provider rotation logic now tracks endpoint health scores

### Fixed
- Ethereum EIP-55 checksum validation false negatives on mixed-case addresses
- BNB Chain balance queries returning stale cached data
- Windows installer failing on paths with Unicode characters

## [3.1.0] — 2026-01-20

### Added
- Avalanche (AVAX) C-Chain support
- Polygon (MATIC) support
- Scan scheduling — set daily time windows for automatic scanning
- Export scan results to encrypted JSON

### Changed
- Polkadot address encoding switched from generic SS58 to network-specific prefix
- Improved Solana RPC fallback — 3 providers with automatic rotation
- Reduced memory footprint by 40% via streaming address derivation

### Fixed
- Dogecoin address generation producing invalid checksums on rare byte sequences
- XRP balance check timeout not being respected (stuck at 30s regardless of setting)
- Light theme contrast issues on scan progress indicators

## [3.0.0] — 2025-10-05

### Added
- Polkadot (DOT) support with SS58 address encoding
- Dogecoin (DOGE) support with Base58Check addresses
- Ripple (XRP) support
- Auto-update checker — notifies when new versions are available
- License system: Trial mode (rate-limited) and Pro mode (full speed)
- Sound notifications on wallet hit

### Changed
- **Breaking:** configuration file format changed from INI to JSON
- Migrated from Electron 28 to Electron 31
- Address derivation paths now follow SLIP-0044 registered coin types exactly
- Scan results stored in local encrypted SQLite instead of flat files

### Removed
- Legacy CSV export (replaced by encrypted JSON in v3.1)
- Python helper scripts (all functionality now native)

### Fixed
- BIP39 word list validation rejecting valid 12th words due to checksum bit miscalculation
- Crash on macOS Ventura when system theme changes mid-scan
- High CPU usage when app is minimized to tray

## [2.1.0] — 2025-07-12

### Added
- Cardano (ADA) support with Shelley-era addr1 addresses
- BNB Chain support (EVM-compatible, shared derivation with ETH)
- Persistent scan statistics across sessions
- Configurable API rate limiting per chain

### Fixed
- Bitcoin Bech32 encoding producing invalid checksums for specific witness programs
- Solana balance check returning 0 for accounts with only SOL (no SPL tokens)
- UI freeze when rapidly starting/stopping scans

## [2.0.0] — 2025-04-18

### Added
- Solana (SOL) support with Ed25519 key derivation
- HD wallet derivation (BIP32/BIP44) — proper hierarchical key generation
- Provider fallback system — automatic rotation when an API endpoint fails
- Dark theme

### Changed
- **Breaking:** complete rewrite of scanning engine
- Switched from single-threaded scanning to async parallel architecture
- Bitcoin address generation: legacy (1...) → native SegWit (bc1q...)
- Ethereum address generation now produces EIP-55 checksummed output

### Removed
- Single-address mode (all scanning now uses HD derivation)

### Fixed
- False positive hits caused by API returning non-zero balances for dust amounts
- Memory consumption growing linearly with scan duration

## [1.2.0] — 2025-02-28

### Added
- Tor/SOCKS5 proxy support for all network requests
- Encrypted local logging with AES-256-GCM
- System tray mode — minimize to tray, scan in background

### Fixed
- Ethereum balance check failing for addresses with pending transactions
- App window not restoring from minimized state on Windows

## [1.1.0] — 2025-01-15

### Added
- Ethereum (ETH) support — EVM address derivation and balance checking
- Settings panel with persistent configuration
- Scan rate display (seeds/minute)

### Changed
- Improved BIP39 seed generation randomness (switched to crypto.getRandomValues)
- Better error messages when network requests fail

## [1.0.0] — 2024-12-15

### Added
- Initial release
- Bitcoin (BTC) support — BIP39 seed generation, address derivation, balance checking
- Basic dashboard with scan counter and elapsed time
- macOS and Windows builds
