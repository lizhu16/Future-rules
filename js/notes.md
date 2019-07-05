## 1.单行注释

必须独占一行。`//`后跟一个空格，缩进与下一行被注释说明的代码一致

## 2.多行注释

避免使用 /*...*/ 这样的多行注释。有多行注释内容时，使用多个单行注释


## 3.函数/方法注释

函数/方法注释必须包含函数说明，有参数和返回值时必须使用注释标识


``` javascript
 /**
 *
 * 功能详细描述
 * @create author 作者
 * @create time 创建时间
 * @update time 修改时间 (2017/08/09 xx:xx)
 * @param <String> arg1 参数1
 * @param <Number> arg2 参数2
 * @return <Boolean> 返回值
 */

 ```


## 4.文件注释

文件注释应包括文件版本、创建或者修改时间、功能、作者
``` javascript
  /**
 * 功能详细描述
 * @version 文件版本
 * @file index.js
 * @create author 创建者
 * @create time 创建时间
 * @update time 修改时间 (2017/08/09 xx:xx)
 */

 ```


  >**注意Vue项目中data中数据应添加注释说明data的用途**