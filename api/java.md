# Java

The Java binding links the C ABI via a small JNI shim. Construct a `TimeMachine`
and drive it with `command(json) -> json`.

```xml
<!-- Maven Central -->
<dependency>
  <groupId>org.wickra</groupId>
  <artifactId>wickra-timemachine</artifactId>
  <version>0.1.0</version>
</dependency>
```

```java
import org.wickra.timemachine.TimeMachine;

try (TimeMachine tm = new TimeMachine("{}")) {
    tm.command("{\"cmd\":\"load\",\"data\":\"<jsonl records>\"}");
    String snapshot = tm.command("{\"cmd\":\"seek\",\"ts\":20}");
    System.out.println(snapshot);
}
```

## More

- [central.sonatype.com/artifact/org.wickra/wickra-timemachine](https://central.sonatype.com/artifact/org.wickra/wickra-timemachine)
- [Source & examples](https://github.com/wickra-lib/wickra-timemachine/tree/main/examples/java)
