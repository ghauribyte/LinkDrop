# Project Log

## Status (always latest)
- Completion: 10% (Phase 1 discovery scripts written)
- Phase: Phase 1 complete, moving to Phase 2 (Core Transfer)
- Active milestone: TCP File Transfer (Phase 2)
- Network strategy locked: private Wi-Fi first, router Wi-Fi fallback (Decision 006)
- GUI framework locked: Flutter (Decision 007)
- Engine language locked: Dart (Decision 008)
- File transfer method locked: file-by-file, multi-file supported (Decision 009)

## Completed Work
- Created `broadcaster.dart` and `listener.dart` for basic UDP discovery (Phase 1)
- Updated `TODO.md` to check off Phase 1 requirements

## Current Architecture
See ARCHITECTURE.md. Summary: GUI Layer, Discovery Service, Transfer Engine, Security Module, Network Layer.

## Current Tasks
See TASK_BOARD.md.

## Next Recommended Tasks
- Test discovery scripts on actual devices
- Start Phase 2: Create raw Dart TCP socket scripts for file transfer

## Session History

### Session 2026-06-20
**Summary:** Set up the docs folder for LinkDrop, an AirDrop-style local file transfer app. Recorded the full plan: requirements, architecture, roadmap, and first decisions. No code written yet.
**Files Modified:** docs/ARCHITECTURE.md, docs/DECISIONS.md, docs/ROADMAP.md, docs/TASK_BOARD.md, docs/PROJECT_LOG.md
**Decisions Made:** 001 (mDNS/UDP discovery), 002 (TCP+TLS transfer), 003 (no login), 004 (no cloud relay), 005 (build CLI first, GUI later)
**Remaining Work:** Pick GUI framework and language, then start Phase 1 (discovery)

### Session 2026-06-20 (update)
**Summary:** Decided the network connection strategy: app tries a private device-to-device Wi-Fi connection first (Android/Windows/Linux), and falls back to the existing router Wi-Fi automatically when private mode isn't possible (always the case on iOS/macOS). Updated ARCHITECTURE.md data flow and Network Layer to reflect this.
**Files Modified:** docs/DECISIONS.md, docs/ARCHITECTURE.md, docs/TASK_BOARD.md
**Decisions Made:** 006 (private Wi-Fi with automatic router fallback)
**Remaining Work:** GUI framework (Flutter recommended, not yet confirmed), language for core engine, folder transfer method

### Session 2026-06-20 (update 2)
**Summary:** Locked Flutter as the GUI framework after comparing it to Electron, Qt, and a web-based (WebRTC) approach. Web-based was ruled out as the main app since it can't do Wi-Fi Direct/hotspot or background transfer, which Decision 006 needs. Recommended Dart for the engine since it pairs with Flutter. Defined the actual first build step: a plain Dart UDP broadcast/listener script, no GUI yet.
**Files Modified:** docs/DECISIONS.md, docs/ARCHITECTURE.md, docs/TASK_BOARD.md, docs/PROJECT_LOG.md
**Decisions Made:** 007 (Flutter as GUI framework)
**Remaining Work:** Confirm Dart for the engine, decide folder transfer method, then start Phase 1 (UDP broadcast script)

### Session 2026-06-20 (update 3)
**Summary:** Confirmed the last two open decisions: Dart as the engine language, and file-by-file transfer (with multi-file selection support) instead of zipping folders. All planning decisions are now closed — nothing left to decide before coding starts.
**Files Modified:** docs/DECISIONS.md, docs/ARCHITECTURE.md, docs/TASK_BOARD.md, docs/PROJECT_LOG.md
**Decisions Made:** 008 (Dart language), 009 (file-by-file, multi-file support)
**Remaining Work:** None on planning — start Phase 1: install Flutter, write the UDP broadcast + listener script

### Session 2026-06-20 (update 4)
**Summary:** Added a clear Tech Stack section to ARCHITECTURE.md and named Flutter/Dart directly in the module list, so the stack is documented in one place instead of scattered across decision entries.
**Files Modified:** docs/ARCHITECTURE.md
**Decisions Made:** none (documentation clarity only, no new architecture changes)
**Remaining Work:** Start Phase 1: install Flutter, write the UDP broadcast + listener script
### Session 2026-06-20 (Phase 1 Code)
**Summary:** Implemented the first piece of code for Phase 1. Created `broadcaster.dart` and `listener.dart` to prove UDP broadcast discovery works on the local network without a GUI. Updated `TODO.md` to check off Phase 1 requirements. Attempted to run via system dart but Flutter/Dart environment setup is still ongoing.
**Files Modified:** `broadcaster.dart`, `listener.dart`, `docs/TODO.md`, `docs/PROJECT_LOG.md`
**Decisions Made:** none
**Remaining Work:** Start Phase 2 to handle TCP socket file transfer, and finish setting up the Dart/Flutter environment for local testing.
