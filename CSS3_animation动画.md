## 1. 关键帧@keyframes
关键帧是让开发者能够指定动画中特定的时间点必须展现的关键帧样式来控制CSS动画的中间环节，可以更加精细的去控制动画
##### 格式：
```
<!-- 格式1 -->
@keyframes animationName {
    from{
        transform：rotateX(0deg)//起始样式值
    }
    to{
        transform：rotateX(360deg)//结束样式值
    }
}
```
```
<!-- 格式2 -->
@keyframes animationName {
    0%{
        transform：rotateX(0deg);//起始样式值
    }
    50%{
        rotateX(180deg);
    }
    100%{
        transform：rotateX(360deg);//结束样式值
    }
}
```
## 2. 动画内属性
### 1. 动画名 animation-name
关键帧所指定的一系列动画，值为一系列动画的名称，初始值为none，不是继承属性
### 2. 延迟 animation-duration
指动画持续的时间，默认值为0s，不是继承属性
### 3. animation-timing-function
动画执行函数，值可以为一个或多个timing-function，默认值为ease

timing-function | 功能
--- | ---
ease | 先快后慢
ease-in | 先慢后快
ease-out| 先快后慢
ease-in-out | 先慢后快再慢
linear | 线性运动（匀速）
cubic-bezier | 贝塞尔曲线
step-start | 以起始帧下一个的时间点作为起始点，再跳到下一时间点
step-end | 以起始帧跳到下一时间点
steps(4, end) | 从起始帧跳4次到下一个时间点
ease, step-start, cubic-bezier(0.1, 0.7, 1.0, 0.1) | 混合作用

### 3. 动画执行次数 animation-iteraion-count
动画结束前执行的次数，默认值为1，不是继承属性，值可以为1，也可以为infinite（无穷大）
### 4. animation-fill-mode
指定在动画执行之前和之后如何给动画的目标应用样式，默认值为none，不是继承属性
值 | 作用
--- | ---
none | 动画前后不改变样式
forwards | 动画执行完目标保持最后一帧的样式，取决于方向和次数
backwards | 动画执行之前保持animation-delay时第一帧的样式
both | 动画将会执行 forwards 和 backwards 执行的动作

### 5. 动画运行状态 animation-play-state
定义一个动画是否运行，可以通过查询此项确定动画是否正在运行，回复已暂停动画，初始值为running，不是继承属性
值 | 作用
--- | ---
running | 当前动画正在运行
paused | 当前动画被暂停
## 2. 动画外属性
### 1. 动画的方向 animation-direction
指定动画是否反方向，默认值为normal，不是继承属性
值 | 作用
---|---
normal | 向前循环
alternate | 动画交替反向运行，带时间功能的函数也反向
reverse | 反向运行动画，每周期结束动画由尾到头运行
alternate-reverse | 当动画执行多次时，先反向，后正向，时间功能函数也反向
### 2. 动画推迟 animation-delay
推迟动画从何时开始，默认值为0s，不是继承属性
## 3. animation简写属性
animation属性是如下属性的一个简写属性形式: 
- animation-name
- animation-duration
- animation-timing-function
- animation-delay
- animation-iteration-count 
- animation-direction
- animation-fill-mode
##### eg: animation: move_eye 4s linear 0s infinite alternate;
第一个时间会默认被设定为animation-duration的值，其他属性位置随便
## 4. 案例

```
<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width,initial-scale=1.0,user-scalable=no" />
    <title></title>
    <style type="text/css">

        *{
            margin: 0;
            padding: 0;
        }

        @keyframes move{
            from{
                top: 10px;
            }
            to{
                top: -10px;
            }
        }

        html,body{
            height: 100%;
            overflow: hidden;
        }

        #wrap{
            position: relative;
            height: 100%;
            overflow: hidden;
            background: gray;
        }
        #inner{
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate3d(-50%,-50%,0);
            font:16px helvetica;
            white-space: nowrap;
        }


        #inner span{
            position: relative;
            /*animation: move 1s infinite;*/
        }
    </style>
</head>
<body>
<div id="wrap">
    <div id="inner">
        <span>几</span>
        <span>百</span>
        <span>斤</span>
        <span>的</span>
        <span>人</span>
        <span>了</span>
        <span>上</span>
        <span>课</span>
        <span>还</span>
        <span>要</span>
        <span>装</span>
        <span>可</span>
        <span>爱</span>
    </div>
</div>
</body>
<script type="text/javascript">
    document.addEventListener("touchstart",function(ev){
        ev=ev||event;
        ev.preventDefault();
    });

    (function(){
        var styleNode = document.createElement("style");
        var width = document.documentElement.clientWidth;
        styleNode.innerHTML="html{font-size:"+(width/16)+"px !important}"
        document.head.appendChild(styleNode);
    })()


    window.onload=function(){
        setLoding();
        function setLoding(){
            var spanNodes =document.querySelectorAll("#inner span");
            var colors=["red","yellow","green","blue","pink","deeppink","hotpink"];
            for(var i=0;i<spanNodes.length;i++){
                spanNodes[i].style.color=colors[i%colors.length];
                spanNodes[i].style.animation="move .4s infinite "+(i/spanNodes.length)+"s alternate both";
            }
        }
    }
</script>
</html>
```
#### 效果图：
![image](http://note.youdao.com/yws/api/personal/file/WEBeb5bef21b9187147d146bd15a13cb895?method=download&shareKey=06df9dd4a7404f8f10cf532d8b8951d5)







