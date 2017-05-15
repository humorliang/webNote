# 表单操作
## 示例：
服务器接收的信息：
请求的url:http://www.xx.cn/menu
格式：application/x-www-form-urlencoded
参数：name-value
```html
<form action="post" action="http://xxx.xx.x/menu"
enctype="application/x-www-form-urlencoded">
<label>用户名：<input type="text" name="user"></label>
<div>
性别：
<label>男：<input type="radio" name="sex" value="man"></label>
<label>女：<input type="radio" name="sex" value="woman"></label>
</div>
</form>
添加required属性：<input required>,可以在submit时检测出没有填写的表单
并给用户提示。
```
## 表单元素
### 1.form元素
```html
<form novalidate
      name="user"
      target="_blank"
      method="post"
      autocomplete="off"
      accept-charset="UTF-8"
      action="url"
      enctype="application/x-www-form-urlencoded">           
</form> 
name属性有助于拿到form表单：
var userForm=document.forms.user;
```
### 2.form的接口
reset()
可重置元素：input、keygen、output、select、textarea、
阻止reset事件的默认行为，可选择取消重置。
还可以用于文件选择器input type="file"已选中的文件的删除。

### 3.select的属性和方法
```javascript
select.name;
select.value;
select.multiple;
select.options;
select.selectedOptions;
select.selectedIndex;
select.add(element.beforeElement)
select.remove(index);

optgroup.disabled;
optgroup.label;

option.disabled;
option.label;
option.value;
option.text;
option.index;
option.selected;
option.defaultSelected;

```
#### 创建选项：
```javascript
//示例：
document.createElement('option');
//等于
new Option();
//语法：
new Option(text[,value[,defaultSelected[,selected]]]);
```
#### 添加选项
```javascript
//示例
element.insertAdjacentHTML("beforeBegin",option);
select.add(option,before);
//语法
selectObject.add(optionElement,beforeElement);
element.insertAdjacentHTML(position,element);
```
#### 删除选项
```javascript
//示例
opt.parentNode.removeChild(opt)
select.remove(2);
//语法
select.remove(index);
```
[级联下拉器]()

## 表单验证
可验证表单：button input select textarea
element的属性方法：

* willValidite  可用于判断元素是否会被验证
* checkValidity 验证某个元素
* validity 存储验证结果，错误信息等
* validationMessage 验证信息
* setCustomValidity 设置自定义的异常显示信息

自定义异常：
[示例]()

## 表单提交
submit()  实现手动提交表单
onsubmit  事件绑定的方法中，可以通过阻止默认事件触发，阻止表单提交刷新页面

## 表单应用

验证手机号了可以在标签中写pattern：
```html
<input type="tel" name="telephone" pattern="^0?(1[34578])[0-9]{9}$">
```
[示例]()