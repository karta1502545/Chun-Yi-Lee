---
title: "Understanding Go Slice Behind the Scene"
date: "2024-08-26T23:03:48+08:00"
tags: ["Go", "Slice"]
draft: false
---

*This article refers to [Golang slice append implementation details](https://yushuanhsieh.github.io/post/2021-12-29-golang-slice-append/).*

---

Welcome to a deep dive into Go slices! In this article, we unravel the inner workings of Go's slice data structure, answering fundamental questions that every Go developer should know. You'll gain insights into how slices are structured, how their capacity dynamically grows when elements are appended, and crucially, how to avoid unintentional data overlaps or modifications when manipulating multiple slices using `append()`.

By the end, you'll have a clear understanding of how slices manage memory, expand capacity, and maintain data integrity in your Go applications. Let's dive in!

- **Slice data structure**: How a slice looks like?
- **Slice capacity growth**: How a slice's capacity increases as elements are appended?
- **Avoiding data contamination**: How to prevent unintended data overlap or modification when using `append()` with multiple slices?

---

## Slice Data Structure

```go
type slice struct {
  array unsafe.Pointer // a pointer to array
  len   int            // length
  cap   int            // capacity
}
```

## How Does Slice Capacity Grow?

- **Capacity growth**: `cap * 2` if `cap ≤ 256`. `cap * 1.25` if `cap ≥ 256`.

```go
func main() {
 slice1 := []int{0}
 fmt.Printf("Slice1: %v, address: %p\n", slice1, &slice1)

 slice2 := append(slice1, 1)
 fmt.Printf("Slice2: %v, address: %p\n", slice2, &slice2[0])
 slice2 = append(slice2, 2)
 fmt.Printf("Slice2: %v, address: %p\n", slice2, &slice2[0])
 slice2 = append(slice2, 3)
 fmt.Printf("Slice2: %v, address: %p\n", slice2, &slice2[0])
 slice2 = append(slice2, 4)
 fmt.Printf("Slice2: %v, address: %p\n", slice2, &slice2[0])

 slice3 := append(slice2, 7)
 fmt.Printf("Slice3: %v, address: %p\n", slice3, &slice3[0])
}
```

Output:

```
Slice1: [0], address: 0x140000b4000            cap = 1
Slice2: [0 1], address: 0x140000a4030          cap = 2
Slice2: [0 1 2], address: 0x140000b8020        cap = 4
Slice2: [0 1 2 3], address: 0x140000b8020      cap = 4
Slice2: [0 1 2 3 4], address: 0x140000b2080    cap = 8
Slice3: [0 1 2 3 4 7], address: 0x140000b2080  cap = 8
```

## How to Avoid Data Contamination While Using `append()` on Different Slices?

```go
s1 := make([]int, 0)
s1 = append(s1, 1)      // s1: [1], len=1
s1 = append(s1, 2)      // s1: [1,2], len=2
s2 := append(s1, 10)    // s2: [1,2,10], len = 2(from s1) + 1 = 3
s1 = append(s1, 20)     // s1: [1,2,20], len = 2(from s1) + 1 = 3
s3 := append(s2, 30)    // s3: [1,2,20,30], len = 3(from s2) + 1 = 4
```

To create a new address space to store the new slice, rather than using the same address space:

1. First, create a new slice using:

```go
newSlice := make([]int, len, cap)
copy(newSlice, oldSlice)
```

2. Then append to the new slice.

```go
newSlice = append(newSlice, newData)
```

**Do not do:**

```go
newSlice := append(oldSlice, newData)
```