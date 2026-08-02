# ImmortalWrt-Builder-24.10 🚀

![GitHub Workflow Status](https://img.shields.io/github/workflow/status/hhCodingCat/ImWRT-798X/ImmortalWrt-24.10-6.6固件构建?label=Build%20Status)
![License](https://img.shields.io/github/license/hhCodingCat/ImWRT-798X?color=blue)

This project provides a **GitHub Actions workflow** for automatically building [ImmortalWrt 24.10](https://github.com/padavanonly/immortalwrt-mt798x-24.10) firmware for devices based on the **MediaTek MT7981** chipset. It supports regularly checking for source updates, building firmware for multiple device models, and uploading firmware files to **GitHub Releases** and **WebDAV**. Select a device model from an intuitive **dropdown list**—the process is simple and especially suitable for beginners and users with no prior experience.

---

## ✨ Highlights

- **Supported devices** 📡:
  - China Mobile RAX3000M NAND
  - China Mobile RAX3000M eMMC
  - Cudy AP3000 AX3000
  - Cudy AP3000 Outdoor Edition
  - Cudy M3000 AX3000
  - Cudy RE3000 AX3000 Repeater
  - Cudy TR3000 AX3000
  - Cudy TR3000 AX3000 256MB
  - Cudy WR3000 AX3000
  - Cudy WR3000S AX3000 Enhanced Edition
  - GL.iNet Mango AX MT2500
  - GL.iNet Beryl AX MT3000
  - GL.iNet X3000 LTE
  - GL.iNet XE3000 Industrial LTE
  - H3C NX30 Pro Magic Router
  - Huasifei WH3000 Pro
  - Huasifei WH3000 eMMC
  - JCG Q30 Pro AX3000
  - Livinet ZR3020 AX3000
  - Routerich AX3000
  - Routerich AX3000 V1
  - Xiaomi AX3000T
  - Xiaomi WR30U Stock Firmware
  - Redmi AX6000 Stock Firmware
  - Zyxel EX5601-T0 Stock Firmware
  - Zyxel NWA50AX Pro AP

- **Automatic builds** ⏰: Every Friday at **15:00 Beijing time (07:00 UTC)**, the source repository is checked for updates. When new commits are detected, firmware is automatically built for all supported devices.
- **5G 25 dB enhancement** 📶: Supports enabling 5G high-power mode (enabled by default; manual builds let you choose whether to enable it).
- **Firmware uploads** 📤: After a build finishes, `sysupgrade.bin` and `factory.bin` files are uploaded to GitHub Releases and WebDAV, together with a README.md information file.
- **Cleanup** 🧹: Keeps the latest **5 GitHub Releases** and workflow runs from the **last 7 days or at least 3 runs**, automatically deleting older records to save space.
- **Features** 💻:
  - Improved network performance and stability
  - Android USB tethering support
  - USB network adapter and USB Wi-Fi support
  - MediaTek HNAT hardware acceleration
  - Ksmbd file sharing
  - Default management address: `192.168.2.1`, with no password
- **Beginner-friendly** 🖱️: Choose a device model from the **GitHub Actions dropdown list** without manually editing configuration files. The process is straightforward even for first-time users.

---

## 🛠️ How to Use

### 1. Configure the repository

1. Fork or clone this repository to your GitHub account: [hhCodingCat/ImWRT-798X](https://github.com/hhCodingCat/ImWRT-798X).
2. In the repository, open **Settings > Secrets and variables > Actions** and add these Secrets:
   - `WEBDAV_URL`: WebDAV server address (for example, `https://dav.example.com/firmware/`)
   - `WEBDAV_USERNAME`: WebDAV username
   - `WEBDAV_PASSWORD`: WebDAV password

### 2. Start a manual build

1. Open the repository's **Actions** page and select the `ImmortalWrt-24.10-6.6固件构建` workflow.
2. Click **Run workflow** and use the **dropdown list** to select:
   - `device_model`: Target device model (select it directly without memorizing complex codes)
   - `enable_5g_25db`: Whether to enable 5G 25 dB enhancement (enabled by default)
   - Optional: custom `repo_url` and `repo_branch`
3. Start the workflow. The firmware will be built automatically and uploaded to GitHub Releases and WebDAV.

### 3. Scheduled builds

- No manual action is required. Every Friday at **15:00 Beijing time (07:00 UTC)**, the workflow checks the `openwrt-24.10-6.6` branch of [padavanonly/immortalwrt-mt798x-24.10](https://github.com/padavanonly/immortalwrt-mt798x-24.10).
- When updates are detected, firmware is automatically built for all supported device models and uploaded.

### 4. Download the firmware

- **GitHub Releases** 📦: Open the repository's **Releases** page and find a tag such as `ImmortalWrt-24.10-<device_code>-<version>`. Download `sysupgrade.bin`, `factory.bin`, and `README.md`.
- **WebDAV** ☁️: Access the firmware through the configured WebDAV server. Files are named `<device_code>_25dB-on_<version>_<type>.bin`.

### 5. Flash the firmware

1. Confirm that the device model matches the firmware.
2. Back up the device's existing configuration.
3. Flash the firmware through the web interface or SSH:
   - `sysupgrade.bin` (keeps the existing configuration)
   - `factory.bin` (fresh installation)
4. Make sure the power supply is stable during the upgrade and do not interrupt the process.

---

## ⚠️ Important Notes

- **Risk warning**: Flashing firmware can brick a device. Proceed carefully and make sure the firmware exactly matches the device model.
- **WebDAV configuration**: Make sure the WebDAV server is accessible and the Secrets are configured correctly; otherwise, uploads may fail.
- **Build time**: Building a single device may take **1–2 hours**, depending on GitHub Actions resources.
- **5G 25 dB enhancement**: High-power mode may be restricted by local regulations. Confirm that its use is legal in your region.
- **Management address**: The default firmware IP address is `192.168.2.1`, with no password. Check your network settings after upgrading.

---

## 📚 Source Code

- This workflow is based on [padavanonly/immortalwrt-mt798x-24.10](https://github.com/padavanonly/immortalwrt-mt798x-24.10).
- Branch: `openwrt-24.10-6.6`.
- Repository: [hhCodingCat/ImWRT-798X](https://github.com/hhCodingCat/ImWRT-798X).

---

## 🙏 Acknowledgements

Special thanks to the following authors and contributors:

- **[P3TERX](https://p3terx.com)**: Provided the initial framework for the `diy-part1.sh` and `diy-part2.sh` scripts, which was essential to the project's automated build process.
- **[padavanonly](https://github.com/padavanonly)**: Maintains the ImmortalWrt MT798x 24.10 source repository and provides the core firmware source code.
- **ImmortalWrt community**: Thanks to the community developers for their continued work on performance optimization and feature improvements.

---

## 🤝 Contributing

Issues and **Pull Requests** are welcome. Help improve the workflow and add new features so we can continue developing this project together!

---

## 📄 License

This project is released under the **MIT License**. See [LICENSE](LICENSE) for details.
