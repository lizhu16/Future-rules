## 1.命名
+ 使用驼峰命名方式
+ boolean 类型的变量使用 is 或 has 开头
  
**推荐**
``` javascript
let isReady = false;
let hasMoreCommands = false;
```

## 2.操作符的空格
+ 操作符前后都需要添加空格
  
**推荐**
``` javascript
var sum = 1 + 2
```

##3.首选函数式风格

函数式编程让你可以简化代码并缩减维护成本，因为它容易复用，又适当地解耦和更少的依赖。

**不推荐**
``` javascript
var arr = [10, 3, 7, 9, 100, 20]
var sum = 0
var i

for(i = 0; i < arr.length; i++) {
  sum += arr[i]
}

console.log('The sum of array ' + arr + ' is: ' + sum)
``` 

**推荐**
``` javascript
var arr = [10, 3, 7, 9, 100, 20]

var sum = arr.reduce(function(prevValue, currentValue) {
  return prevValue + currentValue
}, 0)

console.log('The sum of array ' + arr + ' is: ' + sum)

``` 

## 4.避免不必要的 DOM 操作
