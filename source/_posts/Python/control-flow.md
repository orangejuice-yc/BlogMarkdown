---
title: 控制流
date: 2019-11-08 14:59:02
tag: 'Python'
category: 'Python'
---
## 条件语句
### if语句
if语句是是一种条件语句，根据条件为 true 还是 false 运行或执行相关代码。
``` python
if phone_balance < 5:
    phone_balance += 10
    bank_balance -= 10
```
if 语句以关键字 if 开始，然后是要检查的条件，在此例中是 phone_balance < 5，接着是英文冒号。
条件用布尔表达式指定，结果为 True 或 False。
这行之后是一个条件为 true 时将执行的缩进代码块。在此例中，仅在 phone_balance 小于 5 时才执行使 phone_balance 递增和使 bank_balance 递减的行。如果不小于 5，这个 if 块中的代码将被跳过。