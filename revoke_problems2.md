```text
ascii/1.0.0
182:test ascii_str::tests::as_mut_ascii_str ... error: Undefined Behavior: trying to reborrow <468243> for Unique permission at alloc177241[0x0], but that tag only grants SharedReadOnly permission for this location
188:     |         trying to reborrow <468243> for Unique permission at alloc177241[0x0], but that tag only grants SharedReadOnly permission for this location
```
Not an error related to my change (actual use of `&` as `&mut`). Seems to be fixed in the latest on master (maybe add an issue for new version).

```text
half/1.8.2
236:error: Undefined Behavior: trying to reborrow <3066> for Unique permission at alloc1636[0x0], but that tag only grants SharedReadOnly permission for this location
242:    |         trying to reborrow <3066> for Unique permission at alloc1636[0x0], but that tag only grants SharedReadOnly permission for this location
```
Not an error related to my change (actual use of `&` as `&mut`).

```text
itoa/1.0.1
58:test test_i128_min ... error: Undefined Behavior: trying to reborrow <193482> for Unique permission at alloc76288[0x14], but that tag only grants SharedReadOnly permission for this location
64:    | trying to reborrow <193482> for Unique permission at alloc76288[0x14], but that tag only grants SharedReadOnly permission for this location
```

```text
serde_urlencoded/0.7.1
89:test serialize_newtype_i128 ... error: Undefined Behavior: trying to reborrow <209634> for Unique permission at alloc83061[0x14], but that tag only grants SharedReadOnly permission for this location
95:    | trying to reborrow <209634> for Unique permission at alloc83061[0x14], but that tag only grants SharedReadOnly permission for this location
```

```text
rgb/0.8.32
71:test bytes ... error: Undefined Behavior: trying to reborrow <226692> for Unique permission at alloc88850[0x0], but that tag only grants SharedReadOnly permission for this location
77:    |         trying to reborrow <226692> for Unique permission at alloc88850[0x0], but that tag only grants SharedReadOnly permission for this location
```

```text
prettytable-rs/0.8.0
447:test csv::tests::from ... error: Undefined Behavior: trying to reborrow <512807> for Unique permission at alloc191376[0x0], but that tag only grants SharedReadOnly permission for this location
453:    |                     trying to reborrow <512807> for Unique permission at alloc191376[0x0], but that tag only grants SharedReadOnly permission for this location
515:error: Undefined Behavior: trying to reborrow <27006> for Unique permission at alloc11766[0x0], but that tag only grants SharedReadOnly permission for this location
521:    |                     trying to reborrow <27006> for Unique permission at alloc11766[0x0], but that tag only grants SharedReadOnly permission for this location
```

```text
tonic/0.7.2
2171:error: Undefined Behavior: trying to reborrow <12003> for Unique permission at alloc2637[0x0], but that tag only grants SharedReadOnly permission for this location
2177:     |                                              trying to reborrow <12003> for Unique permission at alloc2637[0x0], but that tag only grants SharedReadOnly permission for this location
2591:error: Undefined Behavior: trying to reborrow <12003> for Unique permission at alloc2637[0x0], but that tag only grants SharedReadOnly permission for this location
2597:     |                                              trying to reborrow <12003> for Unique permission at alloc2637[0x0], but that tag only grants SharedReadOnly permission for this location
```

