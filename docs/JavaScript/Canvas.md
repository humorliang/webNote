# Canvas
在canvas标签中指定宽高。
```html
<canvas id="myCanvas" width="300" height="280" >你的浏览器不支持canvas</canvas>
```
1. 找到 <canvas> 元素:
```javascript
var c=document.getElementById("myCanvas"); 
```
2. 创建 context 对象(获取渲染上下文对象)
```javascript
var ctx=c.getContext("2d"); 
```
3. getContext("2d") 对象是内建的 HTML5 对象，拥有多种绘制路径、矩形、圆形、字符以及添加图像的方法。
```javascript
ctx.fillRect(0,0,150,75); 
```
4. 设置fillStyle属性可以是CSS颜色，渐变，或图案。
```javascript
ctx.fillStyle="#FF0000";
```
### Canvas 坐标
canvas 是一个二维网格。
canvas 的左上角坐标为 (0,0)
上面的 fillRect 方法拥有参数 (0,0,150,75)。
意思是：在画布上绘制 150x75 的矩形，从左上角开始 (0,0)。


### Canvas - 路径
在Canvas上画线，我们将使用以下两种方法：
- moveTo(x,y) 定义线条开始坐标 
- lineTo(x,y) 定义线条结束坐标 
绘制线条我们必须使用到 "ink" 的方法，就像stroke().

```javascript
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.moveTo(0,0);
ctx.lineTo(200,100);
ctx.stroke();
```
### 在canvas中绘制圆形, 我们将使用以下方法:
arc(x,y,r,start,stop) 
实际上我们在绘制圆形时使用了 "ink" 的方法, 比如 stroke() 或者 fill().
```javascript
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.beginPath();
ctx.arc(95,50,40,0,2*Math.PI);
ctx.stroke();
```
### 使用 canvas 绘制文本，重要的属性和方法如下：

font - 定义字体 
fillText(text,x,y) - 在canvas上填充"filled" 的文本 
strokeText(text,x,y) - 在canvas上填充的文本(no fill) 
使用 fillText():

```javascript
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.font="30px Arial";
ctx.fillText("Hello World",10,50);

//使用 strokeText():
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.font="30px Arial";
ctx.strokeText("Hello World",10,50);
```
### Canvas - 渐变
以下有两种不同的方式来设置Canvas渐变:

* createLinearGradient(x,y,x1,y1) - 创建线条梯度 
* createRadialGradient(x,y,r,x1,y1,r1) - 创建一个径向/圆梯度 
当我们使用渐变对象，必须使用两种或两种以上的停止颜色。

addColorStop()方法指定颜色停止，参数使用坐标来描述，可以是0至1.

使用渐变，设置设置fillStyle或strokeStyle的值为梯度，然后绘制形状，如矩形，文本，或一条线。


```javascript
//使用 createLinearGradient():
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");

//  创建渐变
var grd=ctx.createLinearGradient(0,0,200,0);
grd.addColorStop(0,"red");
grd.addColorStop(1,"white");

// 用渐变填充
ctx.fillStyle=grd;
ctx.fillRect(10,10,150,80);

//使用 createRadialGradient():
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");

// 创建渐变
var grd=ctx.createRadialGradient(75,50,5,90,60,100);
grd.addColorStop(0,"red");
grd.addColorStop(1,"white");

// 用渐变填充
ctx.fillStyle=grd;
ctx.fillRect(10,10,150,80);
```
### Canvas - 图像
把一幅图像放置到画布上, 使用以下方法:

drawImage(image,x,y)
```javascript
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
var img=document.getElementById("scream");
ctx.drawImage(img,10,10);   
```
[mdnCanvas示例]()

