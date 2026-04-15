# Troubleshooting

Common issues and their solutions.

## Installation Issues

### macOS: "App is damaged and can't be opened"

**Cause:** macOS quarantine flag on downloaded files.

**Fix:**
```bash
xattr -cr /Applications/SeedHunter\ Pro.app
```

### macOS: "App can't be opened because it is from an unidentified developer"

**Fix:** Right-click → Open → click Open in the dialog. Only needed once.

### Windows: SmartScreen blocks the installer

**Fix:** Click "More info" → "Run anyway". This is normal for apps without
an EV code signing certificate.

### Windows: Antivirus quarantines the app

**Cause:** Electron apps that make network requests are sometimes flagged
by heuristic scanners.

**Fix:**
1. Restore from quarantine
2. Add an exclusion for the installation folder
3. If using Windows Defender: Settings → Virus protection → Exclusions → Add

## Runtime Issues

### App stuck on splash screen

**Possible causes:**
- No internet connection (the app checks for updates on launch)
- License server temporarily unreachable
- Corrupted config file

**Fix:**
1. Check your internet connection
2. Wait 30 seconds — the timeout will pass and the app will continue
3. If persistent: delete the config file and relaunch
   - macOS: `rm ~/Library/Application\ Support/SeedHunter\ Pro/config.json`
   - Windows: delete `%APPDATA%\SeedHunter Pro\config.json`

### Scan rate is very slow

**Possible causes:**
- Trial mode (limited to ~50 seeds/min)
- Slow network connection
- Too many chains selected simultaneously
- API rate limiting

**Fix:**
1. Activate a Pro license for full speed
2. Reduce the number of selected chains (3-4 gives the best speed/coverage ratio)
3. Use a wired connection instead of WiFi
4. Enable provider rotation in Settings → Network

### "Network Error" or "Connection Timeout"

**Possible causes:**
- Blockchain API endpoint is down
- Firewall blocking outbound connections
- VPN/proxy misconfiguration

**Fix:**
1. Check the Network panel — if all indicators are red, it's a connectivity issue
2. Try disabling your firewall temporarily to test
3. If using a proxy: verify the SOCKS5 address and port in Settings → Network
4. Wait a few minutes — public API endpoints occasionally have downtime

### High memory usage

**Possible causes:**
- Long-running scan session (>12h)
- Logs not being purged

**Fix:**
1. Update to v3.2.1 (fixed a log buffer memory leak)
2. Restart the app periodically for very long sessions
3. Enable auto-purge in Settings → Privacy → Auto-Purge Logs

### No sound on wallet hit

**Fix:**
1. Check Settings → Display → Sound is enabled
2. Check your system volume
3. macOS: ensure SeedHunter Pro has notification permissions
   (System Settings → Notifications → SeedHunter Pro)

## Balance Checking Issues

### False "0 balance" results

**Possible causes:**
- API endpoint returned an error that was parsed as zero
- Account exists on a different derivation path
- Chain-specific minimum balance requirements (XRP: 10 XRP reserve)

**Note:** SeedHunter currently checks one derivation path per chain. Wallets
using non-standard paths may not be detected. Multi-path scanning is planned
for v4.0.

### Incorrect USD values

**Cause:** Prices are fetched from CoinGecko once at launch and refreshed
every 15 minutes.

**Fix:** If prices seem stale, restart the app to force a refresh.

## Reporting Bugs

If your issue isn't listed here:

1. Note your SeedHunter Pro version (Settings → About)
2. Note your OS and version
3. Describe the steps to reproduce
4. Open an issue on [GitHub](../../issues/new?template=bug_report.md)
   or message [@seedhunter_support](https://t.me/seedhunter_support)
