# Python

The Python package wraps the Rust core over the C ABI. Construct a `TimeMachine`,
`load` recorded records, then `seek` — all over `command(json) -> json`.

```bash
pip install wickra-timemachine
```

```python
import json
from wickra_timemachine import TimeMachine

tm = TimeMachine("{}")

records = "\n".join([
    '{"ts":10,"symbol":"BTC-USDT","feed":{"kind":"market","type":"trade","price":"100","quantity":"1"}}',
    '{"ts":20,"symbol":"BTC-USDT","feed":{"kind":"market","type":"trade","price":"110","quantity":"2"}}',
])
tm.command(json.dumps({"cmd": "load", "data": records}))

snapshot = json.loads(tm.command(json.dumps({"cmd": "seek", "ts": 20})))
print(snapshot)  # reconstructed at ts=20
```

## More

- [pypi.org/project/wickra-timemachine](https://pypi.org/project/wickra-timemachine/)
- [Source & examples](https://github.com/wickra-lib/wickra-timemachine/tree/main/examples/python)
