# Omit Non-empty JSON Field

As we know, we can omit struct field from being marshaled by adding `omitempty` on our json tag when the value is an empty value. We can also omit the struct field from being marshaled even though the field has a value by unexporting the field.

What if we want to export the field to be used for other part of our code, but we didn't want the field to be marshaled ? Go provide a special case for omitting exported field from being marshaled by specifying the tag value as `"-"`. The usage will look like this:

```go
type Person struct {
	Name string `json:"name"`
	Age  int    `json:"-"`
}
```

If we actually need `"-"` as JSON property, we can still use it by using `json:"-,"`.

---
For more information regarding JSON encoding
[Documentation](https://golang.org/pkg/encoding/json/)