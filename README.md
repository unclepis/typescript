# typescript
personal tutorial  to learn typescript


# TypeScript
## Ts
简单的理解，ts中的type就是指在js语法的基础上，增加了静态类型检查，并且这个是发生在ts编译期进行的，并不会在ts编译成js之后增加任何类型检查的相关代码。
	
	js:
	function test(msg){
		console.log('This is a test'+ msg);
	}
	ts:
	function test(msg:string):void{
		console.log('This is a test ${msg}');
	}
- 对函数类型增加了类型void，即没有返回值;
- 对变量类型增加了类型备注，msg为string类型，如果传入的参数不是string在ts编译成js的时候就会报错
- 另外ts允许使用模板字符串，不需要使用字符串拼接的方式在字符串中加入变量。
	
## 语言特性：

- 静态类型语言，需要编译，拥有编译时类型检查的特性；

- 扩展名为.ts,一个ts应用应该包含对个ts代码文件，一个代码文件可以包含多个class，class也可以组成模块。ts的模块和c#的名称空间namespace比较接近。

## 数据类型：
### TS的基本类型有
	
	string -  let color:string = 'red';
	number -  var age:number = 18;
	boolean - let gender:boolean = true;
	any - var info :any = 4; info = 'personal information';
	array -  var Array[string] = ['pis','cindy']; 或者 var list:number[]= [1,2,3];
	tuple - var test:[string,number] = ['pis',18];
	enum - enum test{0,1,2}; var result :test = test[0];
	null和undefined
#### numbers
	TS中所有的数字类型都是numebers，不分int和double，number都是浮点数
	var a:number 6; 
#### strings
		- 使用双引号或者单引号来围绕字符串数据
		- 可以使用模板字符串：
			- 字符串使用单引号包围
			- 嵌入的表达式使用${}形式表示
			- 可以替换es5中字符串和变量使用加号进行拼接的写法：
				var a = 'my name is '+ name;
				var name:string = "pis";
				var a :string = 'my name is ${name}';

#### structures
		- array:在数组元素类型后面添加[]/Array[数组元素类型]
			- var a:number[] = [1,2,3,4];
			- var Array[number] = [1,2,3]
		
#### boolean
		- var a :boolean = true;
		
#### enum
		- enum name {pis,eric,cindy}
		- var a :name = name.pis;
			- 可以指定枚举类型的index，当然默认是从0开始的
				- enum name {pis = 1,eric =4, cindy= 6}
			- 枚举类型有一个便捷特性，类似数组一样，可以使用index的值来查询对应的枚举元素
				- enum name {pis =1, cindy, eric}
				- var a :string = name[2];// cindy
				
#### 其他类型：
- any：动态类型
	-当我们不确定数据类型的时候就可以使用any，类似于es5的var

		var a:any =1;// number
		a = 'hello'; // string

	- 在种种情况下，将会略过对这些变量的类型检查
- tuple: 组合类型
	
		var a :[string,number] = ['pis',18];
		可以使用数组检索index获取元素，a[0].substr(1); //is
		当index超过边界，将会使用联合类型处理，也就是说这几种类型都有这个操作才行；
		a[6].toString()// string和number都有toString方法

#### 函数类型限定：
当一个函数没有返回值的时候，使用void类型，这个c#的pulic void 
main声明主函数类似
	
	function test():void{
	console.log('This function do not have return value');
		}	

## 类型推断和类型标注
- 当右侧表达式足以确定变量的类型时，ts可以自动确定变量的类型，这就是类型推断
- 类型标注就是讲变量的类型以可选的方式写在后面，这就是类型标注。

## 模块/类型/接口
- 模块：用于代码组织，类似c#的namespace，一个模块可以包含多个类和接口，可以将类和接口私有化或者导出，导出就是公开，让其他模块可以访问。
	- ts实际上就是隐藏了js的原型设计，采用基于类型的面向对象的方式，扩展class，实现多个接口，添加构造函数，公开属性和方法。
- interface接口

		interface config {
			color:string;
			width:number;
		}
			
		interface config{
			readonly x:number;
			readonly y:number; // 只读属性不能对它进行重新赋值
		}
		
		interface config{
			color?:string; // 可选属性？
			[propName:string]:any; // 动态属性any
		}

	
