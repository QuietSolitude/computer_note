# 入门
## 简介
 C#是一门面向对象，面向组件的强类型编程语言。  
 C#有统一类型系统，所有的类型都继承自object类型。所有的类型公用一组通用的运算，任何类型的值都可以一致进行存储，传输和处理。

## .NET体系结构
 C#程序在.NET上运行，.NET是由Common Language runtime(CLR)的虚拟执行系统和一组类库。  
   CRL是Microsoft对公共语言基础结构(Common Language Infrastructure CLI)国际标准实现的。CLI是语言和库创建执行和开发环境的基础。    
 C#编写的源代码会被编译成符合CLI规范的中间语言(Common Intermediate language CIL)，并将CIL代码和资源(位图和字符串)存在扩展名.dll的程序  
 集中。CIL是符合公共类型(Common Type Specification CTS)规范，可以和通过.NET版本的其他编程语言编写的代码交互，就行它们是用同一种语言编  
 写的一样，这也是.NET语言互相操作性的重要功能。
    注：程序集包含一个介绍程序集的类型，版本和区域性的清单。  
 C#程序执行时，CLR加载程序集，执行JIT(Just In Time)编译，将CIL代码转换成本机指令。这些代码也可以叫托管代码。    
 全局程序集缓存（Global Assembly Cache, GAC）：将可重用的代码放在所有应用程序都可以访问的地方。     
 垃圾回收（garbage collection）：释放程序不在使用的内存，这是托管代码最重要的一个功能。