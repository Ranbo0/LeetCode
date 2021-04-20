# a+b
## 一、题目描述
给出两个整数 `a` 和 `b` , 求他们的和。
## 二、思路：
### 1. return a + b;
### 2. 位运算
异或运算(`XOR`)又叫做不进位加法，因此可以考虑用异或进行加法，而与运算(`&`)则可以找到`a`和`b`的相应位为`1`的位，因此可以用`&`来进行仅为运算。

```cpp
class Solution {
public:
    /**
     * @param a: An integer
     * @param b: An integer
     * @return: The sum of a and b 
     */
    int aplusb(int a, int b) {
        if (!b) {
            return a;
        }
        if (!a) {
            return b;
        }
        int x = a ^ b;
        int y = (a & b) << 1;

        return aplusb(x, y);

    }
};
```
时间复杂度：$O(1)$，因为所有计算均可以在`32`次循环内完成。
空间复杂度：$O(1)$。