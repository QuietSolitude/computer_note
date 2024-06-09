# C++基础知识
###### C++的基本知识    
```c++
#include <iostream>

using std::cout;
using std::endl;

int main()
{
	cout << "Come up and C++ me some time.";
	cout << endl;
	cout << "You won't regret it!" << endl;

	return 0;
	
}
```
1.程序的分析
  函数头：是指返回类型或者void、函数名和括号组成，函数头是程序其他部分调用的接口。eg: int main()    
  形参列表：是指函数名后括号中的部分，描述了从调用函数传递给被调用函数的信息。eg: int add(int number)    
  函数体： 是指函数头下的花括号包括的部分，是指明函数应该做什么。eg {}。   
  语句：是指以分号结尾的表达式。 eg: cout << endl;    
  返回语句：结束该函数。 eg: return 0;    
  终止符：分号就是一个终止符，表示结束语句。   

  int main() 函数   
    与C不同，C++中让括号空着与在括号中使用viod是等效的，而C是意味着对是否接受参数保持沉默。   
	  除了一些例外情况，C++程序执行通常是从main函数开始执行的，每个独立的程序都需要main函数，没有定义，编译器会提示要定义main函数。   

  注释单行用//多行注释用/* */。    

  预处理器和iostream的联系       
    `# include <iostream>` C++自带预处理器会在编译程序时自动处理名称以#开头的编译指令。会将iostream文件替换或者添加源代码中的	`# include <iostrem>`代码行，将源代码文件和iostream文件合成一个复合文件，等待编译下一阶段来使用。    
    `iostream`C++的输出输出都定义在这个文件中。    

  名称空间 
    1. 当不同程序出现相同名称的函数或者类时，可以使用名称空间来进行区分，避免出现编译器不知道调用那个。    
	    eg: A类的play函数和B类的play函数，分别使用Aspace和Bspace来封装，这样编译器就知道要调用那个函数了。   
    2. C++的标准组件都放在std这个名称空间中，比如cout等都是, 在每次使用cout必须在其前面使用std::cout才可以。
	    using命令是告诉编译器要使用那个名称空间里的名称。在要使用组件前面使用using，就不用每次在前面加名称空间了。    
```c++
  int main() {
	  using std:: cout;
		using std:: endl;

		cout << "hello!" << endl;
		cout << "Hi" << endl;
	}
```   
    3. `using namespace std` 则是偷懒的做法，可以使用std里的所有名称。

  `cout << "Come up and C++ me some time"` 这代码表示将字符串信息插入输出流中。   
	  在用双引号括起来的一系列字符叫做字符串。    
	  输出是一个流，cout就是表示这种流。
	  <<（插入运算符） 是指信息流动的路径，将右侧的信息流进左侧。   
	

  `endl`和`\n`的区别
	 这两个有换行的功能，endl是控制符确保程序继续运行前刷新输出，而\n换行符不能提供这样的保证。在有些系统中，可以能在你输入信息后才会打印字符串。     
	 在显示字符串时，在字符串中包含换行应使用换行符\n这样可以减少输出量。   
```c++
cout << "Pluto is a dwarf planet.\n";
cout << "Pluto is a dwarf planet." << endl;
```

  标记（token）和空白（white space）    
	  标记是指一行代码中不可分割的元素。    
		必须用空格、制表符和回车将两个标记分开，这些统称空白。     
```c++
cout << "xxx" << endl; //在这些两个标记之间的空格就是空白
```

2.函数    
 C++函数分为有返回值的函数和没有返回值的函数。     

 自定义函数时，要将函数原型放在main函数前面。
  函数原型是有返回类型、函数名、括号和分号组成的，如果没有分号，编译器解释为一个函数头。eg: double sqrt(double);
```c++
//convert.cpp -- converts stone to pounds

#include <iostream>

int stonetolb(int sts);

int main()
{
	using std::cout;
	using std::cin;
	using std::endl;

	int stone;

	cout << "Enter the weight in stone: ";
	cin >> stone;
	int pounds = stonetolb(stone);
	cout << stone << " stone = ";
	cout << pounds << " pounds." << endl;

	return 0;
}

int stonetolb(int sts)
{
	return 14 * sts;
}
```
