# Padavan 4.4 - The "Dave Täht Tribute" Edition

> **"When you miss Dave, modprobe sch_cake!"**
> — *A tribute to the soul of bufferbloat mitigation.*

---

## 🕊️ In Loving Memory of Dave Täht

### **"穿越時空的夢想，我來幫他實現！"**
**(Making a time-traveling dream come true!)**
### **🇹🇼：靈魂永駐，精神長存**
### **🇺🇸：May his soul find eternal peace, and his spirit live on forever.**

This project is dedicated to **Dave Täht**, a visionary whose work on **FQ-CoDel**, **CAKE**, and **LibreQoS** changed the internet forever. We are fulfilling a wish he made 5 years ago on Reddit:

### ❝ Help port the code to more chipsets. ❞

> **The BEST engineering result I ever had:**
> Essentially the summation of my 16+ years of work to that point on making wifi better. Unpatented. Please share and enjoy.
> **Help port the code to more chipsets.**
>
> — *Dave Täht (Reddit, 5 years ago)*

*Original Source:* [Reddit - r/Starlink](https://www.reddit.com/r/Starlink/comments/okmx3x/comment/h61unnn/)

Dave turned down numerous lucrative contracts to keep his code **Free and Open Source**. He valued global impact over prestige. Because of him, millions of devices—from Starlink satellites to rural ISP routers—deliver smoother connectivity, enabling telemedicine, education, and connection for the underserved.

**May his soul find eternal peace, and his spirit live on forever in our routers.**

[👉 Read the full Memorial at LibreQoS](https://libreqos.io/2025/04/01/in-loving-memory-of-dave/)

---

## 🌟 Project Philosophy: Open & Accessible

### **「永遠保持開放且開源的精神」**
**(Forever maintaining an open and open-source spirit)**

This repository is based on the original `rt-n56u` with the latest **MTK 4.4.198 kernel**. We believe in giving power back to the user while honoring the giants who paved the way.

1.  **CAKE Integration**: By default, we aim to support the `sch_cake` module (where applicable) to honor Dave's legacy.
2.  **Easy Multi-Model Support**: Support for a wide range of devices, keeping them alive and fast.
3.  **Flexible Language System**:
    * **English Base**: The firmware defaults to a clean, English-only interface.
    * **Custom Language Packs**: You can select *one* additional language (Traditional Chinese, Russian, etc.) during the build process to keep the firmware lightweight yet localized.

---

## 🗣️ Tributes from the Community

> "Dave’s impact on society was immense... He wanted, ultimately, to speed up the internet so that a drummer in London could play in real-time with a guitarist in Los Angeles."
> — **Steven J. Vaughan-Nichols**

> "I will miss him but will be always grateful to have known him."
> — **Vint Cerf**

> "Without him, Netflix and similar services might still be plagued by glitches and stutters."
> — **Eric S. Raymond**

### See also:

* [LibreQoS Project](https://libreqos.io/)
* [LibreQoS Github Project](https://github.com/LibreQoE/LibreQoS/)
* [Dave's Talks: Reducing Network Latency (GOTO 2024)](https://www.youtube.com/watch?v=UDo9W4tt69c)

![Dave Täht Tribute](https://i0.wp.com/libreqos.io/wp-content/uploads/2025/04/WISPAPALOOZA-2024_6.jpg)
*[Image Credit: LibreQoS]*

---

## 🚀 Supported Devices (Kernel 4.4)

We have expanded support to cover a wide range of MT7621 devices. Pick the one you love!

| Brand | Models |
| :--- | :--- |
| **Phicomm** | K2P, K2P-USB, K2P-NANO |
| **Xiaomi** | MI-R3P, MI-R3G, RM2100 |
| **JCG** | JCG-Q20, JCG-AC860M, JCG-836PRO, JCG-Y2 |
| **D-Link** | DIR-878, DIR-882 |
| **Others** | CR660x, MR2600, NETGEAR-BZV, XY-C1, NEWIFI3 |

---

## ✨ Features

* **Kernel**: Based on Linux 4.4.198 (MTK fork).
* **Wireless**: Supports MT7615D/MT7615N/MT7915D chips.
* **Performance & Queue Management**:
    * **CAKE / FQ_CoDel** (The Dave Täht Special) - mitigating bufferbloat.
    * Hardware NAT (hwnat) with legacy drivers.
    * QCA Shortcut-FE support.
* **Network**:
    * IPv6 NAT based on netfilter.
    * **WireGuard** integrated in kernel.
    * Fullcone NAT (by Chion82).
* **Control**: LED & GPIO control via sysfs.

---

## 🛠️ Compilation Guide

We support both **GitHub Actions** (for ease of use) and **Manual Compilation**.

### Option A: GitHub Actions (Recommended)

## 🛠️ Usage (How to Build)

This workflow uses **GitHub Actions** to build firmware in the cloud. You don't need a Linux PC!

### 1. Start the Workflow
1.  Go to the **[Actions](../../actions)** tab in this repository.
2.  Select the workflow **"Custom-Router-Build-Final-Fix"** (or `CI.yml`) from the left sidebar.
3.  Click the **Run workflow** button on the right.

### 2. Configure Your Build (Interactive Inputs)
You will see a menu with the following options. **Customize it to your liking!**

* **target_select** (Required):
    * Choose your router model from the list (e.g., `K2P`, `MI-R3P`, `RM2100`...).
    * *Note: This list includes all supported 4.4 kernel devices.*

* **language_select** (New!):
    * `English_Only`: Keeps the interface clean and lightweight.
    * `CN (繁體中文)` / `RU` / `ES` etc.: Automatically adds your selected language pack.

* **nanoversion**:
    * `true`: Performs extreme size optimization (removes unused modules) to fit into small flash memory.

* **customization**:
    * Set your default WiFi SSID, Password, and Login credentials here (JSON format).

* **toolchain_select**:
    * Choose between `Default` (hanwckf/linux-4.4) or `Padavan-NG` toolchains.

### 3. Wait & Download
1.  Click the green **Run workflow** button.
2.  The build process usually takes **15 to 40 minutes**.
3.  When the circle turns **Green (Success)**, click on the task.
4.  Scroll down to the **Artifacts** section to download your firmware `.zip` file.

Just go to the `Actions` tab in this repository, select `Custom-Router-Build-Final-Fix`, and choose:

1.  **Target Model**: (e.g., `K2P`, `MI-R3P`, `RM2100`...)
2.  **Language**: (e.g., `English_Only` or `CN-繁體中文`)
3.  **Toolchain**: (Default or Padavan-NG)

The system will automatically apply the **CAKE Patch**, configure your language, and build your firmware.

### Option B: Manual Compilation

#### 1. Install Dependencies

**Find out your OS:**

- Compilation step
  - Install dependencies
    ```sh
    # Debian/Ubuntu
    sudo apt install unzip libtool-bin curl cmake gperf gawk flex bison nano xxd \
        fakeroot kmod cpio git python3-docutils gettext automake autopoint \
        texinfo build-essential help2man pkg-config zlib1g-dev libgmp3-dev \
        libmpc-dev libmpfr-dev libncurses5-dev libltdl-dev wget libc-dev-bin

    # Archlinux/Manjaro
    sudo pacman -Syu --needed git base-devel cmake gperf ncurses libmpc \
            gmp python-docutils vim rpcsvc-proto fakeroot cpio help2man

    # Alpine
    sudo apk add make gcc g++ cpio curl wget nano xxd kmod \
        pkgconfig rpcgen fakeroot ncurses bash patch \
        bsd-compat-headers python2 python3 zlib-dev \
        automake gettext gettext-dev autoconf bison \
        flex coreutils cmake git libtool gawk sudo
    ```
  - Clone source code
    ```sh
    git clone https://github.com/hanwckf/padavan-4.4.git
    ```
  - Prepare toolchain
    ```sh
    cd padavan-4.4/toolchain-mipsel

    # (Recommend) Download prebuilt toolchain for x86_64 or aarch64 host
    ./dl_toolchain.sh

    # or build toolchain with crosstool-ng
    # ./build_toolchain
    ```
  - Modify template file and start compiling
    ```sh
    cd padavan-4.4/trunk

    # (Optional) Modify template file
    # nano configs/templates/K2P.config

    # Start compiling
    fakeroot ./build_firmware_modify K2P

    # To build firmware for other devices, clean the tree after previous build
    ./clear_tree
    ```

- Manuals
  - Controlling GPIO and LEDs via sysfs
  - How to use NAND RWFS partition
  - How to use IPv6 NAT and fullcone NAT
  - How to add new device support with device tree

---
Original readme below
# padavan-4.4 #

This project is based on original rt-n56u with latest mtk 4.4.198 kernel, which is fetch from D-LINK GPL code.

- Features
  - Based on 4.4.198 Linux kernel
  - Support MT7621 based devices
  - Support MT7615D/MT7615N/MT7915D wireless chips
  - Support raeth and mt7621 hwnat with legency driver
  - Support qca shortcut-fe
  - Support IPv6 NAT based on netfilter
  - Support WireGuard integrated in kernel
  - Support fullcone NAT (by Chion82)
  - Support LED&GPIO control via sysfs

- WIP
  - 802.11kvr and mtkiappd roam functions
  - IPTV related functions

- Supported devices
  - CR660x
  - JCG-Q20
  - JCG-AC860M
  - JCG-836PRO
  - JCG-Y2
  - DIR-878
  - DIR-882
  - K2P
  - K2P-USB
  - NETGEAR-BZV
  - MR2600
  - MI-R3P
  - XY-C1

- Compilation step
  - Install dependencies
    ```sh
    # Debian/Ubuntu
    sudo apt install unzip libtool-bin curl cmake gperf gawk flex bison nano xxd \
        fakeroot kmod cpio git python3-docutils gettext automake autopoint \
        texinfo build-essential help2man pkg-config zlib1g-dev libgmp3-dev \
        libmpc-dev libmpfr-dev libncurses5-dev libltdl-dev wget libc-dev-bin

    # Archlinux/Manjaro
    sudo pacman -Syu --needed git base-devel cmake gperf ncurses libmpc \
            gmp python-docutils vim rpcsvc-proto fakeroot cpio help2man

    # Alpine
    sudo apk add make gcc g++ cpio curl wget nano xxd kmod \
        pkgconfig rpcgen fakeroot ncurses bash patch \
        bsd-compat-headers python2 python3 zlib-dev \
        automake gettext gettext-dev autoconf bison \
        flex coreutils cmake git libtool gawk sudo
    ```
  - Clone source code
    ```sh
    git clone https://github.com/hanwckf/padavan-4.4.git
    ```
  - Prepare toolchain
    ```sh
    cd padavan-4.4/toolchain-mipsel

    # (Recommend) Download prebuilt toolchain for x86_64 or aarch64 host
    ./dl_toolchain.sh

    # or build toolchain with crosstool-ng
    # ./build_toolchain
    ```
  - Modify template file and start compiling
    ```sh
    cd padavan-4.4/trunk

    # (Optional) Modify template file
    # nano configs/templates/K2P.config

    # Start compiling
    fakeroot ./build_firmware_modify K2P

    # To build firmware for other devices, clean the tree after previous build
    ./clear_tree
    ```

- Manuals
  - Controlling GPIO and LEDs via sysfs
  - How to use NAND RWFS partition
  - How to use IPv6 NAT and fullcone NAT
  - How to add new device support with device tree
