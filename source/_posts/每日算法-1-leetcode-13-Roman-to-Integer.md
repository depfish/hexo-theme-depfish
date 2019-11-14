---
title: '每日算法#1 leetcode#13 Roman to Integer'
catalog: true
date: 2019-11-10 00:46:18
subtitle:
header-img:
tags:
- 算法
- leetcode
- 简单
---

### 罗马数字转整型

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

```
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```

```go
func main() {
	//IV
	fmt.Println(romanToInt("XXVII"))

}

func romanToInt(s string) int {
	mp := make(map[string]int)
	mp["I"] = 1
	mp["V"] = 5
	mp["X"] = 10
	mp["L"] = 50
	mp["C"] = 100
	mp["D"] = 500
	mp["M"] = 1000
	var sum int
	for i := 0; i < len(s); i++ {
		if i+1 == len(s) {
			sum += mp[string(s[i])]
			break
		}
		if i+1 < len(s) && mp[string(s[i])] >= mp[string(s[i+1])] {
			sum += mp[string(s[i])]
			continue
		}

		sum -= mp[string(s[i])]

	}

	return sum
}

```

[leetcode完整代码](https://github.com/depfish/leetcode/tree/master/easy)