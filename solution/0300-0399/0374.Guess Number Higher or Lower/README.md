# [374. 猜数字大小](https://leetcode-cn.com/problems/guess-number-higher-or-lower)

[English Version](/solution/0300-0399/0374.Guess%20Number%20Higher%20or%20Lower/README_EN.md)

## 题目描述

<!-- 这里写题目描述 -->

<p>猜数字游戏的规则如下：</p>

<ul>
	<li>每轮游戏，我都会从 <strong>1</strong> 到 <em><strong>n</strong></em> 随机选择一个数字。 请你猜选出的是哪个数字。</li>
	<li>如果你猜错了，我会告诉你，你猜测的数字比我选出的数字是大了还是小了。</li>
</ul>

<p>你可以通过调用一个预先定义好的接口 <code>int guess(int num)</code> 来获取猜测结果，返回值一共有 3 种可能的情况（<code>-1</code>，<code>1</code> 或 <code>0</code>）：</p>

<ul>
	<li>-1：我选出的数字比你猜的数字小 <code>pick < num</code></li>
	<li>1：我选出的数字比你猜的数字大 <code>pick > num</code></li>
	<li>0：我选出的数字和你猜的数字一样。恭喜！你猜对了！<code>pick == num</code></li>
</ul>

<p>返回我选出的数字。</p>

<p> </p>

<p><strong>示例 1：</strong></p>

<pre>
<strong>输入：</strong>n = 10, pick = 6
<strong>输出：</strong>6
</pre>

<p><strong>示例 2：</strong></p>

<pre>
<strong>输入：</strong>n = 1, pick = 1
<strong>输出：</strong>1
</pre>

<p><strong>示例 3：</strong></p>

<pre>
<strong>输入：</strong>n = 2, pick = 1
<strong>输出：</strong>1
</pre>

<p><strong>示例 4：</strong></p>

<pre>
<strong>输入：</strong>n = 2, pick = 2
<strong>输出：</strong>2
</pre>

<p> </p>

<p><strong>提示：</strong></p>

<ul>
	<li><code>1 <= n <= 2<sup>31</sup> - 1</code></li>
	<li><code>1 <= pick <= n</code></li>
</ul>


## 解法

<!-- 这里可写通用的实现逻辑 -->

<!-- tabs:start -->

### **Python3**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```python
# The guess API is already defined for you.
# @param num, your guess
# @return -1 if my number is lower, 1 if my number is higher, otherwise return 0
# def guess(num: int) -> int:

class Solution:
    def guessNumber(self, n: int) -> int:
        low, high = 0, n
        while low < high:
            mid = low + high >> 1
            if guess(mid) <= 0:
                high = mid
            else:
                low = mid + 1
        return low
```

### **Java**

<!-- 这里可写当前语言的特殊实现逻辑 -->

```java
/** 
 * Forward declaration of guess API.
 * @param  num   your guess
 * @return 	     -1 if num is lower than the guess number
 *			      1 if num is higher than the guess number
 *               otherwise return 0
 * int guess(int num);
 */

public class Solution extends GuessGame {
    public int guessNumber(int n) {
        int low = 1, high = n;
        while (low < high) {
            int mid = low + high >>> 1;
            if (guess(mid) <= 0) {
                high = mid;
            } else {
                low = mid + 1;
            }
        }
        return low;
    }
}
```

### **C++**

```cpp
/** 
 * Forward declaration of guess API.
 * @param  num   your guess
 * @return 	     -1 if num is lower than the guess number
 *			      1 if num is higher than the guess number
 *               otherwise return 0
 * int guess(int num);
 */

class Solution {
public:
    int guessNumber(int n) {
        int low = 1, high = n;
        while (low < high) {
            int mid = low + (high - low) / 2;
            if (guess(mid) <= 0) {
                high = mid;
            } else {
                low = mid + 1;
            }
        }
        return low;
    }
};
```

### **Go**

```go
/** 
 * Forward declaration of guess API.
 * @param  num   your guess
 * @return 	     -1 if num is lower than the guess number
 *			      1 if num is higher than the guess number
 *               otherwise return 0
 * func guess(num int) int;
 */

func guessNumber(n int) int {
    low, high := 1, n
    for low < high {
        mid := (low + high) >> 1
        if guess(mid) <= 0 {
            high = mid
        } else {
            low = mid + 1
        }
    }
    return low
}
```

### **...**

```

```

<!-- tabs:end -->
