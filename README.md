# Local Anti-Cheat Server (LACS)

A lightweight, local server-based anti-cheat system prototype designed to run alongside games on the user's PC. This system aims to provide fast cheat detection and banning by prioritizing small data packets and analyzing user input, with potential for cross-platform compatibility (Windows/Linux via Proton).

## ⚠️ Important Note

This is a **prototype** and a **standalone system**. It is **not directly integrated** into any game. For actual use in a game, further integration is required to connect the game's data (e.g., player actions, memory, input) with this server.

## Features

- **Local Server**: Runs as a lightweight service on the user's PC alongside the game.
- **Cheat Detection**: Analyzes incoming data packets and user inputs (mouse, keyboard) for suspicious patterns (e.g., aimbot keywords, rapid clicks).
- **Process Scanning**: Detects known cheating tools (e.g., Cheat Engine, IDA, x64dbg) running on the system.
- **IP & HWID Banning**: Automatically bans users based on their IP address or Hardware ID (HWID) upon cheat detection.
- **Heartbeat Monitoring**: Monitors the game's heartbeat signal. Disconnects and bans if the signal stops.
- **SQM Integration**: Prioritizes small data packets using Linux SQM (Stochastic Queue Management) for faster detection.
- **Cross-Platform Potential**: Designed with potential portability to Linux via Wine/Proton in mind.

## How It Works

1. The game connects to the local server.
2. The server receives data packets from the game, including:
   - Heartbeat signals
   - User inputs (mouse, keyboard)
   - General game events
3. The server analyzes these packets for cheat signatures or suspicious patterns.
4. If a cheat is detected, the server bans the user (IP/HWID) and disconnects the client.
5. SQM ensures small packets (e.g., cheat commands) are processed with higher priority.

## Requirements

- Python 3.x
- `psutil` library (`pip install psutil`)
- Linux (for SQM integration)
- SQM tools (`sudo pacman -S sqm-scripts` on Arch-based systems)

## Installation

1. Clone this repository.
2. Install the required Python libraries:
   ```bash
   pip install psutil

