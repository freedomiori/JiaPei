
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
"Phone":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | UserInfo | 
`UserID` | Int32 | 
`UserName` | String | 
`Phone` | String | 


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
`UName` | String | 
`Password` | String | 


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
`UserID` | Int32 | 
`UserName` | String | 
`Phone` | String | 


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
`UserName` | String | 
`Password` | String | 
`Phone` | String | 
`VCode` | String | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 


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
`UName` | String | 


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
"UName":"",
"Password":"",
"VCode":""
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | ResetPasswordModel | 
`UName` | String | 
`Password` | String | 
`VCode` | String | 


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 
