# GFM-smedley Guidance

This repository is a downstream GFM v3.0 fork that incrementally replaces
selected Clausewitz systems with visible Smedley Lua. The authoritative base is
tag `v3.0`, commit `ee1486e251d3bb4dc5c355f5c2ec34abaea1078d`. Preserve upstream
history and attribution.

## Architecture

- Lua owns GFM-specific policy, tables, composition, and low-rate orchestration.
- `smedley_kernel` owns verified engine facts, identity, indexes, transactions,
  checked mutation, and other native capabilities. Do not encode GFM policy in
  generic kernel APIs.
- Add a native GFM plugin only when a verified synchronous, hot-path,
  high-volume, or lifecycle constraint cannot fit Smedley's copied-state and
  queued-operation scripting model.
- Do not claim that Lua is faster. Performance claims require equivalent saves,
  intervals, instrumentation, and repeated measurements.

## Atomic Replacements

- Add a Lua replacement and remove its original Clausewitz implementation in
  the same commit. Never leave both implementations active.
- Declare every required Smedley capability before removing source behavior.
  Missing capabilities must fail launch preflight rather than run partially.
- Replace only a bounded, behavior-defined subsystem. Preserve unrelated event
  order, random-number consumption, save-visible state, localization, and
  multiplayer behavior unless the change explicitly documents otherwise.
- Compare the original v3.0 behavior and the replacement on identical disposable
  saves. Verify reload behavior and source-save integrity when state changes.

## Scope

- Prefer ports with substantial source reduction, a clearer data model,
  correctness or testability gains, a capability unavailable in Clausewitz, or
  measured performance improvement.
- Do not translate concise working GFM script merely for architectural
  uniformity.
- Keep investigation notes and future work in issues. Commit only complete,
  active replacements and the documentation needed to operate them.
