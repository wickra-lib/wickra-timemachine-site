# Go

The Go binding links the C ABI via cgo. Construct a `TimeMachine` and drive it
with `Command(json) -> (json, error)`.

```bash
go get github.com/wickra-lib/wickra-timemachine-go
```

```go
package main

import (
	"fmt"

	wickra "github.com/wickra-lib/wickra-timemachine-go"
)

func main() {
	tm, err := wickra.New("{}")
	if err != nil {
		panic(err)
	}
	defer tm.Close()

	records := `{"ts":10,"symbol":"BTC-USDT","feed":{"kind":"market","type":"trade","price":"100","quantity":"1"}}`
	if _, err := tm.Command(`{"cmd":"load","data":"` + records + `"}`); err != nil {
		panic(err)
	}
	snapshot, err := tm.Command(`{"cmd":"seek","ts":10}`)
	if err != nil {
		panic(err)
	}
	fmt.Println(snapshot)
}
```

## More

- [pkg.go.dev/github.com/wickra-lib/wickra-timemachine-go](https://pkg.go.dev/github.com/wickra-lib/wickra-timemachine-go)
- [Source & examples](https://github.com/wickra-lib/wickra-timemachine/tree/main/examples/go)
