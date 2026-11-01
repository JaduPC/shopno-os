## [2.3] - 2026-11-02

### ✨ Features

**Desktop and gaming (xfce)**

- Shopno Menu, a Windows 11 style start menu, replaces Whisker Menu (`e88d9cf8`)
- Shopno Quick Settings, a Windows 11 style flyout for Wi-Fi, Bluetooth, volume, brightness, battery, Do not disturb and Night light, with its own tray, replaces the System Tray and PulseAudio plugins on the default panel (`0cbc4f0c`)
- New default panel layout and a matching "ShopnoOS 2.3" panel profile; "ShopnoOS 2.0" stays for the standard System Tray (`0cbc4f0c`)
- Inter as the UI and window title font, and the Quintom Snow cursor theme (`be486e6c`)
- Shopno Update Helper 0.1.1 replaces the yad Update Helper; it updates apt packages and Flatpak apps from one window (`319f1136`, `351b97b7`)
- Default apps are set per file type, so images, PDFs and office documents open in the right app (`dcc8d901`)
- Regenerated applications menu (`db8f460b`)
- sysinfo-viewer v2.1.0 (`0c7938e4`)

**Gaming**

- Installed systems log in to shopno-shell; the live session stays on Xfce for the installer (`0ae7c10b`)
- The mode selector prototype is removed; shopno-shell replaces it (`05d4f2db`)
- retropie-rom-manager v2.3.0 (`8b489a78`)
- Skyscraper installed from a prebuilt .deb (`069d32e9`, `fc697869`)

**Core**

- Installs with the text debian-installer in live mode instead of Calamares (ADR-010) (`3cb5572a`)
- Core-specific GRUB menu (`032a95b6`)

**All editions**

- Edition-themed login greeting (motd), with themes for desktop and gaming (`f7b2362c`)
- Installed systems get deb.debian.org sources with security, updates and backports instead of the build mirror (`1a4df25c`)
- The debian-installer initrd and the medium label in .disk/info carry ShopnoOS branding (`fa4899a9`, `6ead6876`)

### 🐛 Bug Fixes

- Installs done with debian-installer keep the live image's apt sources instead of a cdrom-only sources.list (`68865eb1`)
- DNS: the build uses the host's resolver, and installed systems let systemd-resolved manage DNS with fallback servers (`eb71a734`)
- /etc/os-release is a symlink again (`669ad6cd`)
- Bug tracker URLs point at fa-saikat/shopno-os issues (`ec61ed39`)
- RetroArch config dirs are no longer broken submodules (`a8b26ec5`)
- The vendored isolinux.bin is dropped (`59626e73`)

### 🔧 Build System

- Edition skel overlays, merged after the flavor skel (`b9866f99`, `667e3a14`)
- *.hook.binary hooks are merged from all layers (`22cb155c`)
- Serial console and CI boot-marker support for boot testing (`844061c8`, `e2e43953`, `b4d6914b`, `ed9f2ac6`)
- Container build image: APT sources with the project repo, security pocket, Tier-B package denies, and a determinism check (`4541661a`, `5db4a9bf`, `46703f76`, `f3fc7a9f`)
- clean.sh checks privileges and verifies removal (`8c5bda11`)
- Interactive environment setup script for a fresh build machine (`b8fbe718`)

### 🤖 CI/CD

- ISO builds run on a self-hosted runner, with a core and desktop matrix and a blocking QEMU boot gate (`f400e015`, `e2a707aa`, `30d37500`)
- Container build, smoke test, SBOM, vulnerability scan, keyless signing and SLSA attestation (`dfb89e37`, `a6ed0be7`, `39f0ae21`)
- Third-party actions pinned by commit SHA (`ad826e59`)
- main, dev and v* tags are mirrored to JaduPC/shopno-os; lint, ISO and container jobs run only in fa-saikat/shopno-os (`5a96af85`, `8ad42dd2`, `4e84c89a`)

### 📖 Documentation

- ADR-001 to ADR-010, covering profile composition, the boot gate, local releases, ISO-only distribution, the container supply chain and the core installer
- Project README, container guide, release-process and CI/CD docs updated to match the deployed pipeline
- GitHub releases carry source only; ISOs are published on the JaduPC mirror (`c5f9d0fc`, `cd6002e6`)

---
**Full diff:** [v2.2...v2.3](https://github.com/fa-saikat/shopno-os/compare/v2.2...v2.3)

## [2.2] - 2026-09-13

### ✨ Features

- add gaming in VALID_EDITIONS array (`61283adf`)

### 🐛 Bug Fixes

- duplicate package name (`35fc0744`)
- check duplicate packages edition and flavor wise (`3de151a9`)
- sync branding-guide.md with URL_* convention in urls.env (`e70e2af9`)
- changelog-gen minor fix (`0ea51ac5`)
- remove profile build dir after clean (`714286c6`)
- grub background (`524df7ad`)
- grub background source location (`4847bc8b`)
- grub assests path (`288db5fb`)
- google chrome multiple sources files (`7a0e25e1`)
- post dpkg hook locking apt for too long (`bde6ad7e`)
- iso signing (`02303270`)
- Grub conflict while building iso (`051ea7e0`)
- Unbound variable (`a899cfa4`)

### 📖 Documentation

- release process section 4.2 sanity check (`f6783a59`)
- new naming law (`d36ddf31`)
- add stubs for secret env files (`f30aa674`)
- add secret management (`33d7acee`)
- Add git-guide (`d26301f3`)
- add CHANGELOG.md [v2.0] (`0caa0fa9`)
- initial commit (`3a3cf4c8`)

### 🔧 Build System

- add and source secret.sh in build pipeline (`f46a3038`)

### 🧹 Maintenance

- improve setting keybinding mechanism (`3f9b8af5`)
- remove em dash (`b65483a1`)
- clean up welcome app source (`62abb1f7`)
- excluded heavy assets from tracking (`566054b0`)
- add rules to ignore secrets (`484334ba`)
- Removed chrony from package list (`2081ff1d`)
- Remove duplicate package entries (`6d98ffd5`)
- Inclusion of profile name and output directory (`fd251351`)
- exclusion of chroot/, binary/ (`7fdc0a92`)
- initial hooks for base, each editions and flavors (`5202d496`)
- root files — README, CHANGELOG, LICENSE, direnv (`ca69f6f8`)
- add .gitignore and .gitattributes (`e9e8d862`)

### 📦 Other

-  enforce golden rule within single layer instance (`57489e30`)
- add knwon safe exclusion (`7c956a60`)
- scaffolders to use ${ISO_PREFIX} (`3bc14f0e`)
- change guard variable prefix to `OS_` (`f527462c`)
- update hook to configure edition specific desktop (`5d359c98`)
- improve rom installer visuals, add welcome app icon (`2a2c8996`)
- mode selection window hotkey (`79ee0413`)
- add edition gaming (`6d705955`)
- add profile shopno-os-gaming-xfce (`ea6f120d`)
- copy edition specific background (`dafae267`)
- bump version to 2.1 (`8141b5d9`)
- shopno-os goodies (`1a029f9d`)
- improve os-release generation (`6d606516`)
- minor tweaks (`ad468e82`)
- add support url and distro trademark (`fb30b15d`)
- Update repository root variable name (`cdf5320d`)
- Add new edition and flavor (`1a457ece`)
- Add lint test suite (`6c96614f`)
- Initial test pipeline stubs (`c5d668a6`)
- Add build scripts (`b52064f0`)
- initial vm and nvidia layer stubs (`6d9794fa`)
- calamares installer config and welcome-app stub (`d9e96e56`)
- initial build pipeline — build.sh, brand.sh, common.sh (`f3a1716d`)
- initial build profiles for desktop-xfce (`d011ee05`)
- initial XFCE flavor package lists and config (`fdc5922f`)
- initial desktop edition package lists and hooks (`be1befa2`)
- initial package lists, config, hooks, preseed (`5d6bcd3c`)
- initial identity, assets and branding files (`77335b22`)


## [2.1] — 2026-06-02

### ✨ Features

- add gaming in VALID_EDITIONS array (`61283adf`)

### 🐛 Bug Fixes

- grub background (`524df7ad`)
- grub background source location (`4847bc8b`)
- grub assests path (`288db5fb`)
- google chrome multiple sources files (`7a0e25e1`)
- post dpkg hook locking apt for too long (`bde6ad7e`)
- iso signing (`02303270`)
- Grub conflict while building iso (`051ea7e0`)
- Unbound variable (`a899cfa4`)

### 📖 Documentation

- new naming law (`d36ddf31`)
- add stubs for secret env files (`f30aa674`)
- add secret management (`33d7acee`)
- Add git-guide (`d26301f3`)
- add CHANGELOG.md [v2.0] (`0caa0fa9`)
- initial commit (`3a3cf4c8`)

### 🔧 Build System

- add and source secret.sh in build pipeline (`f46a3038`)

### 🧹 Maintenance

- add rules to ignore secrets (`484334ba`)
- Removed chrony from package list (`2081ff1d`)
- Remove duplicate package entries (`6d98ffd5`)
- Inclusion of profile name and output directory (`fd251351`)
- exclusion of chroot/, binary/ (`7fdc0a92`)
- initial hooks for base, each editions and flavors (`5202d496`)
- root files — README, CHANGELOG, LICENSE, direnv (`ca69f6f8`)
- add .gitignore and .gitattributes (`e9e8d862`)

### 📦 Other

- shopno-os goodies (`1a029f9d`)
- improve os-release generation (`6d606516`)
- minor tweaks (`ad468e82`)
- add support url and distro trademark (`fb30b15d`)
- Update repository root variable name (`cdf5320d`)
- Add new edition and flavor (`1a457ece`)
- Add lint test suite (`6c96614f`)
- Initial test pipeline stubs (`c5d668a6`)
- Add build scripts (`b52064f0`)
- initial vm and nvidia layer stubs (`6d9794fa`)
- calamares installer config and welcome-app stub (`d9e96e56`)
- initial build pipeline — build.sh, brand.sh, common.sh (`f3a1716d`)
- initial build profiles for desktop-xfce (`d011ee05`)
- initial XFCE flavor package lists and config (`fdc5922f`)
- initial desktop edition package lists and hooks (`be1befa2`)
- initial package lists, config, hooks, preseed (`5d6bcd3c`)
- initial identity, assets and branding files (`77335b22`)


## [2.0] - 2026-03-16

### Documentation

- initial commit (`3a3cf4c8`)

### Maintenance

- initial hooks for base, each editions and flavors (`5202d496`)
- root files — README, CHANGELOG, LICENSE, direnv (`ca69f6f8`)
- add .gitignore and .gitattributes (`e9e8d862`)

### Other

- initial vm and nvidia layer stubs (`6d9794fa`)
- calamares installer config and welcome-app stub (`d9e96e56`)
- initial build pipeline — build.sh, brand.sh, common.sh (`f3a1716d`)
- initial build profiles for desktop-xfce (`d011ee05`)
- initial XFCE flavor package lists and config (`fdc5922f`)
- initial desktop edition package lists and hooks (`be1befa2`)
- initial package lists, config, hooks, preseed (`5d6bcd3c`)
- initial identity, assets and branding files (`77335b22`)

