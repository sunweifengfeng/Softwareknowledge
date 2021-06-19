`HTML` 表单是用于搜集不同类型的用户输入的，表单是一个包含表单元素的区域；表单元素是允许用户在表单中（比如：文本域、下拉列表、单选框、复选框等等）输入信息的元素；表单使用表单标签（`form`）定义。

## 一、介绍

1. 表单概念：
表单最重要的表现是在客户端接收用户的信息，然后将数据递交给后台的程序来操控这些数据，从技术的概念上说，表单就是用来操作form对象，对象是一种基本的数据类型

2. 创建表单:
表单通过`form`标签来创建，其中放置表单的对象，如表单域、按钮和其他事物，`form`标签中可扩展几个属性:

- **a.action属性**

通过`form`标签定义的表单里面必须有`action`属性才可以将表单中的数据递交上去
```html
<form action="some.php">

     </form>
```
以上代码表示这个表单的作用是用来提交`some.php`这个页面的数据
- **b.method属性**
该属性的作用是告诉浏览器数据是以何种方式提交上去的，该属性下有两个选择:"get"和"post"，默认情况下，数据被提交的方 式是get,表单域中输入的内容会添加在action指定的URL中，当表单提交后用户便获得一个明确的URL,由于这种方式下数据会添 加到URL中，所以好处是可以保存在收藏夹中和他人分享，直接访问主页的URL可以达到和填写注册后一样的效果，如有些时候，用户将自己已经注册过的一些网站主页加入到自己的收藏夹，再次从收藏夹中打开时，会发现已经是登录的状态。而post 这种方式，数据将以HTTP头的形式发送，表单数据不再是URL中的一部分。二者区别是get在安全性上较差，所有表单域的值 直接呈现，而post除了可见的处理脚本程序以外，别的东西都可以隐藏，所以在实际运用时通常选择post这种处理方式

- **c.name属性**

作用是令提交上去的表单数据可以被处理这些数据的程序识别，大部分页面中放入的表单很可能不止一个，此时就需要给不同 的表单起不同的名字，以便程序识别
```html
<form name="me">
</form>

...

<script language="JavaScript">

      var length=document.me.length.value;

</script>
```
上述部分代码说明通过表单me获取输入的length数值，代码中有不同的表单可以通过name来识别

- **d.enctype属性**

该属性代表HTML表单数据的编码方式，分别有application/x-www-form-urlencoded（标准编码方式，提交的数据被编码为名称/ 值对）、multipart/form-data（表示数据编码为一条信息，为表单定义了MIME编码方式，创建了一个与传统不同的POST缓冲 区，页面上每个控件对应消息的一个部分）和text/plain（表示数据以纯文本的形式进行编码，这样在信息中将不包含控件或格 式字符）共三种方式

e.target属性

目标显示方式，表示在何处打开目标URL，可以设置4种方式，_blank表示在新的页面中打开链接，_self表示在相同的窗口打开 页面，_parent表示在父级窗口打开页面，_top表示将页面载入到包含该链接的窗口，取代任何当前在窗口中的页面.
```html
<form action="mailo:depp59@gmail.com"

      method="post"

      name="me"

      enctype="text/plain"

      target="_blank">

...

</form>
```
这段代码表明该表单的动作是发送到邮箱depp59@gmail.com，使用post的传输方式，使用text/plain编码方式的me表单，使之 在新页面中打开

3. 表单域：即用户输入数据的地方

表单域可以分为`input`、`textarea`、`select` 3个对象，其中大部分表单通过`input`属性来实现，`textarea`和`select`创建一种控制类型

## 二、input对象下的多种表单表现形式

页面中大部分表单的形式都是通过输入标记input来实现的
```html
<input name=""

       type=""

       value=""

       size=""

       maxlength="">
```
- **a.其中name表示输入数据的名字，其作用是为了让程序明白所提交的数据**

```html
<input type="text" name="length">   
这个输入的数据命名为length
var length=document.me.length.value;
```
如果缺少了这样一个name属性，虽然在浏览器中的显示没有什么变化，但是后台程序后JavaScript程序就不能获得提交的数据

- **b.type属性表示所定义的是哪种类型的表单形式，该属性有九个可选值:**

`text` 单行的文本框
`password` 将文本替换为"*"的文本框
`checkbox` 只能做二选一的是或否选择
`radio` 从多个选项中确定的一个文本框
`submit` 确定命令文本框
`hidden` 设定不可被浏览用户修改的数据
`image` 用图片表示的确定符号
`file` 设置文件上传
`button` 用来配合客户端脚本

- **c.size:表示文本框字段的长度**
- **d.maxlength:表示可输入的最长的字符数量** 
- **e.value:表示预先设置好的信息**
4. text文本框的样式表单
```html
<html>
<head>
    <title>text样式表单</title>
    <style type="text/css">
        input{
            font:50% 微软雅黑;
        }
    </style>
</head>
<body>
    <form action="some.php" name="myform">
         输入用户名:<input type="text" name="name" size=20 maxlength=12>  <br>
         输入邮箱地址:<input type="text" name="address" size=20 maxlength=20>
    </form>
</body>
</html>
```
代码中size定义了文本框的长度，而maxlength定义了这个文本框最多只能输入12个字符，如果超出了这个长度数据将不能输入，这两个text样式的数据定义了不同的名字这很关键，否则一旦需要被程序调用数据将无法辨认。

5. password输入密码的样式表单（可以将文本使用保密形式展示出来的一个功能，根据不同的浏览器会使用点状形态或星号符表示）
```html
<html>
<head>
    <title>password样式表单</title>
    <style type="text/css">
        input{
            font:50% 微软雅黑;
        }
    </style>
</head>
<body>
    <form action="some.php" name="myform">
         输入用户名:<input type="text" name="name" size=40 maxlength=12>  <br>
         输入邮箱地址:<input type="text" name="address" size=20 maxlength=20><br>
         输入密码:<input type="password" name="password" size=20 maxlenght=12>
    </form>
</body>
</html>
```
6. checkbox复选框的表单样式（浏览器会在选择栏前面提供一个小方框如果选择小框中会添加小勾符号表示选中）
```html
<html>
<head>
    <title>checkbox样式表单</title>
    <style type="text/css">
        input{
            font:50% 微软雅黑;
        }
    </style>
</head>
<body>
    <form action="some.php" name="myform">
        <h3>注册信息:</h3>
           <input type="checkbox" name="truename" checked="checked">使用真实姓名
        <h3>实名制可以方便您更好地和朋友交流</h3>
           <input type="checkbox" name="address" checked="checked">显示我的地址
        <h3>如果去除勾选，其他用户将无法查到你的地址</h3>
           <input type="checkbox" name="mail"  checked="checked">可以给我发邮件
        <h3>如果勾选，我们将会为您发送来自广告商的信息</h3> 
    </form>
</body>
</html>
```
上面代码中添加了checked="checked"表示复选框默认值设置为checked,那么√符号会被默认添加

7. radio单选按钮的样式表单（多选一表单）

radio样式类似于选择题，在一组选项中选出唯一的一项，发送这列数据，其中给这组选项定义相同的名字，但是通过value属性 来加以区别，因此，这里必须给input对象设定value值，而且不同对象的value值不能相同，否则数据无法辨认
```html
<html>
<head>
    <title>radio样式表单</title>
    <style type="text/css">
        input{
            font:50% 微软雅黑;
        }
    </style>
</head> 
<body>
    <form action="some.php" name="myform">
       <h3>性别</h3>
           <input type="radio" name="gender" value="one">我是男的<br>
       <h3>请正确选择您的性别哦</h3>
           <input type="radio" name="gender" value="two">我是女滴<br>
       <h3>请正确选择您的性别哦</h3>
    </form>
</body>
</html>
```
8. submit提交数据的样式表单
该属性创建一个按钮，该按钮的作用就是提交数据。当点击"提交"按钮时，数据会发送到指定的地方。其中通过value值可以修 改按钮上显示的内容。此外还有一个reset属性，这是一个复位按钮，当被点击时表单的内容会被重新设置，回到页面初始位置
```html
<html>
<head>
    <title>submit样式表单</title>
    <style type="text/css">
        input{
            font:100% 微软雅黑;
        }
    </style>
</head>   
<body>
    <form action="some.php" name="myform">
        <h3>性别</h3>
           <input type="radio" name="gender" value="one">我是男的<br>
        <h3>请正确选择您的性别哦</h3>
           <input type="radio" name="gender" value="two">我是女滴<br>
        <h3>请正确选择您的性别哦</h3>
           <input type="submit" name="submit" value="确定">
           <input type="reset" name="submit" value="复位">
    </form>
</body>
</html>
```
9. hidden隐藏域的样式表单
hidden属性可以创建一个隐藏域，数据会被隐藏起来，用户无法对其进行操作（这些数据通常是用户不关心的但是必须被提交 的数据）
10. image样式的表单（可以看做图像替换按钮的技术，当图像被点击时，数据一并被提交至服务器）
`input type="image" src="" alt="确定"`
使用src属性指定这张图像的路径，使用alt属性来添加文本注释，此时提交按钮被替换成一个小小的图像，当点击图像时，其作 用就相当于submit按钮，但是当表单数据被提交的同时，用户所单击的图像的位置坐标（image.x=23 image.y=59）也会被发送
表单中还有一种触发事件的button表单，它只是一个按钮，单个button按钮并不会提交任何数据，它的作用是用来调用前端页 面，即客户端的脚本程序
`input type="button" value="运行" onclick="calculate();"`
11. file上传文件的样式表单
该表单允许用户上传自己的文件，例如用户上传自己的图像给服务器，用来改变用户在不同网站上的形象图片。需要注意的 是，当使用file样式的表单时，必须在`form`标签中说明编码方式，这样服务器才可以接收到正确信息
```html
<body>
    <h3>上传我的文件</h3>
    <form action="some.php" enctype="multipart/form-data" name="myform">
        <input type="file" name="uploadfile"> 
    </form>
</body>
```
## 三、textarea对象的表单
该对象就像是input对象中的text表单，只不过是扩展过的text样式表单，可以通过行(rows)属性和列(cols)属性来编辑文本域的大小，常见于留言板、论坛中回帖时的文本框等
```html
<html>
<head>
    <title>textarea对象的表单</title>
    <style type="text/css">
        textarea{
            font:100% 微软雅黑;
            color:navy;
        }
    </style>
</head> 
<body>
  <form action="some.php" method="post" enctype="multipart/form-data" name="myform">
      <textarea name="some" rows=10 cols=50 value="say">请文明用语:
      </textarea>
  </form>
</body>
</html>
```
`textarea`属性标签必须要封闭，且生成页面时在文本框中会预先设置好文本“请文明用语”，但是用户不得不先删去预先的文本再编辑自己的内容。当文本框中输入的内容超出预先设置的行数时会自动出现滚动条，如果没有超出文本框的范围则滚动条是灰 色的
## 四、select对象表单
使用`select`将创建一个列表样式的表单，显示为出现一个下拉列表框，令用户可以方便的选择其中一个目录，通常在一些要求填 写地区、生日等信息中，设计者可以给使用者准备好选项，需要使用`option`标签来定义可供选择的每一项
```html
<html>
<head>
    <title>select对象的表单</title>
    <style type="text/css">
        select{
           font:100% 微软雅黑;
           color:Green;
        }
    </style>
</head> 
<body>
   <form action="some.php" method="post" enctype="multipart/form-data" name="myform">
      <h3>地址</h3>
      <select name="上海">
          <option>黄浦区</option>
          <option>虹口区</option>
          <option>静安区</option>
          <option>宝山区</option>
      </select>
   </form>
</body>
</html>
```
用户可以通过下拉列表框选择一个“地址”，而这个数据会被表单发送到服务器，此外还可以通过`value`属性为每一个`option`指定不 同的值，这样的话`value`设置的值将取代`option`的文本内容。注意如果设计者希望预先设置初始值，那么在所希望的option中添加 `selected="selected"`就可以了，如`<option selected="selected">`浦东新区`</option>`,否则默认初始值应该是第一个出现的`<option> `的文本内容。
如果下拉列表内内容太多，可以使用`<optgroup>`标签配合`label`属性来给选项分类
```html
<select name="上海">
      <optgroup label="Team1">
          <option>黄浦区</option>
          <option selected="selected">虹口区</option>
          <option>静安区</option>
          <option>宝山区</option>
      </optgroup>
      <optgroup label="Team2">
          <option>长宁区</option>
          <option>杨浦区</option>
          <option>徐汇区</option>
          <option>普陀区</option>
      </optgroup>        
</select>
```
此外如果不希望`select`对象以下拉列表框的形式展现出来，有一种方式可以将目录项以滚动条的样式表现出来，只需要在`select` 标签中加入`size`属性，如`"size=6"`表示是一个能容纳6行文字的文本框，当目录项超出设置的行数时将出现滚动条
```html
<select name="上海" size="5">
        <option>黄浦区</option>
        <option selected="selected">虹口区</option>
        <option>静安区</option>
        <option>宝山区</option>
        <option>长宁区</option>
        <option>杨浦区</option>
        <option>徐汇区</option>
        <option>普陀区</option>        
</select>
```
## 五、表单域集合
如果表单的项目过多或为了修饰表单部分，可以通过使用表单域将表单分组，表单域的代码由`<fieldset>`标签和`<legend>`标签组 合而成，默认情况下，`<fieldset>`标签勾画出表单域的框形，`<legend>`标签的对象像标题一样出现在框的左上角
```html
<html>
<head>
    <title>表单域</title>
</head> 
<body>
  <form action="some.php" method="post" name="myform">
     <fieldset>
          <legend>注册信息:</legend>
          输入用户名:<input type="text" name="name" size=20 maxlength=12>
          <!--这里可以放入许多样式的表单-->
     </fieldset>
  </form>
</body>
</html>
```