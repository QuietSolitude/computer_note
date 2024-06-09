# 什么是vue？

## Vue的核心功能是是**声明式渲染**：


## vue小知识点
* v-html的用法,v-html里面的东西就是要放到标签里面的.
  ```
  <p
    v-html="'abc'"
  >
  </p>  //这样的显示结果是<p>abc</p>
  ```
* p标签内容可以通过v-html传进去的
* ```
  <p
    class="paragraph-block"
    v-html="parseMarkdown(i18n(blockConfig.content))" //i18n那个函数可以通过你当前选择的语言，来挑选应该显示哪个内容  
                                                      //v-html主要是因为parseMarkdown输出的是HTML。  
                                                      //i18n输出的是字符串。   
  >
  </p>

  content: {
    en: "English",
    de: "Deutsch",
    zh: "中文"
  }

* vue的<template>是html，<script>是vue调用的东西，<style>是写css的地方。
* export default defineComponent({}); vue规定一旦有export default了，后面的内容就必须是vue组件的定义。
* 使用import来导入组件，例如import { useGlobalState } from '@/services/GlobalState';
* {{内容}}表示打印内容。
* <img :src="....">不加冒号，那vue就不会把url的值读出来，而是直接拿“blockConfig.url”这个字符串赋值给src了。冒号的作用是提取值.
* :是绑定值， :src是v-bind:src的简写。  

# 需要记住的内容
  * 自己没有仔细分析语法结构，dota(){return{xxx}} data是个函数，返回obj。

