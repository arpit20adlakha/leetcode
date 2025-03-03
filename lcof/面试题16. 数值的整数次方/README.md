# [面试题16. 数值的整数次方](https://leetcode-cn.com/problems/shu-zhi-de-zheng-shu-ci-fang-lcof/)

## 题目描述
实现函数 double Power(double base, int exponent)，求 base 的 exponent 次方。不得使用库函数，同时不需要考虑大数问题。

**示例 1:**

```
输入: 2.00000, 10
输出: 1024.00000
```

**示例 2:**

```
输入: 2.10000, 3
输出: 9.26100
```

**示例 3:**

```
输入: 2.00000, -2
输出: 0.25000
解释: 2-2 = 1/22 = 1/4 = 0.25
```

**说明:**

- `-100.0 < x < 100.0`
- n 是 32 位有符号整数，其数值范围是  `[−231, 231 − 1]` 。

## 解法
### Python3
```python
class Solution:
    cache = {}
    def myPow(self, x: float, n: int) -> float:
        self.cache = {}
        return self.pow(x, n)

    def pow(self, x, n):
        if self.cache.get('{}-{}'.format(x, n)):
            return self.cache['{}-{}'.format(x, n)]
        if n == 0: return 1
        if n == 1: return x
        if n == -1: return 1 / x

        half = self.pow(x, n // 2)
        self.cache['{}-{}'.format(x, n // 2)] = half
        return half * half * self.pow(x, n % 2)
```

### Java
```java
class Solution {
    public double myPow(double x, int n) {
        if (n == 0) return 1;
        if (n == 1) return x;
        if (n == -1) return 1 / x;
        double half = myPow(x, n / 2);
        return half * half * myPow(x, n % 2);
    }
}
```

### JavaScript
```js
/**
 * @param {number} x
 * @param {number} n
 * @return {number}
 */
var myPow = function(x, n) {
    let r = 1
    let tmp = x
    let tag = 0
    if(n < 0) {
        tag = 1
        n = -n
    }
    while(n) {
        if(n & 1) {
            r *= tmp
        }
        tmp *= tmp
        n >>>= 1
    }
    return tag ? 1/r : r
};
```

### ...
```

```
