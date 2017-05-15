# 动画
三要素：定时器、对象、属性
* setInterval
* setTimeout
* requestAnimationFrame()
```javascript
var intervalId=setInterval(fn,delay);//delay触发的时间间隔
clearInterval(intervalId);//清除定时器

var timeoutId=setTimeout(fn,delay);//delay不写默认为0，立即执行。
clearTimeout(timeoutId);//关闭
```
不同：setTimeout只执行一次，setInterval会重复执行

```javascript
var rAquId=requestAnimationFrame(fn);
cancelAnimationFrame(rAquId);
```
间隔时间不由用户决定，是显示屏的刷新频率控制，大概1s刷新60次。
### 动画基本
* 形变
* 位移
* 旋转
* 透明度
一切复杂的东西都是由简单的构成的，万丈高楼平地起。