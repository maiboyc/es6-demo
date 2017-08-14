第一章

    内容描述：let 和 const 命令

    作用描述：let 是声明一个变量，const是声明常量

    和ES5区别：ES5 声明用var

   let 基本用法：  ES6 新增了let命令，用来声明变量。它的用法类似于var，但是所声明的变量，只在let命令所在的代码块内有效。
   Example 1：
   {
        let a = 10
        var b = 1
    }
    a// 报错 ：a is not defined
    b//  1

    Example 2：
    for(let i = 0 ; i < 10 ; i++){

    }
    console.log(i) //报错： a is not defined . 只在for循环体内有效。在循环体外就会报错


    ES5 的for循环用var ：
    var a = [];
    for(var i = 0; i < 10 ; i++){
        a[i]=function(){
            console.log(i);
        };
    }
    a[6]();
    // 输出结果为10   ES5中 变量i使用var 声明的，在全局范围内有效， 所有，全局只有一个变量i ，
    每一次循环，变量的i的值都会发生改变，而循环内被赋给数组a的函数内部的console.log(i),里面的i 指向就是全局的i
    也就是说，所有数组a 成员里面的 i 的指向都是同一个i ，导致最后一轮的i 的值，也就是10。

    如果使用Es6 的let 声明，

    var a =[];
    for( let i = 0;i < 10 ; i++){
        a[i]=function(){
            console.log(i);
        };
    }
    a[6]();
    //输出结果为6
    因为刚才我们说到了，ES6中let 声明的变量是只在let所在的代码块内有效. 所以当前的i只在本轮循环有效 。
    你可能会问，如果每一轮循环的变量i都是重新声明的，那它怎么知道上一轮循环的值，从而计算出本轮循环的值？
    这是因为 JavaScript 引擎内部会记住上一轮循环的值，初始化本轮的变量i时，就在上一轮循环的基础上进行计算。

    另外，for循环还有一个特别之处，就是设置循环变量的那部分是一个父作用域，而循环体内部是一个单独的子作用域。

    for (let i = 0; i < 3; i++) {
      let i = 'abc';
      console.log(i);
    }









