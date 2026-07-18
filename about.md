# About Wickra Time Machine

Wickra Time Machine scrubs the whole crypto market like a video — every symbol's
full orderbook, trades and funding, rewound to any moment and reconstructed in
O(1) via a deterministic re-fold. A seek is a JSON command — **data, not code** —
so the reconstruction runs in every one of ten languages and returns a
byte-for-byte identical snapshot.

## What makes it different

- **Seek to any moment.** Point it at a recorded universe, `seek(t)`, and it
  re-folds every symbol's orderbook, tape and funding to the exact microstructure
  state at that timestamp — no snapshots, no interpolation.
- **The whole market at once.** Not one symbol — every symbol's full book plus
  trades and funding, reconstructed together at the instant you seek to.
- **O(1) deterministic re-fold.** Reconstruction folds recorded feeds through the
  `wickra-backtest` replay engine, so a seek is fast and reproducible.
- **Indicators at the reconstructed state.** A `TimelineSpec` can name any of the
  514 indicators of the Wickra core, so a seek returns the indicator values as they
  stood, not just the raw book and tape.

## Why it exists

Replaying market microstructure usually means storing periodic snapshots and
interpolating between them — lossy and non-reproducible. Wickra Time Machine folds
the recorded feed **once**, in Rust, and exposes seek as a JSON-over-C-ABI data API
to Rust, Python, Node.js, WASM and — over a C ABI — C, C++, C#, Go, Java and R. The
same timeline scrubs identically anywhere.

## Open source

Released under the **MIT OR Apache-2.0** license — permissive, OSI-approved, free
for any use including commercial. Source, issues and releases on
[GitHub](https://github.com/wickra-lib/wickra-timemachine).

## Disclaimer

Wickra Time Machine is a software library, **not** a trading system, and is
provided **as-is with no warranty**. It reconstructs historical state from recorded
data; it does not give financial advice. Use it at your own risk.
