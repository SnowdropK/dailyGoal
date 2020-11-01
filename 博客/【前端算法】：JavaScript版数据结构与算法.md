#### 1、时间复杂度
>算法的时间复杂度是一个函数，它定性描述该算法的运行时间。
```
O（1）：
let i = 0;
i += 1
只执行一次，所以O(1)
```

```
O(n)
for(let i = 0; i < n; i +=1 ){}

上面两个加在一起：O（1）+ O(n) = O(n)
n足够大，则可以忽略1
```
```
O(n2)
for(let i = 0; i < n; i +=1 ){
  for(let j = 0; j < n; j +=1 ){
    console.log()
  }
}

O(n) x O(n) = O(n2)
相乘和相加不一样
```

```
O(logN)
let i = 1;
whie(i < n) {
 i *= 2; 
}
```

#### 2、空间复杂度
>算法在运行过程中临时占用存储空间大小的量度

```
O（1）：
只声明单个变量
let i = 0;
i += 1
```

```
O(n)：
数组加了n个值，相当于添加n个内存单元
const list = [];
for(let i = 0;i < n; i+= 1){
  list.push(i)
}

O(n2)：
const matrix = [];
for(let i = 0; i < n; i +=1){
  matrix.push([])
  for(let j = 0; j < n; j +=1){
    matrix[i].push(j)
  }
}
```

#### 3、数据结构：栈
>一个后进先出的数据结构

push：入栈
pop：出栈

应用场景：十进制转二进制、判断字符串的括号是否有效、函数调用堆栈

leetcode原题：20
判断字符串的括号是否有效

js中的函数调用堆栈

#### 4、数据结构：队列
1、定义
>一个先进先出的数据结构

2、应用场景：食堂排队打饭、JS异步中的任务队列、计算最近请求次数

3、JS异步中的任务队列：JS是单线程，无法同时处理异步中的并发任务

>输入：inputs = [[],[1],[100],[3001],[3002]]
输出：[null,1,2,3,3]

4、leetcode题号933：最近请求的次数


#### 5、数据结构：链表
1、定义
>多个元素组成的列表；元素存储不连续，用next指针连在一起

2、优点：增删非首尾元素，不需要移动元素，只需要更改next的指向即可

3、代码

4、leetcode：237、206、2、83、141、

5、原型链知识点：
如果A沿着原型链能找到B.prototype，那么A instanceof B为true
```
let a = () => {}
typeof a === 'function' true
a instanceof Function true
a instanceof Object true
```
如果在A对象上没有找到x属性，那么会沿着原型链找x属性
```
const obj = {}
Object.prototype.x = 'x'
const func = () => {}
Function.prototype.y = 'y'
```

6、使用链表指针获取JSON的节点值
```
const json = {
  a: {b: {c: 1}},
  d: {e: 2}
};

const path = ['a', 'b', 'c'];

let p = json
path.foreach(key => {
  p = p[key]
})
```


##### 面试题
1、instanceof的原理，并用代码实现
知识点：如果A沿着原型链能找到B.prototype，那么A instanceof B为true

解法：遍历A的原型链，如果找到B.proptype，返回true，否则false

```
const instanceof = (A,B) => {
  let p = A;
  while(p){
    if(p._proto_ === B.prototype){
      return true;
    }
    p = p._proto_;
  }
  return false;
};
```
2、
知识点：如果在A对象上没有找到x属性，那么会沿着原型链找x属性

解法：明确foo和F变量的原型链，沿着原型链找a属性和b属性
```
let foo = {}
let F = function() {};
Object.prototype.a = 'value a'
Function.prototype.b = 'value b'

console.log(foo.a)
console.log(foo.b)

console.log(F.a)
console.log(F.b)
```

##### 总结
1、链表里的元素存储是不连续的，通过next()连接
2、Javascript中没有链表，但可以用Object模拟链表
3、链表常用操作：修改next()、遍历链表
4、js中的原型链也是一个链表，
5、使用链表指针可以获取JSON的节点值

#### 6、数据结构：集合
1、定义
>一种无序且唯一的数据结构

>Es6中有集合，名为Set；集合的常用操作：去重、判断某元素是否在集合中、求交集

2、代码
```
// 去重
const arr = [1, 1, 2, 2];
const arr2 = [...new Set(arr)];

// 判断元素是否在集合中
const set = new Set(arr);
const has = set.has(3);

// 求交集
const set2 = new Set([2, 3]);
const set3 = new Set([...set].filter(item => set2.has(item)));
```

3、leetcode：349

4、set操作
使用Set对象：new、add、delete、has、size
迭代Set：多种迭代方法、Set与Array互传、求交集/差集

```
let mySet = new Set();

mySet.add(1);
mySet.add(5);
mySet.add(5);
mySet.add('some text');
let o = { a: 1, b: 2 };
mySet.add(o);
mySet.add({ a: 1, b: 2 });

const has = mySet.has(o);

mySet.delete(5);

for(let [key, value] of mySet.entries()) console.log(key, value);

const myArr = Array.from(mySet);

const mySet2 = new Set([1,2,3,4]);

const intersection = new Set([...mySet].filter(x => mySet2.has(x)));
const difference = new Set([...mySet].filter(x => !mySet2.has(x)));
```

#### 7、数据结构：字典
1、定义
>与集合类似，字典也是一种存储唯一值的数据结构，但它是以<b>键值对</b>的形式存储

>Es6中有字典，名为Map

```
const m = new Map();

// 增
m.set('a', 'aa');
m.set('b', 'bb');

// 删
m.delete('b');
// m.clear();

// 改
m.set('a', 'aaa');
```

2、leetcode：349、20、1、3、76

#### 8、数据结构：算法
1、定义
>一种分层数据的抽象模型。（前端工作中常见的树：Dom树、级联选择、树形控件……）

>JS中没有树，但是可以用Object和Array构建树。

>树的常用操作：深度/广度优先遍历、先中后序遍历