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

### 返回结果
所有API均有返回值

返回参数 | 值类型 | 说明
------------ | ------------- | -------------
errcode| int | 0为正常，其他值为异常
msg| string | 正常、或出错时的提示
other | object | 其他类型返回值，不同api返回内容不一样

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

```
{errcode: 0, result: "结果"}
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
```
{msg: "toast by http", errcode: 0}
```

#### 冷却休眠
`xky.sleep(millisecond)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
millisecond| int | 冷却时间，单位是毫秒

```javascript
await xky.sleep(1000);//冷却1秒
```
```
{errcode: 0, msg: "冷却完毕"}
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
```
{errcode: 0, msg: "日志发送完毕"}
```


#### 唤醒机器
`xky.wakeup()`

```javascript
await xky.wakeup();
```
```
{errcode: 0, msg: "done"}
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
```
{msg: "点击完毕", errcode: 0}
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
```
{msg: "鼠标按下", errcode: 0}
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
```
{msg: "鼠标释放", errcode: 0}
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
```
{msg: "鼠标移动", errcode: 0}
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
```
{msg: "鼠标滚动", errcode: 0}
```
>x y均为百分比取值范围是0-1，可配合xiakeuispy工具获取坐标点

#### 按下某个按键
`xky.pressKey(key)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
key| int | 按键代码 [安卓按键代码参考](https://github.com/XKSoft/doc/blob/master/%E5%AE%89%E5%8D%93%E6%8C%89%E9%94%AE%E5%AF%B9%E5%BA%94keycode.md)
```javascript
await xky.pressKey(3);//按下home键
```
```
{msg: "按键操作成功", errcode: 0}
```


#### 设置剪贴板内容
`xky.setClipboardText(value)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
value| string| 要设置的剪贴板内容
```javascript
await xky.setClipboardText('asdf');//把剪贴板内容设置为asdf
```
```
{msg: "剪贴板赋值完成", errcode: 0}
```

#### 读取剪贴板内容
`xky.getClipboardText()`


```javascript
let cb=await xky.getClipboardText();
```
```
{msg: "剪贴板读值完成", errcode: 0, value: "3"}
```

#### 复制 将选定内容复制到剪贴板
`xky.copy()`

```javascript
await xky.copy();
```
```
{msg: "按键操作成功", errcode: 0}
```
>类似pc上的ctrl+c

#### 剪切 将选定内容剪切到剪贴板
`xky.cut()`

```javascript
await xky.cut();
```
```
{msg: "按键操作成功", errcode: 0}
```
>类似pc上的ctrl+x

#### 粘贴 剪贴板中的内容粘贴出来
`xky.paste()`

```javascript
await xky.paste();
```
```
{msg: "按键操作成功", errcode: 0}
```
>类似pc上的ctrl+v

#### 查找元素
`xky.findUiObjects(name, regex)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
name| string| 查找条件，可以是字符串或者正则表达式
regex| bool| 可选 默认值 false 是否是正则表达式

```javascript
await xky.findUiObjects('微信');//查找文字为 微信 的控件 
```
```
{uiObjects: Array(0), errcode: 0}
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
```
{msg: "点击成功", errcode: 0}
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
```
{msg: "赋值成功", errcode: 0}
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
```
{msg: "指令完成", errcode: 0}
```

#### 杀死APP
`xky.killApp(pkname)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
pkname| string| app包名
```javascript
await xky.killApp('com.tencent.mm');//杀死微信
```
```
{errcode: 0, result: ""}
```

#### 清空APP所有数据
`xky.clearApp(pkname)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
pkname| string| app包名
```javascript
await xky.clearApp('com.tencent.mm');//清空微信所有数据
```
```
{errcode: 0, result: ""}
```
>慎重，这样就相当于重装了这个app了，所有数据都清空哦

#### 调用第三方接口Api
`xky.callApi(pkname,action,json)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
pkname| string| 第三方app包名或自定义字符串
action| string| 动作名
json| json| json格式参数（可选）
```javascript
await xky.callApi('com.tencent.mm','sendTextMsg',{wxid:'wxid_xxx',msg:'xxxxxx'});
```
```
{errcode: 0, result: "发送成功"}
```
>第三方Api开发请参考对应文档

#### 通过输入法输入文本(能在任意有焦点的地方输入文本)
`xky.input(text)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
text| string| 输入的内容
```javascript
await xky.input('无敌最寂寞'});
```
```
{errcode: 0, msg: "输入操作完毕"}
```

#### 打开输入法选择界面
`xky.showInputMethod()`


```javascript
await xky.showInputMethod(});
```
```
{errcode: 0}
```

#### 将输入法设置为侠客云X输入法
`xky.setInputMethod()`


```javascript
await xky.setInputMethod();
```
```
{errcode: 0}
```

#### 弹出客户端提示
`xky.showNotification(title,message,level)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
title| string| 弹出框的标题
message| string| 弹出框的内容
level| string| 弹出框格式 可选 succuss error warning info
```javascript
await xky.showNotification('成功','恭喜，快照成功','success');
```
```
{errcode: 0, result: "client_notification发送完毕"}
```

#### 滑动
`xky.swipe(startx,starty,endx,endy,steps)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
startx| double| 开始x坐标
starty| double| 开始y坐标
endx| double| 结束x坐标
endy| double| 结束y坐标
steps| int| 步骤数量 可选 （默认10） 这个值是决定这个滑动的速度，越大越慢
```javascript
await await xky.swipe(0.6,0.8,0.6,0.2,10);//模拟抖音翻下一个视频（从下往上滑）
```
```
{errcode: 0, result: "滑动完成"}
```
>x y均为百分比取值范围是0-1，可配合xiakeuispy工具获取坐标点

#### 设置客户端剪贴板
`xky.setClientClipboardText(value)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
value| string| 剪贴板内容
```javascript
await xky.setClientClipboardText('剪贴板内容');
```
```
{errcode: 0, result: "发送完毕"}
```

#### 从url地址安装apk
`xky.installApkFromUrl(url,newdown)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
url| string| apk的url地址
newdown| bool| 可选 默认否 表示是否全新下载（否则如果有缓存文件，则直接用缓存文件安装）
```javascript
await xky.installApkFromUrl('http://dldir1.qq.com/weixin/android/weixin667android1320.apk');//安装微信667
```
```
{errcode: 0, result: "apk安装完成"}
```

#### 发送输入法动作
`xky.sendEditorAction(code)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
code| int| 动作编号 [输入法动作参考](https://github.com/XKSoft/doc/blob/master/%E5%AE%89%E5%8D%93%E8%BE%93%E5%85%A5%E6%B3%95%E5%8A%A8%E4%BD%9C%E4%BB%A3%E7%A0%81.md)
```javascript
await xky.sendEditorAction(4);//发送
```
```
{errcode: 0, msg: "输入法指令输入完毕"}
```

#### 查找元素
`xky.findUiObjectsAndWait(name, regex)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
name| string| 查找条件，可以是字符串或者正则表达式
num|int|等待时间 秒
regex| bool| 可选 默认值 false 是否是正则表达式

```javascript
await xky.findUiObjects('微信',10);//查找文字为 微信 的控件   等待10秒
```
```
{uiObjects: Array(0), errcode: 0}
```
>控件元素id可配合xiakeyunuispy工具获取

#### 查找并点击一个元素
`xky.findAndClickAndWait(name,num, regex, index)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
name| string| 查找条件，可以是字符串或者正则表达式
num|int|等待时间 秒
regex| bool| 可选 默认值 false 是否是正则表达式
index| int | 可选 默认值0 点击找到的第几个元素
```javascript
await xky.findAndClickAndWait('微信',10);//查找文字为 微信 的控件 并点击 等待10秒
await xky.findAndClickAndWait('微',10,true);//正则方式查找，这里是所有包含 微 的控件 并点击 等待10秒
await xky.findAndClickAndWait('微信',10,false,1);//查找文字为 微信 的控件 并点击，并点击第2个控件（计算机数数从0开始） 等待10秒
```
```
{msg: "点击成功", errcode: 0}
```
>控件元素id可配合xiakeyunuispy工具获取

#### 查找并输入文本 等待完成
`xky.findAndInputAndWait(name,num, value, regex, index)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
name| string| 查找条件，可以是字符串或者正则表达式
num|int|等待时间 秒
value| string| 要输入的内容
regex| bool| 可选 默认值 false 是否是正则表达式
index| int | 可选 默认值0 点击找到的第几个元素
```javascript
await xky.findAndInputAndWait('com.android.messaging:id/recipient_text_view',10,'hahaha');//查找控件并输入 hahahah 等待10秒
```
```
{msg: "赋值成功", errcode: 0}
```
>控件元素id可配合xiakeyunuispy工具获取


#### 创建一个全息硬件信息 【仅侠客云矿机可用】
`xky.createHardware(model)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
model| string| 可选条件，值为需要指定的机型，例如 mi5 nexus6等（具体参考支持列表);
```javascript
await xky.createHardware('nexus6');//生成一个nexus6的硬件全息信息
```
```
{errcode: 0, model: "Nexus 6", key: "c009047c"}
```
>返回值 key 请自行记录，这个表示当前全息信息的唯一值（不变）

#### 还原一个全息硬件信息 【仅侠客云矿机可用】
`xky.restoreHardware(key)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
key| string| 这个key为createHardware方法返回的key
```javascript
await xky.restoreHardware('c009047c');//还原key=c009047c的硬件全息信息
```
```
{errcode: 0, model: "Nexus 6", key: "c009047c"}
```
>返回值 key 请自行记录，这个表示当前全息信息的唯一值（不变）

#### 获取当前设备的硬件全息KEY 【仅侠客云矿机可用】
`xky.getHardwareKey()`

参数 | 值类型 | 说明
------------ | ------------- | -------------
key| string| 这个key为createHardware方法返回的key
```javascript
await xky.getHardwareKey();
```
```
{errcode: 0, key: "c009047c"}
```
>返回值 key 请自行记录，这个表示当前全息信息的唯一值（不变）

#### 备份一个APP的全息快照 【仅侠客云矿机可用】
`xky.backupApp(packName,backupFiles,removeFiles)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
packName| string| app包名
backupFiles| string[]| 可选，这里可以指定备份的文件或目录，不写则全部
removeFiles| string[]| 可选，这里可以指定剔除的文件或目录，不写则不剔除任何文件
```javascript
await xky.backupApp(
    "com.tencent.mm",
    ["MicroMsg", "shared_prefs"],
    ["avatar", "appbrand"]
  );
```
```
{errcode: 0, path: "/sdcard/xbak/19fc.tar", name: "19fc"}
```
>返回值 path 为备份路径 name 为备份名

#### 还原一个APP的全息快照 【仅侠客云矿机可用】
`xky.restoreApp(packName,backupName)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
packName| string| app包名
backupName| string| 备份名（即backupApp方法返回值里的name)
```javascript
await xky.restoreApp("com.tencent.mm", "19fc");
```
```
{errcode: 0, msg: "app包还原完毕"}
```
>返回值 path 为备份路径 name 为备份名

#### 上传一个文件到云端网盘
`xky.uploadFile(filepath,savepath)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
filepath| string| 文件在手机上的路径
savepath| string| 文件在网盘里的路径
```javascript
await xky.uploadFile("/sdcard/xbak/6406.tar", "wedata/6406.tar");
```
```
{errcode: 0, name: "files/anj68vkk9tqmmxb38myg/wedata/6406.tar", url: "https://static.xky.com/files/anj68vkk9tqmmxb38myg/wedata/6406.tar"}
```
>返回值 name 网盘路径 url 下载地址

#### 从侠客云端网盘下载一个文件
`xky.downloadFile(filepath,savepath)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
filepath| string| 网盘上的路径
savepath| string| 手机上的路径
```javascript
await xky.downloadFile("wedata/6406.tar", "/sdcard/xbak/6406.tar");
```
```
{errcode: 0, name: "/sdcard/xbak/6406.tar"}
```
>返回值 name 保存路径

#### 锁屏
`xky.lockScreen()`

```javascript
await xky.lockScreen();
```
```
{errcode: 0, msg: "锁屏完成"}
```

#### 读取联系人
`xky.getContacts()`


```javascript
await xky.getContacts();
```
```
{errcode: 0, msg: "获取到1个联系人", contracts: Array(1)}
```

#### 添加联系人
`xky.insertContacts(contracts)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
contracts| JSON数组| 要添加的联系人列表，格式是json数组
```javascript
await xky.insertContacts([
    { name: "aaa", number: "17877777777" },
    { name: "bbb", number: "18888888888" }
  ]);
```
```
{done: 2, errcode: 0, msg: "成功添加2个联系人"}
```

#### 清空所有联系人
`xky.clearContacts()`


```javascript
await xky.clearContacts();
```
```
{errcode: 0, msg: "清空联系人完毕"}
```

#### 添加媒体文件到系统图库
`xky.insertMedia(path)`

参数 | 值类型 | 说明
------------ | ------------- | -------------
path| string| 图片、视频在手机上的路径，仅限jpg和mp4
```javascript
  let aaa = await xky.insertMedia("/sdcard/aaa.jpg");
```
```
{errcode: 0, msg: "刷新相册完成"}
```

