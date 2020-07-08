---
title: go常用集合
date: 2020-07-08 14:26:52
tags:
  - go
categories:
  - go学习
---

## 数组和切片

### 数组

#### 数组声明

```go
var a [3]int //声明并初始化为默认零值
a[0] = 1
b := [3]int{1,2,3} // 声明同时初始化
c := [2][2]int{{1,2},{3,4}} //多维数组初始化
d :=[...]int{1,3,4,5} //不声明数组有多少元素
```

<!-- more -->
```go
//数组声明
func TestArrayInit(t *testing.T) {
	var arr [3]int
	arr1 := [...]int{1, 2, 3, 4}
	t.Log(arr[1], arr[2])
	t.Log(arr1[1], arr1[2])

}

//循环数组
func TestArrayTravel(t *testing.T) {
	arr1 := [...]int{1, 5, 3, 4}
	for i := 0; i < len(arr1); i++ {
		t.Log(arr1[i])
	}
	//类似foreach
	for idx, e := range arr1 {
		t.Log(idx, e)
	}

	//go语言中，不使用的话不能声明，可以用占位符占用
	for _, e := range arr1 {
		t.Log(e)
	}
}
```

#### 数组截取

a[开始索引（包含），结束索引（不包含）]

```go
a:=[...]int{1,2,3,4,5}
a[:3]  //1,2,3
a[1:]=a[1:len(a)] //2,3,4,5
```

### 切片

![切片](img/切片.png)

```go
func TestSliceinit(t *testing.T) {
	var s0 []int
	t.Log(len(s0), cap(s0))
	s0 = append(s0, 1)
	t.Log(len(s0), cap(s0))

	s1 := []int{1, 2, 3, 4, 8}
	t.Log(len(s1), cap(s1)) //5,5
	//创建长度为3,容量为5的切片
	s2 := make([]int, 3, 5)
	t.Log(len(s2), cap(s2))    //3,5
	t.Log(s2[0], s2[1], s2[2]) //0,0,0
	s2 = append(s2, 1)
	t.Log(s2[0], s2[1], s2[2], s2[3]) //0,0,0,1
	t.Log(len(s2), cap(s2))           //4,5
}
```

切片共享存储结构

```go

func TestSliceGrowing(t *testing.T) {
	s := []int{}
	for i := 0; i < 10; i++ {
		s = append(s, i)
		t.Log(len(s), cap(s))
		// slice_test.go:26: 1 1
		// slice_test.go:26: 2 2
		// slice_test.go:26: 3 4
		// slice_test.go:26: 4 4
		// slice_test.go:26: 5 8
		// slice_test.go:26: 6 8
		// slice_test.go:26: 7 8
		// slice_test.go:26: 8 8
		// slice_test.go:26: 9 16
		// slice_test.go:26: 10 16
	}
}

```

![共享存储结构](img/共享存储结构.png)

```go
func TestSliceSharMemory(t *testing.T) {
	year := []string{"Jan", "Feb", "Mar", "Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"}

	Q2 := year[3:6]
	t.Log(Q2, len(Q2), cap(Q2))

	summer := year[5:8]
	t.Log(summer, len(summer), cap(summer))
	summer[0] = "Unknow"
	t.Log(Q2)
	t.Log(year)

    //切片截取后长度为截取长度，空间为当前位置到源截取切片的连续存储空间（入图）
	// slice_test.go:44: [Apr May Jun] 3 9
	// slice_test.go:47: [Jun Jul Aug] 3 7
	// slice_test.go:49: [Apr May Unknow]
	// slice_test.go:50: [Jan Feb Mar Apr May Unknow Jul Aug Sep Oct Nov Dec]
}

```

### 切片VS数组

1. 容量是否可伸缩（数组不可伸缩，切片可伸缩）
2. 是否可以进行比较（数组相同维数且还有相同个数元素的数组可以比较，切片不可比较）

## Map

### 声明、元素访问及遍历

### Map与工厂模式，在Go语言中实现Set
