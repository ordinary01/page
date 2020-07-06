---
title: go常量定义
date: 2020-07-06 16:47:21
tags:
  - go
categories:
  - go学习
---

```go

package constant_test

import "testing"

const (
	Monday = iota + 1
	Tuesday
	Wednesday
)

const (
	Readable = 1 << iota
	Writable
	Executable
)

func TestConstantTry(t *testing.T) {
	t.Log(Monday, Wednesday)

}

```
