# Pulse 📡

> **Offline-First Peer-to-Peer Messaging & File Sharing**  
> *No internet. No accounts. No servers. Just nearby devices communicating directly.*

---

## 🌟 Overview

**Pulse** is a decentralized, offline-first mobile application designed to enable nearby devices to discover each other, establish secure direct connections, exchange messages, and transfer files without relying on internet connectivity, cellular networks, SIM cards, or centralized cloud servers.

Whether you're in a remote outdoor area, a crowded conference hall, a campus with spotty Wi-Fi, or an emergency scenario with compromised infrastructure, Pulse creates an ad-hoc local network right from your pocket.

---

## ✨ Key Features

- 📴 **100% Offline & Accountless:** No phone numbers, emails, or OTPs. Cryptographic local identity generated and stored directly on your device.
- 🎯 **Radar Discovery:** Visual, animated radar interface using Bluetooth and Wi-Fi to scan and detect nearby peers.
- 💬 **Reliable 1-on-1 Messaging:** Full offline message queue, delivery acknowledgments (Pending, Delivered, Read), sequence ordering, and automatic sync upon reconnection.
- 📁 **Resumable File Sharing:** High-speed peer-to-peer file transfer with SHA-256 chunk validation and automatic pause/resume on connection drop.
- 🔒 **Local-First & Secure:** SQLite database as the single source of truth, cryptographic public-key peer verification (TOFU), and secure key storage.

---

## 🛠 Tech Stack

| Layer | Technology |
|---|---|
| **Framework** | [React Native](https://reactnative.dev/) + [Expo](https://expo.dev/) (TypeScript) |
| **P2P Networking** | [Google Nearby Connections API](https://developers.google.com/nearby/connections/overview) (Android) |
| **Native Integration** | Turbo Native Modules (Kotlin / New Architecture) |
| **Local Database** | SQLite (Local-first persistence) |
| **State Management** | [Zustand](https://github.com/pmndrs/zustand) (Transient UI & session state) |
| **Animations & UI** | [Reanimated](https://docs.swmansion.com/react-native-reanimated/) + [Gesture Handler](https://docs.swmansion.com/react-native-gesture-handler/) |

---

## 🏗 Architecture at a Glance

Pulse follows a layered, local-first architecture ensuring the UI stays fast and responsive:

```text
┌──────────────────────────────────────────────┐
│              PRESENTATION LAYER              │
│       Radar • Chats • Transfers • Profile    │
│            React Native + Reanimated         │
└──────────────────────┬───────────────────────┘
                       │
┌──────────────────────▼───────────────────────┐
│              APPLICATION LAYER               │
│  Discovery • Connection • Messaging • Sync   │
└──────────────┬───────────────────────────────┘
               │
       ┌───────┴───────────────┐
       ▼                       ▼
┌───────────────┐     ┌────────────────────────┐
│  PERSISTENCE  │     │   NETWORK ABSTRACTION  │
│    SQLite     │     │ P2P Transport Protocol │
└───────────────┘     └───────────┬────────────┘
                                  │
                                  ▼
                      ┌────────────────────────┐
                      │     NATIVE LAYER       │
                      │ Nearby Connections SDK │
                      │  (Turbo Native Module) │
                      └────────────────────────┘
```

---

## 🗺 Development Roadmap

- [ ] **Phase 0: Technical Feasibility** — Validate Nearby Connections P2P transport and payload exchange on physical devices.
- [ ] **Phase 1: Foundation & Identity** — Offline profile creation, SQLite schemas, migrations, and permission management.
- [ ] **Phase 2: Discovery & Handshake** — Animated radar interface, advertising/discovery lifecycle, and connection negotiation.
- [ ] **Phase 3: Offline Messaging & Sync** — P2P envelope protocol, persistent outbox, delivery receipts, and reconnect sync.
- [ ] **Phase 4: Resumable File Transfers** — Chunk-based binary transfers, SHA-256 checksums, and interrupt recovery.
- [ ] **Phase 5: Hardening & Security** — Retry policies, battery optimization, and peer trust verification.

---

## 🚀 Getting Started

### Prerequisites

- Node.js (v18+)
- Android SDK & configured emulator or physical Android devices (Recommended for testing Nearby Connections)

### Installation

```bash
# Clone the repository
git clone https://github.com/zarasana-labs/pulse-chat.git
cd pulse-chat

# Install dependencies
npm install

# Start the Expo development server
npx expo start
```

> **Note:** Testing peer-to-peer discovery and data transfer requires testing on **physical Android devices** with Bluetooth and Wi-Fi enabled.

---

## 📄 License

Private repository — © [Zarasana Labs](https://github.com/zarasana-labs). All rights reserved.
