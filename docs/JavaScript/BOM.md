# BOM
## 1.属性
* navigator 浏览器信息
* location 浏览器定位和导航
* history 窗口浏览器历史
* screen 屏幕信息
### navigator
```javascript
window.navigator.platform//win32
window.navigator.userAgent//浏览器的内核信息
```
### location
```javascript
 //表示完整路径，也可以修改这个属性来实现浏览器跳转
window.location.href
```
方法：
```javascript
window.location.assign(url)//跳转页面记录历史
window.location.replace(url)//跳转页面不记录历史
window.location.reload(url)//重载当前页面
```
### history
属性：length

方法：
```javascript
window.history.back(n);//传入正数后退n步
window.history.forward(n);//传入负整数，前进n步
window.history.go(n);//传入整数，正数前进，负数倒退
```
### screen
属性：
availHeight
availWith
加了avail的是可用屏幕，没加的是显示器的属性

## 2.方法

### 对话框

* alert()
* confirm()
* prompt

### 计时器

* setTimeout()
* setInterval()

### 窗口操作

* open()打开新窗口
* close()关闭窗口

## 事件

### 属性

* load  文档和所有图片加载完毕
* unload  离开当前文档时
* beforeunload  与unload类似，但它提供询问用户是否决定离开的机会
* resize 拖动改变浏览器窗口大小时
* scroll 拖动滚动浏览器时
