
## Account

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
### GetInfo

This http POST will be called to 获取个人信息(自动登录)

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
`UserName` | String | 用户昵称：如：Jessie
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
`this` | Boolean | 返回是否发送成功

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
`this` | Boolean | 返回是否成功

===
## Topic

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

This http POST will be called to 删除咨询

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
`[ ].ID` | Int32 | 
`[ ].ParentTopicID` | Nullable < Int32 >  | 
`[ ].ChannelID` | Int32 | 
`[ ].ChannelTitle` | String | 
`[ ].GoodVal` | Int32 | 
`[ ].UserID` | Int32 | 
`[ ].FeedbackNum` | Int32 | 
`[ ].CanGood` | Boolean | 
`[ ].PublishOn` | DateTime | 
`[ ].TopicDetailItems` | IList < ContentItemModel >  | 
`[ ].TopicDetailItems[ ].Type` | String | 类型，目前为2种，"text":文本；"image"：图片
`[ ].TopicDetailItems[ ].Content` | String | 当类型为"text"时，该处为实际文本的内容，当类型为"image"时，该处为图片的名字
`[ ].TopicDetailItems[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序

---
### GetMyTopicMessages

This http POST will be called to 获取我的评论消息

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
`Count` | Int32 | 


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
`[ ].HostTopicID` | Int32 | 
`[ ].HostPublisherID` | Int32 | 
`[ ].HostTopicContent` | String | 
`[ ].HostContentType` | String | 
`[ ].TopicID` | Nullable < Int32 >  | 
`[ ].Publisher` | Publisher | 
`[ ].Publisher.UserID` | Int32 | 
`[ ].Publisher.UserName` | String | 
`[ ].Publisher.PhotoFileName` | String | 
`[ ].TopicContent` | String | 
`[ ].ContentType` | String | 
`[ ].IsGood` | Boolean | 
`[ ].CreateOn` | DateTime | 

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
`Count` | Int32 | 


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
`Count` | Int32 | 
`UserPhotos` | IList < String >  | 

---
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
`[ ].ChannelID` | Int32 | 
`[ ].NewsTypeID` | Int32 | 
`[ ].IconTag` | String | 
`[ ].ChannelTitle` | String | 
`[ ].LatestTopicText` | String | 

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
`[ ].ChannelID` | Int32 | 
`[ ].NewsTypeID` | Int32 | 
`[ ].IconTag` | String | 
`[ ].ChannelTitle` | String | 
`[ ].LatestTopicText` | String | 

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
`ChannelID` | Int32 | 
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
`[ ].ID` | Int32 | 
`[ ].ParentTopicID` | Nullable < Int32 >  | 
`[ ].ChannelID` | Int32 | 
`[ ].ChannelTitle` | String | 
`[ ].GoodVal` | Int32 | 
`[ ].UserID` | Int32 | 
`[ ].FeedbackNum` | Int32 | 
`[ ].CanGood` | Boolean | 
`[ ].PublishOn` | DateTime | 
`[ ].TopicDetailItems` | IList < ContentItemModel >  | 
`[ ].TopicDetailItems[ ].Type` | String | 类型，目前为2种，"text":文本；"image"：图片
`[ ].TopicDetailItems[ ].Content` | String | 当类型为"text"时，该处为实际文本的内容，当类型为"image"时，该处为图片的名字
`[ ].TopicDetailItems[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序

---
### SubmitTopic

This http POST will be called to 提交话题

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
`ChannelID` | Int32 | 
`ParentTopicID` | Nullable < Int32 >  | 
`Items` | IList < SubmitContentItemModel >  | 
`[ ].TopicDetailItems[ ].Type` | String | 类型，目前为2种，"text":文本；"image"：图片
`[ ].TopicDetailItems[ ].Content` | String | 当类型为"text"时，该处为实际文本的内容，当类型为"image"时，该处为图片Base64编码
`Items[ ].ImageExt` | String | 图片后缀名，例如："jpg", ".jpg", "Jpg", "JPg"...


**Returns**

```json
{
"ID":##,
"ParentTopicID":##,
"ChannelID":##,
"ChannelTitle":"",
"GoodVal":##,
"UserID":##,
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
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | TopicDetailModel | 
`ID` | Int32 | 
`ParentTopicID` | Nullable < Int32 >  | 
`ChannelID` | Int32 | 
`ChannelTitle` | String | 
`GoodVal` | Int32 | 
`UserID` | Int32 | 
`FeedbackNum` | Int32 | 
`CanGood` | Boolean | 
`PublishOn` | DateTime | 
`TopicDetailItems` | IList < ContentItemModel >  | 
`[ ].TopicDetailItems[ ].Type` | String | 类型，目前为2种，"text":文本；"image"：图片
`[ ].TopicDetailItems[ ].Content` | String | 当类型为"text"时，该处为实际文本的内容，当类型为"image"时，该处为图片的名字
`[ ].TopicDetailItems[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序

===
## Activity

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
`[ ].ActivityID` | Int32 | 
`[ ].ImageFileName` | String | 
`[ ].TagName` | String | 
`[ ].CarouselTitle` | String | 
`[ ].Url` | String | 
`[ ].SortNum` | Int32 | 

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
`[ ].ActivityTypeID` | Int32 | 
`[ ].TypeName` | String | 
`[ ].IconTag` | String | 
`[ ].SortNum` | Int32 | 

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
`[ ].ActivityID` | Int32 | 
`[ ].URL` | String | 
`[ ].Title` | String | 
`[ ].TitleImageFileName` | String | 
`[ ].StarVal` | Int32 | 
`[ ].Summary` | String | 
`[ ].SortNum` | Int32 | 
`[ ].ParticipantNum` | Int32 | 
`[ ].ButtonText` | String | 
`[ ].CanClick` | Boolean | 
`[ ].StartDate` | DateTime | 
`[ ].EndDate` | DateTime | 

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
`ActivityTypeID` | Int32 | 
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
`[ ].ActivityID` | Int32 | 
`[ ].URL` | String | 
`[ ].Title` | String | 
`[ ].TitleImageFileName` | String | 
`[ ].StarVal` | Int32 | 
`[ ].Summary` | String | 
`[ ].SortNum` | Int32 | 
`[ ].ParticipantNum` | Int32 | 
`[ ].ButtonText` | String | 
`[ ].CanClick` | Boolean | 
`[ ].StartDate` | DateTime | 
`[ ].EndDate` | DateTime | 

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
`[ ].ActivityID` | Int32 | 
`[ ].URL` | String | 
`[ ].Title` | String | 
`[ ].TitleImageFileName` | String | 
`[ ].StarVal` | Int32 | 
`[ ].Summary` | String | 
`[ ].SortNum` | Int32 | 
`[ ].ParticipantNum` | Int32 | 
`[ ].ButtonText` | String | 
`[ ].CanClick` | Boolean | 
`[ ].StartDate` | DateTime | 
`[ ].EndDate` | DateTime | 

---
### Collect

This http POST will be called to 收藏某个活动

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
`ActivityID` | Int32 | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 

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
`ActivityID` | Int32 | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 

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
`ActivityID` | Int32 | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 

===
## User

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
`ImageExt` | String | 
`Image` | String | 


**Returns**

```json
""
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | String | 

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
`UserName` | String | 
`OldPassword` | String | 
`Password` | String | 
`AreaID` | Nullable < Int32 >  | 
`Gender` | Nullable < Int32 >  | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 

===
## Message

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
`this` | Int32 | 

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
`[ ].MessageID` | Int32 | 
`[ ].MessageTitle` | String | 
`[ ].MessageContent` | String | 
`[ ].SendOn` | DateTime | 
`[ ].IsGlobal` | Boolean | 
`[ ].IsRead` | Boolean | 

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
`MessageID` | Int32 | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 

===
## News

### GetAllNewsTypes

This http POST will be called to 获取咨询类目列表

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
`[ ].NewsTypeID` | Int32 | 
`[ ].TypeName` | String | 
`[ ].ChannelID` | Int32 | 
`[ ].SortNum` | Int32 | 
`[ ].Status` | Int32 | 

---
### GetNewsList

This http POST will be called to 获取咨询列表，带分页

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
`NewsTypeID` | Int32 | 
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
`[ ].NewsID` | Int32 | 
`[ ].Title` | String | 
`[ ].Summary` | String | 
`[ ].UsefulVal` | Int32 | 
`[ ].HasCollect` | Boolean | 

---
### GetNewsListTop

This http POST will be called to 获取咨询列表表头

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
`NewsTypeID` | Int32 | 
`Count` | Int32 | 


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
`TopicID` | Int32 | 
`UserPhotos` | IList < String >  | 

---
### GetNewsDetail

This http POST will be called to 获取咨询详细

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
`NewsID` | Int32 | 


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
`Title` | String | 
`NewsTypeName` | String | 
`NewsDetailItems` | IList < ContentItemModel >  | 
`NewsDetailItems[ ].Type` | String | 类型，目前为2种，"text":文本；"image"：图片
`NewsDetailItems[ ].Content` | String | 当类型为"text"时，该处为实际文本的内容，当类型为"image"时，该处为图片的名字
`NewsDetailItems[ ].SortNum` | Int32 | 排序值，从小到大，服务器端已根据这个排序
`NextNewsID` | Nullable < Int32 >  | 
`NextNewsTitle` | String | 

---
### SetCurrentStatus

This http POST will be called to 设置当前状态，正在哪个咨询类目

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
`NewsTypeID` | Int32 | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 

---
### GetCollectedNewsList

This http POST will be called to 获取有用的咨询列表数据

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
 "HasCollect":true
 }
]
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | IList < NewsMainModel >  | 
`[ ].NewsID` | Int32 | 
`[ ].Title` | String | 
`[ ].Summary` | String | 
`[ ].UsefulVal` | Int32 | 
`[ ].HasCollect` | Boolean | 

---
### Collect

This http POST will be called to 收藏某个咨询

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
`NewsID` | Int32 | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 

---
### UnCollect

This http POST will be called to 删除某个咨询的收藏

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
`NewsID` | Int32 | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 

===
## Common

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
`[ ].AreaID` | Int32 | 
`[ ].AreaCode` | String | 
`[ ].AreaName` | String | 
`[ ].LevelNum` | Int32 | 
`[ ].SortNum` | Int32 | 
