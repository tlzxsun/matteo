title: LeetCode.150 Evaluate Reverse Polish Notation
author: Matteo
tags: []
categories:
  - LeetCode
date: 2019-05-25 11:55:00
---
##### 题意
* 计算逆波兰法表示的算式
##### 解法
* 遇到数字存入栈，遇到符号则出栈两个数字，并将结果入栈
```java
class Solution {

    Stack<Integer> integers = new Stack<>();

    public int evalRPN(String[] tokens) {
        for(String token: tokens) {
            if ("+".equals(token)) {
                int n2 = integers.pop(), n1 = integers.pop();
                integers.push(n1 + n2);
            } else if ("-".equals(token)) {
                int n2 = integers.pop(), n1 = integers.pop();
                integers.push(n1 - n2);
            } else if ("*".equals(token)) {
                int n2 = integers.pop(), n1 = integers.pop();
                integers.push(n1 * n2);
            } else if ("/".equals(token)) {
                int n2 = integers.pop(), n1 = integers.pop();
                integers.push(n1 / n2);
            } else {
                integers.push(Integer.parseInt(token));
            }
        }
        return integers.pop();
    }
}
```