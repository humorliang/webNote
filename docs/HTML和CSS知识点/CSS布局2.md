# 布局结局方案

    负边距,flex,table;

※负边距：边距用于截流，边距的正负决定拦截线在对应边框线的哪一边（上下左右）。截流之后元素动不动，往哪里动，还是要看它本身处于哪一种流中。

[具体示例](example/html/margin.html)

## 居中布局

### 1.水平居中
父元素和子元素宽度未知。

方法一：flex + justify-content

[示例](example/html/layout2_cen_1.html)

justify-content设置弹性盒子元素在主轴（横轴）方向上的对齐方式。
```css
    justify-content：flex-start | flex-end | center | space-between | space-around
    flex-start： 弹性盒子元素将向行起始位置对齐。 
    flex-end： 弹性盒子元素将向行结束位置对齐。
    center： 弹性盒子元素将向行中间位置对齐。
    space-between： 弹性盒子元素会平均地分布在行里。
    space-around： 弹性盒子元素会平均地分布在行里，两端保留子元素与子元素之间间距大小的一半。
```
方法二:absolute + transform

[示例](example/html/layout2_cen_1.2.html)

原理:left:50%;在子元素的左侧添加一段距离，父元素宽度的50%。
translateX(-50%)此时的百分数参照物为本身宽度，所以向自身宽度的50%，就居中了。

方法三:inline-block + text-align

[示例](example/html/layout2_cen_1.3.html)

注：父元素设置了text-align:center;子元素可继承导致文字居中，导致文字居中，
则有时在子元素中加上text-align:left;来恢复样式；

方法四:table + margin

[示例](example/html/layout2_cen_1.4.html)

table特点：宽度为内容宽度的块状元素，所以可以用margin:0 auto;居中。

### 2.垂直居中
子元素高度未知

方法一：flex + align-items

[示例](example/html/layout_ver_2.1.html)

```css
    align-items：flex-start | flex-end | center | baseline | stretch
    flex-start： 弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴起始边界。 
    flex-end： 弹性盒子元素的侧轴（纵轴）起始位置的边界紧靠住该行的侧轴结束边界。 
    center： 弹性盒子元素在该行的侧轴（纵轴）上居中放置。 
    baseline： 如弹性盒子元素的行内轴与侧轴为同一条，则该值与'flex-start'等效。
    stretch： 如果指定侧轴大小的属性值为'auto'，则其值会使项目的边距盒的尺寸尽可能接近所在行的尺寸，但同时会遵照'min/max-width/height'属性的限制。 
```
方法二：absolute + transform

[示例](example/html/layout_ver_2.2.html)


方法三：table-cell + vertical-align

[示例](example/html/layout_ver_2.3.html)

vertical-align可以作用在inline元素,inline-table元素，以及table-cell元素上。

### 3.水平垂直居中
父元素和子元素宽高未知。
方法一：flex + justify-content + align-items

[示例](example/html/layout2_cenVer_1.1.html)


方法二：absolute + transform

[示例](example/html/layout2_cenVer_1.2.html)


方法三：[text-align + inline-block] + [table-cell + vertical-align]

[示例](example/html/layout2_cenVer_1.3.html)

## 多列布局

### 1.一列定宽 + 一列自适应

方法一：float + margin

[示例](example/html/layout2_manyLy_1_1.1.html)


方法二：（改进版法1）float + margin +(fix)

[示例](example/html/layout2_manyLy_1_1.2.html)

利用负边距进行布局和position：relative

    纵云梯（引用张鑫旭博客）
    position:relative虽是凡夫肉体，但是却有只有神魔才有的“纵云梯”技能，亦称“垂直升空”的本事。借助z-index这把御剑，就能直接腾空9万里，越于其他凡人之上。且其纵云梯的技能和纯魔鬼血统的position:absolute的技能是平起平坐的。如果两者纵云梯的高度一致（z-index值一样），谁后发制人谁就是上面显示。

方法三：float + overflow

[示例](example/html/layout2_manyLy_1_1.3.html)

原理：设置overflow：hidden;触发BFC模式，而bfc模式内部布局不会受浮动影响,不会围绕左侧，而是跑到left右边去

方法四：table

[示例](example/html/layout2_manyLy_1_1.4.html)

```css
    父元素： display:table;
            table-layout:fixed;//加速table渲染，实现布局优先
    子元素：display:table-cell;
```
方法五：flex

[示例](example/html/layout2_manyLy_1_1.5.html)


### 2.多列定宽+一列自适应
同上再加一列定宽即可。

[示例](example/html/layout2_manyLy_2_1.1.html)


### 3.不定宽+一列自适应

    3.1 可以随意更改宽度，同时不需要更改其他样式，也可以做到两列自适应。
    3.2 或不设置宽度，由里面的子元素宽度决定
方法一：float+overflow

[示例](example/html/layout2_manyLy_3_1.1.html)

方法二：table

[示例](example/html/layout2_manyLy_3_1.2.html)

方法三：flex

[示例](example/html/layout2_manyLy_3_1.3.html)

### 4.两列不定宽+一列自适应

    方法同上再加一列不定宽即可。

[示例](example/html/layout2_manyLy_4_1.1.html)

### 5.等分布局

    C+G=4*(W+G) 假设G=10px
方法一：float

[示例](example/html/layout2_manyLy_5_1.1.html)

方法二：table

    注：因为table的width默认是随内容的宽度变化，所以需手动设置width：100%；又因设置宽度的元素没法用margin设置负值的方法来增加宽度，所以需要在外面加一个父盒子。可用chrome调试工具查看设置父元素width:100%和不设置时实际的宽度来理解。

[示例](example/html/layout2_manyLy_5_1.2.html)

方法三：flex

[示例](example/html/layout2_manyLy_5_1.3.html)

### 6.一列定宽+一列自适应（当其中较高的一列变化，另一列同步变化）

    右侧变高，左侧高度随之变化：

方法一：table
table的列之间本身具有等高性。

[示例](example/html/layout2_manyLy_6_1.1.html)

方法二：flex
flex本身具有等高性，因align-items默认为stretch,即交叉轴默认拉满整个容器。

[示例](example/html/layout2_manyLy_6_1.2.html)

方法三：float + overflow
解析：left的高度实际上并没有改变，而是利用背景变高，实现的一种伪等高。

[示例](example/html/layout2_manyLy_6_1.3.html)

### 7.全等四宫格
方法一：flex

[flex](example/html/layout2_manyLy_7_1.1.html)

方法二：float

[示例](example/html/layout2_manyLy_7_1.2.html)

方法三：table

[示例](example/html/layout2_manyLy_7_1.3.html)

## 全屏布局
### 1.定宽（px）+ 自适应

    只有主内容区随内容滚动。

方法一：position(不适用布局混乱)
```css
//一点奇技淫巧
left:0;right:0;//实用的设置，可以自动占满整行
```

方法二：flex

### 2.百分比定宽(%) + 自适应

    把上面的px定宽写成百分比即可。
方法一：position

方法二：flex

### 3.自适应+自适应

方法一：flex

方法二：Grid(W3c还在草案中)

## 圣杯布局（西方称呼）= 双飞翼布局（淘宝UED）

    三栏布局，两栏固定，一栏自适应
    思路解析：
        1.三列都左浮动。自适应的宽度为100%；
        2.最外层容器设置为overflow触发BFC
        3.左侧盒子设置右负边距，让middle盒子上来,右侧的盒子设置左负边距为自身的宽度，
        则右侧的盒子就可以上来了。
        4.在包裹层盒子设置左右等有两边盒子宽度的内边距，然后再对两个盒子进行相对定位
        分别向两边移动宽度的距离（为了使自适应的内容不被覆盖，处于安全空间）
        
[示例](example/html/layout2_double.html)


