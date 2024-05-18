# Lua 环境安装

## Window 系统上安装 Lua

- Github 下载地址：<https://github.com/rjpcomputing/luaforwindows/releases>

  ![img](https://www.runoob.com/wp-content/uploads/2015/05/8DA9DDFB-E6B8-4101-9BCA-4FFC6E97F7D6.jpeg)

- Google Code下载地址 : <https://code.google.com/p/luaforwindows/downloads/list>

双击安装后即可在该环境下编写 Lua 程序并运行。

你也可以使用 Lua 官方推荐的方法使用 LuaDist：<http://luadist.org/>

# Lua 基本语法

## 注释

### 单行注释

```lua
--
```

多行注释

```lua
--[[
	多行注释
]]--
```

多行注释推荐使用 **--[=[注释内容]=]**，这样可以避免遇到table[table[idx]]时就将多行注释结束了。

## 标示符

标示符以一个字母 A 到 Z 或 a 到 z 或下划线 **_** 开头，最好不要使用下划线加大写字母的标示符，

Lua 不允许使用特殊字符如 **@**, **$**, 和 **%** 来定义标示符。

Lua 是一个区分大小写的编程语言。

## 关键词

以下列出了 Lua 的保留关键词。保留关键字不能作为常量或变量或其他用户自定义标示符：

| and      | break | do    | else   |
| -------- | ----- | ----- | ------ |
| elseif   | end   | false | for    |
| function | if    | in    | local  |
| nil      | not   | or    | repeat |
| return   | then  | true  | until  |
| while    | goto  |       |        |

一般约定，以下划线开头连接一串大写字母的名字（比如 _VERSION）被保留用于 Lua 内部全局变量。

## 全局变量

定义一个变量默认是全局的。且默认初始化为nil

当且仅当一个变量不等于nil时，这个变量即存在。

# Lua 数据类型

Lua 中有 8 个基本类型分别为：nil、boolean、number、string、userdata、function、thread 和 table。

## nil（空）

```lua
print(type(a)) --nil

--对于全局变量和 table，赋一个 nil 值，等同于把它们删掉
tab = { key1 = "val1", key2 = "val2", "val3", "val4"}
tab.key2 = nil
for k, v in pairs(tab) do
    print(k.."--"..v)
end
--[[
1--val3
2--val4
key1--val1
]]

```

### nil 作比较时应该加上双引号 **"**：

```lua

ype(X)==nil --false
type(X)=="nil" --true

-- type(X) 实质是返回的 "nil" 字符串，是一个 string 类型：
type(type(X))==string
```

## boolean（布尔）

```lua
print(type(true)) --boolean
print(type(false)) --boolean
print(type(nil)) --nil

--false 和 nil 都为 false

--数字 0 是 true
```

## number（数字）

```lua
print(type(2))
print(type(2.2))
print(type(0.2))
print(type(2e+1))
print(type(0.2e-1))
print(type(7.8263692594256e-06))
--number
```

