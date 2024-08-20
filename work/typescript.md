# TypeScript

 - 什么是declare关键字。
   告诉编译器，某个类型的存在,是外部文件定义的。可以直接使用函数。    

 - declare可以使用在那些地方。
   可以声明 变量， 类或接口， 模块，函数。    
   只能声明结构。不是它的实现。    

 - declare声明变量。
   ` x = 123 //这个代码报错。因为没有使用let或者var来声明。`     
   使用declare来声明变量的话，就可以在其他地方可以使用，而不是局部。      
   ```ts
   declare let x:number//如果不提供具体类型，那么x的类型是any
   x = 123; 
   ```
 - declare声明函数
   ```ts
   declare function sayHello( name: string): void;
   ```


   - @select="onSelect":  这里是的onSelect是指消息处理函数的名称，不是事件名。事件名字是select，@select是属性，是在属性列表里的。

   