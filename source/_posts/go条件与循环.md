---
title: go条件与循环
date: 2020-07-07 16:27:50
tags:
  - go
categories:
  - go学习
---

主要介绍go语言其他语言区别

<!-- more -->

### 循环

Go语言仅支持循环关键字for，不需要将三段式括号括起来

![代码示例](img/2.png)

### if条件

1. condition表达式结果必须为布尔值
2. 支持变量赋值

```go
if var declaration; condition{

}
```

```go
package loop

import "testing"

func TestIFMultiSec(t *testing.T) {
	if a := 1 == 1; a {
		t.Log("1=1")
	}
}

```

### switch条件

1. 条件表达式不限制为常量或者整数
2. 单个case中，可以出现多个结果选项，使用逗号分隔
3. 与C语言等规则相反，Go语言不需要用break来明确退出一个case
4. 可以不设定switch之后的条件表达式，在此种情况下，整个switch结构与多个if...else...的逻辑作用等同

```go

func TestSwitchMultiCase(t *testing.T) {
	count := 5
	for i := 0; i < count; i++ {
		switch i {
		case 0, 2:
			t.Log("Even")
		case 1, 3:
			t.Log("Odd")
		default:
			t.Log("it is not 0-3")
		}

	}
}

//类似if else
func TestSwitchCaseCondition(t *testing.T) {
	count := 5
	for i := 0; i < count; i++ {
		switch {
		case i%2 == 0:
			t.Log("Even")
		case i%2 == 0:
			t.Log("Odd")
		default:
			t.Log("unknow")
		}
	}
}

```
