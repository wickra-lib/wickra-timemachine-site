# C\#

The .NET binding wraps the C ABI. Construct a `TimeMachine` and drive it with
`Command(json) -> json`.

```bash
dotnet add package Wickra.TimeMachine
```

```csharp
using Wickra.TimeMachine;

using var tm = new TimeMachine("{}");
tm.Command("{\"cmd\":\"load\",\"data\":\"<jsonl records>\"}");
var snapshot = tm.Command("{\"cmd\":\"seek\",\"ts\":20}");
Console.WriteLine(snapshot);
```

## More

- [nuget.org/packages/Wickra.TimeMachine](https://www.nuget.org/packages/Wickra.TimeMachine)
- [Source & examples](https://github.com/wickra-lib/wickra-timemachine/tree/main/examples/csharp)
