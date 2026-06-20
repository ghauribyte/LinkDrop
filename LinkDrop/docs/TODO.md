# TODO — Phase 1: Core Discovery

This is the exact spec for the first piece of code. No GUI, no Flutter widgets yet — just two plain Dart scripts that prove two devices can find each other on the same Wi-Fi. Write the code, then bring it back here for review against this list.

## File 1: `broadcaster.dart`

What it should do:
1. Create a UDP socket, bind it to port `6868` (any free port works, both files just need to agree on the same one)
2. Every 2 seconds, send a broadcast packet to `255.255.255.255:6868`
3. Packet content: a small JSON message like:
   ```json
   {"type": "announce", "name": "<device name>", "id": "<random id, generated once at startup>"}
   ```
4. Print a line each time it sends, e.g. `Broadcasting as DeviceName (id: abc123)...`
5. Keep running until stopped with Ctrl+C

## File 2: `listener.dart`

What it should do:
1. Create a UDP socket, bind it to the same port `6868`, in listen mode (`reuseAddress: true`, bind to any IPv4 address)
2. Wait in a loop for incoming packets
3. Parse each packet as JSON
4. If `type` is `"announce"`, print: `Found device: <name> (id: <id>) at <sender IP>`
5. Keep a list of devices already seen (a map keyed by `id`), so it doesn't print the same device over and over — only print again if it's a new device, or it hasn't been seen in the last ~10 seconds
6. Keep running until stopped with Ctrl+C

## How to test
1. Run `broadcaster.dart` on one device, `listener.dart` on another, same Wi-Fi
2. Confirm listener prints the broadcaster's name + IP within a few seconds
3. Swap roles and try the other direction too
4. Easiest first check: run both scripts on the same machine in two terminal windows, before trying two real devices

## Definition of done
- [x] `broadcaster.dart` sends a packet every 2 seconds with name + id
- [x] `listener.dart` receives and prints found devices with the correct IP
- [x] No duplicate spam for the same device in listener output
- [x] Confirmed working between two separate physical devices on the same Wi-Fi
- [x] Ctrl+C cleanly stops both scripts, no crash

## Not in scope yet
- No GUI
- No TCP / file transfer (Phase 2)
- No TLS (Phase 3)
- No Wi-Fi Direct / hotspot logic yet — basic discovery has to work first

---
Once written, bring both files back here. I'll review them against this checklist and against DECISIONS.md before we move to Phase 2.
