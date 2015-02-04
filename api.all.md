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
"Gender":##
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
"Gender":##
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
"Gender":##
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


## User

### UploadPhoto

This http POST will be called to 上传头像

```json
POST api/User/UploadPhoto
```

```json
{
"ImageExt":"",
"Image":"0x89504E47..."
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | ImageModel | 
`ImageExt` | String | 
`Image` | Byte[] | 


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
"Password":"",
"AreaID":##,
"Gender":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | UpdateUserModel | 
`UserName` | String | 
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
