# Benchmark Go Code

Go provides a built-in code benchmarking using `go test` command.

To benchmark our go code / function, we need to create a test file and create a benchmark function.
To run all benchmarks we can use `go test -bench=.`<br>
Go consider a function to be a benchmark function when the function has the following form.

```go
func BenchmarkXxx(b *testing.B) {
    // code here
}
```

Sample benchmark function to benchmark fmt.Println performance.

```go
func BenchmarkPrintln(b *testing.B) {
    for i := 0; i < b.N; i++ {
        fmt.Println("Hello World!");
    }
}
```

The benchmark function will run N times or until the specified execution time. The output:

```
BenchmarkPrintln-8        29708             43307 ns/op
```

We can also get the memory allocation statistics by running the benchmark using `go test -bench=. -benchmen` The output will look like this:

```
BenchmarkPrintln-8        28310             41324 ns/op              32 B/op          1 allocs/op
```

By default the benchmark will run for **1s** and will tell us how many N times executed. But we can control the N by adding `-benchtime Nx` flag. For example `-benchtime 100x`

We can also run the benchmark for a couple of times in 1 command, by default the benchmark will only run once. We can specify how many times the benchmark run by adding `-count n` flag.

---
For more information regarding go built-in benchmark [Documentation](https://golang.org/cmd/go/#hdr-Testing_flags)