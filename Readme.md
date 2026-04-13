
---

# 📋 Klipboard
**The Bridge for Your Clipboard.** A cross-platform clipboard history manager and synchronizer built with **Kotlin Multiplatform (KMP)** and **Ktor**.

## 🚀 The Problem
Universal Clipboard is a dream if you live strictly in the Apple ecosystem. However, the second you introduce a **Windows** workstation, a **Linux** server, or an **Android** tablet, that seamless "copy-paste" flow breaks. 

**Klipboard** aims to be the universal glue that allows you to:
* Copy code on **Windows** 🪟 and paste on **macOS** 🍎.
* Copy a URL on **Android** 🤖 and paste on an **iPad** 📱.
* Maintain a searchable history of your clips across all devices.

---

## 🛠 Tech Stack
This project serves as a comprehensive practice ground for the modern Kotlin ecosystem:
* **Language:** Kotlin 2.1.0+
* **UI Framework:** [Compose Multiplatform](https://www.jetbrains.com/lp/compose-multiplatform/) (Android, iOS, Desktop)
* **Networking:** [Ktor](https://ktor.io/) (Client for syncing, Server for receiving)
* **Dependency Injection:** Koin
* **Local Storage:** SQLDelight (for clipboard history)
* **Concurrency:** Kotlin Coroutines & Flow

---

## 🏗 Architecture
Klipboard uses a shared logic approach to handle the "heavy lifting" while letting each platform handle its native Clipboard Manager API.



### Core Components
1.  **Shared Module:** Contains the Ktor logic, data encryption, and the shared ViewModel.
2.  **Platform Adapters:** * **macOS/iOS:** `NSPasteboard`
    * **Windows:** Win32 API / `Clipboard`
    * **Android:** `ClipboardManager`
3.  **Ktor Sync Engine:** A lightweight background service that listens for clipboard changes and broadcasts them to your authorized devices.

---

## 🌟 Key Features
* **Instant Sync:** Real-time clipboard synchronization using Ktor WebSockets.
* **History Vault:** Local database of your last 50+ copies.
* **Secure:** Optional AES encryption for data in transit across your local network.
* **Multi-Format:** Support for plain text, URLs, and (eventually) images.

---

## 📂 Project Structure
```text
.
├── composeApp          # Shared UI (Compose Multiplatform)
├── iosApp              # iOS specific entry point
├── server              # Optional: Ktor backend for cloud-sync
└── shared              # Core Logic (Ktor Client, SQLDelight, Business Logic)
    ├── commonMain      # Shared code
    ├── androidMain     # Android specific Clipboard API
    ├── desktopMain     # Windows/macOS specific Clipboard API
    └── iosMain         # iOS specific Clipboard API
```

---

## 🚦 Getting Started

### Prerequisites
* Android Studio (latest) or IntelliJ IDEA.
* Xcode (for iOS/macOS targets).
* Kotlin Multiplatform plugin installed.

### Setup
1.  **Clone the repo:**
    ```bash
    git clone https://github.com/yourusername/klipboard.git
    ```
2.  **Run the Desktop app:**
    ```bash
    ./gradlew :composeApp:run
    ```
3.  **Run the Android app:**
    Select your device/emulator and hit **Run**.

---

## 🧪 Practice Goals (KMP + Ktor)
- [ ] Implement a **Ktor WebSocket** to broadcast clipboard strings.
- [ ] Use **Expect/Actual** to access native clipboard services.
- [ ] Handle **Network Discovery** (mDNS) so devices find each other without typing IP addresses.
- [ ] Practice **State Management** using Kotlin Flows to update the UI when the clipboard changes.

---

## 🛡 License
Distributed under the MIT License. See `LICENSE` for more information.

---

**Happy Coding!** If you run into issues with the Ktor engine or the macOS `NSPasteboard` implementation, feel free to open an issue.