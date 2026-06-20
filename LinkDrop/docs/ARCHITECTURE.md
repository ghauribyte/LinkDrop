# Architecture
# Architecture

## Overview
LinkDrop is an AirDrop-style app. It sends files between devices on the same Wi-Fi network. No cloud, no login — direct device-to-device transfer.

## Modules
1. **GUI Layer** — device list, send/receive buttons, progress bars, accept/reject popup
2. **Discovery Service** — finds other devices on the local network (mDNS/Bonjour or UDP broadcast)
3. **Transfer Engine** — sends/receives file data over TCP
4. **Security Module** — wraps the connection in TLS, verifies the other device before sending
5. **Network Layer** — raw networking underneath: UDP for discovery, TCP+TLS for transfer

## Data Flow
1. Discovery Service broadcasts presence on Wi-Fi
2. Other devices answer back, GUI shows them in a list
3. User picks a device and files, Transfer Engine opens a TCP connection
4. Security Module wraps it in TLS and checks the other device
5. Receiver gets an accept/reject popup
6. If accepted, file data streams over TCP, GUI shows progress
7. Transfer is saved in history

## Dependency Map
```
GUI Layer → Transfer Engine → Security Module → Network Layer
GUI Layer → Discovery Service → Network Layer
```

## Open Items (not decided yet)
- GUI framework: Electron vs Qt vs Flutter
- Programming language for discovery + transfer engine
- How folders are sent: zip the whole folder, or send files one by one