---
layout: home
title: Wickra Time Machine — scrub the market like a video
titleTemplate: false

hero:
  name: "Wickra Time Machine"
  text: "Rewind the market to any moment."
  tagline: "Scrub the whole crypto market like a video — every symbol, full orderbook, trades and funding, rewound to any moment and reconstructed in O(1) via deterministic re-fold. Byte-identical across ten languages."
  image:
    src: /wickra-mark.svg
    alt: Wickra Time Machine
  actions:
    - theme: brand
      text: View on GitHub
      link: https://github.com/wickra-lib/wickra-timemachine
    - theme: alt
      text: TimelineSpec & seek
      link: https://github.com/wickra-lib/wickra-timemachine/blob/main/docs/SPEC.md
    - theme: alt
      text: API
      link: /api/rust

features:
  - icon: ⏮️
    title: Seek to any moment
    details: Point the Time Machine at a recorded universe, seek(t), and it re-folds every symbol's orderbook, tape and funding to the exact microstructure state at that timestamp — no snapshots, no interpolation.
  - icon: 🎬
    title: The whole market at once
    details: "Not one symbol — the whole crypto market, scrubbed like a video. Every symbol's full orderbook plus trades and funding, reconstructed together at the moment you seek to."
  - icon: ⚡
    title: O(1) deterministic re-fold
    details: "Reconstruction folds recorded feeds through the wickra-backtest replay engine in O(1), so seeking to any past timestamp yields the exact state and the same bytes every time."
  - icon: 📈
    title: Indicators at the reconstructed state
    details: "A TimelineSpec can name any of the 514 indicators of the Wickra core, so a seek returns not just the raw book and tape but the indicator values as they stood at that instant."
  - icon: 🌐
    title: Ten languages, one timeline
    details: "The core is a JSON-over-C-ABI data API (TimeMachine::command_json) in Rust, Python, Node.js, WASM, C, C++, C#, Go, Java and R. A developer in any language scrubs the same market."
  - icon: 🧪
    title: Deterministic, proven
    details: Seeking to a given timestamp produces the byte-identical snapshot in every binding, pinned by a golden corpus replayed through each binding in CI — the exact cross-language golden invariant.
---

<script setup>
const installTabs = [
  { label: 'Python', lang: 'bash', code: 'pip install wickra-timemachine' },
  { label: 'Node',   lang: 'bash', code: 'npm install wickra-timemachine' },
  { label: 'Rust',   lang: 'bash', code: 'cargo add wickra-timemachine' },
  { label: 'WASM',   lang: 'bash', code: 'npm install wickra-timemachine-wasm' },
  { label: 'C',      lang: 'bash', code: '# prebuilt header + library from GitHub releases:\n# github.com/wickra-lib/wickra-timemachine/releases' },
  { label: 'C#',     lang: 'bash', code: 'dotnet add package Wickra.TimeMachine' },
  { label: 'Go',     lang: 'bash', code: 'go get github.com/wickra-lib/wickra-timemachine-go' },
  { label: 'Java',   lang: 'xml',  code: '<!-- Maven Central -->\n<dependency>\n  <groupId>org.wickra</groupId>\n  <artifactId>wickra-timemachine</artifactId>\n  <version>0.1.0</version>\n</dependency>' },
  { label: 'R',      lang: 'r',    code: 'install.packages("wickratimemachine", repos = "https://wickra-lib.r-universe.dev")' },
]

const pyCode = `import json
from wickra_timemachine import TimeMachine

tm = TimeMachine("{}")

# Load recorded market records (JSONL), then seek to a timestamp.
records = "\\n".join([
    '{"ts":10,"symbol":"BTC-USDT","feed":{"kind":"market","type":"trade","price":"100","quantity":"1"}}',
    '{"ts":20,"symbol":"BTC-USDT","feed":{"kind":"market","type":"trade","price":"110","quantity":"2"}}',
])
tm.command(json.dumps({"cmd": "load", "data": records}))

snapshot = json.loads(tm.command(json.dumps({"cmd": "seek", "ts": 20})))
print(snapshot)  # the market state reconstructed at ts=20`

const nodeCode = `import { TimeMachine } from 'wickra-timemachine'

const tm = new TimeMachine('{}')

const records = [
  '{"ts":10,"symbol":"BTC-USDT","feed":{"kind":"market","type":"trade","price":"100","quantity":"1"}}',
  '{"ts":20,"symbol":"BTC-USDT","feed":{"kind":"market","type":"trade","price":"110","quantity":"2"}}',
].join('\\n')
tm.command(JSON.stringify({ cmd: 'load', data: records }))

const snapshot = JSON.parse(tm.command(JSON.stringify({ cmd: 'seek', ts: 20 })))
console.log(snapshot) // reconstructed at ts=20`

const cliCode = `# Load a recorded universe (JSONL) and seek to a timestamp:
wickra-timemachine --data ./records.jsonl --seek 1700000000

# Play a window forward, snapshot per step:
wickra-timemachine --data ./records.jsonl --play 1700000000..1700003600 --step 60`

const snippetTabs = [
  { label: 'Python', lang: 'python',     code: pyCode },
  { label: 'Node',   lang: 'javascript', code: nodeCode },
  { label: 'CLI',    lang: 'bash',       code: cliCode },
]
</script>

## Load, then seek

Point the Time Machine at a recorded universe of market records, then `seek` to
any timestamp. The engine re-folds every symbol's orderbook, tape and funding to
the exact state at that instant.

```json
{ "cmd": "seek", "ts": 1700003600 }
```

A `TimelineSpec` can also name indicators to evaluate at the reconstructed state,
so a seek returns the book, the tape **and** the indicator values as they stood.

## Install

The same time machine from every language — native Rust, Python, Node.js and
WASM, plus a C ABI for C, C++, C#, Go, Java and R.

<InstallTabs :tabs="installTabs" />

## Scrub it from any language

Construct a `TimeMachine`, `load` a recorded universe, then `seek`. Every binding
reconstructs the byte-identical snapshot.

<InstallTabs :tabs="snippetTabs" />

## Built on the Wickra core

Wickra Time Machine is part of the [Wickra](https://wickra.org) ecosystem. It
folds recorded feeds from [`wickra-exchange`](https://github.com/wickra-lib/wickra-exchange)
through the [`wickra-backtest`](https://github.com/wickra-lib/wickra-backtest)
replay engine over the 514 indicators of
[`wickra-core`](https://github.com/wickra-lib/wickra) — the same numbers a live
chart would show.

> Wickra Time Machine is a software library, not a trading system, and comes with
> no warranty — use at your own risk.
