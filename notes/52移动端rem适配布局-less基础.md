[toc]



## 维护 css 的弊端

CSS 是一门非程序式语言，没有变量、函数、SCOPE（作用域）等概念。

* CSS 需要书写大量看似没有逻辑的代码，CSS 冗余度是比较高的。
* 不方便维护及扩展，不利于复用。
* CSS 没有很好的计算能力
* 非前端开发工程师来讲，往往会因为缺少CSS编写经验而很难写出组织良好且易于维护的 CSS 代码项目。





## Less 介绍

* Less（Leaner Style Sheets 的缩写）是一门CSS扩展语言，也成为CSS预处理器。
* 做为CSS的一种形式的扩展，它并没有减少 CSS 的功能，而是在现有的 CSS 语法上，为CSS加入程序式语言的特性。
* 它在 CSS 的语法基础之上，引入了变量，Mixin（混入），运算以及函数等功能，大大简化了 CSS 的编写，并且降低了 CSS 的维护成本，就像它的名称所说的那样，Less 可以让我们用更少的代码做更多的事情。
* Less中文网址： http://lesscss.cn/
* 常见的CSS预处理器：Sass、Less、Stylus



> **注意**: **`Less 是一门 CSS 预处理语言，它扩展了CSS的动态特性`**。





##  Less安装

> **注意:** 如果使用vscode无需安装less）

1. 安装nodejs，可选择版本(8.0)，网址：http://nodejs.cn/download/
2. 检查是否安装成功，使用cmd命令（win10 是 window +r 打开 运行输入cmd） --- 输入“ node –v ”查看版本即可
3. 基于nodejs在线安装Less，使用cmd命令 “npm install -g less”即可
4. 检查是否安装成功，使用cmd命令 “lessc -v” 查看版本即可

![image-20240324173710232](http://images.newstar.net.cn/sally-imgsimage-20240324173710232.png) 





## Less 使用

我们首先新建一个后缀名为less的文件， 在这个less文件里面书写less语句。

* Less 变量
* Less 编译
* Less 嵌套
* Less 运算





## Less 变量

`变量`是指没有固定的值，`可以改变`的。因为我们CSS中的一些颜色和数值等经常使用。

```less
@变量名:值;
```





### 变量命名规范

* 必须有@为前缀
* 不能包含特殊字符
* 不能以数字开头
* 大小写敏感

```less
@color: pink;
```





### 变量使用规范

```less
//直接使用
body{
 color:@color;
}
a:hover{
 color:@color;
}
```







## Less导入

在标准 CSS 中，`@import` @ 规则必须在所有其他类型的规则之前。但是 Less 不关心你把 `@import` 语句放在哪里。

* 比如，在index.less中导入common.less
* 语法：

```less
@import “common”
```









##  Less 编译

* 本质上，Less 包含一套自定义的语法及一个解析器，用户根据这些语法定义自己的样式规则，这些规则最终会通过解析器，编译生成对应的 CSS 文件。
* 所以，我们需要把我们的less文件，编译生成为css文件，这样我们的html页面才能使用。



###  vocode Less 插件(重点)

* Easy LESS 插件用来把less文件编译为css文件
* 安装完毕插件，重新加载下 vscode。
* 只要保存一下Less文件，会自动生成CSS文件

![image-20240324174456534](http://images.newstar.net.cn/sally-imgsimage-20240324174456534.png) 







## Less 嵌套

1. 我们经常用到选择器的嵌套

```css
#header .logo {

 width: 300px;

}
```

* **Less 嵌套写法**： 子元素样式直接写到父元素里面即可

```less
#header {
 .logo {
 width: 300px;
 }
}
```



\- 举例说明：

![image-20240324184905391](http://images.newstar.net.cn/sally-imgsimage-20240324184905391.png) 

```less
.header {
  width: 120px;
  height: 120px;
  background-color: plum;

  a {
    color: black;
    text-decoration: none;

    &:hover {
      color: red;
    }
  }

}

.nav {
  .logo {
    font-size: 18px;
    color: pink;
  }
}
```





2. 如果遇见（交集|伪类|伪元素选择器）

   * **内层选择器的前面** `没有 & 符号`，则它被解析为`父选择器的后代`；
   * 如果`有 & 符号`，不是父元素后代，它就被解析为`父元素自身或父元素的伪类`

   ```less
   a:hover{
    color:red;
   }
   ```

   

   * **Less 嵌套写法**

   ```less
   a{
    &:hover{
    color:red;
    }
   }
   ```

   

   



## Less 运算 (重点)

任何数字、颜色或者变量都可以参与运算。就是Less提供了加（+）、减（-）、乘（*）、除（/）算术运算

```less
/*Less 里面写*/
@witdh: 10px + 5;
div {
 border: @witdh solid red;
}
/*生成的css*/
div {
 border: 15px solid red;
}
/*Less 甚至还可以这样 */
width: (@width + 5) * 2;
```



> **注意：** 
>
> 1. 乘号（*）和除号（/）的写法  (注：`除法需要加上括号`)
> 2. `运算符中间左右有个空格隔开 1px + 5`
> 3. 对于`两个不同单位`的值之间的运算，运算结果的值`取第一个值的单位`
> 4. 如果两个值之间`只有一个值有单位`，则运算结果`就取该单位`

![image-20240324200521087](http://images.newstar.net.cn/sally-imgsimage-20240324200521087.png) 



