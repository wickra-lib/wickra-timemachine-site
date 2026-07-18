# Node.js

The Node package is a native napi addon over the Rust core. Construct a
`TimeMachine`, `load` recorded records, then `seek` — over `command(json) -> json`.

```bash
npm install wickra-timemachine
```

```javascript
import { TimeMachine } from 'wickra-timemachine'

const tm = new TimeMachine('{}')

const records = [
  '{"ts":10,"symbol":"BTC-USDT","feed":{"kind":"market","type":"trade","price":"100","quantity":"1"}}',
  '{"ts":20,"symbol":"BTC-USDT","feed":{"kind":"market","type":"trade","price":"110","quantity":"2"}}',
].join('\n')
tm.command(JSON.stringify({ cmd: 'load', data: records }))

const snapshot = JSON.parse(tm.command(JSON.stringify({ cmd: 'seek', ts: 20 })))
console.log(snapshot) // reconstructed at ts=20
```

## More

- [npmjs.com/package/wickra-timemachine](https://www.npmjs.com/package/wickra-timemachine)
- [Source & examples](https://github.com/wickra-lib/wickra-timemachine/tree/main/examples/node)
