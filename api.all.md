# 接口模块说明
本文档按照模块来分别定义了接口说明，具体如下：

1. 通用接口：很多功能可能调用此处接口，如果在对应子模块找不到合适接口，请来此处查找。例如用来获取所有地区，图片，上传手机信息并获取token。

2. 个人中心：列出登陆、注册、找回、通知、头像、个人信息等接口，现在还缺少关于我们、当前版本接口、更新

3. 资讯： 列出获取资讯分类、设置里程碑、获取资讯列表、获取资讯对应话题列表、获取资讯详情、有用、没用。GetCollectedNewsList接口需要修改。

4. 发现： 列出Carousel轮播列表、活动分类、发现首页的活动列表、具体分类的列表、参加。 

收藏某个活动，触发条件：

点击发现的carousel，直接跳转至URL并触发收藏动作。

点击‘去参加’、‘去报名’等跳转至URL并触发收藏动作。


5. 有话说：列出官方频道列表，热门推荐列表，话题列表，我的消息列表、评论我的消息概述、评论我的消息详情、点赞、删除。

缺少：查看更多官方频道，话题明细。 修改：SubmitTopic

返回值只需要返回是否成功。GetMyTopicList，返回值的昵称，头像应该不需要。



## 通用模块

### GetAllArea

This http POST will be called to 获取所有地区数据

```json
POST api/Common/GetAllArea
```

**Returns**

```json
[
 {
 "AreaID":##,
 "AreaCode":"",
 "AreaName":"",
 "LevelNum":##,
 "SortNum":##
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < AreaModel >  | 
`[ ].AreaID` | Int32 | 地区ID
`[ ].AreaCode` | String | 地区编码，2位一个级别，如浙江为01，杭州为0101
`[ ].AreaName` | String | 地区名
`[ ].LevelNum` | Int32 | 地区级别，如浙江为1，杭州为2
`[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序

===
### Image

This http GET will be called to 获取图片，server会根据输入的值来缩放图片，如原图：1000,1000 参数为500,250.  则返回 250，250

```json
GET UI/Image/{filename}?width={width(可选)}&height={height(可选)}
```

width，height为整数
### SImage （建议使用imge）

This http GET will be called to 获取50X50小图片

```json
GET UI/SImage/{filename}
```

------------------
### MImage （建议使用imge）

This http GET will be called to 获取100X100中图片

```json
GET UI/MImage/{filename}
```

------------------
### BImage （建议使用imge）

This http GET will be called to 获取大图片

```json
GET UI/BImage/{filename}
```

------------------
### GetToken

This http POST will be called to 通过手机信息获取token

```json
POST api/Account/GetToken
```

```json
{
"MID":"",
"V":"",
"Mtype":"",
"W":##,
"H":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | PhoneInfoModel | 
`MID` | String | 手机唯一码，能用SSID最好，尽量不要变化。IOS和android不要重复。
`V` | String | 版本号，供个人中心的当前版本使用，如：1.1
`Mtype` | String | 手机型号，如：Iphone5s 1530
`W` | Int32 | 手机分辨率的宽度，如：800
`H` | Int32 | 手机分辨率的高度，如：600


**Returns**

```json
"EFFE6A32-4A1F-4052-B2AE-A0F78C02CEDC"
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Guid | 返回token，客户端得到后放在header内,每次自动上传验证。

---

## 个人中心

### GetInfo

This http POST will be called to 获取个人信息(供自动登录使用，未注册用户则返回Null)

```json
POST api/Account/GetInfo
```

**Returns**

```json
{
"UserID":##,
"UserName":"",
"Phone":"",
"AreaID":##,
"Gender":##,
"PhotoFileName":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | UserInfo | 
`UserID` | Int32 | 用户ID，如：4
`UserName` | String | 用户昵称：如：Jessie
`Phone` | String | 用户手机号：13634131000
`AreaID` | Nullable < Int32 >  | 地区ID，如：1
`Gender` | Int32 | 性别，0 是男 1 是女 不填为null
`PhotoFileName` | String | 头像图片名称，如：b26951fc2a054c84bb6e338f9b245cf7.jpg

---
### Login

This http POST will be called to 登录并返回个人信息

```json
POST api/Account/Login
```

```json
{
"Phone":"",
"Password":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | LoginModel | 
`Phone` | String | 手机号，也是用户名
`Password` | String | 密码


**Returns**

```json
{
"UserID":##,
"UserName":"",
"Phone":"",
"AreaID":##,
"Gender":##,
"PhotoFileName":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | UserInfo | 
`UserID` | Int32 | 用户ID
`UserName` | String | 用户昵称：如：Jessie
`Phone` | String | 手机号
`AreaID` | Nullable < Int32 >  | 地区ID，如：1
`Gender` | Int32 | 性别，0 是男 1 是女 不填为null
`PhotoFileName` | String | 头像图片名称，如：b26951fc2a054c84bb6e338f9b245cf7.jpg

---
### Logout

This http POST will be called to 注销当前用户

```json
POST api/Account/Logout
```

**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否成功

---
### SendVCodeForRegister

This http POST will be called to 发送注册验证码

```json
POST api/Account/SendVCodeForRegister
```

```json
{
"Phone":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | PhoneModel | 
`Phone` | String | 手机号


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否成功

---
### ValidateRegVCode

This http POST will be called to 验证手机注册验证码

```json
POST api/Account/ValidateRegVCode
```

```json
{
"Phone":"",
"VCode":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | ValidateRegModel | 
`Phone` | String | 手机号
`VCode` | String | 手机收到的验证码


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否成功

---
### Register

This http POST will be called to 注册用户第二步并登录

```json
POST api/Account/Register
```

```json
{
"UserName":"",
"Password":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | RegisterModel | 
`UserName` | String | 用户昵称：如：Jessie，可以重复
`Password` | String | 用户密码


**Returns**

```json
{
"UserID":##,
"UserName":"",
"Phone":"",
"AreaID":##,
"Gender":##,
"PhotoFileName":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | UserInfo | 
`UserID` | Int32 | 用户ID
`UserName` | String | 用户昵称：如：Jessie
`Phone` | String | 手机号
`AreaID` | Nullable < Int32 >  | 地区ID，如：1
`Gender` | Int32 | 性别，0 是男 1 是女 不填为null
`PhotoFileName` | String | 头像图片名称，如：b26951fc2a054c84bb6e338f9b245cf7.jpg

---
### SendVCodeForForgetPass

This http POST will be called to 发送忘记密码验证码

```json
POST api/Account/SendVCodeForForgetPass
```

```json
{
"Phone":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | PhoneModel | 
`Phone` | String | 手机号


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否发送成功, 0 false, 1 success, 需要判断是否返回error

---
### ResetPassword

This http POST will be called to 重置密码

```json
POST api/Account/ResetPassword
```

```json
{
"Phone":"",
"Password":"",
"VCode":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | ResetPasswordModel | 
`Phone` | String | 手机号
`Password` | String | 新密码
`VCode` | String | 短信验证码


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否成功, 0 false, 1 success, 需要判断是否返回error

===
### UploadPhoto

This http POST will be called to 上传头像

```json
POST api/User/UploadPhoto
```

```json
{
"ImageExt":"",
"Image":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | ImageModel | 
`ImageExt` | String | 图片后缀名，例如："jpg", ".jpg", "Jpg", "JPg"... 文件名不要上传。
`Image` | String | 图片Base64编码


**Returns**

```json
""
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | String | 返回图片文件名

---
### UpdateUserInfo

This http POST will be called to 修改用户信息

```json
POST api/User/UpdateUserInfo
```

```json
{
"UserName":"",
"OldPassword":"",
"Password":"",
"AreaID":##,
"Gender":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | UpdateUserModel | 
`UserName` | String | 用户昵称
`OldPassword` | String | 原来的密码
`Password` | String | 新密码
`AreaID` | Nullable < Int32 >  | 地区ID
`Gender` | Nullable < Int32 >  | 性别，男：0，女：1


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否成功

===
### GetNewMessageCount

This http POST will be called to 获取新通知的数量

```json
POST api/Message/GetNewMessageCount
```

**Returns**

```json
##
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Int32 | 返回新通知的数量

---
### GetMessageList

This http POST will be called to 获取所有通知列表

```json
POST api/Message/GetMessageList
```

**Returns**

```json
[
 {
 "MessageID":##,
 "MessageTitle":"",
 "MessageContent":"",
 "SendOn":"yyyy-MM-dd HH:mm:ss",
 "IsGlobal":true,
 "IsRead":true
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < MessageItemModel >  | 
`[ ].MessageID` | Int32 | 消息ID
`[ ].MessageTitle` | String | 消息标题
`[ ].MessageContent` | String | 消息正文
`[ ].SendOn` | DateTime | 消息发送时间，服务器已经按时间排序
`[ ].IsGlobal` | Boolean | 是否为全局消息，暂时没用，不要处理
`[ ].IsRead` | Boolean | 是否已读，如果是0，左边框颜色变为蓝色，1的话为灰色。

---
### Delete

This http POST will be called to 删除指定的通知

```json
POST api/Message/Delete
```

```json
{
"MessageID":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | MessageIDModel | 
`MessageID` | Int32 | 消息的ID


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否成功

===
### GetCollectedNewsList

This http POST will be called to 获取有用的资讯列表数据

```json
POST api/News/GetCollectedNewsList
```

```json
{
"Skip":##,
"Take":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | PagedModel | 
`Skip` | Int32 | 跳过条数，即从第几条开始
`Take` | Int32 | 获取条数


**Returns**

```json
[
 {
 "NewsID":##,
 "Title":"",
 "Summary":"",
 "UsefulVal":##,
 "HasCollect":true,
 "CollectOn":"yyyy-MM-dd HH:mm:ss"
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < CollectedNewsMainModel >  | 
`[ ].NewsID` | Int32 | 资讯ID
`[ ].Title` | String | 资讯标题
`[ ].Summary` | String | 资讯简介
`[ ].UsefulVal` | Int32 | 有用值   暂时不用使用
`[ ].HasCollect` | Boolean | 是否已收藏  暂时不用使用
`[ ].CollectOn` | DateTime | 收藏时间

---
### GetCollectedActivityList

This http POST will be called to 获取有趣的活动列表数据

```json
POST api/Activity/GetCollectedActivityList
```

```json
{
"Skip":##,
"Take":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | PagedModel | 
`Skip` | Int32 | 跳过条数，即从第几条开始
`Take` | Int32 | 获取条数


**Returns**

```json
[
 {
 "ActivityID":##,
 "URL":"",
 "Title":"",
 "TitleImageFileName":"",
 "StarVal":##,
 "Summary":"",
 "SortNum":##,
 "ParticipantNum":##,
 "ButtonText":"",
 "CanClick":true,
 "StartDate":"yyyy-MM-dd HH:mm:ss",
 "EndDate":"yyyy-MM-dd HH:mm:ss"
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < ActivityItemModel >  | 
`[ ].ActivityID` | Int32 | 活动ID
`[ ].URL` | String | 活动跳转的URL
`[ ].Title` | String | 活动的标题
`[ ].TitleImageFileName` | String | 活动的图片文件名
`[ ].StarVal` | Int32 | 星值
`[ ].Summary` | String | 活动简介
`[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序
`[ ].ParticipantNum` | Int32 | 活动当前参与人数， 暂时不用
`[ ].ButtonText` | String | 活动按钮文字，如：已满，进行中，去参加
`[ ].CanClick` | Boolean | 活动按钮是否可点击
`[ ].StartDate` | DateTime | 活动开始时间
`[ ].EndDate` | DateTime | 活动结束时间

---
### UnCollect

This http POST will be called to 删除某个活动的收藏

```json
POST api/Activity/UnCollect
```

```json
{
"ActivityID":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | ActivityIDModel | 
`ActivityID` | Int32 | 活动ID


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否成功

---

## 资讯

### GetAllNewsTypes

This http POST will be called to 获取资讯类目列表

```json
POST api/News/GetAllNewsTypes
```

**Returns**

```json
[
 {
 "NewsTypeID":##,
 "TypeName":"",
 "ChannelID":##,
 "SortNum":##,
 "Status":##
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < NewsTypeModel >  | 
`[ ].NewsTypeID` | Int32 | 资讯类别的ID
`[ ].TypeName` | String | 资讯类别的名称
`[ ].ChannelID` | Int32 | 频道ID
`[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序
`[ ].Status` | Int32 | 状态值，0：未开始，1：正在进行，2：已经完成

---
### SetCurrentStatus

This http POST will be called to 设置当前状态，正在哪个资讯类目

```json
POST api/News/SetCurrentStatus
```

```json
{
"NewsTypeID":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | NewsTypeIDModel | 
`NewsTypeID` | Int32 | 资讯类别ID


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否成功

---
### GetNewsListTop

This http POST will be called to 获取资讯列表表头

```json
POST api/News/GetNewsListTop
```

```json
{
"NewsTypeID":##,
"Count":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | GetNewsListTopModel | 
`NewsTypeID` | Int32 | 资讯类别ID
`Count` | Int32 | 希望获取的最新发表话题的用户头像数


**Returns**

```json
{
"TopicID":##,
"UserPhotos":[
""
 ]
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | NewsListTopModel | 
`TopicID` | Int32 | 话题ID
`UserPhotos` | IList < String >  | 发表话题的用户的头像文件名列表

---
### GetNewsList

This http POST will be called to 获取资讯列表，带分页

```json
POST api/News/GetNewsList
```

```json
{
"NewsTypeID":##,
"Skip":##,
"Take":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | GetNewsListModel | 
`NewsTypeID` | Int32 | 资讯类别ID
`Skip` | Int32 | 跳过条数，即从第几条开始
`Take` | Int32 | 获取条数


**Returns**

```json
[
 {
 "NewsID":##,
 "Title":"",
 "Summary":"",
 "UsefulVal":##,
 "HasCollect":true
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < NewsMainModel >  | 
`[ ].NewsID` | Int32 | 资讯ID
`[ ].Title` | String | 资讯标题
`[ ].Summary` | String | 资讯简介
`[ ].UsefulVal` | Int32 | 有用值
`[ ].HasCollect` | Boolean | 是否已经收藏

---
### GetNewsDetail

This http POST will be called to 获取资讯详细

```json
POST api/News/GetNewsDetail
```

```json
{
"NewsID":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | NewsIDModel | 
`NewsID` | Int32 | 资讯ID


**Returns**

```json
{
"Title":"",
"NewsTypeName":"",
"NewsDetailItems":[
  {
  "Type":"",
  "Content":"",
  "SortNum":##
  }
 ],
"NextNewsID":##,
"NextNewsTitle":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | NewsDetailModel | 
`Title` | String | 资讯标题
`NewsTypeName` | String | 资讯类别名
`NewsDetailItems` | IList < ContentItemModel >  | 
`NewsDetailItems[ ].Type` | String | 类型，目前为2种，"text":文本；"image"：图片
`NewsDetailItems[ ].Content` | String | 当类型为"text"时，该处为实际文本的内容，当类型为"image"时，该处为图片的名字
`NewsDetailItems[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序
`NextNewsID` | Nullable < Int32 >  | 下一条资讯ID， <b>用户返回时候，需要重新调用GetNewsList接口，刷新列表界面。</b>
`NextNewsTitle` | String | 下一条资讯标题

---
### Collect

This http POST will be called to 收藏某个资讯

```json
POST api/News/Collect
```

```json
{
"NewsID":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | NewsIDModel | 
`NewsID` | Int32 | 资讯ID


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否成功

---
### UnCollect

This http POST will be called to 删除某个资讯的收藏

```json
POST api/News/UnCollect
```

```json
{
"NewsID":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | NewsIDModel | 
`NewsID` | Int32 | 资讯ID


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否成功

===

## 发现

### GetCarouselList

This http POST will be called to 获取轮播数据

```json
POST api/Activity/GetCarouselList
```

**Returns**

```json
[
 {
 "ActivityID":##,
 "ImageFileName":"",
 "TagName":"",
 "CarouselTitle":"",
 "Url":"",
 "SortNum":##
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < ActivityCarouselItemModel >  | 
`[ ].ActivityID` | Int32 | 活动ID
`[ ].ImageFileName` | String | 活动图片文件名
`[ ].TagName` | String | 活动标签
`[ ].CarouselTitle` | String | 活动标题
`[ ].Url` | String | 活动跳转Url
`[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序

---
### GetTypeList

This http POST will be called to 获取活动类别列表数据

```json
POST api/Activity/GetTypeList
```

**Returns**

```json
[
 {
 "ActivityTypeID":##,
 "TypeName":"",
 "IconTag":"",
 "SortNum":##
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < ActivityTypeItemModel >  | 
`[ ].ActivityTypeID` | Int32 | 活动类别ID
`[ ].TypeName` | String | 活动类别名
`[ ].IconTag` | String | 活动类别图标标识
`[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序

---
### GetFrontList

This http POST will be called to 获取首页活动列表数据

```json
POST api/Activity/GetFrontList
```

**Returns**

```json
[
 {
 "ActivityID":##,
 "URL":"",
 "Title":"",
 "TitleImageFileName":"",
 "StarVal":##,
 "Summary":"",
 "SortNum":##,
 "ParticipantNum":##,
 "ButtonText":"",
 "CanClick":true,
 "StartDate":"yyyy-MM-dd HH:mm:ss",
 "EndDate":"yyyy-MM-dd HH:mm:ss"
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < ActivityItemModel >  | 
`[ ].ActivityID` | Int32 | 活动ID
`[ ].URL` | String | 活动跳转的URL
`[ ].Title` | String | 活动的标题
`[ ].TitleImageFileName` | String | 活动的图片文件名
`[ ].StarVal` | Int32 | 星值
`[ ].Summary` | String | 活动简介
`[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序
`[ ].ParticipantNum` | Int32 | 活动当前参与人数， 暂时不用
`[ ].ButtonText` | String | 活动按钮文字，如：已满，进行中。。。
`[ ].CanClick` | Boolean | 活动按钮是否可点击
`[ ].StartDate` | DateTime | 活动开始时间
`[ ].EndDate` | DateTime | 活动结束时间

---
### GetActivityList

This http POST will be called to 获取某个活动类别下的活动列表数据

```json
POST api/Activity/GetActivityList
```

```json
{
"ActivityTypeID":##,
"Skip":##,
"Take":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | GetActivityListModel | 
`ActivityTypeID` | Int32 | 活动类别ID
`Skip` | Int32 | 跳过条数，即从第几条开始
`Take` | Int32 | 获取条数


**Returns**

```json
[
 {
 "ActivityID":##,
 "URL":"",
 "Title":"",
 "TitleImageFileName":"",
 "StarVal":##,
 "Summary":"",
 "SortNum":##,
 "ParticipantNum":##,
 "ButtonText":"",
 "CanClick":true,
 "StartDate":"yyyy-MM-dd HH:mm:ss",
 "EndDate":"yyyy-MM-dd HH:mm:ss"
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < ActivityItemModel >  | 
`[ ].ActivityID` | Int32 | 活动ID
`[ ].URL` | String | 活动跳转的URL
`[ ].Title` | String | 活动的标题
`[ ].TitleImageFileName` | String | 活动的图片文件名
`[ ].StarVal` | Int32 | 星值
`[ ].Summary` | String | 活动简介
`[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序
`[ ].ParticipantNum` | Int32 | 活动当前参与人数，暂时不用
`[ ].ButtonText` | String | 活动按钮文字，如：已满，进行中。。。
`[ ].CanClick` | Boolean | 活动按钮是否可点击
`[ ].StartDate` | DateTime | 活动开始时间
`[ ].EndDate` | DateTime | 活动结束时间

---
### Collect

This http POST will be called to 收藏某个活动，触发条件：
1.点击发现的carousel，直接跳转至URL并触发收藏动作。
2.点击‘去参加’、‘去报名’等跳转至URL并触发收藏动作。

```json
POST api/Activity/Collect
```

```json
{
"ActivityID":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | ActivityIDModel | 
`ActivityID` | Int32 | 活动ID


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否成功

---
### Participant

This http POST will be called to 参与某个活动

```json
POST api/Activity/Participant
```

```json
{
"ActivityID":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | ActivityIDModel | 
`ActivityID` | Int32 | 活动ID


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否成功

===

## 有话说

### GetTopChannelList

This http POST will be called to 获取上面部分的频道列表

```json
POST api/Topic/GetTopChannelList
```

**Returns**

```json
[
 {
 "ChannelID":##,
 "NewsTypeID":##,
 "IconTag":"",
 "ChannelTitle":"",
 "LatestTopicText":""
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < ChannelItemModel >  | 
`[ ].ChannelID` | Int32 | 频道ID
`[ ].NewsTypeID` | Int32 | 资讯类别ID
`[ ].IconTag` | String | 图标的标识
`[ ].ChannelTitle` | String | 频道标题
`[ ].LatestTopicText` | String | 最新评论的文字，目前只获取类型为"text"的内容

---
### GetHotChannelList

This http POST will be called to 获取热门的频道列表

```json
POST api/Topic/GetHotChannelList
```

**Returns**

```json
[
 {
 "ChannelID":##,
 "NewsTypeID":##,
 "IconTag":"",
 "ChannelTitle":"",
 "LatestTopicText":""
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < ChannelItemModel >  | 
`[ ].ChannelID` | Int32 | 频道ID
`[ ].NewsTypeID` | Int32 | 资讯类别ID，目前热门频道不会挂钩资讯类别
`[ ].IconTag` | String | 图标的标识
`[ ].ChannelTitle` | String | 频道标题
`[ ].LatestTopicText` | String | 最新评论的文字，目前只获取类型为"text"的内容

---
### GetTopicList

This http POST will be called to 获取频道话题列表

```json
POST api/Topic/GetTopicList
```

```json
{
"ChannelID":##,
"Skip":##,
"Take":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | GetTopicListModel | 
`ChannelID` | Int32 | 频道ID
`Skip` | Int32 | 跳过条数，即从第几条开始
`Take` | Int32 | 获取条数


**Returns**

```json
[
 {
 "ID":##,
 "ParentTopicID":##,
 "ChannelID":##,
 "ChannelTitle":"",
 "GoodVal":##,
 "UserID":##,
 "Publisher":  {
  "UserID":##,
  "UserName":"",
  "PhotoFileName":""
  },
 "FeedbackNum":##,
 "CanGood":true,
 "PublishOn":"yyyy-MM-dd HH:mm:ss",
 "TopicDetailItems":[
   {
   "Type":"",
   "Content":"",
   "SortNum":##
   }
  ]
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < TopicDetailModel >  | 
`[ ].ID` | Int32 | 话题ID
`[ ].ParentTopicID` | Nullable < Int32 >  | 被回复的话题ID，肯定为NULL
`[ ].ChannelID` | Int32 | 频道ID
`[ ].ChannelTitle` | String | 频道标题，暂时不用
`[ ].GoodVal` | Int32 | 被点赞的总数
`[ ].UserID` | Int32 | 用户ID
`[ ].Publisher` | Publisher | 
`[ ].Publisher.UserID` | Int32 | 发布者的用户ID
`[ ].Publisher.UserName` | String | 发布者的用户昵称
`[ ].Publisher.PhotoFileName` | String | 发布者的头像文件名
`[ ].FeedbackNum` | Int32 | 被回复的总数
`[ ].CanGood` | Boolean | 是否可被点赞
`[ ].PublishOn` | DateTime | 发布时间
`[ ].TopicDetailItems` | IList < ContentItemModel >  | 
`[ ].TopicDetailItems[ ].Type` | String | 类型，目前为2种，"text":文本；"image"：图片
`[ ].TopicDetailItems[ ].Content` | String | 当类型为"text"时，该处为实际文本的内容，当类型为"image"时，该处为图片的名字
`[ ].TopicDetailItems[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序

---
### SubmitTopic

This http POST will be called to 提交话题，提交回复。 成功后客户端需要调用方法刷新列表。

```json
POST api/Topic/SubmitTopic
```

```json
{
"ChannelID":##,
"ParentTopicID":##,
"Items":[
  {
  "Type":"",
  "Content":"",
  "ImageExt":""
  }
 ]
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | TopicSubmitModel | 
`ChannelID` | Int32 | 频道ID
`ParentTopicID` | Nullable < Int32 >  | 被回复的话题ID
`Items` | IList < SubmitContentItemModel >  | 
`[ ].TopicDetailItems[ ].Type` | String | 类型，目前为2种，"text":文本；"image"：图片
`[ ].TopicDetailItems[ ].Content` | String | 当类型为"text"时，该处为实际文本的内容，当类型为"image"时，该处为图片Base64编码
`Items[ ].ImageExt` | String | 图片后缀名，例如："jpg", ".jpg", "Jpg", "JPg"...


**Returns**

```json
[
 {
 "ID":##,
 "ParentTopicID":##,
 "ChannelID":##,
 "ChannelTitle":"",
 "GoodVal":##,
 "UserID":##,
 "Publisher":  {
  "UserID":##,
  "UserName":"",
  "PhotoFileName":""
  },
 "FeedbackNum":##,
 "CanGood":true,
 "PublishOn":"yyyy-MM-dd HH:mm:ss",
 "TopicDetailItems":[
   {
   "Type":"",
   "Content":"",
   "SortNum":##
   }
  ]
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < TopicDetailModel >  | 
`[ ].ID` | Int32 | 话题ID
`[ ].ParentTopicID` | Nullable < Int32 >  | 被回复的话题ID
`[ ].ChannelID` | Int32 | 频道ID
`[ ].ChannelTitle` | String | 频道标题
`[ ].GoodVal` | Int32 | 被点赞的总数
`[ ].UserID` | Int32 | 用户ID
`[ ].Publisher` | Publisher | 
`[ ].Publisher.UserID` | Int32 | 发布者的用户ID
`[ ].Publisher.UserName` | String | 发布者的用户昵称
`[ ].Publisher.PhotoFileName` | String | 发布者的头像文件名
`[ ].FeedbackNum` | Int32 | 被回复的总数
`[ ].CanGood` | Boolean | 是否可被点赞
`[ ].PublishOn` | DateTime | 发布时间
`[ ].TopicDetailItems` | IList < ContentItemModel >  | 
`[ ].TopicDetailItems[ ].Type` | String | 类型，目前为2种，"text":文本；"image"：图片
`[ ].TopicDetailItems[ ].Content` | String | 当类型为"text"时，该处为实际文本的内容，当类型为"image"时，该处为图片的名字
`[ ].TopicDetailItems[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序

===
### SendGood

This http POST will be called to 点赞

```json
POST api/Topic/SendGood
```

```json
{
"TopicID":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | TopicIDModel | 
`TopicID` | Int32 | 话题ID， 如：2


**Returns**

```json
##
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Int32 | 返回当前点赞的总数

---
### SendNotGood

This http POST will be called to 取消点赞

```json
POST api/Topic/SendNotGood
```

```json
{
"TopicID":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | TopicIDModel | 
`TopicID` | Int32 | 话题ID， 如：2


**Returns**

```json
##
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Int32 | 返回当前点赞的总数

---
### Delete

This http POST will be called to 删除资讯

```json
POST api/Topic/Delete
```

```json
{
"TopicID":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | TopicIDModel | 
`TopicID` | Int32 | 话题ID， 如：2


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 返回是否成功

---
### GetTopMessages

This http POST will be called to 获取最新评论消息条数及评论人头像列表

```json
POST api/Topic/GetTopMessages
```

```json
{
"Count":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | CountModel | 
`Count` | Int32 | 最新评论人的头像最大个数，如：3


**Returns**

```json
{
"Count":##,
"UserPhotos":[
""
 ]
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | TopicsListTopModel | 
`Count` | Int32 | 最新评论消息条数
`UserPhotos` | IList < String >  | 最新评论人的头像文件名

---
### GetMyTopicMessages

This http POST will be called to 获取评论‘我的消息’的消息列表。

```json
POST api/Topic/GetMyTopicMessages
```

```json
{
"Count":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | CountModel | 
`Count` | Int32 | 获取的记录数, 0 为全部。 暂时全部传0。


**Returns**

```json
[
 {
 "HostTopicID":##,
 "HostPublisherID":##,
 "HostTopicContent":"",
 "HostContentType":"",
 "TopicID":##,
 "Publisher":  {
  "UserID":##,
  "UserName":"",
  "PhotoFileName":""
  },
 "TopicContent":"",
 "ContentType":"",
 "IsGood":true,
 "CreateOn":"yyyy-MM-dd HH:mm:ss"
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < TopicMessageModel >  | 
`[ ].HostTopicID` | Int32 | 被评论的话题ID
`[ ].HostPublisherID` | Int32 | 被评论的话题的发布者ID
`[ ].HostTopicContent` | String | 被评论的话题的内容， 当类型为"text"时，该处为实际文本的内容，当类型为"image"时，该处为图片的名字
`[ ].HostContentType` | String | 被评论的话题内容的类型，目前为2种，"text":文本；"image"：图片
`[ ].TopicID` | Nullable < Int32 >  | 回复的话题ID，当为点赞时，该话题ID为null
`[ ].Publisher` | Publisher | 
`[ ].Publisher.UserID` | Int32 | 回复的话题的发布者的用户ID
`[ ].Publisher.UserName` | String | 回复的话题的发布者的用户昵称
`[ ].Publisher.PhotoFileName` | String | 回复的话题的发布者的头像文件名
`[ ].TopicContent` | String | 评论的话题的内容， 当类型为"text"时，该处为实际文本的内容，当类型为"image"时，该处为图片的名字
`[ ].ContentType` | String | 评论的话题内容的类型，目前为2种，"text":文本；"image"：图片
`[ ].IsGood` | Boolean | 是否点赞，当该值为true时，话题ID(TopicID)为null
`[ ].CreateOn` | DateTime | 创建时间，即发布时间

---
### GetMyTopicList

This http POST will be called to 获取我说的列表

```json
POST api/Topic/GetMyTopicList
```

```json
{
"Skip":##,
"Take":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | PagedModel | 
`Skip` | Int32 | 跳过条数，即从第几条开始
`Take` | Int32 | 获取条数


**Returns**

```json
[
 {
 "ID":##,
 "ParentTopicID":##,
 "ChannelID":##,
 "ChannelTitle":"",
 "GoodVal":##,
 "UserID":##,
 "Publisher":  {
  "UserID":##,
  "UserName":"",
  "PhotoFileName":""
  },
 "FeedbackNum":##,
 "CanGood":true,
 "PublishOn":"yyyy-MM-dd HH:mm:ss",
 "TopicDetailItems":[
   {
   "Type":"",
   "Content":"",
   "SortNum":##
   }
  ]
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < TopicDetailModel >  | 
`[ ].ID` | Int32 | 话题ID
`[ ].ParentTopicID` | Nullable < Int32 >  | 被回复的话题ID，暂时肯定为0.
`[ ].ChannelID` | Int32 | 频道ID
`[ ].ChannelTitle` | String | 频道标题
`[ ].GoodVal` | Int32 | 被点赞的总数
`[ ].UserID` | Int32 | 用户ID
`[ ].Publisher` | Publisher | 
`[ ].Publisher.UserID` | Int32 | 发布者的用户ID
`[ ].Publisher.UserName` | String | 发布者的用户昵称
`[ ].Publisher.PhotoFileName` | String | 发布者的头像文件名
`[ ].FeedbackNum` | Int32 | 被回复的总数
`[ ].CanGood` | Boolean | 是否可被点赞
`[ ].PublishOn` | DateTime | 发布时间
`[ ].TopicDetailItems` | IList < ContentItemModel >  | 
`[ ].TopicDetailItems[ ].Type` | String | 类型，目前为2种，"text":文本；"image"：图片
`[ ].TopicDetailItems[ ].Content` | String | 当类型为"text"时，该处为实际文本的内容，当类型为"image"时，该处为图片的名字
`[ ].TopicDetailItems[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序

---
### GetFeedbackList

This http POST will be called to 获取评论列表

```json
POST api/Topic/GetFeedbackList
```

```json
{
"TopicID":##,
"Skip":##,
"Take":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | GetFeedbackListModel | 
`TopicID` | Int32 | 话题ID， 如：2
`Skip` | Int32 | 跳过条数，即从第几条开始
`Take` | Int32 | 获取条数


**Returns**

```json
[
 {
 "ID":##,
 "ParentTopicID":##,
 "ChannelID":##,
 "ChannelTitle":"",
 "GoodVal":##,
 "UserID":##,
 "Publisher":  {
  "UserID":##,
  "UserName":"",
  "PhotoFileName":""
  },
 "FeedbackNum":##,
 "CanGood":true,
 "PublishOn":"yyyy-MM-dd HH:mm:ss",
 "TopicDetailItems":[
   {
   "Type":"",
   "Content":"",
   "SortNum":##
   }
  ]
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < TopicDetailModel >  | 
`[ ].ID` | Int32 | 话题ID
`[ ].ParentTopicID` | Nullable < Int32 >  | 被回复的话题ID
`[ ].ChannelID` | Int32 | 频道ID
`[ ].ChannelTitle` | String | 频道标题 暂时不用
`[ ].GoodVal` | Int32 | 被点赞的总数 暂时不用
`[ ].UserID` | Int32 | 用户ID
`[ ].Publisher` | Publisher | 
`[ ].Publisher.UserID` | Int32 | 发布者的用户ID
`[ ].Publisher.UserName` | String | 发布者的用户昵称
`[ ].Publisher.PhotoFileName` | String | 发布者的头像文件名
`[ ].FeedbackNum` | Int32 | 被回复的总数 暂时不用
`[ ].CanGood` | Boolean | 是否可被点赞 暂时不用
`[ ].PublishOn` | DateTime | 发布时间
`[ ].TopicDetailItems` | IList < ContentItemModel >  | 
`[ ].TopicDetailItems[ ].Type` | String | 类型，目前为2种，"text":文本；"image"：图片
`[ ].TopicDetailItems[ ].Content` | String | 当类型为"text"时，该处为实际文本的内容，当类型为"image"时，该处为图片的名字
`[ ].TopicDetailItems[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序

---







