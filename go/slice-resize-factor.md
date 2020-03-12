# Slice Resize Factor

Slice is a dynamically-sized array. While it is a dynamically-sized, the underlying data structure is still an array. When the underlying array don't have enough space anymore, it will allocate a new array and copy all of the existing elements into the new one. This process will be repeated as many as needed resulting the dynamically-sized array.

The real question is how Go decide how many space needed for the new array ?

Go will allocate the new array by **two times** if the old array's size is under 1024, after that they will grow by **25%** (may vary according to type of the element and the memory round up result)

Block of code in the slice grow implementation:
```go
if old.len < 1024 {
	newcap = doublecap
} else {
	// Check 0 < newcap to detect overflow
	// and prevent an infinite loop.
	for 0 < newcap && newcap < cap {
		newcap += newcap / 4
	}
	// Set newcap to the requested cap when
	// the newcap calculation overflowed.
	if newcap <= 0 {
		newcap = cap
	}
}
```

---
Source: 
[Forum](https://forum.golangbridge.org/t/slice-append-what-is-the-actual-resize-factor/15654)
and
[Source Code](https://golang.org/src/runtime/slice.go#L76)