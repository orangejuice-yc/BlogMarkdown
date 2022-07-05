---
title: 高阶函数（ Higher-order function ）
# date: 2018-07-16 09:39:40
tag: [Higher-order function]
category: "Functonal Programming"
---

## 高阶函数 (Higher-order function)的定义

### 可以把函数作为参数传递给另一个函数
```javascript
// forEach 
function forEach (array, fn) { 
    for (let i = 0; i < array.length; i++) { 
        fn(array[i]) 
    } 
}
// filter 
function filter (array, fn) { 
    let results = [] 
    for (let i = 0; i < array.length; i++) { 
        if (fn(array[i])) { 
            results.push(array[i]) 
        } 
    }
    return results 
}
```
### 可以把函数作为另一个函数的返回结果
```javascript
function makeFn () { 
    let msg = 'Hello function' 
    return function () { 
        console.log(msg) 
    } 
}
const fn = makeFn() 
fn()
```
```javascript
// once 
function once (fn) { 
    let done = false 
    return function () { 
        if (!done) { 
            done = true 
            return fn.apply(this, arguments) 
        } 
    }
}

let pay = once(function (money) { 
    console.log(`支付：${money} RMB`) 
})
// 只会支付一次 
pay(5) 
pay(5) 
pay(5)
```
## 使用高阶函数的意义
抽象可以帮我们屏蔽细节，只需要关注与我们的目标
高阶函数是用来抽象通用的问题
```javascript
// 面向过程的方式 
let array = [1, 2, 3, 4] 
for (let i = 0; i < array.length; i++) { 
    console.log(array[i]) 
}
// 高阶函数 
let array = [1, 2, 3, 4] 
forEach(array, item => { 
    console.log(item) 
})
let r = filter(array, item => { return item % 2 === 0 })
```
## 常用高阶函数
forEach 
map 
filter 
every 
some 
find/findIndex 
reduce 
sort 
……

```javascript
const map = (array, fn) => { 
    let results = [] 
    for (const value of array) { 
        results.push(fn(value)) 
    }
    return results 
}

const every = (array, fn) => { 
    let result = true 
    for (const value of array) {
        result = fn(value) 
        if (!result) { 
            break 
        } 
    }
    return result 
}

const some = (array, fn) => { 
    let result = false 
    for (const value of array) { 
        result = fn(value) 
        if (result) { 
            break 
        } 
    }
    return result 
}
```