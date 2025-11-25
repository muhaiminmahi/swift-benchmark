# Swift Benchmark
Swift Benchmark is a library for writing and running benchmarks in Swift.
## Getting Started
To use `swift-benchmark` in your project, add it to your `Package.swift` dependencies:
```swift
// swift-tools-version:5.3
import PackageDescription
let package = Package(
name: "YourProject",
dependencies: [
.package(url: "https://github.com/google/swift-benchmark.git", from: "0.1.0"),
],
targets: [
.target(
name: "YourProject",
dependencies: ["Benchmark"]),
]
)
```
Then build your project:
```bash
swift build
```
## Example Benchmark
```swift
import Benchmark
let benchmark = BenchmarkSuite(name: "Sample") { suite in
suite.benchmark("Loop") {
for _ in 0..<1_000_000 { }
}
}
Benchmark.main([benchmark])
```
## Running Benchmarks
Use Swift Package Manager:
```bash
swift run BenchmarkMinimalExample
```
Example output:
```
name time std iterations
------------------------------------------------
Loop 12.3 ms ±0.2 ms 100
```
## Writing Good Benchmarks
- Keep your benchmark small and focused
- Avoid doing I/O inside benchmark loops
- Prefer micro-benchmarks to isolate performance of small code blocks
- Benchmark consistent workloads
## Contributing
We welcome contributions! If you want to improve this README or add new
benchmarks:
1. Fork the repository
2. Create a new branch:
```bash
git checkout -b improve-readme
```
3. Make your changes
4. Stage your changes:
```bash
git add README.md
```
5. Commit your changes:
```bash
git commit -m "Improve README with usage and example"
```
6. Push your branch:
```bash
git push origin improve-readme
```
7. Open a Pull Request to the main repository with a clear description
8. Don't forget to sign the Google CLA