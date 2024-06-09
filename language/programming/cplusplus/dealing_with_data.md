# C++ 基本类型
### 简单的变量
 ###### 变量名规则
  1. 只能使用字母字符、数字和下划线定变量名。   
  2. 变量名第一个字符不能是数字。   
  3. 区分大小写。   
  4. 不能将C++关键字作为变量名。   
  5. 以两个下划线或者下划线和大写字母打头的变量名会被保留给实现（编译器及其使用的资源）使用。这个效果会导致行为的不确定性，不知道结果将是什么。   
  6. 一个下划线开头的变量名被保留给实现，用作全局标识符。   
  7. C++对变量名长度没有限制。
  8. 两个或者更多单词组成一个名称，通常是用下划线字符将单词分开，例如 `my_onions;`或第二个单词开始每个单词的第一个字母大写。例如`myOnions`    
 ###### 位与字节 
  计算机内存的基本单位是位(bit)。    
  字节（byte）通常指的是8位的内存单元。描述计算机内存量的度量， 1KB=1024字节， 1MB = 1024KB。    
 ###### 整型
  整型是指没有小数点的数字。    
  术语宽度（width）用于描述存储整数时使用的内存量。    
  计算机内存由一些叫位（bit）的单元组成。    

  1. short至少16位。   
  2. int至少与short一样长。    
  3. long至少32位，且至少与int一样长。   
  4. long long 至少64位，且至少与long一样长。 

```c++
#include <climits>

int main()
{
    using std::cout;
    using std::endl;

    int n_int = INT_MAX;
    short n_short = SHRT_MAX;
    long n_long = LONG_MAX;
    long long n_llong = LLONG_MAX;

    cout << "int is " << sizeof(int) << " bytes." << endl;
    cout << "short is " << sizeof(n_short) << " bytes." << endl;
    cout << "long is " << sizeof(n_long) << " bytes." << endl;
    cout << "long long is " << sizeof(long long) << " bytes." << endl;
    cout << endl;

    cout << "Maximum values: " << endl;
    cout << "int: " << n_int << endl;
    cout << "short: " << n_short << endl;
    cout << "long: " << n_long << endl;
    cout << "long long: " << n_llong << endl;

    cout << "Minimum int value = " << INT_MIN << endl;
    cout << "Bits per byte = " << CHAR_BIT << endl;

    return 0;
}
```   
  1. 运算符sizeof和文件头limit(climit)    
   1.1. sizeof运算符返回类型或者变量的长度，单位是字节。在使用类型名使用sizeof运算符时，应将名称放在括号内，eg `sizeof(int)`,而变量可以不用括号。eg `sizeof n_int`。    
   1.2. limit(climit)是定义了符号常量来表示类型的限制。   
  2. 初始化注意事项：   
   2.1. 在声明变量时对它进行初始化可以避免忘记给它赋值的情况发生。   
   2.2. 在函数内部定义的声明没初始化，则改变量的值将是不确定的。意味着该变量的值将会是被它创建之间，相应内存单位的值。  
   2.3. C++11初始化方式，用于数组和结构，但在C++98中也可用单值变量而C++11使用更多。 eg `int hamburgers = {24};` C++11可以不用=符号。   
    2.3.1. 在大括号内可以不包含任何东西，会初始为0。 eg`int rocs = {};`   
  
  3. 无符号类型：不可以存储负数值的变量类型，增加了储存的最大值。    
   3.1. 使用unsigned来声明无符号的类型。   
   ```c++
      int main()
   { 
       using std::cout;
       using std::endl;

 
       short sam = SHRT_MAX;
       unsigned short sue = sam;
 
       cout << "Sam has " << sam << " dollars and Sue has " << sue;
       cout << " dollars deposited." << endl
            << "Add $1 to each account." << endl << "Now ";
       sam += 1;
       sue += 1;
       cout << "Sam has " << sam << " dollars and Sue has " << sue;
       cout << " dollars deposited.\nPoor Sam!" << endl;

       sam = ZERO;
       sue = ZERO;
       cout << "Sam has " << sam << " dollars and sue has " << sue;
       cout << " dollars deposited." << endl;
       cout << "Take $1 from each accout." << endl << "Now";
 
       sue -= 1;
       cout << "Sam has " << sam << " dollars and Sue has " << sue;
       cout << " dollars deposited " << endl << "Lucky Sue!" << endl;
 
       return 0;
  }
   ```
  
  4. 选择整型类型  
   4.1. 自然长度（natural size）指的是计算机处理起来效率最高的长度，int类型就是被设置这种长度。如果没有没有非常有说服力则应用int类型。   
    4.1.1. 如果需要存储的数值大于16位整数的最大可能，应该用long类型。即使系统是32位也应该这么做，方便移植到16位系统依旧可以工作。  
    4.1.2. 如果只需要一个字符，可使用char类型。   
    4.1.3. 后缀放在常量数字后面也可以表示类型。整数后面的L表示long常量，U表示unsigned int类型。UL是unsigned long, LL是表示longlong类型，ULL则是unsigned long long类型。 eg`cout << 600LL << endl`。 

  5. char类型：字符和小整数
   char类型是专门存储单个字符的类型，也可以当作比short更小的类型。在C++里，用单引用符来表示一个字符。eg`char ch = 'A';`    
```c++
   //chartype.cc -- the char type

#include <iostream>

int main()
{
    using std::cout;
    using std::endl;
    using std::cin;

    char ch;

    cout << "Enter a character: " << endl;
    cin >> ch;
    cout << "Hola!";
    cout << "Thank you for the " << ch << " charater." << endl; 
    //没有显示数字，而是字母。因为cin将输入的字母转为数字存储起来。
    //而cout根据类型是chart就将这个数字转为字母。
    return 0;
}
```
