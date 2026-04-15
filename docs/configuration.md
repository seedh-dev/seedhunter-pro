# Configuration Guide

SeedHunter Pro stores its configuration in a local JSON file. Most settings
are accessible through the in-app Settings panel.

## Settings Panel

Access via the **⚙️ gear icon** in the top-right corner of the dashboard.

### Scanning

| Setting | Default | Description |
|---------|---------|-------------|
| Scan Rate | Auto | Seeds checked per minute. Auto adjusts to network conditions. Manual: 50–500 |
| Target Chains | All | Which blockchains to check for each generated seed |
| Scan Mode | Continuous | `Continuous` (runs until stopped) or `Batch` (set a seed count target) |
| Randomized Intervals | Off | Adds jitter to scan timing. Useful for stealth operation |
| Jitter Range | ±20% | How much variation to add when randomized intervals are enabled |

### Network

| Setting | Default | Description |
|---------|---------|-------------|
| Provider Rotation | Auto | Cycles through API endpoints to avoid rate limits |
| SOCKS5 Proxy | Disabled | Route all traffic through Tor or a custom proxy. Format: `host:port` |
| Timeout | 10s | Maximum wait time for balance check responses |
| Retry on Failure | 2 | Number of retries when an API request fails |

### Privacy

| Setting | Default | Description |
|---------|---------|-------------|
| Log Encryption | AES-256 | Encryption standard for local scan logs |
| Auto-Purge Logs | 7 days | Automatically delete logs older than this |
| Save Hit Details | Yes | Store full seed phrase + addresses when a funded wallet is found |

### Display

| Setting | Default | Description |
|---------|---------|-------------|
| Theme | Dark | `Dark` or `Light` |
| Currency | USD | Fiat currency for balance display |
| Notifications | On | Desktop + sound notifications when a wallet is found |
| Sound | On | Audible alert on hit |

### License

| Setting | Description |
|---------|-------------|
| License Key | Enter your Pro license key to unlock full scan speed |
| Status | Shows current license status (Trial / Pro / Expired) |
| Activate | Validates the key against the license server |

## Configuration File

Settings are stored at:

- **macOS:** `~/Library/Application Support/SeedHunter Pro/config.json`
- **Windows:** `%APPDATA%\SeedHunter Pro\config.json`

You can edit this file directly (when the app is closed) for advanced
configuration not exposed in the UI.

### Example config.json

```json
{
  "scan": {
    "rate": "auto",
    "chains": ["btc", "eth", "sol", "bnb", "ada", "dot", "avax", "matic", "doge", "xrp"],
    "mode": "continuous",
    "jitter": false,
    "jitterRange": 0.2
  },
  "network": {
    "providerRotation": true,
    "proxy": "",
    "timeout": 10000,
    "retries": 2
  },
  "privacy": {
    "logEncryption": "aes-256-gcm",
    "autoPurgeDays": 7,
    "saveHitDetails": true
  },
  "display": {
    "theme": "dark",
    "currency": "USD",
    "notifications": true,
    "sound": true
  }
}
```

## Proxy Configuration

To route all network traffic through Tor:

1. Install and start Tor on your system
2. In SeedHunter Pro: Settings → Network → SOCKS5 Proxy
3. Enter `127.0.0.1:9050` (default Tor SOCKS port)
4. Click Save

All balance checks and price lookups will now go through Tor. Expect
increased latency (~2-5x slower) and occasional timeouts.

For a custom proxy:
- Format: `host:port`
- Supported protocols: SOCKS5
- Authentication: not yet supported (planned for v3.3)

## Command-Line Arguments

SeedHunter Pro accepts optional CLI arguments:

```bash
# macOS
open -a "SeedHunter Pro" --args --config /path/to/config.json

# Windows
"SeedHunter Pro.exe" --config C:\path\to\config.json
```

| Argument | Description |
|----------|-------------|
| `--config <path>` | Use a custom configuration file |
| `--no-update-check` | Skip the update check on launch |
| `--headless` | Run without UI (logs to stdout) — *planned for v4.0* |
