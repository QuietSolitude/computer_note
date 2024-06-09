# vite notes

# 什么是vue？
  vue是一款用于构建用户界面的JavaScript框架。它是基于标准HTML，CSS和JavaScript构建的。  
  声明式渲染：Vue基于标准HTML拓展了一套模板语法。  
  响应性：能在改变时触发更新的状态。  
  * 使用reactive()API来声明响应式状态。会创建一个[JavaScript Proxy](https://developer.mozilla.org/zh-CN/docs/Web/JavaScripReference/Global_Objects/Proxy)对象但是只适用对象(数组和内置类型),reactive返回proxy，可以直接操作.
  * 另一个API ref()则可以接受任何类型。返回一个包裹对象，并在.value属性暴露内值。




# vite注意事项
  1. @是src的别名