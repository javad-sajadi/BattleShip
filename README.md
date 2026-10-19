# BattleShip: Networked Multiplayer Naval Strategy Game

[![Java](https://img.shields.io/badge/Java-11%2B-orange.svg)](https://www.oracle.com/java/)
[![Gradle](https://img.shields.io/badge/Gradle-Build%20Tool-blue.svg)](https://gradle.org/)
[![Architecture](https://img.shields.io/badge/Architecture-Client--Server%20Sockets-brightgreen.svg)](https://en.wikipedia.org/wiki/Client%E2%80%93server_model)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

A full-featured networked multiplayer **Battleship** strategy game built in Java featuring concurrent TCP socket networking, persistent player profiles, interactive Swing graphical interfaces, and live match spectating (streaming).

---

## 📌 Architecture & Features

### 1. Multi-Threaded TCP Server (`server/`)
- **Concurrent Connections:** Manages multiple concurrent player connections via `ServerSideConnection` threads.
- **Account & State Persistence:** Tracks player authentication, win-loss statistics, and leaderboard rankings via `FileManager`.
- **Match Synchronization:** Synchronizes naval grids, shot coordinates, hits, misses, and fleet status between competing clients.

### 2. Client Graphical User Interface (`Client/view/`)
- **Authentication:** Dedicated `LoginView` and `RegistrationView` with event-driven form validation.
- **Ship Placement & Shuffling:** Visual `ShufflePage` and `ShipPaint` enabling manual positioning or randomized fleet layout across grid cells.
- **Battlefield Arena:** Dual grid layout (`GameBoard` and `GamePaint`) displaying your own fleet defense alongside the fog-of-war targeting radar.
- **Spectator Mode:** Live match broadcasting (`StreamView` and `GamePage2`) allowing other connected clients to spectate active battles.

---

## 🚢 Naval Fleet Specifications

| Ship Class | Size (Grid Units) | Fleet Quantity |
| :--- | :---: | :---: |
| **Battleship** | 4 cells | 1 |
| **Cruiser** | 3 cells | 2 |
| **Destroyer** | 2 cells | 3 |
| **Submarine** | 1 cell | 4 |

---

## 🚀 Quick Start

### 1. Requirements
- **Java Development Kit (JDK):** Version 11 or higher
- **Gradle:** Bundled with repository via `gradlew`

### 2. Build the Project
```bash
# On Windows
./gradlew build

# On Linux/macOS
./gradlew build
```

### 3. Launch Server
Start the central game server to accept socket connections:
```bash
./gradlew runServer
```
*(Or execute `server.Server` directly from your IDE).*

### 4. Launch Client Players
In separate terminal windows or machines:
```bash
./gradlew runClient
```
*(Or execute `Client.Client` to open the Swing GUI).*

---

## 📁 Repository Structure

```
.
├── src/main/java/
│   ├── Client/                     # Client application & Swing GUI
│   │   ├── Client.java             # Client entry point
│   │   ├── ClientSideConnection.java # Network socket listener thread
│   │   ├── logic/                  # Client-side fleet & position representations
│   │   └── view/                   # Swing GUI views (Login, Home, GameBoard, Stream)
│   └── server/                     # Central multiplayer game server
│       ├── Server.java             # Socket listener & thread dispatcher
│       ├── ServerSideConnection.java # Client session coordinator
│       └── logic/                  # Turn validation, collision detection & win logic
├── build.gradle                    # Gradle dependency & task definitions
├── gradlew / gradlew.bat           # Cross-platform Gradle wrappers
└── .gitignore                      # Clean Git ignore rules (build/, .gradle/, .idea/)
```

---

## 📜 Author & License
- **Author:** [Javad Sajadi](https://github.com/javad-sajadi)
- **License:** MIT License
