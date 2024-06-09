# HTML/CSS
 ## vw/vh
 ```
 .header_white {
  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background-color: #242424;
}
```
 * 100vw = 是指屏幕的宽度百分之百（viewport width）。
 * 100vh = 是指屏幕的高度百分之百（viewport height）。
 * top是指元素离上方的距离
 * left是指元素离左方的距离

 ## 什么是容器
 * 容器就是指html中外层的元素。比如下面的例子，第一个div就是第二个div的容器 
 ```
 <div>  
 <div> A </div>
 </div>
 ```
 * 注：flex是应用在容器上的。
 * display: flex是横排。
 * flex-direction: row | row-reverse | column | column-reverse;
   * flex-direction属性是Flexible Box Layout模板的

# HTML的标签
 * <hr>是指横线。
 * :class="{ 'abc': booleanValue }" :是说所有引号里面的东西是一个值。
    如果booleanValue的值是true。 abc就会被加到class里面去。

# css知识
 * &_xx{} 表示把外面那层的选择器名字直接拿过来。
   .abc{ &_def{}} 这里的&就相当于.abc.
 *  display: flex;是启动flex，flex-direction默认是row，如果设置column是表示纵排。
 * :class="{ 'abc': booleanValue }" :是说所有引号里面的东西是一个值。
    如果booleanValue的值是true。 abc就会被加到class里面去。
    :class="{ 'abc': true, 'def': false }" 相当于 class="abc"
    :class="{ 'abc': false, 'def': true }" 相当于 class="def"
    :class="{ 'abc': true, 'def': true }" 相当于 class="abc def"

```
<div id="1" class="a">
  <div id="2" class="b">
    <div id="3" class="c"></div>
  </div>
  <div id="4" class="c"></div>
</div>
```
 
# css一些便捷写法
 * margin: 0 auto; 相当于margin-top: 0;margin-bottom: 0;margin-left: auto; margin-right: auto;
   margin的第一个数字是上下的margin，第二个数字是左右的margin， auto是让元素居中。
# 术语
 * icon是指图标。



