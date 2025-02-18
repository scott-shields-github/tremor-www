# json

The JSON extractor converts the input string into its respective JSON representation conforming to The Javascript Object Notation Data Interchange Format (RFC 8259).

## Predicate

When used with `~`, the predicate will pass if the input is a valid JSON

## Extraction

If the predicate passes, the extractor will return the JSON representation of the target. Similar to the [`json` codec](../codecs/json.md), consecutive duplicate keys overwrite previous ones. 

```tremor
match { "test" : "{ \"foo\":\"bar\", "\snot"\:"\badger"\ }" } of
   case foo  = %{ test ~= json|| } => foo
  default => "ko"
end;
```
