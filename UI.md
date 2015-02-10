## UI

### SImage

This http GET will be called to 获取50X50小图片

```json
GET UI/SImage/{filename}
```

------------------
### MImage

This http GET will be called to 获取100X100中图片

```json
GET UI/MImage/{filename}
```

------------------
### BImage

This http GET will be called to 获取大图片

```json
GET UI/BImage/{filename}
```

------------------
### Image

This http GET will be called to 获取图片

```json
GET UI/Image/{filename}?width={width(可选)}&height={height(可选)}
```

width，height为整数
