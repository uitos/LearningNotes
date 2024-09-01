# HTML5

# 常见html5标签

+ 结构标签
+ 内容标签
+ 修饰标签
+ 媒体标签
+ 表单标签

# 结构标签

这些标签全部是独占一行的，根源码顺序无关，是浏览器解析的结果

标题h1~h6

```html
<h1></h1>
<!-- ...  -->
<h6></h6>
```

> <h1>h1标题</h1>
> <h3>h3标题</h6>
> <h6>h6标题</h6>

水平线

```html
<!-- 水平分隔线 horizontal rule  -->
<hr>
```

> <hr>

段落

```html
<!-- p 段落标签 paragraph -->
<p></p>
```

> <p>段落标签</p>

列表

+ 有序列表

  ```HTML
  <!-- 有序列表 ol order list-->
  <ol></ol>
  ```

  > <ol>
  >     <li>孙悟空</li>
  >     <li>沙僧</li>
  >     <li>八戒</li>
  > </ol>

+ 无序列表

  ```html
  <!-- 无序列表 ul under list -->
  <ul></ul>
  ```

+ 每个列表项

  ```html
  <!-- 列表项 li list item -->
  <li><li>
  ```

  > <ul>
  >  <li>李白</li>
  >  <li>韩信</li>
  >  <li>镜</li>
  > </ul>

表格

+ 表格

  ```html
  <!-- 表格标签 -->
  <table></table>		
  ```

+ 表行

  ```html
  <!-- th表头 table head -->
  <tr></tr>
  ```

+ 表头

  ```html
  <!-- tr table row 行 -->
  <th></th>
  ```

+ 表单元格

  ```html
  <!-- td table data 单元格 -->
  <td></td>
  ```

  ```html
  <table>
   <tr>
     <th>姓名</th>
     <th>年龄</th>
   </tr>
   <tr>
     <td>张三</td>
     <td>18</td>
   </tr>
   <tr>
     <td>李四</td>
     <td>22</td>
   </tr>
  </table>
  ```

  > <table>
  >  <tr>
  >    <th>姓名</th>
  >    <th>年龄</th>
  >  </tr>
  >  <tr>
  >    <td>张三</td>
  >    <td>18</td>
  >  </tr>
  >  <tr>
  >    <td>李四</td>
  >    <td>22</td>
  >  </tr>
  > </table>




# 内容标签

无语义布局标签

> 没有任何含义,通常就是用来实现布局

`<div></div>`

> div 用于布局页面 可以设置宽高

<div style="border: 1px solid #000;" >
    <div style="height: 60px;">你好</div>
	<div>不好</div>
</div>


> 独占一行
>
> 宽跟随父标签,高跟随内容
>
> 可以指定宽高(width,height)

`<span></span>`

> 一行可以有多个
>
> 宽高跟随内容,不能设置宽高

`<br/>`

> 换行

<p style="border: 1px solid #000;">
	123<br>
    4&nbsp;&nbsp;5677
</p>


`&nbsp;`

> 文字间空格

`<a></a>`

> 超链接
>
> `href:` hyper reference
>
> 指定跳转的url网址
> `target`
> 指定跳转方式
> `_self`
>
> 本页面打开
> `_blank`
>
> 新的页面标签打开

`<section></section>`

<section>页眉或者页脚</section>

定义页眉或者页脚

# 修饰标签

​		<big></big>
​			定义较大文本
​		<small></small>
​			表示细则一类的旁注,文本缩小显示
​		已废除的修饰元素
​			center
​				文本居中
​			font
​				定义文本样式,颜色,大小
​			strike
​				定义删除线
​		文本格式化标签
​			<strong></strong>
​				加粗
​			<em></em>
​				加斜
​			<ins></ins>
​				显示下划线
​			<del></del>
​				删除线

# 媒体标签

​		controls  loop  autoplay ...
​		<img src ="" alt = "">
​			定义图片
​		video
​			定义视频
​		audio
​			定义音频
​		都可以添加height和width来控制大小

# 表单标签

form表单
			action
				表示要跳转到哪个url地址
			method
				表示提交表单的方式
					get
					post
			enctype
				enctype = "multipart/form-data" 
					只有在使用表单上传文件时才使用
文本框
			input type ="" name = "" placeholder ==""

​				type指定文本框类型

​					1）text：普通文本框

​					2）password：密码框

​					3）date：日期选择框

​					4）radio：单选框

​					5）checkbox：复选框

​					6）file：文件上传

​					7）submit：提交按钮

​					8）reset：重置按钮

​					9）button：普通按钮，通常与js结合使用

​					10) hidden: 隐藏

​					11)tel :必须输入电话号码

​					12)email :必须输入电子邮箱

​					13)number:必须输入数字

​					14)search :搜索文本框

​				name
​					指定文本框提交内容对应的属性名
​				placeholder
​					文本框输入提示
下拉框
​			select
​				option
文本域
​			textarea

```html
<form action="" method="post">
    <p>姓名：<input type="text"></p>
    <p>手机：<input type="tel"></p>
    <p>性别：
    <p>
        <input type="radio" name="sex" id="" value="1">男
        <input type="radio" name="sex" id="" value="2">女
        <input type="radio" name="sex" id="" value="0">未知
    </p>
    <p>年龄：<input type="number"></p>
    <p>QQ：<input type="text"></p>
    <p>学科：
        <select name="" id="">
            <option value="">-请选择学科-</option>
            <option value="java">java</option>
            <option value="前端">前端</option>
            <option value="大数据">大数据</option>
            <option value="测试">测试</option>
            <option value="python">python</option>
            <option value="go">go</option>
        </select>
    </p>
    <p>渠道：
        <select name="" id="">
            <option value="">-请选择学科-</option>
            <option value="线上活动">线上活动</option>
            <option value="推广介绍">推广介绍</option>
        </select>
    </p>
    <p>备注：
        <textarea name="" id=""></textarea>
    </p>
    <p><input type="reset" value="重置">
        <input type="submit" value="提交">
    </p>
</form>
```



<form action="" method="post">
    <p>姓名：<input type="text"></p>
    <p>手机：<input type="tel"></p>
    <p>性别：
    <p>
        <input type="radio" name="sex" id="" value="1">男
        <input type="radio" name="sex" id="" value="2">女
        <input type="radio" name="sex" id="" value="0">未知
    </p>
    <p>年龄：<input type="number"></p>
    <p>QQ：<input type="text"></p>
    <p>学科：
        <select name="" id="">
            <option value="">-请选择学科-</option>
            <option value="java">java</option>
            <option value="前端">前端</option>
            <option value="大数据">大数据</option>
            <option value="测试">测试</option>
            <option value="python">python</option>
            <option value="go">go</option>
        </select>
    </p>
    <p>渠道：
        <select name="" id="">
            <option value="">-请选择学科-</option>
            <option value="线上活动">线上活动</option>
            <option value="推广介绍">推广介绍</option>
        </select>
    </p>
    <p>备注：
        <textarea name="" id=""></textarea>
    </p>
    <p><input type="reset" value="重置">
        <input type="submit" value="提交">
    </p>
</form>

# 所有标签共有属性

class——定义元素标签类名
id——定义元素的唯一标识
style——定义元素样式

```html
<div class="" id="" style=""></div>
```

# CSS3

常见CSS3
	字体样式
		 font-family	设置字体类型	font-family:"隶书";
		 font-size	设置字体大小	font-size:12px;
		 font-style	设置字体风格	font-style:italic;
		 font-weight	设置字体的粗细	font-weight:bold;
		 font	在一个声明中设置所有字体属性	font:italic bold 36px "宋体";
	文本样式
		 color	设置文本颜色	color:#00C;
		 text-indent	设置首行文本的缩进
			按照像素px设置 text-indent:20px;
			按照字符设置 text-indent:2em;
		 text-align	设置元素水平对齐方式	
			text-align:right;
			text-align:left;
			text-align:center;
		 line-height	设置文本的行高	
			line-height:25px;
		 text-decoration	设置文本的装饰	
			text-decoration:underline;添加下划线
			text-decoration:none;去除下划线
	列表样式
		 list-style
		 list-style-type
		 list-style-image
	背景样式
		 background-color
		 background-image:"url"
		 background-position
		 background-size
		background-repeat
			设置图片重复显示
				 no-repeat只显示一次
				repeat
					x,y方向都重复显示
				repeat-x
					x轴方向平铺
				repeat-y
					y轴方向平铺
		 background简写
			  background:#C00 url(../image/arrow-down.gif) 205px 10px no-repeat;
	盒子模型样式
		以想设置边距的标签为中心,以border为边界
			想在border外添加空白则使用margin
				标签有父子关系
			想在border内添加空白则使用padding
				同级标签的留白的使用
		边框(表格)样式
			border-collapse
				单元格合并
			 border-color
			 border-width
			 border-style
			 border简写
				   border:1px solid #3a6587;
		外边距margin
			 margin-top   上边距
			 margin-bottom  下边距
			 margin-left  左边距
			 margin-right  右边距
			 水平居中 margin: 0px auto;
		内边距padding
			 padding-top
			 padding-bottom
			 padding-left
			 padding-right
		圆角边框border-radius
			 border-top-left-radius
			 border-top-right-radius
			 border-bottom-right-radius
			 border-bottom-left-radius
			 border-radius: 20px  10px  50px  30px; 四个属性值按顺时针排列 
		盒子阴影box-shadow
			 它的值包括 6 个参数：阴影类型，X轴位移，Y轴位移，阴影大小，阴影扩展和阴影颜色。此 6 个参数可以有选择地省略。
			  box-shadow:5px 5px;
	浮动float
		 float: right;
		 父级边框塌陷
	定位position 
	透明度
	CSS3变形
	CSS3过渡
	CSS3动画

