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
  >        <li>孙悟空</li>
  >        <li>沙僧</li>
  >        <li>八戒</li>
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
  >     <li>李白</li>
  >     <li>韩信</li>
  >     <li>镜</li>
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
> 

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









# NVM

nvm（[Node](https://so.csdn.net/so/search?q=Node&spm=1001.2101.3001.7020) Version Manager）是一款用于管理 Node.js 版本的工具，可以轻松地在一个系统中切换和安装多个 Node.js 版本。使用 nvm 可以让你轻松地升级或降级 Node.js 版本，也可以在同一台机器上同时使用多个版本的 Node.js。



**如果你的电脑已经安装了 node，那么在安装 nvm 之前要先卸载掉，避免后面产生不必要的冲突**



## Window 安装 nvm

1. **下载nvm**

[nvm GitHub下载地址](https://github.com/coreybutler/nvm-windows/releases)

在下载页面找到如图所示下载即可：

![image-20240810144152467](images/image-20240810144152467.png)

[nvm 官网下载地址](https://nvm.uihtm.com/)

![image-20240810144733805](images/image-20240810144733805.png)

2. **安装**

   路径不要有中文

3. **配置**

打开 nvm 安装目录下的 `settings.text` 如图：

![image-20240810144911269](images/image-20240810144911269.png)

在该文件里添加下面两行代码，然后保存。

使用淘宝境像安装 node 和 npm

```bash
node_mirror:npmmirror.com/mirrors/node/
npm_mirror:npmmirror.com/mirrors/npm/
```

或者

```bash
node_mirror: https://npm.taobao.org/mirrors/node/
npm_mirror: https://npm.taobao.org/mirrors/npm/
```

4. **检验**

```shell
nvm -v
```

显示`1.1.12`,表示安装成功

![image-20240810153105292](images/image-20240810153105292.png)

## 安装Node.js版本

显示可下载版本的部分列表

```shell
nvm list available
```

![image-20240810152256684](images/image-20240810152256684.png)

- **Current 版本**：Current 版本是 Node.js 的最新开发版本，通常每隔几个月发布一次。它包含最新的功能、改进和实验性特性，但不太稳定。Current 版本的目标是提供给开发人员一个平台来尝试新的功能和实验性特性，以便反馈和测试。
- **LTS 版本**：LTS（Long-Term Support）版本是 Node.js 的长期支持版本，通常每隔两年发布一次。LTS 版本的主要特点是稳定性和可靠性。它们接受持续的维护和安全更新，以确保企业和生产环境的稳定性。

指定下载20.10.0版本的node

```shell
nvm install 20.10.0
```

![image-20240810152901215](images/image-20240810152901215.png)

使用指定的20.10.0版本node

```shell
nvm use 20.10.0
```

![image-20240810154140531](images/image-20240810154140531.png)

## 安装node没有npm的问题

安装了 `node` 却没有 `npm` 的问题，那只能手动安装 `npm`，如下

先查看 `node` 不同版本对应 `npm` 版本号：[点击前往](https://nodejs.org/zh-cn/download/releases/)

再去下载对应的 `npm` 版本的 `zip` 文件：[点击前往]([CNPM Binaries Mirror (npmmirror.com)](https://registry.npmmirror.com/binary.html?path=npm/))

下载好之后：

- 把解压出来的文件夹(`cli-xxxx`)重命名为 `npm`
- 放入对应 node 版本下的 `node_modules` 文件夹里面
- 然后打开该 npm 文件夹里的 `bin` 文件夹，把里面的 `npm 文件` 和 `npm.cmd 文件` 复制，放到对应 node 版本下，和 `node_modules` 文件夹同级即可

上面操作完成之后，执行 `node -v` 和 `npm -v` 就都有了

接着需要执行 `nvm on` 命令来开启使用 nvm 来管理 node，**如果这个命令报错，请打开管理员模式的 `cmd` 或 `powershell`，再执行 `nvm on` 即可**

## 修改 npm 全局目录及环境变量

`Window` 下可以使用npm root -g查看npm安装位置

```shell
npm root -g
```

创建全局模块文件夹`node_global`和缓存文件夹`node_cache`

先执行如下两条命令修改默认 `npm` 全局安装路径，和安装过程缓存文件存储路径

```shell
# 上面的路径，如下，如果设置失败看后面的后续处理第 1 条
npm config set prefix 'D:/Program Files/node/node_global'
npm config set cache 'D:/Program Files/node/node_cache'
# 然后输入下面这个命令查看是否修改成功
npm config ls
```



## nvm 常用命令

- `nvm arch`：

  显示node是运行在32位还是64位。

- `nvm install <version> [arch]` ：

  安装node， version是特定版本也可以是最新稳定版本latest。可选参数arch指定安装32位还是64位版本，默认是系统位数。可以添加--insecure绕过远程服务器的SSL。

- `nvm list [available]` ：

  显示已安装的列表。可选参数available，显示可安装的所有版本。list可简化为ls。

- `nvm on` ：

  开启node.js版本管理。

- `nvm off` ：

  关闭node.js版本管理。

- `nvm proxy [url]` ：

  设置下载代理。不加可选参数url，显示当前代理。将url设置为none则移除代理。

- `nvm node_mirror [url]` ：

  设置node镜像。默认是https://nodejs.org/dist/。如果不写url，则使用默认url。设置后可至安装目录settings.txt文件查看，也可直接在该文件操作。

- `nvm npm_mirror [url]` ：

  设置npm镜像。https://github.com/npm/cli/archive/。如果不写url，则使用默认url。设置后可至安装目录settings.txt文件查看，也可直接在该文件操作。

- `nvm uninstall <version>` ：

  卸载指定版本node。

- `nvm use [version] [arch]` ：

  使用指定版本node。可指定32/64位。

- `nvm root [path]` ：

  设置存储不同版本node的目录。如果未设置，默认使用当前目录。

- `nvm version` ：

  显示nvm版本。version可简化为v。

## 报错及解决方法

Error retrieving "http://npm.taobao.org/mirrors/node/index.json": HTTP Status 404

因为淘宝的镜像域名更换，npm.taobao.org域名[HTTPS证书](https://so.csdn.net/so/search?q=HTTPS证书&spm=1001.2101.3001.7020)到期更换为npmmirror.com，故此导致安装依赖报错

```
# 配置node镜像：
node_mirror:npmmirror.com/mirrors/node/
# 配置npm镜像：
npm_mirror:npmmirror.com/mirrors/npm/
```

# 安装Vue

## 安装vue-cli 3.x

1.卸载旧版本

卸载2.x版本 `npm uninstall vue-cli -g`
卸载3.x版本 `npm uninstall @vue/cli -g`

# Npm



## 报错

```
npm ERR! network request to https://registry.npm.taobao.orge/@vue%2fcli failed, reason: getaddrinfo ENOTFOUND registry.npm.taobao.orge
npm ERR! network This is a problem related to network connectivity.
npm ERR! network In most cases you are behind a proxy or have bad network settings.
npm ERR! network
npm ERR! network If you are behind a proxy, please make sure that the
npm ERR! network 'proxy' config is set properly.  See: 'npm help config'
报错：
npm犯错!network与网络连通性有关的问题。 
npm犯错!网络在大多数情况下，你背后的代理或有坏的网络设置。 
npm犯错!网络 npm犯错!网络如果你是一个代理，请确保 npm犯错!网络“代理”配置设置正确。
参见:'npm help config'
```

原理：后台设置的[proxy代理](https://so.csdn.net/so/search?q=proxy代理&spm=1001.2101.3001.7020)环境有问题，可能会有缓存

解决办法：

可以关闭代理然后清理代理环境在进行下载

1. 设置代理关闭

```
npm config set proxy false
```

2. 清除缓存

```
npm cache clean
```

注意，如果出现：清除缓存时报错，如下所示：

```
npm ERR! As of npm@5, the npm cache self-heals from corruption issues 
npm ERR!   by treating integrity mismatches as cache misses.  As a result, 
npm ERR!   data extracted from the cache is guaranteed to be valid.  If you 
npm ERR!   want to make sure 
```

则使用强制清除缓存指令

```
npm cache clean --force
```

注意：若是显示

```
npm WARN using --force Recommended protections disabled.
```

那就说明需要降低npm的版本了，因为安装的npm版本过高





**问题描述：**

近期使用npm淘宝镜像新建项目或依赖时出现报错

**npm ERR! request to https://registry.npm.taobao.org/XXX failed, reason: certificate has expired**

![img](images/1602578-20240322132549321-179440034.png)

**错误原因：**

淘宝镜像过期，具体补充说明如下：

早在 2021 年，淘宝就发文称，npm 淘宝镜像已经从 [http://registry.npm.taobao.org](https://link.zhihu.com/?target=http%3A//registry.npm.taobao.org) 切换到了 [http://registry.npmmirror.com](https://link.zhihu.com/?target=http%3A//registry.npmmirror.com)。旧域名也将于 2022 年 5 月 31 日停止服务（直到 HTTPS 证书到期才真正不能用了）

2024年1 月 22 日，淘宝原镜像域名（[http://registry.npm.taobao.org](https://link.zhihu.com/?target=http%3A//registry.npm.taobao.org)）的 HTTPS 证书正式到期，导致旧的 npm 淘宝镜像在使用时出错了。



**解决方案：**

### 1 清空缓存

```text
npm cache clean --force
```

### 2 查看当前的npm镜像设置

```text
npm config get registry
```

### 3 切换新源

```text
npm config set registry https://registry.npmmirror.com
```

### 4 查看新源是否设置成功

```text
npm config get registry
```

### 5 可以正常安装需要的工具了

```text
npm insatll
```

 可以看到镜像已经切换，再运行npm install

还是报错。。。。。。

后面才发现是package-lock.json中的镜像是之前的淘宝镜像，所以光是在终端更改镜像是没用的。删掉package-lock.json文件，再执行npm install命令，下载依赖成功。

# Yarn

yarn安装

```
npm install -g
```

yarn卸载

```
 yarn npm uninstall yarn -g  
```

## 报错

<font color="red">`yarn : 无法加载文件 D:\Program Files\nodejs\yarn.ps1，因为在此系统上禁止运行脚本。`</font>

先输入 `get-ExecutionPolicy` 查看状态
Restricted 表示禁用

再输入`set-ExecutionPolicy RemoteSigned`

然后就可以正常使用了

<font color="red">`error Error: certificate has expired <br>at TLSSocket.onConnectSecure (_tls_wrap.js:1502:34) at TLSSocket.emit (events.js:314:20)
    at TLSSocket._finishInit (_tls_wrap.js:937:8)`</font>

这个问题提示是证书过期导致的。

可以尝试禁用[SSL证书](https://so.csdn.net/so/search?q=SSL证书&spm=1001.2101.3001.7020)验证。

```vbnet
yarn config set strict-ssl false
```

然后再继续安装。

就可以了。

<font color="red">`[2/4] Fetching packages...
info There appears to be trouble with your network connection. Retrying...
info There appears to be trouble with your network connection. Retrying...
info There appears to be trouble with your network connection. Retrying...
info There appears to be trouble with your network connection. Retrying...
info There appears to be trouble with your network connection. Retrying...
error Error: connect ETIMEDOUT 104.16.0.35:443
    at TCPConnectWrap.afterConnect [as oncomplete] (net.js:1144:16)
info Visit https://yarnpkg.com/en/docs/cli/install for documentation about this command.`</font>

```
[2/4] Fetching packages...
info There appears to be trouble with your network connection. Retrying...
info There appears to be trouble with your network connection. Retrying...
info There appears to be trouble with your network connection. Retrying...
info There appears to be trouble with your network connection. Retrying...
info There appears to be trouble with your network connection. Retrying...
error Error: connect ETIMEDOUT 104.16.0.35:443
    at TCPConnectWrap.afterConnect [as oncomplete] (net.js:1144:16)
info Visit https://yarnpkg.com/en/docs/cli/install for documentation about this command.
```

将strict-ssl设置为false   yarn config set strict-ssl false 重新运行还是会报同样的错

然后将资源地址设置为淘宝镜像

yarn config set registry https://registry.npmmirror.com/

查看设置项 

yarn config get registry

如下



再次yarn install 成功了

