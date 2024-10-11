# 创建 uni-app 项目

## uni-app 支持两种方式创建项目：

- 通过HBuilderX 创建
- 通过命令行创建(不必依赖 HBuilderX)

## 通过HBuilderX 创建

 	

## 命令行创建 uni-app 项目：

vue3+ts版: `npx degit dcloudio/uni-preset-vue#vite-ts 项目名称`

gitee下载：[https://gitee.com/dcloud/uni-preset-vue/repository/archive/vite-ts.zip](https://gitee.com/dcloud/uni-preset-vue/repository/archive/vite-ts.zip)

官网链接：[https://uniapp.dcloud.net.cn/quickstart-cli.html#创建uni-app](https://uniapp.dcloud.net.cn/quickstart-cli.html#创建uni-app)

![image-20241009224301372](images/image-20241009224301372.png)

# 用 VS Code 开发 uni-app 项目

为什么选择 VS Code ？

- HbuilderX 对 TS 类型支持暂不完善
- VS Code 对 TS 类型支持友好，熟悉的编辑器

### 开发流程

![image-20241009225334799](images/image-20241009225334799.png)



1. 安装uni-app插件

![image-20241009225042235](images/image-20241009225042235.png)

> 需要在uni-create-view插件那里打开【设置-扩展设置】
>
> 勾选【创建同名文件夹和文件名(Create-uniapp-view: Directory)】和更改【选择创建的模版(Create-uniapp-view: Template)】为Vue3
>
> 不然没有自动创建目录而且不是Vue3模板

2. ts型校验

experimentalRuntimeMode 已废弃现调整为 nativeTags——"nativeTags": ["block", "component", "template", "slot"]

原配置 experimentalRuntimeMode 现调整为 nativeTags。

2. json注释问题