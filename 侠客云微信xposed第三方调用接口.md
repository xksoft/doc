# 侠客云微信xposed第三方调用接口

### 条件
>1.手机需要root
>2.安装xposed 框架
>3.安装wxapi.apk 




#### 发送文本信息
`xky.callApi('com.tencent.mm','sendTextMsg',{wxid:'wxid_xxx',msg:'msg_xxxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
wxid_xxx| string | 好友微信号
msg_xxxx| string | 需要发送的文本信息


```javascript
xky.callApi('com.tencent.mm','sendTextMsg',{wxid:'wxid_k2qvvyeecbhf22',msg:'hello'})
```

```
{errcode: 0, result: "调用成功"}
```

#### 发送图片
`xky.callApi('com.tencent.mm','sendPic',{wxid:'wxid_xxx',path:'path_xxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
wxid_xxx| string | 好友微信号
path_xxx| string | 图片路径


```javascript
xky.callApi('com.tencent.mm','sendPic',{wxid:'wxid_k2qvvyeecbhf22',path:'/storage/emulated/0/tencent/MicroMsg/16555.jpg'})
```

```
{errcode: 0, result: "调用成功"}
```

#### 发送视频
`xky.callApi('com.tencent.mm','sendVideo',{wxid:'wxid_xxx',path:'path_xxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
wxid_xxx| string | 好友微信号
path_xxx| string | 视频路径


```javascript
xky.callApi('com.tencent.mm','sendVideo',{wxid:'wxid_k2qvvyeecbhf22',path:'/storage/emulated/0/tencent/MicroMsg/15566.mp4'})
```

```
{errcode: 0, result: "调用成功"}
```

#### 发送语音
`xky.callApi('com.tencent.mm','sendVoice',{wxid:'wxid_xxx',path:'path_xxx',playtime:time_xxx});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
wxid_xxx| string | 好友微信号
path_xxx| string | 语音文件路径
time_xxx| int | 播放时间，单位毫秒


```javascript
xky.callApi('com.tencent.mm','sendVoice',{wxid:'wxid_k2qvvyeecbhf22',path:'/storage/emulated/0/15566.amr',playtime:8888});
```

```
{errcode: 0, result: "调用成功"}
```

#### 发送位置信息
`xky.callApi('com.tencent.mm','sendAddr',{wxid:'wxid_xxx',xcoord:xcoord_xx,ycoord:ycoord_xx,lable:'lable_xx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
wxid_xxx| string | 好友微信号
xcoord_xx| double | 横坐标
ycoord_xx| double | 纵坐标
lable_xx| string | 位置名称


```javascript
xky.callApi('com.tencent.mm','sendAddr',{wxid:'wxid_k2qvvyeecbhf22',xcoord:22.831090927124023,ycoord:108.3697738647461,lable:'南宁青秀万达广场(青秀区东葛路118号)'});
```

```
{errcode: 0, result: "调用成功"}
```


#### 发送名片
`xky.callApi('com.tencent.mm','sendCard',{wxid:'wxid_xxx',cardid:'card_xxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
wxid_xxx| string | 好友微信号
card_xxx| string | 名片微信号



```javascript
xky.callApi('com.tencent.mm','sendCard',{wxid:'wxid_k2qvvyeecbhf22',cardid:'wxid_k2qvvyeecbhd233'});
```

```
{errcode: 0, result: "调用成功"}
```


#### 建立群聊
`xky.callApi('com.tencent.mm','buildroomchat',{wxids:'wxid_xxx,wxid_xxx',roomname:'roomname_xxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
wxid_xxx,wxid_xxx| string | 好友微信号,以","分隔
roomname_xxx| string | 群名称



```javascript
xky.callApi('com.tencent.mm','buildroomchat',{wxids:'wxid_k2qvvyeecbhf21,wxid_vq7m1vvo8oo22,wxid_6uq54h678wbs22',roomname:'hello'});
```

```
{errcode: 0, result: "调用成功"}
```


#### 直接拉好友进群（群成员>40时，发送群邀请）
`xky.callApi('com.tencent.mm','pullToRoom',{wxids:'wxid_xxx,wxid_xxx',roomid:'roomid_xxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
wxid_xxx,wxid_xxx| string | 好友微信号,以","分隔
roomid_xxx| string | 群ID（需要安装wxapi.apk,再点进群信息界面查看）



```javascript
xky.callApi('com.tencent.mm','pullToRoom',{wxids:'wxid_k2qvvyeecbhf21,wxid_vq7m1vvo8oo22,wxid_6uq54h678wbs22',roomid:'12130046225@chatroom'});
```

```
{errcode: 0, result: "调用成功"}
```

#### 发送群邀请
`xky.callApi('com.tencent.mm','sendRoomInvite',{wxids:'wxid_xxx,wxid_xxx',roomid:'roomid_xxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
wxid_xxx,wxid_xxx| string | 好友微信号,以","分隔
roomid_xxx| string | 群ID（需要安装wxapi.apk,再点进群信息界面查看）



```javascript
xky.callApi('com.tencent.mm','sendRoomInvite',{wxids:'wxid_k2qvvyeecbhf21,wxid_vq7m1vvo8oo22,wxid_6uq54h678wbs22',roomid:'12130046225@chatroom'});
```

```
{errcode: 0, result: "调用成功"}
```

#### 踢掉群成员
`xky.callApi('com.tencent.mm','removeRoomMember',{wxids:'wxid_xxx,wxid_xxx',roomid:'roomid_xxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
wxid_xxx,wxid_xxx| string | 好友微信号（需以wxid_开头）,以","分隔
roomid_xxx| string | 群ID（需要安装wxapi.apk,再点进群信息界面查看）



```javascript
xky.callApi('com.tencent.mm','removeRoomMember',{wxids:'wxid_k2qvvyeecbhf21,wxid_vq7m1vvo8oo22,wxid_6uq54h678wbs22',roomid:'12130046225@chatroom'});
```

```
{errcode: 0, result: "调用成功"}
```




