---
title: 原生js 转换 Url
date: 2018-03-16 21:27:28
tags:
- 原生js
---
JavaScript正则表达式及字符串匹配函数

解析这样一个Url
```bash
str = "https://www.baidu.com?name=lili&age=20&gender=男";  
```
我们用如下函数来解析
```bash
function parseStrObjByRegExp(strDes) {  
    var obj = {};  
    strDes.replace(/(\w+)(?:=([^&]*))?/g, function (str, key, value) {  
        obj[key] = value;  
    });  
    return obj;  
}  
var obj = parseStrObjByRegExp("name=jack&age=20&love=lily"); 
```
这里应用到了 正则表达式冒号的使用
```bash
   (?:  pattern)是非捕获型括号  匹配pattern，但不捕获匹配结果。
   (pattern )是捕获型括号。  匹配pattern，匹配pattern并捕获结果,自动获取组号
   (?<name> pattern )  匹配pattern，  匹配pattern并捕获结果，设置name为组名 
      使用小括号指定一个子表达式后，匹配这个子表达式的文本(也就是此分组捕获的内容)可以    在表达式或其它程序中作进一步的处理。默认情况下，每个捕获组会自动拥有一个组号，规则   是：从左向右，以分组的左括号为标志，第一个出现的分组的组号为1，第二个为2，以此类推。 
      如果正则表达式中同时存在普通捕获组和命名捕获组，那么捕获组的编号就要特别注意，     编号的规则是先对普通捕获组进行编号，再对命名捕获组进行编号。 
     为了避免括号太多使编号混乱，也为了避免无用的捕获提高效率，在不需要捕获只需要指定   分组的地方就可以使用非捕获型括号。问题里的非捕获型括号就是为此使用的
```
以及replace() 方法用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。
```bash
stringObject.replace(regexp/substr,replacement)
```
```bash

参数         	描述
regexp/substr   必需。规定子字符串或要替换的模式的 RegExp 对象。
                请注意，如果该值是一个字符串，则将它作为要检索的直接量文本模式，而不是首先被转换为 RegExp 对象。

replacement	    必需。一个字符串值。规定了替换文本或生成替换文本的函数。
```
最后解析的结果是这样子的
```bash
obg{
    name:"jack",
    age:"20",
    love:"lily"
    }
```


