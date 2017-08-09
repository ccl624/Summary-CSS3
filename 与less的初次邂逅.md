### less
	less是一种动态样式语言，属于css预处理器的范畴，它扩展了 CSS 语言，
	增加了变量、Mixin、函数等特性，使 CSS 更易维护和扩展
 
	less的中文官网：http://lesscss.cn/
	bootstrap中关于less的介绍：
 
### Less编译工具
	koala 官网:www.koala-app.com 
	
### less中的注释
   	以//开头的注释，不会被编译到css文件中
   	以/**/包裹的注释会被编译到css文件中  
	
### less中的变量
	使用@来申明一个变量：@pink：pink;
	1.作为普通属性值只来使用：直接使用@pink
	2.作为选择器和属性名：#@{selector的值}的形式
	3.作为URL：@{url}
	4.变量的延迟加载

### less中的嵌套规则
	1.基本嵌套规则
	2.&的使用

### less中的混合
	混合就是将一系列属性从一个规则集引入到另一个规则集的方式
	1.普通混合      
	2.不带输出的混合
	3.带参数的混合
	4.带参数并且有默认值的混合
	5.带多个参数的混合
	6.命名参数
	7.匹配模式
	8.arguments变量
	
### less运算
	在less中可以进行加减乘除的运算
### 代码示例
一物理像素

```
//less代码
*{
    margin: 0;
    padding: 0;
}

//一物理像素的
//上边框
.onePx(@_,@c:black){
     position: relative;
     &:before{
        position: absolute;
        content: "";
        display: block;
        width: 100%;
        height: 1px;
//      transform: scaleY(.5);
    }
}
.onePx(top,@c:black){
    &:before{
        top: 0;
        background: @c;
    }
}
.onePx(bottom,@c:black){
    &:before{
        bottom: 0;
        background: @c;
    }
}

#wrap{
    .onePx(top);
    width: 100px;
    height: 100px;
    background: pink;
    margin: 50px;
}
```

```
//HTML代码
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<meta name="viewport" content="width=device-width,initial-scale=1.0,user-scalable=no"/>
		<link rel="stylesheet" type="text/css" href="css/mixin.css"/>
		<title></title>
		
	</head>
	<body>
		<div id="wrap">
			
		</div>
	</body>
</html>
```
