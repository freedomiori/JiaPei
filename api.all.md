
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
POST api/Topic/SendGood/{id}
```

variable | datatype | description
:--------|:-----------|:-----------
`id` | Int32 | 话题ID

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
POST api/Topic/SendNotGood/{id}
```

variable | datatype | description
:--------|:-----------|:-----------
`id` | Int32 | 话题ID

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
POST api/Topic/Delete/{id}
```

variable | datatype | description
:--------|:-----------|:-----------
`id` | Int32 | 话题ID

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
`this` | GetMyTopicListModel | 
`Skip` | Int32 | 
`Take` | Int32 | 


**Returns**

```json
[
 {
 "ID":##,
 "ChannelID":##,
 "ChannelTitle":"",
 "GoodVal":##,
 "UserID":##,
 "FeedbackNum":##,
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
`[ ].ChannelID` | Int32 | 
`[ ].ChannelTitle` | String | 
`[ ].GoodVal` | Int32 | 
`[ ].UserID` | Int32 | 
`[ ].FeedbackNum` | Int32 | 
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
 "ChannelID":##,
 "ChannelTitle":"",
 "GoodVal":##,
 "UserID":##,
 "FeedbackNum":##,
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
`[ ].ChannelID` | Int32 | 
`[ ].ChannelTitle` | String | 
`[ ].GoodVal` | Int32 | 
`[ ].UserID` | Int32 | 
`[ ].FeedbackNum` | Int32 | 
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
POST api/News/GetNewsDetail/{id}
```

variable | datatype | description
:--------|:-----------|:-----------
`id` | Int32 | 咨询ID

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
POST api/News/SetCurrentStatus/{id}
```

variable | datatype | description
:--------|:-----------|:-----------
`id` | Int32 | 咨询类目ID

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
