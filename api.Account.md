
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
`MID` | String | 手机唯一码
`V` | String | 版本号
`Mtype` | String | 手机类型
`W` | Int32 | 分辨率(宽)
`H` | Int32 | 分辨率(高)


**Returns**

```json
"00000000-0000-0000-0000-000000000000"
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Guid | Token


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
"Phone":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | UserInfo | 
`UserID` | Int32 | 用户ID
`UserName` | String | 用户名
`Phone` | String | 手机号


### Login

This http POST will be called to 登录并返回个人信息

```json
POST api/Account/Login
```

```json
{
"UName":"",
"Password":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | LoginModel | 
`UName` | String | 用户名/手机号
`Password` | String | 密码


**Returns**

```json
{
"UserID":##,
"UserName":"",
"Phone":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | UserInfo | 
`UserID` | Int32 | 用户ID
`UserName` | String | 用户名
`Phone` | String | 手机号


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
`this` | Boolean | 是否成功


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
`this` | Boolean | 是否成功


### Register

This http POST will be called to 注册用户并登录

```json
POST api/Account/Register
```

```json
{
"UserName":"",
"Password":"",
"Phone":"",
"VCode":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | RegisterModel | 
`UserName` | String | 用户名
`Password` | String | 密码
`Phone` | String | 手机号
`VCode` | String | 验证码


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 是否成功


### SendVCodeForForgetPass

This http POST will be called to 发送忘记密码验证码

```json
POST api/Account/SendVCodeForForgetPass
```

```json
{
"UName":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | UNameModel | 
`UName` | String | 用户名/手机号


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 是否成功


### ResetPassword

This http POST will be called to 重置密码

```json
POST api/Account/ResetPassword
```

```json
{
"UName":"",
"Password":"",
"VCode":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | ResetPasswordModel | 
`UName` | String | 用户名/手机号
`Password` | String | 密码
`VCode` | String | 验证码


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 是否成功
