---
title: go变量定义
date: 2020-07-06 16:32:31
tags:
  - go
categories:
  - go学习
---

变量的三种定义方式

<!-- more -->
```go

func TestFibList(t *testing.T) {
    //方式一
	// var a int = 1
	// var b int = 1
    //方式二
	// var (
	// 	a int = 1
	// 	b     = 1
	// )
    //方式三
	a := 1
	b := 1
	t.Log(a)
	for i := 0; i < 5; i++ {
		t.Log(" ", b)
		tmp := a
		a = b
		b = tmp + a
	}

}

```

更换两变量值

```go
func TestExchange(t *testing.T) {
	a := 1
	b := 2
	a, b = b, a
	t.Log(a, b)
}
```
