# Js基础

​	Js基本介绍
​		JavaScript是一门Web开发语言现代的所有的浏览器都内嵌了JavaScript引擎,因此Js源码可以直接在浏览器解释执行
​		编程范式
​			面向对象
​				有类class
​			面向函数
​				有lambda表达式
​		语言范畴
​			Js属于C语系范畴,类似语言有C,C++,C#,Java,Python等,这些语言具有相近的语法特征,学习时应当相互借鉴,触类旁通
​			弱语言类型,用var关键字声明变量
​			java是强语言类型
​	引入js的两种方式
​		用<script></script>标签包括js代码块,一般放在html的head或body里面(实际可以放任意位置)
​			缺点,无法代码复用
​		编写单独的以.js结尾的文件,然后用<script src="" ></script>引入
​	语法规范
​		编码:unicode
​		大小写敏感
​		代码格式化
​			会忽略分隔符
​				可充分利用这些符号对js代码排版
​				制表符\t,
​				换行符\n
​				空白符\s
​				...
​		驼峰命名
​		代码注释
​			单行注释//
​			多行注释/* */
​		关键字
​			

分号作为结束符;
	与java不同的是;可加可不加
变量遵循先声明后使用的原则

基本语法
	输出与输入
		输出
			document.write()
				向浏览器html输出
			console.log()
				向浏览器控制台输出
			window.alert();
				窗体弹出
		输入
			prompt("输入提示",输入值1,输入值2....)
	变量
		var
			声明全局变量
		let
			声明局部变量(函数内的变量)
		const
			声明常量
	数据类型
		数字
			除了正常数字外还有一个Nan
		字符串
			单双引号都行,一般使用单引号较多
			如果使用``  反引号,则可定义模板字符串,字符串中直接使用${变量名}来读取变量值,不需要使用+号拼接
		布尔
			布尔表示
				布尔类型:false 假  true 真
				字符串类型: 空为假
				数值类型: 0是假
				对象类型: null和undefined是假 
		undefined
			变量声明后的默认值
		null
			没有引用对象
		数组
			var heros = ["大乔,小乔,鲁班"];
			索引也是从0开始
		对象
			如何定义对象?
				对象包含属性和行为
					属性用变量表示
					行为用函数表示
				完整对象表示
					对象都用{}包裹
					用名/值对表示属性以及行为,名和值之间用:隔开,多个名值对之间用,隔开
					如果名对应的值为函数则使用匿名函数,此时名则为匿名函数的名
					例子:
						 var student = {
    name:"hah",
    age: 18,
    playgame:function(name){
      document.write("<div>"+this.name+"喜欢玩"+name+"</div>")
    }
};
student.playgame("英雄联盟");
	运算符
		算数运算符
			+号两边一旦有一边是字符串类型的时候,表示的是字符串拼接
			字符串字面值参与运算的时候会自动转为数字
			/法运算会按照人类运算执行
		比较运算符
			== 会进行类型转换然后再比较内容
			=== 恒等 先比较类型后比较内容
	流程控制语句
		分支
			条件语句
				自行练习
					 var age = prompt("请输入您的年龄");
switch(age){
  case "1":
    alert("您上初一");
    break;
  case "2":
    alert("您上初二");
    break;
  case "3":
    alert("您上初三");
    break;
  default:
    alert("您已步入社会");
}
				if...else if...else
				switch...case..default
		循环
			也有break,continue,return
			while
			for...i
				for(var i =0 ;i<10;i++){}
			增强for
				for( 变量 in 对象或数组){}
					将遍历对象或数组里的所有值
			练习:定义一个数组,并把数组中的内容使用循环写入到页面当中
	异常捕获
		try{

}catch(ex){

}finally{

}
			throw 异常信息
			自行练习案例
				try{
      alert("执行程序");
      var err = new Error("发生错误了哟");
      throw err;
    }catch(e){
      alert("错误信息"+e.message);
    }finally{
      alert("程序结束.....");
    }

# Js进阶

​	函数
​		概念
​			执行任务的代码块,调用之后执行,方便复用重复逻辑
​		使用function关键字
​			无参
​				function 函数名(){}
​			有参(一个函数最多有255个参数)
​				function 函数名(没有类型的参数){}
​			有返回值
​				function 函数名(有参或无参){return ......}
​			匿名函数function(参数){};
​		函数调用
​			函数名(实参或无实参)
​		匿名函数
​			没有名字的函数
​				因为没有名字,因此调用时要把匿名函数先赋值给一个变量
​				直接使用function
​				使用箭头语法()=>{}
​		特点

			1. 形式参数和返回值不需要定义类型
			2. js中如果出现同名的方法，后面的会覆盖前面的(尽量不要同名)
			3.js没有规定形参和实参数量一定对等
				形参大于实参则多出的形参为undefined
				实参大于形参,多出的实参被自动忽略
	自定义对象数据类型
		如何定义对象?
			对象包含属性和行为
				属性用变量表示(let)
				行为用函数表示(function)
			完整对象表示
				对象都用{}包裹
				用名/值对表示属性以及行为,名和值之间用:隔开,多个名值对之间用,隔开
				如果名对应的值为函数则使用匿名函数,此时名则为匿名函数的名
				例子:
					 var student = {
        name:"hah",
        age: 18,
        playgame:function(name){
            document.write("<div>"+this.name+"喜欢玩"+name+"</div>")
        }
            };
            student.playgame("英雄联盟");
	js中的内置对象
		Array
		String
		Json
			使用大括号来包裹,其内的值全是名值对,名值对用:隔开,多个名值对用,隔开
			Json.parse
				json字符串转json对象
			Json.stringify
				json对象转json字符串
	BOM对象
		浏览器对象模型Browser Object Model
		目的
			把浏览器各个部分封装为对象,使Js能够直接和浏览器对话
		组成
			Window
				浏览器窗口对象
					属性
						history
							获取历史记录对象
						location
							获取地址栏对象
					方法
						弹窗
							confirm()
							alert()
						定时器
							setTimeout(函数,毫秒)
								延迟执行
							setInterval(函数,毫秒)
								周期性执行
			Navigator
				浏览器对象
			Screen
				屏幕对象
			History
				历史记录对象
			Location
				地址栏对象
					属性
						href
							设置或者获取地址栏url
	DOM对象
		概念
			文档对象模型Document Object Model
		目的
			将html的各个组成部分封装为对象,方便直接操作html
		组成
			Document
				文档对象
					整个html页面当成对象
			Element
				元素对象
					将html中的所有标签当成对象
			Attribute
				属性对象
					将html中所有标签中定义的属性当成对象
			Text
				文本对象
					html中的文字
			Comment
				注释对象
					html中的注释
		获取元素
			document.querySelector('选择器')
			document.querySelectorAll('选择器')
		操作内容
			js对象.innerHTML='xxx'
		操作属性
			js对象.属性名
		练习
			实现倒计时页面跳转
	函数监听事件
		作用
			JS可以监听用户的行为,并调用函数来完成用户交互功能
		常用事件
			页面加载完毕事件
				window.onload
			值改变时
				onchange
			下拉框改变
				onchange
			表单事件
				submit
				input
			鼠标事件
				单击时
					onclick
				鼠标移入
					mouseenter
				鼠标移出
					mouseleave
			键盘事件
				键盘按下
					keydown
				键盘抬起
					keyup
			焦点事件
				获取焦点
					onfocus
				失去焦点
					onblur
			添加多个事件
				addEventListener('上面列举的时间类型',触发函数)
		事件练习
			事件绑定练习1
				<input type="button" onclick="on()" value="按钮1">
				 document.getElementById('btn').onclick=function(){
        alert('我被点击了!');
}
			事件绑定练习2
				<input type="text" name="" id="文本1">
				var b = document.getElementById("文本1");
        b.onfocus = function(){
                b.value = "你是不是点我了?"
        }
			事件绑定练习3
				随机点餐
					1.定义一个数组用于存放菜品
					2.定义两个按钮一个启动,一个停止
					3.定义一个文本框用于展示最终选择的菜品
					4.点击启动触发随机选餐但是不能停止
						随机数可以考虑使用Math.random()
					5.点击停止最终展示菜品
						setInternal
						clearInternal
			自行练习课件中的隔行换色
	Js模块化
		即js文件中函数的导出与导入
		export
			在js文件中的函数前加export关键字
				export function add(a,b){return a + b}
		import
			在js文件中最上方使用import导入某个js文件中导出的函数
				import { add} form .....
		实现按需导入,不必把一个js中不用的函数全部导入进来

# Js常用Api

​	Math
​		Math.PI
​			获取圆周率
​		Math.ceil()
​		Math.floor
​		Math.max(值1,值2,值3....)
​		Math.min(值1,值2,值3....)
​		Math.random()
​		Math.pow()
​		Math.abs()
​		.....
​	Array数组
​		数组函数式方法,传递lamda表达式
​		数组变量.toString
​		数组变量.join()
​			指定连接数组格式
​		数组变量.concat(arr1,arr2)
​			拼接多个数组
​		数组变量.slice(开始索引,结束索引)
​		数组变量.reverse
​			数组反转
​		数组变量.splice(删除位置索引,删除数量,要补充的值....)
​		数组变量.sort(lamda表达式)
​			数组排序
​		数组变量.push()
​			末尾添加
​		数组变量.pop()
​			末尾删除
​		数组变量.shift()
​			头部添加
​		数组变量.unshift()
​			头部删除
​		数组变量.indexOf()
​			检测元素存在,存在返回索引,不存在返回-1
​		foreach()
​			遍历
​		map()
​			映射
​		filter()
​			过滤
​		reduce()
​			归约/折叠
​		some()
​			数组中只要有一个符合条件即返回true
​		every()
​			数组中全部元素符合条件才返回true
​	String
​		length
​		trim
​			去除首位空格
​		charAt
​		split
​		toUpperCase/toLowerCase
​		slice
​	Json
​		JSON.parse
​		JSON.stringify