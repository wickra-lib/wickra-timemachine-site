# R

The R package links the C ABI. Build a time machine with `wktimemachine_new`, then
drive it with `wktimemachine_command`.

```r
install.packages("wickratimemachine", repos = "https://wickra-lib.r-universe.dev")
```

```r
library(wickratimemachine)

tm <- wktimemachine_new("{}")
records <- '{"ts":10,"symbol":"BTC-USDT","feed":{"kind":"market","type":"trade","price":"100","quantity":"1"}}'
wktimemachine_command(tm, paste0('{"cmd":"load","data":"', records, '"}'))
snapshot <- wktimemachine_command(tm, '{"cmd":"seek","ts":10}')
cat(snapshot)
```

## More

- [wickra-lib.r-universe.dev](https://wickra-lib.r-universe.dev)
- [Source & examples](https://github.com/wickra-lib/wickra-timemachine/tree/main/examples/r)
