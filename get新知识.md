- 2018/03/17

  - ##### 1、getComputedStyle和style的区别

    - ***getComputedStyle***
      - 获取当前元素所有最终使用的CSS属性，返回的是一个CSS样式声明对象。
      - 只读，只能获取样式，不能设置。
      - 该方法会返回对象属性中length属性值(即使样式中没有写)
    - ***style***
      - 可以读取也可以设置
      - 只能获取style样式中设置的样式
    - ***currentStyle***
      - 是IE浏览器的一个属性和style类似
      - 不支持伪类样式获取

- 2018/03/26

  - ##### 1、对于动态添加的内容，不支持click事件，需要添加on事件

    ```
    $(e).on('click','.class',function){}
    ```

- 2018/03/29

  - ##### 1、使用less文件

    - ***1、引入 .less 文件的时候要设置rel属性值为“stylesheet/less”***

      ```
      <link rel = "stylesheet/less" type="text/css" href="style.less">
      ```

    - ***2、然后在&lt;head>中引入：less.js文件***

      ```
      <script type="text/javascript" src="less.js"></script>
      ```

    - ***3、注意：(1)、less样式文件一定在引入less.js文件前引入***

      ​		***(2)、在服务器环境下使用,本地打开可能会报错***

- 2018/04/08

  - ##### 1、获取页面中元素滚出页面的高度

    - ***1、document.body.scrollTop***

    - ***2、document.documentElement.scrollTop***

    - ***3、区别：1、当页面具有DTD(document type definition )时，或者说指定了DOCTYPE时,使用document.documentElement；2、当页面不具有DTD时,或者说没有指定DOCTYPE时,使用document.body***

    - ***4、兼容：***

      ```
      var scollTop = window.pageOffset || document.document.scrollTop || document.body.scrollTop || 0;
      ```

  - ##### 2、引入公共html页面的几种方法

    - ***(1)、PHP/ASP.NET —— inclue***

      ```
      <strong>inclue 'test.html';require 'test.html';</strong>
      ```

    - ***(2)、iFrame***

      ```
      <iframe src="http://baidu.com" width="";height=""frameborder="0" scrolling="no"></iframe>
      缺点：页面结构杂乱、不易被搜索引擎搜索、导航链接等等问题
      ```

    - ***(3)、Javascript/jQuery：利用js(jQuery)或ajax从服务器上取回需要的公共页面后插入页面***

      ```
      $("#myDiv").load("url",params)
      var test={  
          "type1":"paramer1","type2":"paramer2"};  
          $.ajax({  
              url:'myTest.php',  
              type:'post',  
          dataType:'html',  
          data:parames,  
          error: function(){alert('error');},  
          success:function(data){  
              $("#myDiv").html(data);  
          }  
      });  
      ```

    - ***(4)、SSI(server SideInc lude),通常称为服务器端嵌入，是一种类似于ASP的基于服务器的网页制作技术。html页面的命令，需要由服务器在提供页面的时候进行处理，该方法需要有服务器的支持才能使用.***

      - 配置方式：

        - 1、打开apache安装目录，找到httpd.conf文件，用编辑器打开，找到如下两行，将前面的#号去掉。

          ```
          #AddType text/html .shtml  
          #AddOutPutFilter INCLUDES .shtml 
          ```

        - 2、找到"Options Indexes FollowSymLinks"，在后面加上Includes

          ```
          Options Indexes FollowSymLinks Includes
          ```

        - 3、使用格式如下

          ```
          <!--#include  "test.html"-->  
          ```

    - ***(5)、Clam:calm开发出来的功能之一就是构建模块化的前端项目；[https://www.npmjs.org/package/clam](https://www.npmjs.org/package/clam)***

      ```
        - calm的使用首先需要安装node.js，然后使用npm安装
      ```

      ```
        npm -g install clam  

        - 安装好之后，创建项目可以查看链接

        - 在需要引入其他页面的地方加上
          <!--#include  "test.html"-->
        - 格式和asp、SSI一样。这种方式的好处之一是不用再去配置，且使用的是http服务器,不用为了使用公共部分代码而不得不使用php等技术
      ```

    - ***(6)、<object&gt;***

      ```
      <object type="text/x-scriptlet" data="import.htm" width=100% height=30></object>
      ```
   - ##### 3、jQuery对象和DOM对象的互转

     - ***1、DOM对象转jQuery对象***

       ```
        $(dom对象)----->jQuery对象
       ```

     - ***2、jQuery对象转DOM对象***

       ```
        1、var $li = $('li');
        2、$li.get(0);
       ```
        ​

- 2018/04/10

  - 微信小程序 仿美团城市选择 城市切换[https://blog.csdn.net/liguanjie8/article/details/54692576](https://blog.csdn.net/liguanjie8/article/details/54692576)

- 2018/04/12

  - ##### 1、元素和节点的区别？

    - ***1、元素也是节点的一种，即元素节点***
    - ***2、在HTML DOM(文档对象模型)中,每个部分都是节点***
      - ***(1)、文档本身是文档节点***
      - ***(2)、所有HTML元素是元素节点***
      - ***(3)、所有HTML属性是属性节点***
      - ***(4)、HTML元素内的文本是文本节点***
      - ***(5)、注释是注释节点***

  - ##### 2、jQuery获取元素的方法？

    - ***1、获取元素的方法分为两种：jQuery选择器、jQuery遍历函数***

      - ***(1)、jQuery选择器***

        | 选择器               | 实例                     | 说明                                       |
        | ----------------- | ---------------------- | ---------------------------------------- |
        | #id               | $('#myId')             | ID选择器:可以获取到ID为“myId”的元素,区分大小写            |
        | .class            | $('#myClass')          | 类选择器:获取到class为’myClass‘的元素               |
        | element           | $('p')                 | 获取所有p元素                                  |
        | :header           | $(':header')           | 获取所有标题元素：<h1&gt;~<h6&gt;                 |
        | :animated         | $(':animated')         | 获取所有动画元素                                 |
        | contains(text)    | $('p:contains(hello)') | 获取包含文本为hello的<p&gt;元素,中间的文本区分大小写         |
        | :hidden           | $(':hidden')           | 获取所有的隐藏元素：width和height为0、display:none、type=hidden |
        | [attribute]       | $('[href]')            | 属性选择器：获取所有含有属性为href的元素                   |
        | [attribute=value] | $('[href=a.html]')     | =   获取所有带有属性href，并且值为a.html的元素                                                                    !=  获取所有带有属性href，并且值不等于为a.html的元素                                                   $=  获取所有带有属性href，并且值以a.html结尾的元素                                                       ^=  获取所有带有属性href，并且值以a.html开头的元素                                                       ~=  获取所有带有属性href，并且值包含单词”a.html“的元素                                             *=  获取所有带有属性href，并且值包含文本”a.html“的元素 |
        | :input            | $(':input')            | 获取所有input元素                              |
        | :radio            | $(':radio')            | 所有带有 type="radio" 的 input 元素;           类似的有：:text、:checkbox、:password、:submit、:reset、:button、:file |
        | :enabled          | $(':enabled')          | 所有启用的input元素。 :disabled  则相反             |
        | :checked          | $(':checked')          | 所有选中的input选择（单选框、复选框）                    |
        | :gt(index)        | $('p:gt(2)')           | index从0开始，获取index大于（不包含）2的所有<p>元素        |
        | :lt(index)        | $('p:lt(2)')           | index从0开始，获取index小于（不包含）2的所有<p>元素        |
        | :even             | $('tr:even')           | 所有偶数<tr&gt;元素                            |
        | :odd              | $('tr:odd')            | 所有奇数<tr&gt;元素                            |

      - ***(2)、jQuery选择器+遍历函数***

        | 方法      | 描述               |
        | ------- | ---------------- |
        | eq()    | 返回带有被选中的指定索引号的元素 |
        | first() | 返回被选元素的第一个元素     |
        | last()  | 返回被选元素的最后一个元素    |

      - ***(3)、获取同级元素***

        - a、选择器

          | 选择器                | 实例           | 说明                   |
          | ------------------ | ------------ | -------------------- |
          | element + next     | $('div + p') | 每个div相邻的下一个<p&gt; 元素 |
          | element ~ siblings | $('div ~ p') | 获取跟div同级的所有<p&gt; 元素 |

        - b、遍历函数

          | 方法        | 描述              |
          | --------- | --------------- |
          | next()    | 返回被选元素的下一个同级元素  |
          | nextAll() | 返回被选元素之后的所有同级元素 |
          | prev()    | 返回被选元素的前一个同级元素  |
          | prevAll() | 返回被选元素之前的所有同级元素 |

      - ***(4)、获取父级元素***

        - a、选择器

          | 选择器     | 实例            | 说明           |
          | ------- | ------------- | ------------ |
          | :parent | $('p:parent') | 获取所有p元素的父级元素 |

        - b、遍历函数

          | 方法        | 描述            |
          | --------- | ------------- |
          | parent()  | 获取被选元素的父级元素   |
          | parents() | 获取被选元素的所有祖先元素 |

      - ***(5)、获取子级元素***

        - a、选择器

          | 选择器               | 实例          | 说明                             |
          | ----------------- | ----------- | ------------------------------ |
          | parent > child    | $('div> p') | 获取div直接子元素的所有<p&gt; 元素         |
          | parent descendant |             | $('div  p')获取div所有后代的<p&gt; 元素 |

        - b、遍历函数

          | 方法         | 描述                        |
          | ---------- | ------------------------- |
          | children() | 返回被选元素的所有直接子元素            |
          | contents() | 返回被选元素的所有直接子元素(包含文本和注释节点) |
          | find()     | 返回被选元素的后代元素               |

          ​
