---
title: 无符号右移（>>>）
slug: Web/JavaScript/Reference/Operators/Unsigned_right_shift
---

{{jsSidebar("Operators")}}

**无符号右移运算符（`>>>`）**（零填充右移）将左操作数计算为无符号数，并将该数字的二进制表示形式移位为右操作数指定的位数，取模 32。向右移动的多余位将被丢弃，零位从左移入。其符号位变为 `0`，因此结果始终为非负数。与其他按位运算符不同，零填充右移返回一个无符号 32 位整数。

{{EmbedInteractiveExample("pages/js/expressions-unsigned-right-shift.html")}}

## 语法

```js-nolint
a >>> b
```

## 描述

该运算符将第一个操作数向右移动指定的位数。向右移动的多余位将被丢弃。零位从左侧移入。其符号位变为 `0`，因此其表示的结果始终为非负数。与其它按位运算符不同，零填充右移返回无符号 32 位整数。

以十进制（以 10 为基数）数字 `9` 和 `-9` 的 32 位二进制表示为例：

```
     9 (base 10): 00000000000000000000000000001001 (base 2)
    -9 (base 10): 11111111111111111111111111110111 (base 2)
```

请注意，负十进制（以 10 为基数）数字 `-9` 的二进制表示形式是正十进制（以 10 为基数）数字 `9` 的[二进制补码](https://zh.wikipedia.org/wiki/二補數)。也就是说，它是通过反转 `00000000000000000000000000001001` 的所有位并添加 `1` 来计算的。

在这两种情况下，二进制数的符号都由其最左边的位给出：对于正十进制数 `9`，二进制表示的最左边位是 `0`，对于负十进制数 `-9`，二进制表示的最左边位是 `1`。

对于正数 `9`，零填充右移和[符号传播右移](/zh-CN/docs/Web/JavaScript/Reference/Operators/Right_shift)产生相同的结果：`9 >>> 2` 产生 `2`，与 `9 >> 2` 相同：

```
      9 (base 10): 00000000000000000000000000001001 (base 2)
                   --------------------------------
9 >>  2 (base 10): 00000000000000000000000000000010 (base 2) = 2 (base 10)
9 >>> 2 (base 10): 00000000000000000000000000000010 (base 2) = 2 (base 10)
```

请注意，最右边的两个位 `01` 被移出，两个零从左边移入。

但是，请注意 `-9` 会发生什么情况：`-9 >> 2`（[符号传播右移](/zh-CN/docs/Web/JavaScript/Reference/Operators/Right_shift)）产生 `-3`，但 `-9 >>> 2`（零填充右移）产生 1073741821：

```
      -9 (base 10): 11111111111111111111111111110111 (base 2)
                    --------------------------------
-9 >>  2 (base 10): 11111111111111111111111111111101 (base 2) = -3 (base 10)
-9 >>> 2 (base 10): 00111111111111111111111111111101 (base 2) = 1073741821 (base 10)
```

请注意最右边的两个位 `11` 是如何移出的。对于 `-9 >> 2`（[符号传播右移](/zh-CN/docs/Web/JavaScript/Reference/Operators/Right_shift)），最左边的 `1` 位的两个副本已从左侧移入，这保留了负号。另一方面，对于 `-9 >>> 2`（零填充右移），零从左移入，因此不会保留数字的负号，结果是一个（大）正数。

左操作数将被转换为无符号 32 位整数，这意味着浮点数将被截断，而超出 32 位边界的数字将溢出/下溢。

右操作数将转换为无符号的 32 位整数，然后取模 32，因此实际移位偏移量将始终是介于 0 和 31 之间的正整数（包括 0 和 31）。例如，`100 >>> 32` 与 `100 >>> 0` 相同（并产生 `100`），因为 32 模 32 是 0。

## 示例

### 使用无符号右移

```js
9 >>> 2; // 2
-9 >>> 2; // 1073741821
```

## 规范

{{Specifications}}

## 浏览器兼容性

{{Compat}}

## 参见

- [JS 指南：位运算符](/zh-CN/docs/Web/JavaScript/Guide/Expressions_and_Operators#位运算符)
- [无符号右移赋值运算符](/zh-CN/docs/Web/JavaScript/Reference/Operators/Unsigned_right_shift_assignment)