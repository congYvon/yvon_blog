1、重置表单样式

<style>
        /* 重置表单样式 */
        input,button,select,textarea{
            -webkit-appearance: none;
            -moz-appearance: none;
            appearance: none;
            outline: none;
            border: none;
        }
    </style>

    <input type="text">
    <input type="button" value="Button">
    <input type="checkbox" name="" id="">
    <input type="radio" name="" id="">

2、css 变量

<style>
        :root{
            --theme_color:red;
        }
        body{
            color: var(--theme_color,'#000');
        }
        /* 将变量声明到局部,只能在子节点中使用 */
        .selector { --color: yellow } 
        .selector span { color: var(--color) }
    </style>

    <p class="selector">
        <span>123</span>
    </p>
    <script>
        // -> 操作全局变量
        document.documentElement.style.setProperty('--theme_color','blue');
    </script>

3、移动端常用操作

<style>
        /* 禁止保存图片 */
        .no-callout {
            -webkit-touch-callout: none
        }
        /* 禁止长按文字选择功能 */
        .unselect {
            -webkit-touch-callout: none;
            -webkit-user-select: none;
            -khtml-user-select: none;
            -moz-user-select: none;
            -ms-user-select: none;
            user-select: none
        }
        /* 移动端顺畅滚动 */
        .scroll-touch {
            -webkit-overflow-scrolling: touch;
        }
        /* 移动端屏幕旋转时字体大小保持不变 */
        html,
        body,
        form,
        p,
        div,
        h1,
        h2,
        h3,
        h4,
        h5,
        h6 {
            -webkit-text-size-adjust: 100%;
            -ms-text-size-adjust: 100%;
            text-size-adjust: 100%
        }
        /* 移动端横竖屏的适配 */
        @media all and (orientation:portrait) {
            body::after {
                content: '竖屏'
            }
        }
        @media all and (orientation:landscape) {
            body::after {
                content: '横屏'
            }
        }
        /* 改变input光标的颜色 */
        .input {
            caret-color: red;
        }
        /* 移动端Android设备上去掉语音输入按钮 */
        input::-webkit-input-speech-button {
            display: none
        }
        /* 去掉为search自带的清空按钮 */
        .search::-webkit-search-cancel-button {
            display: none
        }
    </style>

4、文字模糊

<style>
        .blur {
            color: transparent;
            text-shadow: 0 0 5px rgba(0, 0, 0, 0.5)
        }
    </style>

    <p class="blur">Hello World</p>

5、换行

<style>
        *{
            margin: 0;
            padding: 0;
        }
        .box{
            width: 100px;
            height: 100px;
            border: 1px solid #000;
        }
        .box p{
            /* 不换行 */
            white-space: nowrap;
            /* 自动换行 */
            word-wrap: break-word;
            word-break: normal;
            /* 强制换行 */
            word-break: break-all;
        }
    </style>

    <div class="box">
        <p>你可能就基本后看门狗就弄卡盟你今年可能你你你看看那就</p>
    </div>

6、vertical-align

<style>
        *{
            margin: 0;
            padding: 0;
        }
        .box{
            border: 1px solid red;
            font-size: 100px;
        }
        .wrap{
            display: inline-block;
            width: 100px;
            height: 100px;
            background-color: red;
            /* baseline - 默认是基线,比如说是本实例x的下边缘 */
            /* top - 元素的顶端与行中最高元素的顶端对齐 */
            /* text-top - 元素的顶端与父元素字体的顶端对齐 */
            /* bottom - 元素的低端与行中最低元素的顶端对齐 */
            /* text-bottom - 元素的低端与父元素字体的低端对齐 */
            /* middle - 相对于中线对齐 (中线就是小写x的高度的一半) */
            vertical-align: middle;
        }
    </style>

    <!--
        vertical-align 垂直对齐
            - 适用于inline inline-block
    -->
    <div class="box">
        <div class="wrap"></div>xXay
    </div>

7、cursor

<style>
        *{
            margin: 0;
            padding: 0;
        }
        .box{
            width: 500px;
            height: 500px;
            background-color: red;
            margin: 50px auto;
            /* 
                cursor:
                    pointer     箭头
                    wait        等待
                    help        帮助
                    pointer     小手
                    text        文本
                    move        鼠标移动
            */
            /* cursor: pointer; */
            /* 自定义鼠标样式 */
            cursor: url("https://p1.ssl.qhimg.com/t01a472755aac62783f.png"),wait;
        }
    </style>

    <div class="box"></div>

8、逗号分隔列表

<style>
        p>span:not(:last-child)::after{
            content: ',';
        }
    </style>

    <p>
        <span>1</span>
        <span>2</span>
        <span>3</span>
        <span>4</span>
    </p>

9、checkbox 改造成 Switch

<style>
        /* 背景层 */
        .switch-component {
            position: relative;
            width: 60px;
            height: 30px;
            background-color: #dadada;
            border-radius: 30px;
            border: none;
            outline: none;
            -webkit-appearance: none;
            transition: all .2s ease;
        }
        /* 按钮 */
        .switch-component::after {
            content: attr(data-content);
            position: absolute;
            top: 0;
            left: 0;
            width: 50%;
            height: 100%;
            text-align: center;
            line-height: 30px;
            color: #dadada;
            background-color: #fff;
            border-radius: 50%;
            transition: all .2s ease;
        }
        /* 选中状态时，背景色切换 */
        .switch-component:checked {
            background-color: #86c0fa;
        }
        /* 选中状态时，按钮的位置移动 */
        .switch-component:checked::after {
            left: 50%;
            color: #ccc;
        }
    </style>

    <input class='switch-component' type='checkbox' data-content="关">
    <script>
        var needContributions;
        document.querySelector(".switch-component").onclick=function() {
            if (this.checked) {
                var needContributions = 0;
                console.log(needContributions);
                this.setAttribute('data-content', "开")
            } else {
                var needContributions = 1;
                console.log(needContributions);
                this.setAttribute('data-content', "关")
            }
        }
    </script>

10、隐藏没有静音就自动播放的 video

<style>
        video[autoplay]:not([muted]) {
            display: none
        }
    </style>

11、input 获取焦点上浮效果

<style>
        input{
            appearance: none;
            outline: none;
            border: none;
            padding: 1rem;
            border-bottom: 1px solid #ebebeb;
            transition: all .2s ease-in-out;
        }
        input:focus{
            box-shadow: 0 3px 10px 1px rgba(0,0,0,.1);
            transform: translateY(-.5rem);
        }
    </style>

    <input type="text" placeholder="请输入">

12、菜单栏的弹性伸缩

<style>
        body,
        html {
            height: 100%;
            overflow-x: hidden;
        }
        .index {
            height: 100%;
        }
        /* 菜单栏的初始样式 */
        .menu {
            position: fixed;
            top: 0;
            left: 0;
            width: 10rem;
            height: 100%;
            background-color: darkgrey;
            transform: translateX(-10rem);
            z-index: 1;
            transition: all .2s ease-in;
        }
        /* 内容区的初始样式 */
        .content {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 100%;
            height: 100%;
            background-color: cornsilk;
            transform: translateX(0);
            transition: all .3s ease-in;
        }
        input {
            display: none;
        }
        /* 切换按钮的初始样式 */
        label {
            position: fixed;
            top: 1rem;
            left: 1rem;
            z-index: 2;
            transition: all .2s ease-in;
        }
        /* 切换按钮选中的样式 */
        input:checked~label {
            left: 12rem;
        }
        /* 切换按钮文字的切换样式 */
        input:not(:checked)~label::after {
            content: '拉出'
        }
        input:checked~label::after {
            content: '收起'
        }
        /* 菜单栏显示的样式 */
        input:checked~.menu {
            transform: translateX(0)
        }
        /* 内容区显示的样式 */
        input:checked~.content {
            transform: translateX(10rem)
        }
    </style>

    <div class="index">
        <input type="checkbox" id="btn">
        <label for="btn"></label>
        <div class="menu"></div>
        <div class="content">
            <p>我是内容</p>
        </div>
    </div>

13、波浪效果

<style>
        body {
            background-color: #313131;
        }
        .wave {
            position: absolute;
            top: 0;
            left: 0;
            right: 0;
            bottom: 0;
            margin: auto;
            width: 200px;
            height: 200px;
            background-color: #5291e0;
            overflow: hidden;
        }
        .wave::before,
        .wave::after {
            content: '';
            position: absolute;
            left: 50%;
            width: 500%;
            height: 500%;
            background-color: #fff;
            border-radius: 48%;
            animation-name: rotate;
            animation-iteration-count: infinite;
            animation-timing-function: linear;
        }
        .wave::before {
            bottom: 15%;
            border-radius: 45%;
            animation-duration: 15s;
        }
        .wave::after {
            bottom: 10%;
            opacity: .5;
            border-radius: 47%;
            animation-duration: 15s;
        }
        @keyframes rotate {
            0% {
                transform: translate(-50%, 0) rotateZ(0deg);
            }
            50% {
                transform: translate(-50%, 0) rotateZ(180deg);
            }
            100% {
                transform: translate(-50%, 0) rotateZ(360deg);
            }
        }
    </style>

    <div class="wave"></div>

14、导航跟随效果

<style>
        ul {
            list-style: none;
            font-size: 0;
        }
        li {
            position: relative;
            display: inline-block;
            padding: 1rem;
            cursor: pointer;
            font-size: 16px;
        }
        li::after {
            content: "";
            position: absolute;
            bottom: 0;
            left: 100%;
            width: 0;
            height: 0;
            border-bottom: 1px solid #000;
            transition: .3s ease;
        }
        li:hover::after {
            width: 100%;
            left: 0;
        }
        li:hover~li::after {
            left: 0;
        }
    </style>

    <ul>
        <li>1111</li>
        <li>2222</li>
        <li>3333</li>
        <li>4444</li>
    </ul>

15、左右滑动

<style>
        .box {
            width: 500px;
            height: 200px;
        }
        .box .item {
            width: 80px;
            height: 200px;
            margin-left: 20px;
            background: plum;
        }
        .scroll-x {
            display: flex;
            width: auto;
            overflow-x: auto;
            -webkit-overflow-scrolling: touch
        }
        .scroll-x>.scroll-x-item {
            flex-shrink: 0;
            margin-right: .5rem
        }
    </style>

    <div class="scroll-x box">
        <div class="scroll-x-item item">1</div>
        <div class="scroll-x-item item">2</div>
        <div class="scroll-x-item item">3</div>
        <div class="scroll-x-item item">4</div>
        <div class="scroll-x-item item">5</div>
        <div class="scroll-x-item item">6</div>
    </div>

16、水平居中方法

<style>
        /* 
            方法1
                优点：兼容性较好,甚至可以兼容ie6,ie7
                缺点：child里的文字也会水平居中,可以在.child添加text-align:left;还原
        */
        /* .parent {
            width: 200px;
            height: 200px;
            background-color: aquamarine;
            text-align: center;
        }
        .child {
            display: inline-block;
        } */
        /* 
            方法2
                优点：只设置了child,ie8以上都支持
                缺点：ie6,7不支持将div换成table
        */
        /* .parent {
            width: 200px;
            height: 200px;
            background-color: aquamarine;
        }
        .child {
            display: table;
            margin: 0 auto;
        } */
        /* 
            方法3
                优点：居中元素不会对其他的产生影响
                缺点：transform属于css3内容,兼容性存在一定问题,高版本浏览器需要添加一些前缀
        */
        /* .parent {
            width: 200px;
            height: 200px;
            background-color: aquamarine;
            position: relative;
        }
        .child {
            position: absolute;
            left: 50%;
            transform: translateX(-50%);
        } */
        /* 
            方法4
                优点：简单快捷
                缺点：低版本浏览器不支持
        */
        /* .parent {
            width: 200px;
            height: 200px;
            background-color: aquamarine;
            display: flex;
        }
        .child {
            margin: 0 auto;
        } */
        /* 
            方法5
                优点：简单,设置parent即可
                缺点：低版本浏览器不支持
        */
        /* .parent {
            width: 200px;
            height: 200px;
            background-color: aquamarine;
            display: flex;
            justify-content: center;
        } */
        /* 
            方法6
                使用grid网格布局
        */
        .parent {
            width: 200px;
            height: 200px;
            background-color: aquamarine;
            display: grid;
        }
        .child {
            justify-self: center;
        }
    </style>

    <div class="parent">
        <div class="child">Jerry</div>
    </div>

17、水平垂直居中

<style>
        * {
            margin: 0;
            padding: 0;
        }
        /* 
            方法1
                absolute + 负margin值
                父元素设置相对定位,子元素设置绝对定位,margin值设置为负数
                子元素需要定高
        */
        /* .parent {
            width: 200px;
            height: 200px;
            border: 1px solid #000;
            position: relative;
        }
        .child {
            position: absolute;
            top: 50%;
            left: 50%;
            margin-left: -50px;
            margin-top: -50px;
            width: 100px;
            height: 100px;
            background-color: #f00;
        } */
        /* 
            方法2
                absolute + margin auto
                父元素设置相对定位,子元素设置绝对定位,margin值设置auto,四个方向设置为0
                子元素需要定宽高
        */
        /* .parent {
            width: 200px;
            height: 200px;
            border: 1px solid #000;
            position: relative;
        }
        .child {
            position: absolute;
            left: 0;
            right: 0;
            top: 0;
            bottom: 0;
            margin: auto;
            width: 100px;
            height: 100px;
            background-color: #f00;
        } */
        /* 
            方法3
                absolute + calc
                父元素设置为相对定位,子元素设置绝对定位,使用ralc
                子元素需要定宽高
        */
        /* .parent {
            width: 200px;
            height: 200px;
            border: 1px solid #000;
            position: relative;
        }
        .child {
            position: absolute;
            top: calc(50% - 50px);
            left: calc(50% - 50px);
            width: 100px;
            height: 100px;
            background-color: #f00;
        } */
        /* 
            方法4
                absolute + transform
                父元素设置相对定位,子元素设置绝对定位,使用transform
        */
        /* .parent {
            width: 200px;
            height: 200px;
            border: 1px solid #000;
            position: relative;
        }
        .child {
            position: absolute;
            left: 50%;
            top: 50%;
            transform: translate(-50%, -50%);
            background-color: #f00;
            width: 100px;
            height: 100px;
        } */
        /* 
            方法5
                使用flex
                子元素可以不用设置
        */
        /* .parent {
            width: 200px;
            height: 200px;
            border: 1px solid #000;
            display: flex;
            justify-content: center;
            align-items: center;
        }
        .child {
            width: 100px;
            height: 100px;
            background-color: #f00;
        } */
        /* 
            方法6
                使用grid网格布局
                子元素可以不用设置宽高
        */
        .parent {
            width: 200px;
            height: 200px;
            border: 1px solid #000;
            display: grid;
        }
        .child {
            width: 100px;
            height: 100px;
            background-color: #f00;
            align-self: center;
            justify-self: center;
        }
    </style>

    <div class="parent">
        <p class="child"></p>
    </div>

18、自定义滚动条

<style>
        /* Document scrollbar */
        ::-webkit-scrollbar {
            width: 8px;
        }
        ::-webkit-scrollbar-track {
            box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
            border-radius: 10px;
        }
        ::-webkit-scrollbar-thumb {
            border-radius: 10px;
            box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.5);
        }
        /* Scrollable element */
        .some-element::webkit-scrollbar {
        }
    </style>

    <div class="custom-scrollbar">
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Iure id exercitationem nulla qui repellat laborum vitae, molestias tempora velit natus. Quas, assumenda nisi. Quisquam enim qui iure, consequatur velit sit?</p>
    </div>

19、缓冲动画 - animation-delay 为负值

<style type="text/css">
        /*
            animation-delay
                定义动画何时开始
                默认为0 - 立即开始执行动画
                正值 - 延迟指定时间后,开始执行动画
                负值 - 立即执行,但跳过指定时间后进入动画
        */
        body{
          color: #fff;
          background: #fff;
        }
        h1{
            font-size: 14px;
            font-family: "Microsoft Yahei";
            text-align: center;
        }
        .spinner{
            width: 800px;
            height: 50px;
            margin: 100px auto;
            text-align: center;
        }
        .spinner>div{
            width: 6px;
            height: 100%;
            display: inline-block;
            background: green;
            -webkit-animation:strechdelay 1.2s infinite ease-in-out;
        }
        .spinner .line2{
          -webkit-animation-delay:-1.1s;
        }
        .spinner .line3{
          -webkit-animation-delay:-1.0s;
        }
        .spinner .line4{
          -webkit-animation-delay:-0.9s;
        }
        .spinner .line5{
          -webkit-animation-delay:-0.8s;
        }
        @-webkit-keyframes strechdelay{
             0%,40%,100%{
            -webkit-transform:scaleY(0.4);
            }
             20%{
                -webkit-transform:scaleY(1);
            }
        }
    </style>

    <!-- 缓冲动画 -->
    <div class="spinner">
        <div class="line1"></div>
        <div class="line2"></div>
        <div class="line3"></div>
        <div class="line4"></div>
        <div class="line5"></div>
    </div>

20、缓冲动画 - 妙用 border 颜色

<style type="text/css">
        body{
          color: #fff;
          background: #222;
        }
        h1{
            font-size: 14px;
            font-family: "Microsoft Yahei";
            text-align: center;
        }
        .spinner{
            width: 100px;
            height: 100px;
            border-radius: 100%;
            margin: 100px auto;
            border:10px solid rgba(255,255,255,0.2);
            border-left-color:#fff; 
            -webkit-animation:start 1.2s infinite linear;
        }
        @-webkit-keyframes start{
                from{
                    transform: rotate(0deg);
                }
                to{
                    transform: rotate(360deg);
                }
    
        }
    </style>

    <div class="spinner"></div>

21、缓冲动画 - 气泡 loading 效果

<style type="text/css">
        body{
          color: #222;
        }
        h1{
            font-size: 14px;
            font-family: "Microsoft Yahei";
            text-align: center;
        }
        .spinner{
            width: 40px;
            height: 40px;
            border-radius: 100%;
            background-color: green;
            margin: 100px auto;
            -webkit-animation:fadeOut 1s infinite ease-in-out;
        }
        @-webkit-keyframes fadeOut{
            from{
                transform: scale(0);
            }
            to{
                transform: scale(1);
                opacity: 0;
            }
        }
    </style>

    <div class="spinner"></div>

22、2 倍/3 倍图 css 技巧
/_普通显示屏_/
.css{
background-image: url(img*1x.png);
}
/* 高清显示屏(设备像素比例大于等于 2)使用 2 倍图 _/
@media only screen and (-webkit-min-device-pixel-ratio:2){
.css{
background-image: url(img_2x.png);
}
}
/_ 高清显示屏(设备像素比例大于等于 3)使用 3 倍图 \_/
@media only screen and (-webkit-min-device-pixel-ratio:3){
.css{
background-image: url(img_3x.png);
}
}
23、css 图形画法 - 扇形

<style>
        #sx{
            width: 0;
            height: 0;
            border-left: 70px solid transparent;
            border-right: 70px solid transparent;
            border-top: 100px solid red;
            border-radius: 50%;
        }
    </style>

    <div id="sx"></div>

24、css 图形画法 - 梯形

<style>
        #tx {
            width: 100px;
            height: 0;
            border-left: 50px solid transparent;
            border-right: 50px solid transparent;
            border-bottom: 100px solid red;
        }
    </style>

    <div id="tx"></div>

25、css 图形画法 - 平行四边形

<style>
        #sbx {
            width: 150px;
            height: 100px;
            transform: skew(20deg);
            background-color: red;
        }
    </style>

    <div id="sbx"></div>

26、css 图形画法 - 五边形

<style>
        #wbx{
            position: relative;
            width: 54px;
            box-sizing: content-box;
            border-width: 50px 18px 0;
            border-style: solid;
            border-color: red transparent;
            margin-top: 50px;
        }
        #wbx:before {
            content: "";
            position: absolute;
            width: 0;
            height: 0;
            top: -85px;
            left: -18px;
            border-width: 0 45px 35px;
            border-style: solid;
            border-color: transparent transparent red;
        }
    </style>

    <div id="wbx"></div>

27、css 图形画法 - 六边形

<style>
        #hexagon {
            width: 100px;
            height: 55px;
            background: red;
            position: relative;
            margin-top: 50px;
        }
        #hexagon:before {
            content: "";
            position: absolute;
            top: -25px;
            left: 0;
            width: 0;
            height: 0;
            border-left: 50px solid transparent;
            border-right: 50px solid transparent;
            border-bottom: 25px solid red;
        }
        #hexagon:after {
            content: "";
            position: absolute;
            bottom: -25px;
            left: 0;
            width: 0;
            height: 0;
            border-left: 50px solid transparent;
            border-right: 50px solid transparent;
            border-top: 25px solid red;
        }
    </style>

    <div id="hexagon"></div>

28、css 图形画法 - 返回箭头

<style>
        #curvedarrow {
            position: relative;
            width: 0;
            height: 0;
            border-top: 9px solid transparent;
            border-right: 9px solid red;
            transform: rotate(10deg);
        }
        #curvedarrow:after {
            content: "";
            position: absolute;
            border: 0 solid transparent;
            border-top: 3px solid red;
            border-radius: 20px 0 0 0;
            top: -12px;
            left: -9px;
            width: 12px;
            height: 12px;
            transform: rotate(45deg);
        }
    </style>

    <div id="curvedarrow"></div>

29、css 图形画法 - 五角星

<style>
        #star-five {
            margin: 50px 0;
            position: relative;
            display: block;
            color: red;
            width: 0px;
            height: 0px;
            border-right: 100px solid transparent;
            border-bottom: 70px solid red;
            border-left: 100px solid transparent;
            transform: rotate(35deg);
        }
        #star-five:before {
            border-bottom: 80px solid red;
            border-left: 30px solid transparent;
            border-right: 30px solid transparent;
            position: absolute;
            height: 0;
            width: 0;
            top: -45px;
            left: -65px;
            display: block;
            content: '';
            transform: rotate(-35deg);
        }
        #star-five:after {
            position: absolute;
            display: block;
            color: red;
            top: 3px;
            left: -105px;
            width: 0px;
            height: 0px;
            border-right: 100px solid transparent;
            border-bottom: 70px solid red;
            border-left: 100px solid transparent;
            transform: rotate(-70deg);
            content: '';
        }
    </style>

    <div id="star-five"></div>

30、css 图形画法 - 心形

<style>
        #heart {
            position: relative;
            width: 100px;
            height: 90px;
        }
        #heart:before,
        #heart:after {
            position: absolute;
            content: "";
            left: 50px;
            top: 0;
            width: 50px;
            height: 80px;
            background: red;
            border-radius: 50px 50px 0 0;
            transform: rotate(-45deg);
            transform-origin: 0 100%;
        }
        #heart:after {
            left: 0;
            transform: rotate(45deg);
            transform-origin: 100% 100%;
        }
    </style>

    <div id="heart"></div>

31、css 图形画法 - 结形

<style>
        #infinity {
            position: relative;
            width: 212px;
            height: 100px;
            box-sizing: content-box;
        }
        #infinity:before,
        #infinity:after {
            content: "";
            box-sizing: content-box;
            position: absolute;
            top: 0;
            left: 0;
            width: 60px;
            height: 60px;
            border: 20px solid red;
            border-radius: 50px 50px 0 50px;
            transform: rotate(-45deg);
        }
        #infinity:after {
            left: auto;
            right: 0;
            border-radius: 50px 50px 50px 0;
            transform: rotate(45deg);
        }
    </style>

    <div id="infinity"></div>

32、同级变淡效果

<style>
        span {
            padding: 0 1rem;
            transition: opacity 0.2s;
        }
        .sibling-fade:hover span:not(:hover) {
            opacity: 0.5;
        }
    </style>

    <div class="sibling-fade">
        <span>Item 1</span>
        <span>Item 2</span>
        <span>Item 3</span>
        <span>Item 4</span>
        <span>Item 5</span>
        <span>Item 6</span>
    </div>

33、环形旋转

<style>
        @keyframes donut-spin {
            0% {
                transform: rotate(0deg);
            }
            100% {
                transform: rotate(360deg);
            }
        }
        .donut {
            display: inline-block;
            border: 4px solid rgba(0, 0, 0, 0.1);
            border-left-color: #7983ff;
            border-radius: 50%;
            width: 30px;
            height: 30px;
            animation: donut-spin 1.2s linear infinite;
        }
    </style>

    <div class="donut"></div>

34、文本省略
/_文本-省略号 截断_/
.ellipsis{
word-wrap: normal;/_ for IE _/
-webkit-text-overflow: ellipsis;
-moz-text-overflow: ellipsis;
-o-text-overflow: ellipsis;
text-overflow: ellipsis;
white-space: nowrap;
overflow: hidden;
}
/_多行位置截断_/
.line-clamp {
overflow : hidden;
-webkit-text-overflow: ellipsis;
-moz-text-overflow: ellipsis;
-o-text-overflow: ellipsis;
text-overflow: ellipsis;
display: -webkit-box;
-webkit-line-clamp: 2;/_行数_/
-webkit-box-orient: vertical;
}
35、透明度优化
.opa{
opacity: .2;
-ms-filter: progid: DXImageTransform.Microsoft.Alpha(Opacity = 20);
filter: alpha(opacity = 20);
-moz-opacity: .2;
-khtml-opacity: .2;
}
36、input-placeholder 样式设置
/_ WebKit browsers _/
::-webkit-input-placeholder {
color: #ababab;
}
/_ Mozilla Firefox 4 to 18 _/
:-moz-placeholder {
color: #ababab;
opacity: 1;
}
/_ Mozilla Firefox 19+ _/
::-moz-placeholder {
color: #ababab;
opacity: 1;
}
/_ Internet Explorer 10+ _/
:-ms-input-placeholder {
color: #ababab;
}
37、1 像素优化
.retainbt,.retainbb,.retainbl,.retainbr,.retainb { position:relative; }
.retainbt:before,.retainbb:after {pointer-events: none;position: absolute;content: ""; height: 1px; background: rgba(32,35,37,.24);left: 0;right: 0}
.retainbt:before {top: 0}
.retainbb:after {bottom: 0}
.retainbl:before,.retainbr:after {pointer-events: none;position: absolute;content: ""; width: 1px; background: rgba(32,35,37,.24); top: 0; bottom: 0}
.retainbl:before {left: 0}
.retainbr:after {right: 0}
.retainb:after {position: absolute;content: "";top: 0;left: 0; -webkit-box-sizing: border-box; box-sizing: border-box; width: 100%; height: 100%; border: 1px solid rgba(32,35,37,.24); pointer-events: none}
@media (-webkit-min-device-pixel-ratio:1.5),(min-device-pixel-ratio:1.5),(min-resolution: 144dpi),(min-resolution:1.5dppx) {
.retainbt:before,.retainbb:after {-webkit-transform:scaleY(.5);transform: scaleY(.5) }
.retainbl:before,.retainbr:after {-webkit-transform: scaleX(.5); transform: scaleX(.5) }
.retainb:after { width: 200%; height: 200%;-webkit-transform: scale(.5); transform: scale(.5) }
.retainbt:before,.retainbl:before,.retainb:after {-webkit-transform-origin: 0 0;transform-origin: 0 0}
.retainbb:after,.retainbr:after { -webkit-transform-origin: 100% 100%;transform-origin: 100% 100%}
}
@media (-webkit-device-pixel-ratio:1.5) {
.retainbt:before,.retainbb:after { -webkit-transform: scaleY(.6666); transform: scaleY(.6666) }
.retainbl:before,.retainbr:after {-webkit-transform: scaleX(.6666); transform: scaleX(.6666)}
.retainb:after {width: 150%; height: 150%;-webkit-transform: scale(.6666); transform: scale(.6666) }
}
@media (-webkit-device-pixel-ratio:3) {
.retainbt:before,.retainbb:after { -webkit-transform: scaleY(.3333); transform: scaleY(.3333)}
.retainbl:before,.retainbr:after { -webkit-transform: scaleX(.3333); transform: scaleX(.3333)}
.retainb:after {width: 300%;height: 300%; -webkit-transform: scale(.3333);transform: scale(.3333)}
}
38、消除 transition 闪屏
.transition-css{
/_设置内嵌的元素在 3D 空间如何呈现：保留 3D_/
-webkit-transform-style: preserve-3d;
/_（设置进行转换的元素的背面在面对用户时是否可见：隐藏）_/
-webkit-backface-visibility: hidden;
}
39、开启硬件加速 / 解决页面闪白 / 保证动画流畅
.run-css{
-webkit-transform: translate3d(0, 0, 0);
-moz-transform: translate3d(0, 0, 0);
-ms-transform: translate3d(0, 0, 0);
transform: translate3d(0, 0, 0);
}
40、图像灰度
img {
filter: gray;
-webkit-filter: grayscale(1);
}
41、长文本自动换行
pre {
white-space: pre-line;
word-wrap: break-word;
}
42、css 实现省略号动画
.point:after {
overflow: hidden;
display: inline-block;
vertical-align: bottom;
animation: ellipsis 2s infinite;
content: "\2026";
}
@keyframes ellipsis {
from {
width: 2px;
}
to {
width: 15px;
}
}
43、清除浮动
.clearfix:before, .container:after { content: ""; display: table; }
.clearfix:after { clear: both; }
.clearfix { zoom: 1; }
44、css 元素透明
.transparent {
filter: alpha(opacity=50);
-khtml-opacity: 0.5;
-moz-opacity: 0.5;  
 opacity: 0.5;  
}
45、通用媒体查询
@media only screen and (min-device-width : 320px) and (max-device-width : 480px) {
/_ Styles _/
}
@media only screen and (min-width : 321px) {
/_ Styles _/
}
@media only screen and (max-width : 320px) {
/_ Styles _/
}
/_ iPad _/
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) {
/_ Styles _/
}
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : landscape) {
/_ Styles _/
}
@media only screen and (min-device-width : 768px) and (max-device-width : 1024px) and (orientation : portrait) {
/_ Styles _/
}
/_ 桌面 _/
@media only screen and (min-width : 1224px) {
/_ Styles _/
}
@media only screen and (min-width : 1824px) {
/_ Styles _/
}
@media only screen and (-webkit-min-device-pixel-ratio:1.5), only screen and (min-device-pixel-ratio:1.5) {
/_ Styles _/
}
46、全屏背景图
html {
background: url('bg.jpg') no-repeat center center fixed;
background-size: cover;
}
47、css3 渐变模板
.bg {
background: #629721;
background-image: -webkit-gradient(linear, left top, left bottom, from(#83b842), to(#629721));
background-image: linear-gradient(top, #83b842, #629721);
}
48、@font-face 使用
@font-face {
font-family: 'MyWebFont';
src: url('webfont.eot');
src: url('webfont.eot?#iefix')
url('webfont.woff') format('woff'),
url('webfont.ttf') format('truetype'),
url('webfont.svg#svgFontName') format('svg');
}
body {
font-family: 'MyWebFont', Arial, sans-serif;
}
49、css3 阴影
/_ 内盒阴影 _/
.div {
box-shadow: inset 2px 0 4px #000;
}
/_ 外盒阴影 _/
.div {
box-shadow: 0 2px 2px -2px rgba(0, 0, 0, 0.52);
}
50、css3 对话气泡
.line {
background-color: #ededed;
border: 2px solid #666;
font-size: 35px;
line-height: 1.3em;
margin: 10px auto;
padding: 10px;
position: relative;
text-align: center;
width: 300px;
border-radius: 20px;
box-shadow: 0 0 5px #888;
}
.chat-bubble-arrow-border {
border-color: #666 transparent transparent transparent;
border-style: solid;
border-width: 20px;
height: 0;
width: 0;
position: absolute;
bottom: -42px;
left: 30px;
}
.chat-bubble-arrow {
border-color: #ededed transparent transparent transparent;
border-style: solid;
border-width: 20px;
height: 0;
width: 0;
position: absolute;
bottom: -39px;
left: 30px;
}
51、css3 悬浮提示文本
a {
border-bottom:1px solid #bbb;
color:#666;
display:inline-block;
position:relative;
text-decoration:none;
}
a:hover,
a:focus {
color:#36c;
}
a:active {
top:1px;
}
a[data-tooltip]:after {
border-top: 8px solid #222;
border-top: 8px solid hsla(0,0%,0%,.85);
border-left: 8px solid transparent;
border-right: 8px solid transparent;
content: "";
display: none;
height: 0;
width: 0;
left: 25%;
position: absolute;
}
a[data-tooltip]:before {
background: #222;
background: hsla(0,0%,0%,.85);
color: #f6f6f6;
content: attr(data-tooltip);
display: none;
font-family: sans-serif;
font-size: 14px;
height: 32px;
left: 0;
line-height: 32px;
padding: 0 15px;
position: absolute;
text-shadow: 0 1px 1px hsla(0,0%,0%,1);
white-space: nowrap;
-webkit-border-radius: 5px;
-moz-border-radius: 5px;
-o-border-radius: 5px;
border-radius: 5px;
}
a[data-tooltip]:hover:after {
display: block;
top: -9px;
}
a[data-tooltip]:hover:before {
display: block;
top: -41px;
}
a[data-tooltip]:active:after {
top: -10px;
}
a[data-tooltip]:active:before {
top: -42px;
}
52、论文页面的卷曲效果
ul.box {
position: relative;
z-index: 1;
overflow: hidden;
list-style: none;
margin: 0;
padding: 0;
}
ul.box li {
position: relative;
float: left;
width: 250px;
height: 150px;
padding: 0;
border: 1px solid #efefef;
margin: 0 30px 30px 0;
background: #fff;
-webkit-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.27), 0 0 40px rgba(0, 0, 0, 0.06) inset;
-moz-box-shadow: 0 1px 4px rgba(0, 0, 0, 0.27), 0 0 40px rgba(0, 0, 0, 0.06) inset;
box-shadow: 0 1px 4px rgba(0, 0, 0, 0.27), 0 0 40px rgba(0, 0, 0, 0.06) inset;
}
ul.box li:before,
ul.box li:after {
content: '';
z-index: -1;
position: absolute;
left: 10px;
bottom: 10px;
width: 70%;
max-width: 300px; /_ avoid rotation causing ugly appearance at large container widths _/
max-height: 100px;
height: 55%;
-webkit-box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
-moz-box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
-webkit-transform: skew(-15deg) rotate(-6deg);
-moz-transform: skew(-15deg) rotate(-6deg);
-ms-transform: skew(-15deg) rotate(-6deg);
-o-transform: skew(-15deg) rotate(-6deg);
transform: skew(-15deg) rotate(-6deg);
}
ul.box li:after {
left: auto;
right: 10px;
-webkit-transform: skew(15deg) rotate(6deg);
-moz-transform: skew(15deg) rotate(6deg);
-ms-transform: skew(15deg) rotate(6deg);
-o-transform: skew(15deg) rotate(6deg);
transform: skew(15deg) rotate(6deg);
}
53、max-width 防止图片撑破容器
img{
max-width：100%；
display：inline-block;
}
54、css 优化、提高性能的方法
加载性能
（1）css 压缩：将写好的 css 进行打包压缩，可以减少很多体积
（2）css 单一样式：margin-left，margin-bottom 会比 margin:12px 0 12px 0 执行效率更高
（3）减少使用@import，建议使用 link，因为后者是在页面加载时一起加载，前者是等待页面加载完成之后再进行加载
选择器性能
