# CSS——BEM命名规范
 1.什么是BEM命名规范
  * Bem 是块（block）、元素（element）、修饰符（modifier）的简写，由 Yandex 团队提出的一种前端 CSS 命名方法论。  
     - 中划线 ：仅作为连字符使用，表示某个块或者某个子元素的多单词之间的连接记号。  
     __ 双下划线：双下划线用来连接块和块的子元素。  
     _ 单下划线：单下划线用来描述一个块或者块的子元素的一种状态。

     双下划线连接块（block）和元素（element）。
     双横线连接块（block）和修改器（modifier）或者是元素和修改器。
     修改器表示块或者元素的不同版本。
     alt表示img没加载出来显示的文字。
你写了个simple_picture

 1.1 BEM 命名约定的模式是：
 ```javascript
 //每一个块（block）名应该有一个命令空间（前缀）
 .block{} //表示更高级的抽象或者组件

 .block__element{} 
 //代表了.block的后代，用于形成一个完整的.block的整体

 .block--modifier{}
 //代表了.block的不同版本或者状态。

