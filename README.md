# DirectX11 With Windows SDK系列教程与演示项目

## 基本配置
IDE：Visual Studio 2017 Community

语言：C++/HLSL

项目依赖项：DXTK(目前仅使用其键鼠类和纹理加载)

Windows SDK支持版本：</br>
-**10.0.17134.0(项目默认配置)**</br>
-10.0.16299.0(已测试通过)</br>
-更低版本的10.0.XXXXX.0(未测试，理论上可以通过</br>

> 注意: 关于Windows SDK 8.1，鉴于DXTK现在已经删去了有关该SDK版本的项目，我现在无法测试它。但是可以确定的是，所有的示例教程项目理论是可以在该版本编译出来的，但需要**关闭符合模式**(/permissive-), 光是这样仅保证`Release`模式通过，若要在`Debug`模式下通过，还需要将`d3dApp.cpp`中所有ComPtr所使用的IUnknown::QueryInterface方法改写成使用ComPtr<T1>::As<T2>方法。

平台: 支持x86/x64, 可Debug/Release模式


## 注意事项
下载项目后理论上是可以直接编译的。如果是DirectXTK的问题，请到下面链接寻找合适的解决方案尝试编译，若能够通过则替换掉现有的DirectXTK_Desktop_2017_Win10项目，按照博客第4章教程进行配置即可。

该项目作为教程演示项目，并不是以实现一个软引擎为目标，因此不会刻意进行架构组织。建议读者在跟随教程学习的同时要动手实践。

**紧急事项(2018/9/3):如果现在DirectXTK无法通过编译，出现了下面的错误：**</font>

**C7510 "Callback": 模板 从属名称的使用必须以"模板"为前缀 event.h**</font>

**在**[**StackOverflow**](https://stackoverflow.com/questions/51864528/update-visual-studio-2017-now-getting-compile-error-c7510-callback-use-of-d)**找到了问题所在**

**双击该错误，首先定位到316行，把:** `return DelegateHelper::Traits::Callback(Details::Forward(callback));` 修改为 `return DelegateHelper::Traits::template Callback(Details::Forward(callback));`

**然后定位到324行，把:** `DelegateHelper::Traits::Callback(` **修改为** `DelegateHelper::Traits::template Callback(`

## 如何打开教程项目
若要指定哪个项目，需要对项目右键-设为启动项。

![](https://github.com/MKXJun/DirectX11-With-Windows-SDK/blob/master/MarkdownFiles/001.jpg)

然后对项目右键-选择生成，或者对整个解决方案进行生成都可以。

![](https://github.com/MKXJun/DirectX11-With-Windows-SDK/blob/master/MarkdownFiles/002.jpg)

## 博客教程

目前对应的博客更新：

[博客园](https://www.cnblogs.com/X-Jun/p/9028764.html)（优先保证最新）

[CSDN](https://blog.csdn.net/x_jun96/article/details/80293670)

## QQ群交流

QQ群号：727623616

欢迎大家来交流，以及项目有什么问题也可以在这里提出。


## 更新记录

该项目的更新记录位于Updates.md

