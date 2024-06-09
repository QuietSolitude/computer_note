# Javascript基础

## 关键字
  * Let, var, const之间的区别  
    1.var声明变量在最外层函数时，该变量变成全局变量，如果声明在函数内部将会变成局部变量。
    ```Javascript
    var newV = 'hello';

    function newFunction() {
      var newC = '局部变量';
    }
    ```
    var声明的变量可以重新声明或者修改
    ```Javascript
    var newC = 'hello C';
    newC = 'hello cc';
    var newC = 11;
    ```
    var的变量声明在在代码执行之后，var变量声明会移到使用该变量的顶部，并且赋上undefined的值。
    ```Javascript
    console.log(newc);
    var newC = 'say hello';

    //代码会被解释成
    var newC；
    console.log(newC);
    newC = 'say hello';
    ```
  
    var的缺陷:由于var修饰的变量可以被重新定义，则可以在别的地方定义并赋上值，其他地方使用该变量的函数或者变量将会被影响。    

    2.块级作用域是指又{}界定的代码块。在这个花括号内的任何内容都是在一个块的作用域。

    let就是块级作用域，仅可以在块中使用。
    ```Javascript
    {
      let name = 'Solitude';
      console.log(name);
    
      if(true) {
        let name = 'CSC'; // 不同作用域可以定义相同变量
      }
    }

    {
      console.log(name); //这就报错了，因为超过了name的作用域。
    }
    ```
    let修饰变量可以被修改，但不可以被重新声明
    ```Javascript
    let name = 'Solitude';
    name = 'AAA';

    let name = 'C.C'; //错误，不能被重新声明。
    ```
    let变量可以和var一样，在变量被执行之后，会生成提前的let变量，但是不会初始化。  
 
    3.const和let声明很多相似处，但是const不能被修改并且不能被重新声明，每个const变量必须初始化。