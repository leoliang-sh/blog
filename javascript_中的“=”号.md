##JavaScript 中的“=”号
作者：梁志艳  
email：liangzhiyan@kyee.com.cn
###前言
js中我们最常使用到的操作符就应该是“=”号了，学过编程的孩子都知道“=”代表赋值的意思。但是在js中有时候“=”的行为往往出乎我们的意料。
###例子
运行下面代码

	console.log("#primitive value");
	console.log("##int");
	var a=1;
	b=a;
	a=2;
	console.log("a="+a);
	console.log("b="+b);
	
	console.log("##string");
	var a='foo';
	b=a;
	a='bar';
	console.log("a="+a);
	console.log("b="+b);
	
	console.log("#reference value");
	var a={};
	b=a;
	a.foo="foo";
	console.log("a="+JSON.stringify(a));
	console.log("b="+JSON.stringify(b));

输出：

	#primitive value
	##int
	a=2
	b=1
	##string
	a=bar
	b=foo
	#reference value
	a={"foo":"foo"}
	b={"foo":"foo"}
	
###原理
js类型共有两种：  
1. 基本类型 (primitive values) - 包括Undefined, Null, Boolean, Number和String五种基本数据类型  
2. 引用类型 (reference values) - 保存在内存中的对象们，不能直接操作，只能通过保存在变量中的地址引用对其进行操作  

事实上js中的变量不是存放基本类型就是存放引用类型的指针。赋值就是把变量在内存上面的表示更换，对于基本类型就是更换值，对于引用类型就是更改地址。
###传参
js中的传参也可以用这个来解析。  
执行下面代码：

	console.log("#primitive value");
	function A(val){
	    val=1;
	}
	var a=2;
	console.log("before a="+a);
	A(a);
	console.log("after a="+a);
	
	console.log("#reference value");
	function B(val){
	    val.foo=1;
	}
	var b={foo:0};
	console.log("before b="+JSON.stringify(b));
	B(b);
	console.log("after b="+JSON.stringify(b));
	
输出

	#primitive value
	before a=2
	after a=2
	#reference value
	before b={"foo":0}
	after b={"foo":1}

可见，函数把参数压栈的时候也进行了赋值操作。

##相等
同样js中的等于判断也可以用这个来解析。事实上我们比较的是基本类型或者引用。  

	var a=1;
	var b=1;
	console.log(a===b);
	
	var a={};
	var b={};
	console.log(a===b);
	
运行结果

	true
	false



