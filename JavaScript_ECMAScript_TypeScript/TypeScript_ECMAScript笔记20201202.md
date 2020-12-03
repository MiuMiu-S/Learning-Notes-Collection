2020-12-02

一个视频[笔记](https://www.imooc.com/coursescore/763)，视频很短，简单流畅。


[TypeScript官网](https://www.typescriptlang.org/)

##### 编译
```
tsc hello.ts
```


##### 自动拆分字符串
```
function test(template: any, name: string, age: number) {
    console.log(3, template);
    console.log(4, name);
    console.log(5, age);
}

var myname = 'shf'
var myage = (()=>{
  return 18;
})

// 调用
test`hello, my name is ${myname},i am ${myage()}.`

// [LOG]: 3,  ["hello, my name is ", ",i am ", "."] 
// [LOG]: 4,  "shf" 
// [LOG]: 5,  18
```

##### 其他1
```
function func(...args) {
    args.forEach(item => {
        console.log(item);
    })
    
}
func(1,2,3,4)
```
```
function func(a, b, c) {
    console.log(a);
    console.log(b);
    console.log(c);
    
}
const arg = [1,2,3]
func(...arg);
```

##### 其他2
```
function* doSomething() {
    console.log(1);
    
     yield;
     
     console.log(2);
}

var func1 = doSomething();
func1.next();
func1.next();
```

```
function* getStockPrice(stock) {
    while(true) {
        yield Math.random()*100;
    }
}
var priceGenerator = getStockPrice("IBM");
var linmitPrice = 100;

while(price > linmitPrice) {
    price = priceGenerator.next().value;
    console.log(`获得的价格是${price}`);
}
```



#### 类的构造函数
```
class Person {
    constructor(name: string) {
        this.name = name;
    }
    name;
    eat() {
        console.log(this.name);
    }
}
var p1 = new Person('sss');
p1.name = 'aaa';
p1.eat();
// 等价于
class Person {
    constructor(public name: string) { // 通过构造函数的时候建立了一个约定，实例化的时候必须指定name
        console.log('haaa');
    }
    eat() {
        console.log(this.name);
    }
}
var p1 = new Person('bbb');
p1.eat();

// constructor(name: string)，constructor( public name: string)不一样 ，后者这个声明了name

```





#### 继承、泛型
```
class Person {
    constructor(public name: string) {
            console.log('haaa');
    }
    eat() {
        console.log('eating');
    }
}
class Employee extends Person {
    constructor(name: string, code: string) {
        super(name); // 继承：super用法1，调父类的构造函数
        console.log('xiiii');
        this.code = code;
    }
    
    code: string;

    work() {
        super.eat(); // 继承：super用法2，调父类的其他方法
        this.doWork();
    }
    
    private doWork() {
        console.log('working');
    }
}

// 泛型
var worker: Array<Person> = [];
worker[0] = new Person('zhangsan');
worker[1] = new Employee('lisi', '2');
// worker[2] = 2; 这样是不符合Person的要求会报错

var e1 = new Employee('name', '1');
e1.work();

```




### 接口 Interface
######  interface用法1
```
interface IPerson {
    name: string;
    age: number;
}

class Person {
    constructor(public config: IPerson) {
        console.log(config);
    }
}

var p1 = new Person({
    name: 'aaa',
    age: 18
});
```
###### interface用法2
```
interface Animal {
    eat();
}

class Sheep implements Animal {
    eat() {
        console.log(11111);
    }
}

```
 