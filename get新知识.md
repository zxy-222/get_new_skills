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

      ​


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