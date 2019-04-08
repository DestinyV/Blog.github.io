---
title: 数组sort()中文排序
date: 2018-03-16 22:19:17
tags:
- 原生js
---
   sort() 方法用于对数组的元素进行排序,并返回数组。默认排序顺序是根据字符串Unicode码点。
   ```bash
   var newArr = [];
       newArr[0] = "aa";
       newArr[1] = "ee";
       newArr[2] = "dd";
       newArr[3] = "uu";
       newArr[4] = "ee";
       newArr[5] = "cc";
       newArr[6] = "qq";
       newArr[7] = "bb";
       document.write(newArr+'</br>');
       document.write(newArr.sort() +'</br>');
       //aa,ee,dd,uu,ee,cc,qq,bb
       //aa,bb,cc,dd,ee,ee,qq,uu
   ```
   语法：arrayObject.sort(sortby)；参数sortby可选。规定排序顺序。必须是函数。
   注：如果调用该方法时没有使用参数，将按字母顺序对数组中的元素进行排序，说得更精确点，是按照字符编码的顺序进行排序。要实现这一点，首先应把数组的元素都转换成字符串（如有必要），以便进行比较。
   
   如果想按照其他标准进行排序，就需要提供比较函数，该函数要比较两个值，然后返回一个用于说明这两个值的相对顺序的数字。比较函数应该具有两个参数 a 和 b，其返回值如下：
   若 a 小于 b，在排序后的数组中 a 应该出现在 b 之前，则返回一个小于 0 的值。
   若 a 等于 b，则返回 0。
   若 a 大于 b，则返回一个大于 0 的值。
   
   ```bash
   var newBrr = [];
       newBrr[0] = 55;
       newBrr[1] = 5;
       newBrr[2] = 4;
       newBrr[3] = 45;
       newBrr[4] = 59;
       newBrr[5] = 15;
       newBrr[6] = 35;
       newBrr[7] = 75;
       document.write(newBrr+'</br>');
       document.write(newBrr.sort(orderNumber) +'</br>');
       function orderNumber(a,b) {
         if(a>b){
             console.info(newBrr);
             //return 1;
             return -1;
         }else if(a<b){
             console.info(newBrr);
            // return -1;
             return 1;
         }else{
             console.info(newBrr);
             return 0;
         }
       }
       //55,5,4,45,59,15,35,75
       //75,59,55,45,35,15,5,4  这里是倒序！
       ```
       特定顺序的汉字排序！！！
       
       ```bash
       var arr = [
               {age:11,name:"好好"},
               {age:11,name:"得到"},
               {age:11,name:"嗯嗯"},
               {age:11,name:"好好"},
               {age:11,name:"哇喔"},
               {age:11,name:"前期"},
               {age:11,name:"刚刚"}
           ];
           for(i = 0;i<arr.length;i++){
               document.write(arr[i].name+"<br/>");
           }
       
           var arrComp ={
               "好好":4,
               "得到":7,
               "嗯嗯":1,
               "哇喔":5,
               "好好":3,
               "前期":2,
               "刚刚":6
               };
               /*我想得到：嗯嗯
                        前期
                        好好
                        好好
                        哇喔
                        刚刚
                        得到   这样的排序！*/
       
           /*document.write(arr.name+'</br>');
           document.write(arr.sort(CompareText)+'</br>');*/
           var show = arr.sort(CompareText);
           for(i = 0; i < show.length;i++)
           {
       
               document.write(show[i].name+"</br>");
           }
           /**
            * @return {number}
            */
           function CompareText(a,b) {
               return arrComp[a.name] - arrComp[b.name];
           }
           /*
           好好
           得到
           嗯嗯
           好好
           哇喔
           前期
           刚刚*/
           /*
           嗯嗯
           前期
           好好
           好好
           哇喔
           刚刚
           得到*/
           ```
