# Project Log

## Status (always latest)
- Completion: 0% (planning stage, no code written yet)
- Phase: Pre-development, Phase 1 not started
- Active milestone: Core discovery (Phase 1)
- Network strategy locked: private Wi-Fi first, router Wi-Fi fallback (Decision 006)

## Completed Work
_(none yet)_

## Current Architecture
See ARCHITECTURE.md. Summary: GUI Layer, Discovery Service, Transfer Engine, Security Module, Network Layer.

## Current Tasks
See TASK_BOARD.md.

## Next Recommended Tasks
- Resolve pending decisions: GUI framework, language, folder transfer method (see DECISIONS.md)
- Start Phase 1: build discovery as a command-line tool, no GUI yet

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
