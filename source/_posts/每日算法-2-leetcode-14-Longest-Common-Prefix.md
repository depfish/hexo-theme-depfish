---
title: '每日算法#2 leetcode#14 Longest Common Prefix'
catalog: true
date: 2019-11-11 22:34:20
subtitle:
header-img:
tags:
- 算法
- leetcode
- 简单
---

### 最长公共前缀

Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".

Example 1:
```
Input: ["flower","flow","flight"]
Output: "fl"
```

Example 2:
```
Input: ["dog","racecar","car"]
Output: ""
```

Explanation: There is no common prefix among the input strings.
Note:

All given inputs are in lowercase letters a-z.



我的解答：

```go
func main() {
	//                0        1      2     3
	//var strs = []string{"flower", "flow", "flight"}
	var strs2 = [] string{"","a"}
	//strs[0]="ggmm"

	//fmt.Printf("str is %v \n",strs)
	fmt.Println(longestCommonPrefix(strs2))
}

// ["dog","racecar","car"]
// ["abab","aba",""]
// ["","b"]
//  ["aa","a"]
// ["aac","acab","aa","abba","aa"]
func longestCommonPrefix(strs []string) string {
	var result string

	var maxIndex int
	for n, str := range strs {
		strLen := len(str)
		if n == 0  && strLen > 0{
			maxIndex = strLen - 1
			result = str
			continue
		}
		if strLen == 0  || (result[0] != str[0]) {
			result = ""
			break
		}

		if strLen -1 < maxIndex {
			maxIndex = strLen -1
			result = result[:strLen]
		}

		for i := 0; i <= maxIndex && i < strLen; i++ {
			if result[i] != str[i] {
				maxIndex=i -1
				result = result[:i]
			}
		}
	}
	return result
}

```

![mybook](/img/article/Longest_Common_Prefix.jpeg)

令人高兴的是，居然打败了100%的Gopher😂

链接：https://leetcode-cn.com/problems/longest-common-prefix
