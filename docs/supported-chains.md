# Supported Blockchains

Detailed specifications for each blockchain supported by SeedHunter Pro.

## Overview

SeedHunter Pro supports 10 blockchains as of v3.2.1. Each chain uses
BIP39-derived seed phrases with chain-specific key derivation and address
encoding.

All derivation follows the BIP32/BIP44/SLIP-0044 standards. The coin type
numbers are registered in the
[SLIP-0044 registry](https://github.com/satoshilabs/slips/blob/master/slip-0044.md).

## Chain Details

### Bitcoin (BTC)

| Property | Value |
|----------|-------|
| Coin Type | 0 |
| Derivation Path | m/84'/0'/0'/0/0 |
| Address Format | Bech32 (bc1q...) — Native SegWit P2WPKH |
| Key Curve | secp256k1 |
| Balance API | Blockstream Esplora, mempool.space |
| Added in | v1.0.0 |

SeedHunter generates **native SegWit (bc1q) addresses** by default. These
are the most common address type since 2020. Legacy (1...) and wrapped
SegWit (3...) addresses are not currently scanned — planned for v4.0
multi-path derivation.

### Ethereum (ETH)

| Property | Value |
|----------|-------|
| Coin Type | 60 |
| Derivation Path | m/44'/60'/0'/0/0 |
| Address Format | EIP-55 checksummed hex (0x...) |
| Key Curve | secp256k1 |
| Balance API | Public RPC endpoints (eth_getBalance) |
| Added in | v1.1.0 |

Ethereum addresses are EVM-compatible. The same derivation produces valid
addresses on all EVM chains (BSC, Polygon, Avalanche C-Chain, Arbitrum, etc.),
but SeedHunter checks them independently per chain due to different balance states.

### Solana (SOL)

| Property | Value |
|----------|-------|
| Coin Type | 501 |
| Derivation Path | m/44'/501'/0'/0' |
| Address Format | Base58 (Ed25519 public key) |
| Key Curve | Ed25519 |
| Balance API | Solana public RPC (getBalance) |
| Added in | v2.0.0 |

Solana uses Ed25519 (not secp256k1). SeedHunter derives the Ed25519 keypair
from the BIP39 seed using the Solana-standard derivation path.

### BNB Chain (BNB)

| Property | Value |
|----------|-------|
| Coin Type | 714 |
| Derivation Path | m/44'/714'/0'/0/0 |
| Address Format | 0x... (EVM-compatible, same as ETH) |
| Key Curve | secp256k1 |
| Balance API | Public BSC RPC endpoints |
| Added in | v2.1.0 |

Shares address format with Ethereum. A wallet generated from the same seed
has the same 0x address on both ETH and BSC — but different balances.

### Cardano (ADA)

| Property | Value |
|----------|-------|
| Coin Type | 1815 |
| Derivation Path | m/1852'/1815'/0'/0/0 |
| Address Format | Bech32 (addr1...) — Shelley era |
| Key Curve | Ed25519-BIP32 |
| Balance API | Blockfrost, Koios |
| Added in | v2.1.0 |

Cardano uses a modified BIP32-Ed25519 derivation (CIP-1852). SeedHunter
generates Shelley-era base addresses (`addr1`).

### Polkadot (DOT)

| Property | Value |
|----------|-------|
| Coin Type | 354 |
| Derivation Path | m/44'/354'/0'/0/0 |
| Address Format | SS58 (prefix 0, starts with 1...) |
| Key Curve | Sr25519 |
| Balance API | Public Polkadot RPC |
| Added in | v3.0.0 |

### Avalanche (AVAX)

| Property | Value |
|----------|-------|
| Coin Type | 9005 |
| Derivation Path | m/44'/9005'/0'/0/0 |
| Address Format | 0x... (C-Chain, EVM-compatible) |
| Key Curve | secp256k1 |
| Balance API | Public Avalanche C-Chain RPC |
| Added in | v3.1.0 |

SeedHunter checks the **C-Chain** (Contract Chain), which is EVM-compatible.
X-Chain and P-Chain addresses use different formats and are not currently
supported.

### Polygon (MATIC)

| Property | Value |
|----------|-------|
| Coin Type | 966 |
| Derivation Path | m/44'/966'/0'/0/0 |
| Address Format | 0x... (EVM-compatible) |
| Key Curve | secp256k1 |
| Balance API | Public Polygon RPC |
| Added in | v3.1.0 |

### Dogecoin (DOGE)

| Property | Value |
|----------|-------|
| Coin Type | 3 |
| Derivation Path | m/44'/3'/0'/0/0 |
| Address Format | Base58Check (starts with D) |
| Key Curve | secp256k1 |
| Balance API | Blockchair, SoChain |
| Added in | v3.0.0 |

Dogecoin uses the same key curve as Bitcoin but with a different version byte
(0x1e) producing addresses starting with `D`.

### Ripple (XRP)

| Property | Value |
|----------|-------|
| Coin Type | 144 |
| Derivation Path | m/44'/144'/0'/0/0 |
| Address Format | Base58 (starts with r) |
| Key Curve | secp256k1 |
| Balance API | Public XRPL WebSocket |
| Added in | v3.0.0 |

XRP Ledger requires a **minimum reserve of 10 XRP** to activate an account.
Addresses with less than 10 XRP may show as unfunded even if they hold a
balance below the reserve.

## Planned Chains

The following chains are under consideration for future releases:

| Chain | Ticker | Status | Target |
|-------|--------|--------|--------|
| Litecoin | LTC | In development | v3.3.0 |
| Tron | TRX | Planned | v3.3.0 |
| Cosmos | ATOM | Researching | v4.0.0 |
| Algorand | ALGO | Researching | v4.0.0 |
| Bitcoin (Legacy) | BTC | Planned (1... addrs) | v4.0.0 |
| Bitcoin (Wrapped SegWit) | BTC | Planned (3... addrs) | v4.0.0 |
