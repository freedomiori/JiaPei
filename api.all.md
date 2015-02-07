
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
`MID` | String | 
`V` | String | 
`Mtype` | String | 
`W` | Int32 | 
`H` | Int32 | 


**Returns**

```json
"00000000-0000-0000-0000-000000000000"
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Guid | 


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
`UserID` | Int32 | 
`UserName` | String | 
`Phone` | String | 
`AreaID` | Nullable < Int32 >  | 
`Gender` | Int32 | 
`PhotoFileName` | String | 


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
`Phone` | String | 
`Password` | String | 


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
`UserID` | Int32 | 
`UserName` | String | 
`Phone` | String | 
`AreaID` | Nullable < Int32 >  | 
`Gender` | Int32 | 
`PhotoFileName` | String | 


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
`this` | Boolean | 


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
`Phone` | String | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 


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
`Phone` | String | 
`VCode` | String | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 


### Register

This http POST will be called to 注册用户并登录

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
`UserName` | String | 
`Password` | String | 


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
`UserID` | Int32 | 
`UserName` | String | 
`Phone` | String | 
`AreaID` | Nullable < Int32 >  | 
`Gender` | Int32 | 
`PhotoFileName` | String | 


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
`Phone` | String | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 


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
`Phone` | String | 
`Password` | String | 
`VCode` | String | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 


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
`TopicID` | Int32 | 


**Returns**

```json
##
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Int32 | 


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
`TopicID` | Int32 | 


**Returns**

```json
##
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Int32 | 


### Delete

This http POST will be called to 删除话题

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
`TopicID` | Int32 | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 


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
`Skip` | Int32 | 
`Take` | Int32 | 


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
`[ ].TopicDetailItems[ ].Type` | String | 
`[ ].TopicDetailItems[ ].Content` | String | 
`[ ].TopicDetailItems[ ].SortNum` | Int32 | 


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
`TopicID` | Int32 | 
`Skip` | Int32 | 
`Take` | Int32 | 


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
`[ ].TopicDetailItems[ ].Type` | String | 
`[ ].TopicDetailItems[ ].Content` | String | 
`[ ].TopicDetailItems[ ].SortNum` | Int32 | 


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
`Skip` | Int32 | 
`Take` | Int32 | 


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
`[ ].TopicDetailItems[ ].Type` | String | 
`[ ].TopicDetailItems[ ].Content` | String | 
`[ ].TopicDetailItems[ ].SortNum` | Int32 | 


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
`Items[ ].Type` | String | 
`Items[ ].Content` | String | 
`Items[ ].ImageExt` | String | 


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
`TopicDetailItems[ ].Type` | String | 
`TopicDetailItems[ ].Content` | String | 
`TopicDetailItems[ ].SortNum` | Int32 | 


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
`Skip` | Int32 | 
`Take` | Int32 | 


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
`NewsDetailItems[ ].Type` | String | 
`NewsDetailItems[ ].Content` | String | 
`NewsDetailItems[ ].SortNum` | Int32 | 
`NextNewsID` | Nullable < Int32 >  | 
`NextNewsTitle` | String | 


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


### GetCollectedActivityList

This http POST will be called to 获取有用的咨询列表数据

```json
POST api/News/GetCollectedActivityList
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
`Skip` | Int32 | 
`Take` | Int32 | 


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
