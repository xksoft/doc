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
{errcode: 0, result: "sendTextMsg调用成功"}
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
{errcode: 0, result: "sendPic调用成功"}
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
{errcode: 0, result: "sendVideo调用成功"}
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
{errcode: 0, result: "sendVoice调用成功"}
```

#### 发送文件
`xky.callApi('com.tencent.mm','sendFile',{wxid:'wxid_xxx',path:'path_xxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
wxid_xxx| string | 好友微信号
path_xxx| string | 文件路径


```javascript
xky.callApi('com.tencent.mm','sendFile',{wxid:'wxid_k2qvvyeecbhf22',path:'/sdcard/temp/temp/1'});
```

```
{errcode: 0, result: "sendFile调用成功"}
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
{errcode: 0, result: "sendAddr调用成功"}
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
{errcode: 0, result: "sendCard调用成功"}
```


#### 发送分享链接
`xky.callApi('com.tencent.mm','sendShareLinks',{wxid:'wxid_xxx',url:'url_xxx',appId:'appId_xx',appName:'appNa_xx',title:'title_xx',description:'des_xx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
wxid_xxx| string | 好友微信号
url_xxx| string | 分享链接的url
appId_xx| string | 手机应用appid
appNa_xx| string | 手机应用名称
title_xx| string | 分享链接标题头
des_xx| string | 分享链接描述




```javascript
xky.callApi('com.tencent.mm','sendShareLinks',{wxid:'wxid_k2qvvyeecbhf21',
                                                url:'https://www.shouyu.com/course.html?curriculaThemeId=ct-7e5ca4fd-8c4b-4bc6-ad16-23cf0c6b9017',
                                                appId:'wx0f73cdef9a0b09b0',appName:'授渔',
                                                title:'短视频自媒体实战运营速成到精通',description:'快来报名参加吧'});
```

```
{errcode: 0, result: "sendShareLinks调用成功"}
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
{errcode: 0, result: "buildroomchat调用成功roomId :4868493411@chatroom"}
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
{errcode: 0, result: "pullToRoom调用成功"}
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
{errcode: 0, result: "sendRoomInvite调用成功"}
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
{errcode: 0, result: "removeRoomMember调用成功"}
```

#### 获取所有好友wxid
`xky.callApi('com.tencent.mm','getAllcontactsWxid');`


```javascript
xky.callApi('com.tencent.mm','getAllcontactsWxid');
```

```
{errcode: 0, result: "getAllcontactsWxid调用成功", wxids: "[wxid_6uq54h678wbs22, wxid_vq7m1vvo8oo22, wxid_k2qvvyeecbhf21]"}
```


#### 获取所有好友微信号
`xky.callApi('com.tencent.mm','getAllcontactsalias');`


```javascript
xky.callApi('com.tencent.mm','getAllcontactsalias');
```

```
{errcode: 0, result: "getAllcontactsalias调用成功", alias: "["wxid_7cmde6vkbgrl22","rsdayu","wxid_mmgkwjlolwyt…pnnw822","wxid_k2qvvyeecbhf21","jinbw8085854192"]"}
```

#### 获取某群成员wxid
`xky.callApi('com.tencent.mm','getRoomMembersWxid',{roomid:'roomid_xxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
roomid_xxx| string | 群ID（需要安装wxapi.apk,再点进群信息界面查看）



```javascript
xky.callApi('com.tencent.mm','getRoomMembersWxid',{roomid:'51014915912@chatroom'});
```

```
{errcode: 0, result: "getRoomMembersWxid调用成功", wxids: "[wxid_k2qvvyeecbhf21, wxid_6uq54h678wbs22, wxid_vq7m1vvo8oo22]"}
```

#### 获取所有群id
`xky.callApi('com.tencent.mm','getAllRoomids');`


```javascript
xky.callApi('com.tencent.mm','getAllRoomids');
```

```
{errcode: 0, result: "getAllRoomids调用成功", roomids: "["10592148314@chatroom","4645643461@chatroom","6802458544@chatroom","9869997871@chatroom"]"}
```

#### 获取所有群所有群成员wxid
`xky.callApi('com.tencent.mm','getAllRoomMembersWxid');`


```javascript
xky.callApi('com.tencent.mm','getAllRoomMembersWxid');
```

```
{errcode: 0, result: "getAllRoomMembersWxid调用成功", wxids: "[wxid_k2qvvyeecbhf21;wxid_6uq54h678wbs22;wxid_vq7m…yeecbhf21;wxid_6uq54h678wbs22;wxid_vq7m1vvo8oo22]"}
```


#### 根据wxid 打开个人详情界面
`xky.callApi('com.tencent.mm','openPersonDesbywxid',{wxid:'wxid_xxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
wxid_xxx| string | wxid好友微信号



```javascript
xky.callApi("com.tencent.mm", "openPersonDesbywxid", {wxid:"wxid_k2qvvyeecbhf21"});
```

```
{errcode: 0, result: "openPersonDesbywxid调用成功"}
```


#### 根据roomid 打开群详情界面
`xky.callApi('com.tencent.mm','openRoomByRoomid',{roomid:'roomid_xxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
roomid_xxx| string | roomid



```javascript
xky.callApi('com.tencent.mm','openRoomByRoomid',{roomid:"6802458544@chatroom"});
```

```
{errcode: 0, result: "openRoomByRoomid调用成功"}
```


#### 根据群邀请链接content 打开群邀请界面
`xky.callApi('com.tencent.mm','openInvitedByxmlcontent',{content:'content_xxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
content_xxx| string | 群邀请链接content(群邀请在微信数据库的存储content字段)



```javascript
xky.callApi('com.tencent.mm','openInvitedByxmlcontent',{content:"<msg><appmsg appid=\"\" sdkver=\"\"><title><![CDATA[邀请你加入群聊]]>....</msg>"});
```

```
{errcode: 0, result: "openInvitedByxmlcontent调用成功"}
```



#### 查询微信数据库
`xky.callApi('com.tencent.mm','runSql',{sql:'sql_xxx'});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
sql_xxx| string | SQL SELECT 语句



```javascript
xky.callApi('com.tencent.mm','runSql',{sql:'select username,nickname from rcontact where type = 4 '});
```

```
{errcode: 0, result: "runSql调用成功", details: Array(69)}
```

#### 发送朋友圈（文字、图片、短视频）
`xky.callApi("com.tencent.mm","sendMoments",{"des":"txt_xx","picpaths":"picpaths_xx","KSightPath":"ksightpath_xx","KSightThumbPath":"ksightThpath_xx"});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
txt_xx| string | 朋友圈文字描述，可为空（""）
picpaths| string | 朋友圈图片路径，最多为9张图片，用","分隔,可为空（""）
KSightPath| string | 短视频路径，可为空（""）
KSightThumbPath| string | 短视频封面路径,可为空（""）,为空时默认为短视频第一帧图片



```javascript
xky.callApi("com.tencent.mm","sendMoments",{"des":"大家好","picpaths":"","KSightPath":"","KSightThumbPath":""});
```

```
{errcode: 0, result: "sendMoments调用成功"}
```

```javascript
xky.callApi("com.tencent.mm","sendMoments",{"des":"大家好","picpaths":"/storage/emulated/0/DCIM/1528426443248.jpg,/storage/emulated/0/6443248.jpg","KSightPath":"","KSightThumbPath":""});
```

```
{errcode: 0, result: "sendMoments调用成功"}
```

```javascript
xky.callApi("com.tencent.mm","sendMoments",{"des":"大家好","picpaths":"","KSightPath":"/sdcard/tencent/MicroMsg/WeiXin/wx_camera_1531102334784.mp4","KSightThumbPath":""});
```

```
{errcode: 0, result: "sendMoments调用成功"}
```

#### 改变微信定位
`xky.callApi('com.tencent.mm','changlocation',{loctoX:X_xxx,loctoY:Y_xxx});`

参数 | 值类型 | 说明
------------ | ------------- | -------------
loctoX| double | 改变定位的x坐标
loctoX| double | 改变定位的y坐标


```javascript
xky.callApi('com.tencent.mm','changlocation',{loctoX:31.245682,loctoY:121.522522});
```

```
{errcode: 0, result: "changlocation调用成功"}
```

#### 获取登录用户信息（account,wxid,name...）
`xky.callApi('com.tencent.mm','getMyinfo');`


```javascript
xky.callApi('com.tencent.mm','getMyinfo');
```

```
{errcode: 0, result: "getMyinfo调用成功", details: {…}}
```






