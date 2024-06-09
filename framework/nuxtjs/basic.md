# NUXT Notes
 ## 语法
 * `<style scoped><style></style>`是让这个标签里的样式只在当前组件生效。
 * `export default Vue.extend({})`定义component的typescript
 * `export default vue.extend`里面的东西是component的typescript的内容。

 ```
 <nav v-show="isShow" class="header__navigation" @click="toggleShowMenu">
   <ul>
    <li>Home</li>
   </ul>
 ```
 * DOM元素是指把每一个HTML元素当作一个对象，而HTML是树状结构，DOM树就是指HTML
 * v-if和v-show动态显示或者隐藏DOM元素,但是v-if是向DOM树添加或删除DOM元素，而v-show是通过向DOM元素设置样式display属性控制显示或者隐藏
 * v-if是惰性的，初始值为false，是不会编译的，除非是值为true。而v-show是不管值是什么都会马上编译存入缓存，保留DOM。
 * v-if切换性能消耗较大，适合切换不是很频繁追求稳定的，而v-show最初渲染消耗较大，适合切换频繁的情况。
 * v-if其他语法：v-if可与v-else、v-else-if配合使用进行判断执行，但一定需要相邻，不可中断。

 ## nuxtjs文件夹
   * assets文件夹是存放全局的css
   * static文件夹是存静态文件
   * store文件夹是存放整个网站共享的信息
   * pages文件时存放页面
   * components文件夹时存放不是一个页面的文件
