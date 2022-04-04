 

# js

## math

数学函数：但是它不是一个函数，他是一个对象，对象中存储了很多操作数字的属性方法，因此被称为数学函数。

```javascript
console.log(typeof Math);
console.dir(Math);
Math = {
    PI: 3.141592653589793,
    abs: function() {
        [native code]
    }
    ceill: function() {
        [native code]
    }

}
Math.PI
Math.abs()
```

### Math中的常用属性和方法 

Math.abs([number value]) 

获取绝对值 

如果是数字类型就直接转成绝对值，如果是其他类型使用Number先转成数字，不能转成数字的会返回NaN 

```javascript
console.log(Math.abs(12.5)) //=>12.5
console.log(Math.abs(-12.5)) //=>12.5
console.log(Math.abs(0)) //=>0
console.log(Math.abs('1')) //=>1
console.log(Math.abs('12px')) //=>NaN
console.log(Math.abs(true)) //=>1
```

2. Math.ceil / floor /

 把一个数向上或者向下取整

 ceil:向上取整

 向上取整，贞要有小数就往整数位+1，负数相反

```javascript
console.log(Math.ceil(12.1))
console.log(Math.ceil(12.5))
console.log(Math.ceil(12.9))
console.log(Math.ceil(-12.1))
console.log(Math.ceil(-12.5))
console.log(Math.floor(-12.9))
console.log(Math.ceil('-12px'))
```

// floor:向下取整

// 只要有小数就往整数位+1，正数直接去除小数位

```javascript
console.log(Math.floor(12.1))
console.log(Math.floor(12.5))
console.log(Math.floor(12.9))
console.log(Math.floor(-12.1))
console.log(Math.floor(-12.5))
console.log(Math.floor(-12.9))
console.log(Math.floor('-12px'))
```

round:四舍五入, 负数中的, 5属于舍 

```javascript
console.log(Math.round(12.1))
console.log(Math.round(12.5))
console.log(Math.round(12.9))
console.log(Math.round(-12.1))
console.log(Math.round(-12.5))
console.log(Math.round(-12.9))
console.log(Math.round('-12px'))
```

Math.max / min 最大值和最小值 

```javascript
conso1e.log(Math.max(12, 5, 68, 23, 45, 3, 27));
conso1e.log(Math.min(12, 5, 68, 23, 45, 3, 27));
```

 思考题：如何基于Math.max/min获取数组中的最大值最小值？ 

```javascript
console.log(Math.max([12, 5, 68, 23, 45, 3, 27])); // =>NaN此处是只传第一个值，是个数组，和内置的语法要求不符
```

 开平方 

```javascript
console.log(Math.sqrt(9)); // =>3符合N*N=M这样的M才能整开平方
console.log(Math.sqrt(-9)); // =>NaN负数开不了平方
```

底数 

```javascript
// console.log(Math,pow (底数， 幂))
// console.log(Math,pow(2, 10)); //=>1024
```

随机数 

```javascript
for (var i = 0; i < 10; i++) {
    console.log(Math.random())
}
```

获取m~n之间的整数



## 数组

### 数组及数组的常用方法

#### 数组是对象数据类型

```javascript
let ary = [12, 23, 34, 45]
console.log(typeof ary); //=>"object"
console.dir(ary);
// ary = {
//     0: 12,
//     1: 23,
//     2: 34,
//     3: 45,
//     length: 4
// }
// 数字作为索引(key属性名)
// length长度
// ary[0]根据索引获取指定项的内容
// ary,length获取数组的长度
// ary.length - 1最后一项的索引
```

### 数组的常用方法

- 方法的作用和含义
- 方法的实参（类型和含义）
- 方法的返回值
- 原来的数组是否会发生改变

#### 实现数组增删改的方法

这一部分都会修改原有的数组

数组的构造函数Array,我们创建的所有数组都是通过这个构造函数创建出来的对象

而构造函数的共有方法放到原型对象身上，所以如果你要看数组的方法，需要找到构造函数的原型对象上

```javascript
console.log(Array.prototype)
// at:f at()
// concat:f concat()
// constructor:f Array()
// copywithin:f copywithin()
// entries:f entries()
```



`push`

push：向数组末尾增加内容
@params
多个任意类型
@dreturn
新增后数组的长度 

原数组会被改变

```
let ary = [10, 20];
let res = ary.push(30, 'AA');
console.log(res, ary); // [10,20,30,'AA']
```

基于原生JS操作键值对的方法，也可以向末尾添加一项新的内容

```
ary[ary.length] = 30;
ary[ary.length] = 'AA';
console.log(ary)
```



`unshift` 

unshift:向数组开始位置增加内容

@params

多个任意类型

@areturn

新增后数组的长度

原数组会被改变

```
let ary = [10, 20];
let res = ary.unshift(30, 'AA');
console.log(res, ary) //=>4 [30,'AA',10,20]
```

如何基于原生JS实现向数组开头添加内容？ 

```
res=[40,...ary];
console.log(res,ary);//=>[40,30,'AA',10,20]
```

基于原生ES6展开运算符，把原有的ARY克隆一份，在新的数组中创建第一项，其余的内容使用原始ARY中的信息即可，也算实现了向开始追加的效果 



`pop`:删除数组的最后一项

@params

没有参数，但是传参之后不会报错，因为放到arguments里面了

@areturn

新增后数组的长度

原数组会被改变

```
let ary = [10, 20, 30, 40];
let res = ary.pop();
console, log(res, ary) //=>40[10,20,30]
```

基于原生JS实现删除最后一项 

```
ary[2] = nu11; //=>假删除
console.log(ary); //=>[10,20,nu11]
```

```
delete ary[2];
console.log(ary); //=>[10,20,empty]
```

```
ary.length--;
console.log(ary); //=>[10,20]
```



`shift`

shift:删除数组中的第一项

@params

@dreturn

删除的那一项

```javascript
let ary = [10, 20, 30, 40];
let res = ary.shift();
console.log(res, ary) //=>10[20,30,40]
```

基于原生]S中的DELETE,把数组当做普通的对象，确实可以别除掉某一项内容，但是不会影响数组本身的结构特点(length长度不会跟着修改)，真实项目中杜绝这样的别除使用 

```javascript
delete ary[0];
console.log(ary); //=>{1:30,2:40,length:3}
```



`splice`

splice: 实现数组增加，删除，修改

@params

n,m都是数字从索引n开始删除m个元素(m不写，是删除到末尾) 

@dreturn

把删除的部分用新数组存储起来返回 

```javascript
let ary = [10, 20, 30, 40, 50, 60, 70, 80, 90]; 
let res = ary.sp1ice(2, 4); //=>从下标2的位置往后删除4个
console.log(res, ary) //=>[30,40,50,60][10,20,70,80,90]
```

基于这种方法可以清空一个数组，把原始数组中的内容以新数组存储起来（有点类似数组的克隆： 把原来数组克隆一份一模一样的给新数组) 

```javascript
let ary = [10, 20, 30, 40, 50, 60, 70, 80, 90];
let res = ary.splice(0); //=>从下标2的位置往后删除4个
console.log(res, ary)
```

//删除最后一项和第一项

```
ary.splice(ary.length - 1);
console.1og(ary)//=>[18,20,70,88]
ary.splice(0, 1);
console.log(ary) //=>[20,70,80]
```

// 原数组会被改变

基本功能，用插入的元素替代的删除元素

```
let ary = [10, 20, 38, 40, 50, 60, 78, 88, 90];
let res = ary.splice(1, 3, 40, 50, 60);
console.log(res, ary);
```

实现增加

```
let ary = [10, 20, 30, 40, 50, 60, 70, 80, 90];
let res = ary.splice(3, 0, 100);
console.log(res, ary)
```

向数组末尾追加 / 向数组开头追加 

```
let ary = [10, 20, 30, 40, 50, 60, 70, 80, 90];
let res = ary.splice(ary.length, 0, 100);
console.log(res, ary)
```

```
let ary = [10, 20, 30, 40, 50, 60, 70, 80, 90];
let res = ary.splice(0, 0, 100);
console.log(res, ary)
```

#### 数据的拼接

此组学习的方法,原来数组不会改变

`slice` 

slice:实现数组的查询 

@params

n, m都是数字从索引n开始， 找到索引为m的地方（ 不包含m这一项,含头不含尾）

@return

把找到的内容以一个新数组的形式返回

原数组不会被改变

基础用法，获取数组中的某一段片段 

```javascript
let ary = [10, 20, 30, 40, 50];
let res = ary.slice(1);
console.log(res, ary) //=>[10,20,30]  [10,20,30,40,50]
```

m不写是找到末尾 

```
res = ary.slice(1);
console.log(res); //=>[20,30,40,50]
```

//数组的克隆，参数0不写也可以 

```
res = ary.slice(0);
console.log(res);//=>[10,20,30,40,50]
```

如果n/m为负数会怎样，如果n>m又会怎样，如果是小数会怎样，如果是非有效数字会咋滴，如果m或者n的值比最大索引都大会怎样？ 

```
let ary = [10, 20, 30, 40, 50];
console.log(ary[-2]); //=>undefined
console.log(res, ary) //=>[10,20,30]  [10,20,30,40,50]
res = ary.slice(-3, -1); //slice方法会将你传入的负数，转换成从右往左数的元素个数
console.log(res); //=>[30,40]
```

```
let ary = [10, 20, 30, 40, 50];
res = ary.slice(3, 1) // slice默认从从左往右，起始下标大于了结束下标，返回空数组
```

```
let ary = [10, 20, 30, 40, 50];
res = ary.slice(1.4, 3.6); // slice如果传入小数，会将小数向下取整，再使用
console.log(res); //=>[20,30]
```

```
let ary = [10, 20, 30, 40, 50];
res = ary.slice('AA', 'BB') //slice传入非有效字符。返回空数组
console.log(res); //=>[]
```

```
let ary = [10, 20, 30, 40, 50];
res = ary.slice(5, 6) //slice中的m和n如果超出最大下标，返回空数组
console.log(res);
```



笔试题：请写出3种数组的克隆方式

可以用ES6语法...ary展开进行克隆

可以用slice切片把值改为0也可以克隆

可以用concat拼接输出也可以克隆



`concat`

concat:实现数组拼接
@params
多个任意类型值
@return
拼接后的新数组
原数组不会被改变

```
let ary1 = [10, 20, 30];
let ary2 = [40, 50, 60];
let res = ary1.concat();
console.log(ary1, res); //=>如果不加任何参数，可以将元素克隆
```

```
let ary1 = [10, 20, 3 o];
let ary2 = [40, 58, 60];
let res = ary1.concat(1, 2, 'AA', ary2, {
    name: '王二麻子'
});
console.log(ary1, res) //=>[16,26,30,1,2,"AA',49,50,60,{...}]
```

#### 数组转字符串

`tostring`

tostring:数组转字符串
@params
@return
转换后的字符串,每一项用逗号分离
原数组不会被改变

```
let ary1 = [10, 20, 30];
let res = ary1.tostring();
console.log(res); //=>'10,20,30'
console.log([].tostring()); //=>''
console.log([12].tostring()); //=>'12'
```

`join`

join:把数组转换为字符串
@params
定制的分隔符字符串格式
@return
转换后的字符串
原数组不会被改变

```
let ary1 = [10, 28, 30];
let res = ary1.join(); //=>默认用逗号隔开
console.log(res); //=>10,20,30
```

```
let ary1 = [18, 28, 30];
let res = ary1.join('+');
console.log(res); //=>10+20+30
console.log(eval(res)) //=>eval将字符串格式的代码执行，60
```



`indexof`/`lastIndexof` 

indexOf/lastIndexOf:检测当前项在数组中第一次或者最后一次出现位置的索引值（在IE6-8中不兼容） 

@params
制定的分隔符（字符串格式）
@return
这一项出现的位置索引值（数字），如果数组中没有这一项，返回的结果是-1
原数组不会被改变

```
let ary1=[10,28,30];
let res = ary1.indexof(10);
console.log(res); //=>0
```

```
let ary1=[10,2,30];
let res = ary1.indexof(40);
console.log(res); //=>-1
```

```
let ary1 = [16, 20, 30];
let res = ary1.lastIndexof(40);
console.log(res); //=>-1
```

```
let ary1 = [18, 20, 30];
let res = ary1.lastIndexof(30);
console.log(res); //=>2
```

```
let ary1 = [10, 20, 30];
if (ary1.indexof('AA') < 0) {
    //不包含
}
```

```
console.log(ary1.includes(10));
if (!ary1.includes('AA')) {
    //不包含
}
```

#### 数组的排序和排列 

`reverse` 

reverse: 把数组倒过来排列
@params
@return
排列后的新数组
原来数组改变

```
let ary = [12, 15, 9, 28, 10, 22];
ary.reverse();
console.log(ary); //=>[22,10,28,9,15,12]
```



`sort` 

@params
可以没有， 也可以是个函数
@return
排列后的新数组
原来数组改变

```
let ary = [12, 15, 9, 28, 18, 22];
let ary = [3, 6, 7, 4, 1, 3, 5, 9];
let res = ary.sort() // => 不传参的时候ǐ无法排序2位数以上的数字(个位数默认从小到大排序)
console.log(res, ary); // =>[16,12,15,22,28,9]
```

```
let ary = [12, 15, 9, 28, 10,
ary.sort(function(n, m) {
    return n - m; //=>从大到
}); //=>如果要进行多位数的排
console.log(ary);
```

```
let ary = [12, 15, 9, 28, 10, 22];
ary.sort(function(n, m) {
    return m - n; //=>从小到大排序
}); //=>如果要进行多位数的排序，需要传入一个回调函数
console.log(ary);
```

以后尽量使用箭头函数 

```
let ary = [12, 15, 9, 28, 10, 22];
ary.sort((n, m) => m - n); //=>扒大到小排序
console.log(ary);
```





#### 遍历数组中每一项的方法

`forEach`
`map`
`filter`
`find`
`reduce`
`some`
`every`

`forEach`
forEach: 遍历数组中的每一项内容
@params
回调函数
@return
没有返回值
原来数组不变

```
let ary = [12, 15, 9, 28, 10, 22];

// 基于原生JS实现数组的遍历
// for (var i 0; i ary.length; i++) {
// console.log('索引：' + i, '值：+ary[i]);
// }

ary.forEach((item, index) => console.log('索引：' + index + '值：' + item));
```





#### 数组去重

1. 把最后一项的值获取到替换当前这一项

2. 删除最后一列

   ```javascript
   let ary = [1, 2, 3, 1, 2, 1, 2, 3, 2, 1, 2, 3];
   
   let obj = {};
   
   for (var i = 0; i < ary.length; i++) {
   
   // 2,循环数组中的每一项，把每一项向对象中进行存储=>item:item
   
   let item = ary[i]
   
   // 3.每一次存储之前进行判断：验证obj中是否存在这一项
   
   if (obj[item] !== undefined) {
   
   // 已经存在这一项
   
   ary[i] = ary[ary.length - 1];
   
   ary.length--;
   
   i--;
   
   continue;
   
    }
   
        obj[item] = item;
   
    }
   
    console.log(ary)
   ```






#### 封装函数

```
function unique(ary) {
    let obj = 0;
    for (var i = 0; i < ary.length; i++) {
        let item = ary[i];
        if (obj[item] !== undefined) {
            ary[i] = ary[ary.length - 1];
            ary.length--;
            i--;
            continue;
        }
        obj[item] = item;
    }
}
```



## 字符串

### 字符串中常用方法

所有用单引号、双引号、反引号包起来的都是字符串 

`charAt`: 根据索引获取指定位置的字符

`charCodeAt`: 获取指定字符的ASII码值(Unicode编码值)

@params

n[number] 获取字符指定的索引

@return

返回查找到的字符

找不到返回的是字符串不是undefined, 或者对应的编码值

```javascript
let str = 'asdlkjasdlkjasdlkjasdlkjasdlkjasdlkj'
console.log(str.charAt(3)) //l;
console.log(str[3]) //l;
console.log(str.charAt(10000)) //''
console.log(str[10000]) //undefined
console.log(str.charCodeAt(3)) //108
console.log(string.fromcharCode(108)); //=>'l'
```



都是为了实现字符串的截取(在原来字符串中查找到自己想要的)
`substr`(n,m):从索引n开始截取m个字符,m不写截取到末尾
`substring`(n,m):从索引n开始找到索引为m处(含头不含尾)
`slice`(n, m): 和substring一样， 都是找到索引为m处， 但是slice可以支持负数作为索引， 其余两个方法时不可以的

```javascript
let str = 'asdlkjasdlkjasdlkjasdlkjasdlkjasdlkj';
console.log(str.substr(3, 7)) //lkjasdl
console.log(str.substring(3, 7)) //lkja

console.log(str.substr(3)); //lkjasdlkjasdlkjasdlkjasdlkjasdlkj
console.log(str.substring(3, 10000)); //lkjasdlkjasdlkjasdlkjasdlkjasdlkj
//超过索引的也会截取到末尾

console.log(str.substring(-7, -3)) //''
console.log(str.slice(-7, -3)) //jasd
//slice可以倒着查找
```



验证字符是否存在
`indexOf`(x,y):获取x第一次出现位置的索引,y是控制查找的起始位置索引
`lastIndexOf`(x):最后一次出现位置的索引

`includes`(x)不兼容IE6~8,而字符串中includes是兼容的

没有这个字符,返回的结果是-1

```
let str = 'asdlkjasdlkjasdlkjasdlkjasdlkjasdlkj';
 console.log(str.indexOf('l')); //3
 console.log(str.lastIndexOf('l')); //33
 console.log(str.indexOf('@')); //-1

console.log(str.indexOf('kja')); //4  验证整体第一次出现的位置,返回的索引是第一个字符所在位置
console.log(str.indexOf('qwer')); //-1验证整体第一次出现的位置，有任何不匹配都找不到，返回-1
console.log(str.indexOf('l', 10)); //15查找字符串索引20及之后的字符串中，第一次出现的位置

// 如何判断一个字符串中是否包含字符
if (str.indexOf('@') === -1) {
     // 不存在
 }

//数组中的includes不兼容IE6~8,而字符串中includes是兼容的
 if (!str.includes('@')) {
     // 不存在
 }
```



字符串中字母的大小写转换 

`toUpperCase`():转大写
`toLowerCase`():转小写

```
let str = 'asdlkjasdlkjasdlkjasdlkjasdlkjasdlkj';
str = str.toUpperCase();
console.log(str)

str = str.toLowerCase();
console.log(str)

// 实现字符串首字母大写
str = str[0].toUpperCase() + str.substring(1, str.length);
console.log(str)
```



`split`([分隔符]):把字符按照指定的分隔符拆分成数组(分数组中join对应
split支持传递正则表达式
@params
   分隔符或者正则表达式
@return
   用分隔符分隔开的字符串组成的数组
需求:把|分隔符变为,分隔符

```
let str = 'music|movieleat|sport';
let ary = str.split('|'); //['music', 'movieleat', 'sport']
// ary = ary.join('~'); //music~movieleat~sport
console.log(ary)
```



`replace`(老字符,新字符):实现字符串的替换(经常伴随着正则使用) 

```
let str = 'asdlkjasdlkjasdlkjasdlkjasdlkjasdlkj';
let res = str.replace('aa', 'a')
console.log(str, res)
```

```
let str = '真爱@无价@倒拔@垂杨柳 ';
str = str.replace('@', '-'); //=>在不使用正则表达式的情况下，执行一次replace只能暂换一次字符
console.log(str);
```

```
str = str.replace(/@/g, '-');
console.log(str);
```

`match`
`localCompare`
`trim/trimLeft/trimRight`

...

控制台输出String.prototype查看所有字符串中提供的方法





#### 实现一些常用的需求

方案一：一路replace 

封装一个函数，传入字符串格式的时间，返回需要的日期格式 

```
time = time.replace('-', '年').replace('-', '月').replace(' ', '日').replace(':', '时').replace(':', '分') + '秒';
console.log(time);
```

方案二：先劈成2个大数组 

```
time = time.split(' ');
let dat = time[0].split('-');
time = time[1].split(':');
let year = dat[0];
let month = dat[1];
let day = dat[2];
let hour = time[0];
let min = time[1];
let second = time[2];
console.log(year + '年' + month + '月' + day + '日' + hour + '时' + min + '分' + second + '秒')
```

方案三： 

```
let ary = time.split(/(?: |-|:)/g)
console.log(ary[0] + '年' + addZreo(ary[1]) + '月' + ary[2] + '日' + ary[3] + '时' + addZreo(ary[4]) + '分' + ary[5] + '秒');
```



```
function timeFormat(time, templates) {
    let ary = time.split(/(?: |-|:)/g);
    templates = ary[0] + 'addZreo(ary[1])+' + addZreo(ary[2]) + '' + addZreo(ary[3]) + '时' + addZreo(ary[4]) +
        '分' + addZreo(ary[5]) + '秒';
    return templates;
}
```



// 获取问号后面的值 

```
let url = 'https://www.baidu.com/?1x=1&name=aaa&teacher=bbb#box';
        // 实现一个方法queryURLParameter获取一个URL地址问号后面传递的参数信息
let askIndex = url.indexOf('?');
let wellIndex = url.indexOf('#');
let askText = url.substring(askIndex + 1, wellIndex);
let wellText = url.substring(wellIndex + 1);
let askary = askText.split('&');
let askObj = {};
askary.forEach(function(item) {
    //['1x=1','name=aaa','teacher=bbb']
    let ary = item.split('=');
    askObj[ary[0]] = ary[1];
});
askObj['HASH'] = wellText;
console.log(askObj);
```



```
function queryURLParams(url) {
            let result = {},
                reg1 = /([^?=&#]+)=([^?=&#]+)/g,
                reg2 = /#([^?=&#]+)/g
            url.replace(reg1, (n, x, y) => result[x] = y);
            url.replace(reg2, (n, x) => result['HASH'] = x);
            return result;
        }
        console.log(queryURLParams(url));

```



## 时间对象

```
let time = new Date();
// 获取当前客户端(本地电脑)本地的时间
// 这个时间用户是可以自己修改的，所以不能作为重要的参考依据
// Thu Mar 24 2022 11:01:56 GMT+0800 (中国标准时间)
// 获取的结果不是字符串类型是对象数据类型的，属于日期对象（或者说是Date这个类的实例对象）
console.log(typeof time); //=>object
console.dir(Date.prototype);
```



> 标准日期对象中提供了一些属性和方法，供我们操作日期信息

- getFullYear()获取年

- getMonth()获取月结果是0-11代表第一月到第十二月 
- getDate()获取日 
- getDay()获取星期,结果是0~6代表周日到周六
- getHours()获取时
- getMinutes()获取分
- getSeconds()获取秒
- getMiliseconds()获取毫秒
- getTime()获取当前日期距离1970/1/1 00:00:00这个日期之间的毫秒差(时间戳)

- toLocaleDateString()获取年月日(字符串)
- toLocaleString()获取完整的日期字符串



new Date()

>new Date()除了获取本机时间，还可以把一个时间格式字符串转换为标准的时间格式



电子时钟

```javascript
var time = document.getElementById('time');
var dateContent = document.getElementById('date-content');
var day = document.getElementById('day');
let num = 0;
let swt = false;


let timeview = () => {
    let date = new Date();
    let addZero = value => value < 10 ? value = '0' + value : value;
    // 将时间放在第一个div中
    let timeText = date.getHours() + ':' + date.getMinutes() + ':' + date.getSeconds();
    time.innerHTML = timeText;

    // 将日期放在第一个div中
    let dateText = date.getFullYear() + '年' + date.getMonth() + '月' + date.getDate() + '日';
    dateContent.innerHTML = dateText;

    // 将星期放在第一个div中
    let week = ['日', '一', '二', '三', '四', '五', '六'];
    let dayText = '星期' + week[date.getDay()]
    day.innerHTML = dayText;

}
timeview();

setInterval(() => {
    timeview();
}, 1000);

setInterval(() => {
    time.style.textShadow = '0 0 10px aqua'.replace('10px', num + 'px');
    if (num >= 50) {
        swt = false;
    } else if (num <= 0) {
        swt = true;
    }
    swt ? num++ : num--
}, 20);
```



时间格式化的三种方式

1.字符串切割 

```javascript
let addZero = value => value < 10 ? '0' + value : value;
function formatTime(time) {
    // 2.基于时间对象处理
    let ary = time.split(' '),
        aryLeft = ary[0].split('/'),
        aryRight = ary[1].split(':');
    ary = aryLeft.concat(aryRight);
    let result = ary[0] + '年' + addZero(ary[1]) + '月' + addZero(ary[2]) + '日';
    result += addZero(ary[3]) + '时' + addZero(ary[4]) + '分' + addZero(ary[5]) + '秒';
    return result;
}
let time = '2022/3/24 15:28:30';
console.log(formatTime(time))
```

```javascript
let addZero = value => value < 10 ? '0' + value : value;
function formatTime(time) {
    // 2.基于时间对象处理
    let date = new Date(time); //->Thu Mar 24 2022 15:28:30GMT+g8g0(中国标准时间)
    let year = date.getFullYear();
    let month = date.getMonth();
    let day = date.getDate();
    let hour = date.getHours();
    let minute = date.getMinutes();
    let second = date.getSeconds();
    let result = year + '年' + addZero(month) + '月' + addZero(day) + '日';
    result += addZero(hour) + '时' + addZero(minute) + '分' + addZero(second) + '秒';
    return result;
}
let time = '2022/3/24 15:28:30';
console.log(formatTime(time))

```



## DOM及其基本操作

DOM:document object model 文档对象模型, 提供一些属性和方法提供我们操作页面中的元素

**获取DOM元素的方法**

`document.getElementById()`指定在文档中，基于元素的ID或者这个元素对象

`[context].getElementsByTagName()`在指定上下文（容器）中，通过标签名获取一组元素集合

`[context].getElementsByclassName()`在指定上下文中，通过样式类名获取一组元素的集合(不兼容IE6~8)

`[context].getElementsByName()`在整个文档中，通过标签的Name属性值获取一组元素的集合(在IE中只有表单元素的NAME才能识别，所以我们一般应用于表单元素的处理)

`document.body`/`document.head`/`document.documentElement`获取页面中的head/body/html三个元素

`[context].querySelectorl([selector])`在指定上下文中，通过选择器获取
到指定的元素对象

`[context].querySelectorAll([selector])`在指定上下文中，通过选择m获取到指定的元装对象集合



### JS中的节点和描述节点之间关系的属性

> 节点：Node(页面中所有的东西都是节点)
> 节点集合：NodeList(getElementsByName/querySelectorAll)获取的都是节点集合)

- 元素节点

  nodeType:1

  nodeName:大写的标签名

  npdeValue:null

- 文本节点

  nodeType:3

  nodeName:'#text'

  npdeValue:文本内容

- 注释节点

  nodeType:8

  nodeName:'#commer'

  npdeValue:注释内容

- 文档节点

  nodeType:9

  nodeName:'#document'

  npdeValue:null

### 描述这些节点之家关系的属性

chidNodes:获取所有的子节点

children:获取所有元素的子节点(子元素标签的集合)

firtChild:获取第一个子节点

lastChild:获取最后一个子节点

firstElementChild/lastElementChild:获取第一个和最后一个元素子节点(不兼容IE6~8)

previousSibing:获取上一个哥哥节点

nextSibing:获取下一个弟弟节点

parent:获取父级节点



#### JQ的小例子

```javascript
var box = document.querySelector('ul');
// 标准浏览器(非IE6~8)中会把空格当作文本节点处理(childNodes包含所有节点)
console.log(box.childNodes);

// 只想要元素节点(但是IE6~8下， 使用children会把注释也当做元素节点)
console.log(box.children);



// children:获取指定上下文中，所有的子节点
// @params
// context[element]指定的上下文元素信息
// @return
// [array]返回所有的元素节点的集合

function children(context) {
    var resAry = [];
    var allNodeChild = context.childNodes
    for (var i = 0; i < allNodeChild.length; i++) {
        var item = allNodeChild[i];
        item.nodeType === 1 ? resAry.push(item) : null
    }
    return resAry;
}
children(box)
```



获取一个哥哥元素节点 

```javascript
var fangqi = document.querySelector('#fangqi');

function previ(context) {
    var ele = context.previousSibling;

    while (ele.nodeType !== 1) {
        ele = ele.previousSibling;
    }
    return ele;
}
console.log(previ(fangqi))
```

#### 在JS中动态增删改元素

`createElenent`创建元对象

`createTextNode`创建文本对象

`appendChild`把元素添加到容器的末尾

`insertBeFore`把元素添加到指定容器中指定元素的前面

```javascript
var box = document.createElement('div')
box.style.width = '200px';
box.style.height = '200px';
box.style.backgroundColor = 'skyblue';

var text = document.createTextNode('wdnmd')
// 放到父元素的末尾，类似push
// document.body.appendChild(box)
// 插入到指定元素前面
// 父节点.insertBefore(需要插入的节点， beforeElement)
document.body.insertBefore(box, span);
```



cloneNode(true/false)克隆元素或者节点

removeChild移除容器中的某个元素



```javascript
var box = document.getElementById('box')
var li = box.querySelector('li:nth-child(3)')

// cloneNode();的参数为false时，浅克隆，为true时，深克隆
// var liCone = li.cloneNode(false);
// console.log(liCone);
// var liCone = li.cloneNode(true);
// console.log(liCone);

// 移除容器中的某个元素
li.removeChild(li);
```



自定义属性的另一种添加方式

`setAttribute`/`getAttribute`/`remiveAttribute`设置获取移出元素

自定义属性信息(这种方式是把自定义属性放到元素结构上)

`setAttribute`

```
var btn = document.querySelectorAll('button')
for (var i = 0; i < btn.length; i++) {

// 实现原理：通过给对象(堆内存)添加一个新的属性的方式，来将每一个i的值，精选保存在使用的时候去对象的身上寻找这个属性
// btn[i].myIndex = i
// btn[i].onclick = function() {
//     alert(this.myIndex);
// }
}
```

`getAttribute`

```
var btn = document.querySelectorAll('button')
for (var i = 0; i < btn.length; i++) {
// 实现原理2：给相对应的标签添加自有属性并保存相应的值，在需要的时候，通过标签的属性去获取这个值
// 注意：通过给对象添加属性的方式，只能使用对象的获取方式(obj,属性名)，设置在元素结构上的内容只能通过相对应的方式来获取(getAttribute)
// var btns = btn[i];
// btns.setAttribute('myIndex', i);
// btns.onclick = function() {
//     alert(this.getAttribute('myIndex'))
// }
}
```

## GIT 于NPM 

GIT基础管理：下载安装、基本介绍、集中式、分布式、工作流程、基础命令等（这是第一阶段：基础应用)
GIT-HUB的应用网站的常规操作、与GT操作结合管理
NODE模块管理工具：NPM的基础应用



GIT基础管理
官网：https:/git-scm.com/
git的发展历史
版本控制系统：集中式vs分布式
git的工作流程
git中常用的命令操作



GIT版本控制系统

版本控制系统：
1.记录历史版本信息（记录每一次修改的记录）
2.方便团队相互之间协作开发

....



常用的版本控制系统

cvs/svn:集中式版本控制系统

git:分布式版本控制系统





## git的全局配置

第一次安装完成git后，我们在全局环境下配置基本信息：我是谁？

```powershell
$ git config -l //查看全局信息
$ git config --global -l //查看全局配置信息

配置全局信息 用户名和邮箱
$ git config --global user.name 'xxx'
$ git config --global user.email 'xxx@xxx.xxx'
```

### 创建仓库完成版本控制

**创建本地git仓库**

```powershell
$ git init
// 会生成一个隐藏文件夹'.git'(这个文件夹千万不要删，因为暂存区和历史区还有一些其它的信息都在这里，删了就不是一个完整的gt仓库))
```

**在本地编写完成代码后（在工作区），把一些文件提交到暂存区**

```powershell
$ git add xxx  把某一个文件或者文件夹提交到暂存区
$ git add .  把当前仓库中所有最新修改的文件都提交到暂存区
$ git add -A

$ git status 查看当前文件的状态（红色代表在工作区，绿色代表在暂存
区，看不见东西证明所有修改的信息都已经提交到历史区)
```

**提交到历史区**

```powershell
$ git commit -m '注释'  将暂存区的文件提交到历史，并生成版本号
aa969e0a6d55bebbffceea0d7f324821e983376d

$ git log  查看提交记录
```

**版本控制的回滚**

```powershell
$ git reset --hard HEAD^  回到上一个版本
$ git reset --hard HEAD~2  回滚到防2个版本
$ git reset --hard xxx(版本号或版本号前7位)，回滚到指定版本号，如果是版本号的前几位，git会自动局找匹配的版本号
$ git reset --hard xxx(版本号或板本号前7位)filename,回某个文件到指定版本号
$ git reflog 若想回滚到未来版本，输出用户之前的所有命令找到用户以前的commit操作的版本id
```

**git和git-hub**

GIT-HUB https://www.github.com

一个网站(一个开源的源代码管理平台)，用户注册后，可以在自己账户下创建一个仓库，用来管理项目的源代码(源代码是基于git传到仓库中)

我们熟知的插件，类库、框架等都在这个平台上有托管。我们可以下我观看和研究原码等



settings 用户设置

account 可以修改用户名

securty 可以修改自己的密码

emalis 邮箱(必须进行邮箱效验)



**创建仓库**

new repository ->填写信息->Create repository

public 公共仓库作为开源的项目

private 私有仓库作为内部团队协作管理的项目

setings->删除仓库 Delete this repository

Code 可以查看历史版本信息和分支信息



**把本地仓库信息提交到远程仓库**

```powershell
//=>建立本地仓厍和远程仓阵挂接
查看本地仓库和那些远程仓库保特链接
$ git remote -v
让本地仓库和远程仓库新建一个链接origin是随便起的一个链接名（可以改成目己想受的，只不过一般都用这个名字）
$ git remote add origin[GIT远程仓厍地址]
刷除关联信息
$ git remote rm origin
```

```powershell
提交之前最好先拉取
$ git pull origin main
把本地心码提交到远程仓库（需受输入GitHub的用户名和密码）
$ git push origin main
```



```powershell
$ git clone [远程仓库git地址] [别名:可以不设置，默认是仓库名]
真实项目开发流程
1.组长或者负责人先创建中央仓库(增加协作者)
2.小组成员基于$ git clone 把远程仓库及默认的内容克隆到本地一份(解决了三件事:初始化一个本地仓库'$ git init',和对应的远程仓库保持了关联'$ git remote add',把远程仓车默认内客拉取到本地'git pull')
库'$ git init',和对应的远程仓库也保特了关联"git remote add"、把远程仓库默认内容拉取到本地”$ git pull”)
3.每个组员写完自己的程序后，基于”git add./git comnit"把自己德改的内客存故到历史区，然后运过"git
pull/git push“把本地信息和运程仓库信息保持同步即可（可能涉及冲突的处理）
```



**NPM**

node package manger :NODE模块管理工具，根据NPM我们可快速安装卸载所需要的资源文件（例如：jQuery、vue、Vue-router...)

去NODE官网：https://nodejs.org/zh-cn下载NODE(长期支持
版)，安装NODE后，NPM也就跟音安装了
$ node -v
$ npm -v  出现版本号证明安装成功



**基于NPM进行模块管理**

https:/www.npmjs..com：基于npm是从npmjs.com平台上下载安装

```powershell
$ npm install xxx  把模块安装在当前项目中(node_modules)
$ npm install xxx -g  把模块安装在全局环境中
$ npm i xxx@1.0.0 安装指定版本号的模块
$ npm view xxx versions > xxx.version.json:查看某个模块的版本信息（输出到指定JSON文件中）
$ npm uninstall xxx 把当前项目中的模块卸载
$ npm uninstall xxx -g 把全局环境中的模块卸载

$ npm root -g 查看模块全局安装路径


安装在本地项目中的模块
->可以在项目中导入进来使用
->但是默认不能基于命令来操作（因为没有.cmd文件）
->但是可以基于package.json中的scripts,配置一些npm可以执行命令，配置后通过$ npm run xxx执行

$ npm init -y初始化当前项目的配置依赖清单（项目文件加的名字中不能出现中文、大写字母和特殊符号)
=>创建成功后在当前项目中生成package.json的清单文件
dependencies:生产依？模块（开发和项目部署的时候都需要）
devDependencies:开发依赖模块（只有开发的时候需要）
scripts:配置本地可执行命令的

$ npm i xxx --save 把模块保存在清单生产依赖中
$ npm i xxx --save-dev 把模块保存在清单开发依懒中
$ npm install 跑环境，按照清单安装所需的模块
```



**npm+git全流程**

```
一个新项目的开始：
1.创建项目文件夹
2.把它作为一个新的仓库进行代码管理(可以基于$ git clone 把远程仓库克隆下来即可)
3.初始化模块配置清单package,json:$ npm init -y
4.安装所需要的模块：$ npm i jquery bootstrap@3 less..
5.正常开发
6.开发中：可能需要在本地配置命令去完成一些功能(例如LEss文件编译，此时需要配置npm可执行的命令)
"scripts":{
'yadang':'lessc css/index.less css/index.min.css -x',
'xxx'webpack
}
7,开发中我们需要基于g1t把文件进行管理：生成对应的历史版本
提交到暂存区、历史区、远程仓库的时候，项目中很多文件是无需处理和提交的,例如:node_modules,.idea...、不需要提交的，我们生成一个.gitignore忽略文件
8.由于每次git提交的时候，我们都不去提交node_modules,所以团队协作开发中，我们每当pull了之后，都需要“跑环境”：执行$ npm install,按照项目中的package.json中的依赖项信息，把缺失的模块都安装一遍

```



**基于yarn 进行第三方模块管理**

$ npm install yarn -g 使用npm安装yarn

$ yarn init/yarn install 初始化package.json文件

$ yarn add xxx@x.xx.Xx -dev 安装需要的包模块

$ yarn remove xxx 移除相应包模块

...

yarn不能安装全局模块



**基于nrm切源提高npm的速度**

$ npm install nrm -g 全局安装nrm

$ nrm ls 查看可用的国内镜像源

$ nrm use xxx 切换到你想用的镜像源

接下来正常使用npm命令即可，它会自动从你选择的镜像源去获取资源







## 变量提升

> 当浏览器开辟出供代码执行的栈内存后，代码并没有自上而下立即执行，而是继续做了一些事情：**把当前作用域中所有带var/function关键字的精选提前的声明和定义=>变量提升机制**

- 带var的知识提前声明(declare) 'var a', 如果知识声明没有赋值,默认值是undefined
- 带function的不仅声明，而且还定义了(defined) 'a=13'定义其实就是赋值，准确来说就是让变量和某个值进行关联



![](C:\Users\Administrator\Downloads\uTools_1648606430935.png)





```javascript
console.log(a); //=>undifined
var a = 12;
var b = a;
b = 13;
console.log(a); //=>12
console.log(sum(10, 20)); //=>30
function sum(m, n) {
    return m + n;
}
console.log(sum(10, 20)); //=>30
```

函数表达式方式，由于使用VAR来创建SUM,变量提升阶段只会声明变量，不会赋值，所以此时函数在前面执行， 函数是没有值的， 不能执行（ 真实项目中这种方式最常用， 因为它操作严谨) 

```javascript
console.log(sum(10, 20)); //=>Uncaught TypeError:sum is not a function
var sum = function(m, n) {
    return m = n;
}
console.log(sum(10, 20));
```



```javascript
console.log(sum(10, 20)); //=>Uncaught TypeError:sum is not a function
var sum = function(m, n) {
    return m = n;
}
console.log(sum(10, 20));
```

不能在声明之前使用（禁止声明提前）
不能重复声明

```javascript
console.log(a); //=>Uncaught ReferenceError:Cannot access 'a'before initialization
let a = 13;
a = 12;
console.log(a);
```

带var和不带var的区别

在全局作用域下的区别

不带var的：相当于给全局对象windowi设置了一个属性a

```javascript
window.a = 13;
a=13;
console.log(window.a);//=>window.a
```

栈内存变量存储空间

b

带var的：是在全局作用域下声明了一个变量b(全局变量)，但是在全局下声明的变量也同样相当于给window.增加了一个对应的属性（只有全局作用域具备这个特点)

```javascript
var b=14;//=>创建变量b & 给window设置了属性b
console.log(b);//=>14
console.log(window.b);//=>14
// let 不会给window添加属性
```



1. let 和const 不存在变量提升机制

创建变量有六种方式中var / function 有变量提升,而且let.const/class/import都不存在这种机制

2. var 允许重复声明,而let是不允许的

在相同的作用域中（或执行上下文中）

- 如果使用var/function关键词声明变量并且重复声明，是不会有影响的（声明第一次之后，之后再遮到就不再重复声明了)
- 但是使用let/consti就不行，浏览器会校验当前作用域中是否已经存在这个变量了，如果已经存在了，则再次基于lt等重新声明就会报错







```
fn()//=>5
function = fn() {console.log(1);}
fn()//=>5
function = fn() {console.log(2);}
fn()//=>5
var fn = function = fn() {console.log(3);}
fn()//=>3
function = fn() {console.log(4);}
fn()//=>3
function = fn() {console.log(5);}
fn()//=>3
```



if分支会对声明提前产生影响吗？
会，但是不会对var产生影响

```javascript
console.log(a);//=>undefined
if(!('a' in window)){
    var a = 13;
}
console.log(a)//=>undefomed
```



全局作用域

1.变量提升

但是如果是函数的话有特殊性：在老版本浏览器中，确实不论条件是否成立，函数也是提前声明或者定义的，但是新版版浏览器中，为了兼容ES6严谨的语法规范，条件中的函数在变量提升阶段贝能提前声明，不能提前定义

```javascript
fn();//=>报错
if ('fn' in window){
    function fn(){
        console.log('哈哈哈')；
    }
}
fn();//=>'哈哈哈
console.log(fn);//=>f
```

in是干什么的

```javascript
var obj = {
    name :"jack"
    age：18
}
console.log('gender' in obj);
//[property] in [object] 验证当前属性是否属于这个对象
```



```javascript
console.log(fn);//=>undefined
if (!('fn'in window)){//=>true
    //进来之后第一件事，给fn赋值
    fn();
    function fn(){
        console.1og('哈哈哈')；
    }
}
fn()
```



//=>自执行函数：前面加的()或者！+-~只有一个目的，让语法符合而已
//=>自执行函数本身不进行变量提升（没名字）

(function (n){})(10);
~function (n){}(10);
+function (n){}(10);
-function (n){}(10);
!function (n){}(10);



```javascript
f = function() { return true };
g = function() { return false };
(function() {
    if (g() && [] == ![]) {
        f = function() { return false; }

        function g() { return true; }
    }
})();
console.log(f());
console.log(g());
```

let能解决typeof检测时出现的暂时性死区问题

```javascript
console.log(a)
//=>Uncaught ReferenceError:a is not k
console.log(typeof a);
//=>"undefined"这是浏览器的BUG,本应该是报错的，因为没有a(暂时性死区)
console.log(typeof a);//=>Uncaught ReferenceError:Cannot access 'a'before initialization
let a;
```



**简单的闭包原理和作用域解释**

闭包：函数执行形成的私有栈内存，会把内存中所有私有变量保护起来，和外边没有任何关系  函数的这种保护机制就是"闭包"

私有栈内存中代码执行的时候，如果遇到一个变量首先看到的是否为自己的，是自己的以后操作都用自己的，不是自己的去上级作用域这家拍卖行查找...一直到全局作用域位置；

**作用域链的解释**

找到就拿来用，找不到可能会报错



```javascript
console.log(a, b, c); //=>undefined undefined undefined
var a = 12,
    b = 13,
    c = 14;

function fn(a) {
    console.log(a, b, c); //=>10,13,14 
    a = 100;
    c = 200;
    console.log(a, b, c); //=>100, 13, 200
}
b = fn(10);
console.log(a, b, c); //=>12, 13, 200
```



```javascript
var ary = [12,23];
function fn(ary){
    console.log	(ary);
    ary[0] = 100;
    ary = [100];
    ary[0] = 0;
    console.log(ary);
}
fn(ary);
console.log(ary);
```





如何查找上级作用域和堆栈内存的释放问题

```javascript
var n =1;
function fn(){
    var n =2;
    function f(){
        n--;
        console.log(n);
    }
    f();
    return f;
}
var x = fn();
×();
console.log(n);
```





## 闭包的作用域

1. 创建函数

- 开辟一个堆内存

- 把函数体中的代码当作字符串储存进去

- 把堆内存的地址赋值给函数名/变量名

- **函数在哪创建，那么它执行的时候所需要查找的上级作用域就是谁**

2. 函数执行

- 形成一个全新的私有作用域，执行上下文，私有栈内存  (执行一次形成一个，多个之间也不会产生影响)
- 形参赋值&变量提升
- 代码执行(把所属堆内存中的代码字符串拿出来一行行执行)
- 遇到一个变量，首先看他是否为私有变量(形参和在私有作用域中声明的变量是私有变量)，是私有的就操作自己的变量即可，不是私有的则向上级作用域中查找，一直找到全局作用域为止=>作用域链查找机制
- 私有变量和外界的变量没有必然关系，可以理解为被私有栈内存保护起来了，这种机制其实就是**闭包的保护机制**







![1648778689455](C:\Users\Administrator\AppData\Local\Temp\1648778689455.png)



**关于堆栈内存释放问题(以谷歌webkit内核为例子)**

函数执行就会形成栈内存（从内存中分配的一块空间），如果内存都不销毁释放，很容易就会导致栈内存溢出（内存爆满，电脑就卡死了)，堆栈内存的释放问题是学习JS的核心知识之一



**堆内存释放问题**

创建一个引用类型值，就会产生一个堆内存

如果当前创建的堆内存不被其它东西所占用了（浏览器会在空闲的时候，查找每一个内存的引用状况，不被占用的都会给回收释放掉)，则会释放

```javascript
let obj  ={
    name = 'zhufeng'
};
let oop = obj;
// 此时obj和oop都占用着对象的堆内存，想要释放堆内存，需要手动解除变量和值的关联(null:空对象指针)
obj = null;
oop = null;
```



栈内存释放

打开浏览器形成的全局作用域是栈内存

手动执行函数形成的私有作用域也是栈内存

基于ES6中的let/const形成的块级作用域意识栈内存

...  



全局栈内存：关掉页面的时候才会销毁

私有栈内存：

- 一般情况下，函数只要执行完成，形成的私有栈内存就会被销毁释放掉(排除无限极递归，出现死循环的模式)
- 但是一旦栈内存中的某个东西(一般都是堆地址)被私有作用域以外的事务给占用了，则当前私有栈内存不能立即被释放销毁(特点：私有作用域中的私有变量等信息也被保留下来了)=>市面上认为的闭包：函数执行形成不能被释放的私有栈内存，这样的才是闭包



![uTools_1648780163441](C:\Users\Administrator\Downloads\uTools_1648780163441.png)





**闭包的两大作用**

1. 保护（私有变量和外界没有必然联系）
2. 保存（形成不销毁的栈内存，里面的私有变量等信息保存下来了