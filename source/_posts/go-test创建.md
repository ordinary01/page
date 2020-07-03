---
title: go test创建
date: 2020-07-03 17:59:22
tags:
  - go
categories:
  - go学习
---

```go
    package try_test

    import "testing"

    func TestFirstTry(t *testing.T) {
        t.Log("My First Log")
    }

```
<!-- more -->
vscode需要执行

```go
go test -v try_test.go
```
