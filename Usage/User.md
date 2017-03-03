# 用户

## 获取实例

```
$user = $zCrawler->user;
```

## 修改密码

### 方法

```
$user->modifyPassword($newPassword) : bool
```

### 功能

修改用户密码

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$newPassword | string | Y | 新密码

### 返回值

`bool` 是否修改成功，修改成功返回 true
