# WASM

The WebAssembly build runs the same Rust core in the browser or any WASM runtime.
Construct a `TimeMachine`, `load` records, then `seek` — over `command(json) -> json`.

```bash
npm install wickra-timemachine-wasm
```

```javascript
import init, { TimeMachine } from 'wickra-timemachine-wasm'

await init() // fetches and instantiates the .wasm module

const tm = new TimeMachine('{}')
const records = '{"ts":10,"symbol":"BTC-USDT","feed":{"kind":"market","type":"trade","price":"100","quantity":"1"}}'
tm.command(JSON.stringify({ cmd: 'load', data: records }))
const snapshot = JSON.parse(tm.command(JSON.stringify({ cmd: 'seek', ts: 10 })))
console.log(snapshot)
```

Seeking to a given timestamp yields a snapshot byte-identical to the native build.
See the [live demo](/demo) for the Wickra core running in your browser.

## More

- [npmjs.com/package/wickra-timemachine-wasm](https://www.npmjs.com/package/wickra-timemachine-wasm)
- [Source & examples](https://github.com/wickra-lib/wickra-timemachine/tree/main/bindings/wasm)
