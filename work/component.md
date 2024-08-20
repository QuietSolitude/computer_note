# 记录着我用过的component
 - `<page-layout></page-layout>`
   - 栏是印刷的术语。例如一张试卷的一面包含两栏，分别是左边一部分内容这是左栏，右边一部分内容，这是右栏。
   - 这个组件是实现了让页面左边一栏和右边一栏的布局。在我工作中是左边是表格，右边是编辑器。
   - 使用这个component需要在`<script lang="ts">`里面加上setup，不让不会有效果，`<script setup lang="ts">`不能粗心忘记这个点。
    - 标签是指<>符号包含的元素。例如<p>是p元素。
   - 属性是元素的配置或者提供的功能，例如 <p class='a'> class这个是元素的属性,'a'是属性的值。
   - 这个component有两个属性，一个是calss是给CSS使用的。一个是title，这个是显示在左边栏左上角的标题。
 - <template #table></template>
   - 标签的内容是指一对标签<template #table></template>之间包含的内容。
   - 这对标签是将包含的内容都显示在左边栏。

   ```ts
      <data-table
        :columns="[
          { label: 'Id', dataExtractor: (article) => article.id, align: 'left', isKey: true },
          { label: 'Title', dataExtractor: (article) => article.title, align: 'left' },
        ]"
        :data="articles"
        :selected="selectedArticles"
      />
   ```
 - <data-table/>
   - 这个component是实现一个表格。
   - 有两个主要的属性，一个是columns，一个是data。
    - columns是定义每一个列的，列头是label定义的，提取这个列里面的数据是dataExtractor定义的。align是定义左对齐还是右对齐，当align的值是left，那么是左对齐。
     - 特别注意的是isKey，它的值如果是true，那么就是每一行的key，必须唯一且不重复的。
      `{ label: 'Id', dataExtractor: (article) => article.id, align: 'left', isKey: true } //这里一行的key是Id`
    - data属性是一个数组。存储各种对象的数组。dataExtractor就是在这个数组提取数据。
    - selected属性是表示选中哪一行的key。
  特别注意事项：    
   `@select="onSelect"`    
   这里是一个事件。select是事件名， onSelect是消息处理函数的名称。当触发事件后，会运行这个消息处理函数onSelect。    
   @select是属性，select这个事件名也是在元素的属性列表里的，但是事件名不是属性。    

- 队长的思路是：
  - 首先知道要做什么，要怎么做。
  - 从哪做起，知道在哪做起了。
  - 看看这些component是做什么。谁写的。
  - 去问或者去看写的人说明这些组件是做什么的。
  - 了解怎么使用这些组件，然后按照规定的使用方法用起来。
  - 跑跑看是不是自己想要的结果。
  - 然后赶紧做笔记。一遍做一边记笔记。