# 侠客云模块API大全

### 入口方法
>模块内必须包含此方法，否则无法运行
```javascript
async function main(xky, args) {
  //模块执行代码
}
```
### 关于异步
所有api均为异步方法，如需同步执行，请在代码前添加await
例：
```javascript
async function main(xky, args) {
  //冷却10秒后弹出提示
  await xky.sleep(10 * 1000); //单位是毫秒
  xky.toast("哈哈，我是个提示"); //这里之所以不加await是因为这提示不重要，可以异步让她执行，不影响流程
}
```
>异步特性是很重要的一个环节，可以按需决定接口是同步模式执行还是异步，一般需要等待的方法都用同步方式，而不需要等待的方法（如提示消息、日志信息）等，可以直接异步执行，提高效率

### API大全
>所有api均属于xky这个对象下
>api文档随时增删，请以本文档最新版本做参考

#### 执行adb命令
`xky.adbCommand(command)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
command| string | adb指令

>adb指令可以是任意adb命令例如 adb shell ls 
```javascript
await xky.adbCommand('shell ls');
```

#### toast提示信息
`xky.toast(toast)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
toast| string | 提示的内容
style| int | 提示风格_可选项（可选1 2 3 4 5 6 ）


```javascript
await xky.toast('我是提示');
await xky.toast('我是提示',1);
```

#### 冷却休眠
`xky.sleep(millisecond)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
millisecond| int | 冷却时间，单位是毫秒

```javascript
await xky.sleep(1000);//冷却1秒
```
>此命令必须加await 否则就没什么作用了，会一跳而过

#### 在控制台打印日志
`xky.log(log)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
log| object | 日志内容，可以是任意对象

```javascript
await xky.log('我是日志');
```

#### 点击某个位置
`xky.click(x,y)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
x| double | x坐标
y| double | y坐标
```javascript
await xky.click(0.5,0.5);//点击屏幕中间位置
```
>x y均为百分比取值范围是0-1，可配合xiakeuispy工具获取坐标点

#### 按下某个位置
`xky.mousedown(x,y)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
x| double | x坐标
y| double | y坐标
```javascript
await xky.mousedown(0.5,0.5);//按下屏幕中间位置
```
>x y均为百分比取值范围是0-1，可配合xiakeuispy工具获取坐标点

#### 释放某个位置(先执行mousedown)
`xky.mouseup(x,y)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
x| double | x坐标
y| double | y坐标
```javascript
await xky.mouseup(0.5,0.5);//从这个位置释放屏幕中间位置
```
>x y均为百分比取值范围是0-1，可配合xiakeuispy工具获取坐标点

#### 移动某个位置(先执行mousedown)
`xky.mousedrag(x,y)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
x| double | x坐标
y| double | y坐标
```javascript
await xky.mousedrag(0.5,0.5);//移动到这个位置
```
>x y均为百分比取值范围是0-1，可配合xiakeuispy工具获取坐标点

#### 滚动页面
`xky.wheel(x, y, updown, leftright)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
x| double | x坐标
y| double | y坐标
updown| int | 垂直滚动量 可选，默认值0
leftright| int |水平滚动量 可选，默认值0
```javascript
await xky.wheel(0.5,0.5,-2);//往下滚动-2个位置
```
>x y均为百分比取值范围是0-1，可配合xiakeuispy工具获取坐标点

#### 查找元素
`xky.findUiObjects(name, regex)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
name| string| 查找条件，可以是字符串或者正则表达式
regex| bool| 可选 默认值 false 是否是正则表达式
```javascript
await xky.findUiObjects('微信');//查找文字为 微信 的控件
await xky.findUiObjects('微',true);//正则方式查找，这里是所有包含 微 的控件
```
>控件元素id可配合xiakeyunuispy工具获取

#### 查找并点击一个元素
`xky.findAndClick(name, regex, index)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
name| string| 查找条件，可以是字符串或者正则表达式
regex| bool| 可选 默认值 false 是否是正则表达式
index| int | 可选 默认值0 点击找到的第几个元素
```javascript
await xky.findAndClick('微信');//查找文字为 微信 的控件 并点击
await xky.findAndClick('微',true);//正则方式查找，这里是所有包含 微 的控件 并点击
await xky.findAndClick('微信',false,1);//查找文字为 微信 的控件 并点击，并点击第2个控件（计算机数数从0开始）
```
>控件元素id可配合xiakeyunuispy工具获取

#### 查找并输入文本
`xky.findAndInput(name, value, regex, index)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
name| string| 查找条件，可以是字符串或者正则表达式
value| string| 要输入的内容
regex| bool| 可选 默认值 false 是否是正则表达式
index| int | 可选 默认值0 点击找到的第几个元素
```javascript
await xky.findAndInput('com.android.messaging:id/recipient_text_view','hahaha');//查找控件并输入 hahahah
```
>控件元素id可配合xiakeyunuispy工具获取

#### 重新启动APP(如果没启动则新启)
`xky.restartApp(pkname)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
pkname| string| app包名
```javascript
await xky.restartApp('com.tencent.mm');//启动微信
```

#### 杀死APP
`xky.killApp(pkname)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
pkname| string| app包名
```javascript
await xky.killApp('com.tencent.mm');//杀死微信
```

#### 清空APP所有数据
`xky.clearApp(pkname)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
pkname| string| app包名
```javascript
await xky.clearApp('com.tencent.mm');//清空微信所有数据
```
>慎重，这样就相当于重装了这个app了，所有数据都清空哦


