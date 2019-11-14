---
title: '每日算法#3 leetcode#20 Valid Parentheses'
catalog: true
date: 2019-11-14 07:33:15
subtitle:
header-img:
tags:
- 算法
- leetcode
- 简单
---

### 有效的括号
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Note that an empty string is also considered valid.

Example 1:
```
Input: "()"
Output: true
```
Example 2:
```
Input: "()[]{}"
Output: true
```
Example 3:
```
Input: "(]"
Output: false
```
Example 4:
```
Input: "([)]"
Output: false
```
Example 5:
```
Input: "{[]}"
Output: true
```

#### 解题思路
开始我打算遍历字符串，最后发现根本不行，后参考了2个例子，用stack实现。

[https://www.cnblogs.com/TimLiuDream/p/9979158.html](https://www.cnblogs.com/TimLiuDream/p/9979158.html) 这个例子比较简单，容易理清思路，但是每次要把rune转成string，有改进空间。

[https://studygolang.com/articles/15781](https://studygolang.com/articles/15781) 最终参考了这个例子，算是比较优的解。

```go
func isValid(s string) bool {
	strLen := len(s)
	if strLen == 0 {
		return true
	}

	if strLen %2 !=0{ //奇数个括号肯定不是，必须要成对出现
		return false
	}

	brackets := map[rune]rune{ ')' : '(', '}' : '{', ']' : '[' }

	var stack []rune
	for _,char:= range s{
		if char ==brackets[')'] || char == brackets['}'] || char==brackets[']']{
			stack=append(stack,char)
		}else if len(stack) >0 && brackets[char]==stack[len(stack)-1]{
			stack=stack[:len(stack)-1]
		}else {
			return false
		}
	}

	return len(stack) == 0

}
```
[leetcode完整代码](https://github.com/depfish/leetcode/tree/master/easy)

题目链接：https://leetcode-cn.com/problems/valid-parentheses
