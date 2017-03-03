# 登录

## 获取实例

```
$login = $zCrawler->login;
```


## 免验证码登录

### 方法

```
$login->noCode() : GuzzleHttp\Cookie\CookieJar;
```

### 功能

直接免验证码登录，获取用户登录后的 Cookie

### 参数

无

### 返回值

`GuzzleHttp\Cookie\CookieJar` Cookie 对象


## 获取登录验证码

### 方法

```
$login->getCaptcha($path) : string
```

### 功能

获取登录用的验证码，实现验证码登录，纵使免验证码登录入口全部封杀，这个方法也无法封杀

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$path | string | Y | 验证码图片保存路径，例如 'storage/'，必须以 `/` 结尾

### 返回值

`string` 验证码路径，例如 'storage/a3f60445f2031b5cd83534130eeba64cf4a0887b
.gif'


## 使用验证码登录

### 方法

```
$login->withCode($code) : GuzzleHttp\Cookie\CookieJar
```

### 功能

用户填写上一方法获取的验证码图片中的数字字母后，输入验证码实现登录

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$code | string | Y | 人工或代码识别后的验证码，例如 'pian'

### 返回值

`GuzzleHttp\Cookie\CookieJar` Cookie 对象


## 获取 Cookie

### 方法

```
$login->getCookie($forceRefresh = false, $method = 'noCode') : GuzzleHttp\Cookie\CookieJar
```

### 功能

获取 Cookie，如果存在 Cookie，直接从缓存中获取，不存在则登录获取

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$forceRefresh | bool | N | 是否强制获取 Cookie，如果是，会重新获取 Cookie 而不从缓存获取，默认 `false`
$method | string/array | N | 获取验证码的方法，目前有 `withCode`, `noCode`，如果是数组，使用 $method['method'] = 'withCode', $method['param'] = [$code], 如果是字符串，使用 $method = 'noCode'

### 返回值

`GuzzleHttp\Cookie\CookieJar` Cookie 对象


## 设置 Cookie

### 方法

```
$login->setCookie(CookieJar $cookie) : bool
```

### 功能

设置 Cookie 到缓存

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$cookie | CookieJar | Y | `GuzzleHttp\Cookie\CookieJar` Cookie 对象

### 返回值

`bool` 设置成功返回 true, 失败返回 false
