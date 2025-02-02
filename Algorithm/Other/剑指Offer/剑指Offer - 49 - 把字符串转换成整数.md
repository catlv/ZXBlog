## 把字符串转换成整数

#### [题目链接](https://www.nowcoder.com/practice/1277c681251b4372bdef344468e4f26e?tpId=13&tqId=11202&tPage=3&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking)

> https://www.nowcoder.com/practice/1277c681251b4372bdef344468e4f26e?tpId=13&tqId=11202&tPage=3&rp=1&ru=%2Fta%2Fcoding-interviews&qru=%2Fta%2Fcoding-interviews%2Fquestion-ranking

#### 题目

![pic](images/49_t.png)

> 注意可以包含**字母和符号**。

### 解析

比较简单的模拟题。但是也要注意一些情况:

* 前面的空字符要去掉；
* 然后就是第一个如果是符号要判断；
* 还有一个就是判断溢出，这个问题可能有点麻烦，方式挺多，但是很多都有小问题；

代码:

```java
public class Solution {
    public int StrToInt(String str) {
        if (str == null || str.trim().length() == 0) {
            return 0;
        }
        int start = (str.charAt(0) == '+' || str.charAt(0) == '-') ? 1 : 0;
        long res = 0;
        for (int i = start; i < str.length(); i++) {
            if (str.charAt(i) > '9' || str.charAt(i) < '0') {
                //return后整个方法就结束了，也就是如果里面有非数字型的数值，直接返回0
                return 0;
            }
            res = res * 10 + (str.charAt(i) - '0');
        }
        //int 范围为 -2147483648~2147483647
        if (str.charAt(0) == '-') {
            res = -res;
            return res < Integer.MIN_VALUE ? 0 : (int) res;
        } else {
            return res > Integer.MAX_VALUE ? 0 : (int) res;
        }
    }
}
```

