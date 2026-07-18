# Rust

The native crate. Parse recorded records and reconstruct a snapshot with
`seek_snapshot`, or drive a `TimeMachine` handle with the JSON command protocol
every other binding uses.

```bash
cargo add wickra-timemachine
```

```rust
use timemachine_core::{parse_records_jsonl, seek_snapshot};

let records = parse_records_jsonl(DATA).expect("valid records");
let snapshot = seek_snapshot(&records, 1_700_003_600).expect("seek");

println!("{:?}", snapshot);
```

## More

- [crates.io/crates/wickra-timemachine](https://crates.io/crates/wickra-timemachine) - [docs.rs](https://docs.rs/wickra-timemachine)
- [Source & examples](https://github.com/wickra-lib/wickra-timemachine/tree/main/examples/rust)
- [TimelineSpec & seek](https://github.com/wickra-lib/wickra-timemachine/blob/main/docs/SPEC.md)
