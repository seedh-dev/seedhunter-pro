# Installation Guide

## Download

Download the latest version from the
[GitHub Releases page](../../releases/latest).

| Platform | File | Checksum |
|----------|------|----------|
| macOS (Universal) | `SeedHunter-Pro-3.2.1.dmg` | `Available soon...` |
| Windows (64-bit) | `SeedHunter-Pro-Setup-3.2.1.exe` | `50e4ee0b0e90eb71a15cf9adfdcd8b553b4febd186c831194f927ddcb0a2d234` |

## macOS Installation

### Step 1: Open the DMG

Double-click `SeedHunter-Pro-3.2.1.dmg`. A Finder window opens with the
application icon and an Applications folder shortcut.

### Step 2: Install

Drag **SeedHunter Pro** into the **Applications** folder.

### Step 3: First Launch

macOS Gatekeeper blocks unsigned applications by default. To open SeedHunter Pro
for the first time:

1. Open **Applications** in Finder
2. Right-click (or Control-click) on **SeedHunter Pro**
3. Select **Open** from the context menu
4. Click **Open** in the dialog that appears

After the first launch, you can open the app normally.

> **Why the warning?** Apple requires a $99/year Developer ID certificate to
> sign macOS apps. We've chosen not to participate in Apple's program to
> maintain developer anonymity. The app is safe — binary checksums are
> provided above for verification.

### macOS Troubleshooting

**"SeedHunter Pro is damaged and can't be opened"**

This happens when macOS quarantine flags the downloaded file. Fix:

```bash
xattr -cr /Applications/SeedHunter\ Pro.app
```

Then re-open the app.

**Apple Silicon (M1/M2/M3)**

The app includes a universal binary that runs natively on both Intel and
Apple Silicon. No Rosetta required.

## Windows Installation

### Step 1: Run the Installer

Double-click `SeedHunter-Pro-Setup-3.2.1.exe`.

### Step 2: SmartScreen Warning

Windows SmartScreen may display a warning:

1. Click **More info**
2. Click **Run anyway**

> **Why the warning?** Windows SmartScreen flags executables that haven't been
> seen by enough users yet. An Extended Validation (EV) code signing
> certificate costs $400+/year and requires a registered business entity.
> We provide SHA-256 checksums instead for manual verification.

### Step 3: Setup Wizard

- **Install location:** default is fine (`C:\Users\[you]\AppData\Local\Programs\SeedHunter Pro`)
- **Desktop shortcut:** optional
- **Start menu shortcut:** recommended

### Step 4: Launch

Open SeedHunter Pro from the Start menu or desktop shortcut.

### Windows Troubleshooting

**Antivirus false positive**

Some antivirus products flag Electron apps that make network requests.
If your AV quarantines SeedHunter Pro:

1. Open your AV's quarantine/history
2. Restore the file
3. Add an exclusion for the SeedHunter Pro installation folder

This is a known issue with Electron-based applications and not specific
to SeedHunter Pro.

## Verify Download Integrity

Every release includes SHA-256 checksums. After downloading, verify:

**macOS/Linux:**
```bash
shasum -a 256 SeedHunter-Pro-3.2.1.dmg
# Compare output with the checksum on the release page
```

**Windows (PowerShell):**
```powershell
Get-FileHash .\SeedHunter-Pro-Setup-3.2.1.exe -Algorithm SHA256
# Compare output with the checksum on the release page
```

## First Run

1. Launch SeedHunter Pro
2. The splash screen checks for updates and loads configuration
3. You're greeted by the main dashboard in **Trial Mode**
4. To activate a Pro license: Settings → License → enter your key

See [Configuration Guide](configuration.md) for next steps.

## Uninstall

**macOS:** drag SeedHunter Pro from Applications to Trash. To remove
all data: `rm -rf ~/Library/Application\ Support/SeedHunter\ Pro`

**Windows:** Settings → Apps → SeedHunter Pro → Uninstall. Or use
the uninstaller in the Start menu folder.
