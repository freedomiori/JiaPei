
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
`ImageExt` | String | 文件后缀名，例如".jpg", "jpg"
`Image` | Byte[] | 文件数据，base64编码


**Returns**

```json
""
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | String | 文件名


### UpdateUserInfo

This http POST will be called to 修改用户信息

```json
POST api/User/UpdateUserInfo
```

```json
{
"UserName":"",
"Password":"",
"AreaID":##
}
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | UpdateUserModel | 
`UserName` | String | 昵称
`Password` | String | 密码
`AreaID` | Nullable < Int32 >  | 地点ID


**Returns**

```json
true
```

variable | datatype | description
:--------|:-----------|:-----------
`this` | Boolean | 是否成功
