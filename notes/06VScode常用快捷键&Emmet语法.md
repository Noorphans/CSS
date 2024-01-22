# VScode常用快捷键&Emmet语法

[toc]





## VScode常用快捷键

1. 选定多个相同的单词： **ctrl + d**

   先双击选定一个单词，然后ctrl + d 可以往下一次选择相同的单词，方便同时修改相同的单词

   

2. 快速定位某一行，定位代码位置： **ctrl + g**

   当页面较长时，上下滚动页面不方便，采取ctrl+g，输入行数，快速调到指定行数上

   

3. 添加多个光标： **ctrl + Alt + (上/下箭头)**

   

4. 全局替换某个单词： **ctrl + h**(注意选择全部替换即可)

   当我们一个页面需要修改大量相同文件时，就使用全局替换

   

5. 复制代码： **shift + Alt + (上/下箭头)**

   

6. 选择某个区块： 按住 **shift + Alt** 然后**拖动鼠标**

   

7. 放大缩小编辑界面 ：Ctrl + 加号键 ，Ctrl + 减号键  

8. 自动换行： Alt + z

   

9. 自定义快捷键：有些快捷键使用不习惯，可自定义，比如

> 多行注释： vscode中 设置-首选项-键盘快捷方式-输入shift+alt+a或者块注释并双击-直接按下ctrl+shift+/  ，回车确认即可









## Emmet语法生成html标签

目标：能使用emmet语法

Emmet语法的前身是Zen coding,它使用缩写,来提高html/css的编写速度, Vscode内部已经集成该语法

1. 快速生成HTML结构语法

2. 快速生成CSS样式语法



### 快速生成HTML结构语法

1. 生成标签 直接输入标签名 按tab键即可，比如：
   * 输入！或html：5 + tab键，就可以生成html骨架
   * 输入div + tab 键， 就可以生成 < div>< /div>

2. 如果想要`生成多个相同标签`，加上 ` * ` 就可以了，比如：

   ```html
    <!-- tab*3 加tab键 -->
     <tab></tab>
     <tab></tab>
     <tab></tab>
   ```

   

3. 如果生成有**父子级关系(包含关系)**的标签，可以用 `> `比如，

   ```html
   <!-- ul>li加tab键 -->
     <ul>
       <li></li>
     </ul>
     <div><span></span></div>
   ```

   

4. 如果生成有`兄弟关系`的标签，用` +` ，比如：

   ```html
    <!-- div+p 加tab键 -->
     <div></div>
     <p></p>
   ```

   

5. 如果生成带`有类名`或者`id名字`的， 直接写 `.demo` 、`#two`或者 `标签名.demo` 加tab键，比如：

   ```html
    <!-- .demo #two-->
     <div class="demo"></div>
     <div id="two"></div>
   
     <!--table.demo  p#two -->
     <table class="demo"></table>
     <p id="two"></p>
   
    <!--ul>li#gray加tab键 -->
     <ul>
       <li id="gray"></li>
     </ul>
   ```

   

6. 如果想生成的div` 有顺序的类名`，用 自增符号 `$` * 数字，比如：

   ```html
    <!-- .demo$*5 -->
     <div class="demo1"></div>
     <div class="demo2"></div>
     <div class="demo3"></div>
     <div class="demo4"></div>
     <div class="demo5"></div>
   ```

   

7. 如果想要在`生成的标签内部 默认带有文字内容` 可以用`标签名加{ } `表示,比如：

   ```html
     <!-- 如果想要在 生成的标签内部 默认带有文字内容 可以用{ } 表示 -->
     <!-- h1{带有文字内容} -->
     <h1>带有文字内容</h1>
   
     <!-- div{熊猫}*3 -->
     <div>熊猫</div>
     <div>熊猫</div>
     <div>熊猫</div>
   
    <!-- div{$}*5 -->
     <div>1</div>
     <div>2</div>
     <div>3</div>
     <div>4</div>
     <div>5</div>
   
   <!-- div>p.pink{粉色系列} -->
     <div>
       <p class="pink">粉色系列</p>
     </div>
   ```

   





### 快速生成CSS样式语法

CSS 基本采取简写形式即可.

1. 比如 w200 按tab 可以生成 width: 200px;

2. 比如 lh26px 按tab 可以生成 line-height: 26px;
3. 比如 tac 按tab 可以生成 text-align: center;

![image-20240122094652762](http://images.newstar.net.cn/sally-imgsimage-20240122094652762.png) 







### 快速格式化代码

1. Vscode 快速格式化代码: shift+alt+f
2. **也可以设置 当我们 保存页面的时候自动格式化代码:**
   * 文件 ------.>【首选项】---------->【设置】----->文本编辑器---->格式化---->勾上Format On Save

