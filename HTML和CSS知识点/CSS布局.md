## 导航条垂直居中

导航条nav 从左到右分为nav-left，nav-mid，nav-mid

1.0 从左到右依次排列，且全部垂直居中
```css
    全部设置float：left
    设置父元素的line-hight等于height就可以
```
1.1 ul>li>a构成的导航条内部导航水平居中：
```css
    ul设置 :text-align:center;
    li和a都设置 : display:inline-block;
```
[示例](example/html/layout_nav_1.html)

## 清除父元素的浮动

    假设父元素为warp，未设高度，含有三个子元素left mid right,三列布局
    三个元素都float：left，并设置合理的宽度，假设为30%，由于子元素
    脱离文档流父元素无法撑开，缩成一条，需要清除浮动，此时用clear：both；不好用
    因为只适合左侧和右侧的浮动。

### 1.overflow：hidden

overflow不是默认的visible，就会触发BFC，而BFC有自己的布局方式规则：

    内部的Box会在垂直方向，一个接一个地放置。
    Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠 每个元素的margin box的左边，
    与包含块border box的左边相接触(对于从左往右的格式化，否则相反)。即使存在浮动也是如此。 BFC的区域不会与float
    box重叠。 BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此。
[示例](example/html/clear_float_1.html)

#### 计算BFC的高度时，浮动元素也参与计算

注意最后一条，因为计算BFC高度时，浮动元素也参与计算，所以父元素的高度被撑开。而这也正符合包含块未设置高度（height: auto;）时的裁切准则。因为包含块高度（height: auto;），所以永远不会出现内容超出包含块的情况，因此overflow:hidden应用后，需要计算内部所有元素高度才能进行裁切。

补充下哪些元素会生成BFC：

        根元素 
        float属性不为none 
        position为absolute或fixed 
        display为inline-block,table-cell, table-caption, flex, inline-flex 
        overflow不为visible

### 2.空div标签法
[示例](example/html/clear_float_2.html)

#### 在父元素的后面加一个空的div标签，并设置clear：both;

### 3.:after伪元素法
[示例](example/html/clear_float_3.html)

#### 在父元素上加一个clearfix类：
```css
    .clearfix:after{
        content:"反正你也看不见";
        display:block;
        clear:both;
        //上面是清除浮动用的
        height:0;
        overflow:hidden;
        visibility:hidden;//他与display的区别为占不占位置
        //上面的是为了看不见东西的
    }
```
## CSS Reset
1.作用

    1.1 清除浏览器默认样式
    1.2 全局样式定义
2.注意点

    2.1 项目开发初期定好
    2.2 reset.css放在第一位引入
    2.3 不同项目reset.css不一样
3.table合并边框间距
```css
    table{
        border-collapse:collapse;//合并边框
        border-spacing:0;//边框间距，当上面值为seperate时生效
    }
```
4.一些元素的默认样式的清除和设定
```css
    caption,th{
        text-align:left;
        font-weight:normal;
        }
    html,body,fieldset,img,iframe,abbr{
        border:0;
        }
     i,cite,em,var,address,dfn{
         font-style:normal;
        }
    [hidefocus],summary{
        outline:0;
        }
    li{
        list-style:none;
        }
    h1,h2,h3,h4,h5,h6,small{
        font-size:100%;
        }
    sup,sub{
        font-size:83%;
        }
    pre,code,kbd,samp{
        font-family:inherit;
        }
    q:before,q:after{
        content:none;
        }
    textarea{
        overflow:auto;resize:none;
        }
    label,summary{
        cursor:default;
        }
    a,button{
        cursor:pointer;
        }
    h1,h2,h3,h4,h5,h6,em,strong,b{
        font-weight:normal;
        }
    del,ins,u,s,a,a:hover{
        text-decoration:none;
        }
    body,textarea,input,button,select,keygen,legend{
        font:12px/1.14 arial,simsun;color:#333;outline:0;
        }
    body{
        background:#fff;
        }
    a,a:hover{
        color:#333;
        }
```



