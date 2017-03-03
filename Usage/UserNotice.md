# 教务通知

## 获取实例

```
$notice = $zCrawler->user_notice;
```


## 获取通知内容列表

### 方法

```
$notice->contentList() : array
```

### 功能

获取通知内容列表，仅仅包含标题，不包含详情

### 参数

无

### 返回值

array
```
array(7) {
  [0] => array(5) {
    ["url"] => string(57) "ggsm.aspx?fbsj=2017-02-23 09:20:00&yxqx=2017-03-03&xh=100"
    ["title"] => string(83) "2016-2017-2学期在线学习网络通识课程选课、学习、考核等的说明"
    ["unit"] => string(9) "教务处"
    ["publish_time"] => string(19) "2017-02-23 09:20:00"
    ["expire_time"] => string(10) "2017-03-03"
  }
  [1] => array(5) {
    ["url"] => string(56) "ggsm.aspx?fbsj=2017-02-21 12:54:22&yxqx=2017-02-27&xh= "
    ["title"] => string(48) "退补选和重修选课开始时间延迟通知"
    ["unit"] => string(9) "教务处"
    ["publish_time"] => string(19) "2017-02-21 12:54:22"
    ["expire_time"] => string(10) "2017-02-27"
  }
  ...
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
url | string | 通知链接
title | string | 通知标题
unit | string | 通知单位
publish_time | datetime | 发布时间
expire_time | date | 有效期


## 获取通知详情

### 方法

```
$notice->contentDetail($url, $attachSavePath = '') : array
```

### 功能

根据内容的链接获取内容详情

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$url | string | Y | 通知链接
$attachSavePath | string | N | 附件保存路径，例如 'storage/'，必须以 `/` 结尾，如果为空，则不下载附件

### 返回值

array
```
array(3) {
  ["title"] => string(47) "2016-2017-2学期退补选和重修选课通知"
  ["body"] => string(1258) "&lt;p&gt;各位本科生同学：&lt;br/..."
  ["attaches"] => array(1) {
    [0] => array(2) {
      ["file_name"] => string(52) "2016-2017-2学期退补选和重修选课通知.docx"
      ["save_name"] => string(45) "1f3bced7faff93848cfb6a12bb7ea5f801279604.docx"
    }
  }
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
title | string | 通知标题
body | string | 通知详情，HTML 字符串
attaches | array | 附件信息数组，如果没有设置保存附件，改数组为空
attaches.file_name | string | 附件原文件名
attaches.save_name | string | 附件保存文件名


## 下载附件

### 方法

```
$notice->downloadAttach($fileName, $attachSavePath, $saveName = null) : array
```

### 功能

下载附件到本地

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$fileName | string | Y | 附件原文件名
$attachSavePath | string | Y | 附件保存路径，例如 'storage/'，必须以 `/` 结尾
$saveName | string | N | 附件保存文件名，如果设置必须包含文件扩展名，不设置自动生成

### 返回值

array
```
array(2) {
  ["file_name"] => string(52) "2016-2017-2学期退补选和重修选课通知.docx"
  ["save_name"] => string(45) "31d480781d698ac5d21e7d42f332169bb8e4a13d.docx"
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
file_name | string | 附件原文件名
save_name | string | 附件保存文件名


## 一次性获取所有内容详情列表

### 方法

```
$notice->contentDetailList($attachSavePath = '') : array
```

### 功能

一次性获取所有通知详情

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$attachSavePath | string | N | 附件保存路径，例如 'storage/'，必须以 `/` 结尾，如果为空，则不下载附件

### 返回值

array
```
 [0] => array(6) {
    ["url"] => string(57) "ggsm.aspx?fbsj=2017-02-23 09:20:00&yxqx=2017-03-03&xh=100"
    ["title"] => string(83) "2016-2017-2学期在线学习网络通识课程选课、学习、考核等的说明"
    ["unit"] => string(9) "教务处"
    ["publish_time"] => string(19) "2017-02-23 09:20:00"
    ["expire_time"] => string(10) "2017-03-03"
    ["detail"] => array(3) {
      ["title"] => string(83) "2016-2017-2学期在线学习网络通识课程选课、学习、考核等的说明"
      ["body"] => string(1219) "&lt;p&gt;各位同学：&lt;..."
      ["attaches"] => array(1) {
        [0] => array(2) {
          ["file_name"] => string(46) "在线学习网络通识课程相关说明.rar"
          ["save_name"] => string(44) "47f5955813c6e120af41c41c8558d3c5491241a7.rar"
        }
      }
    }
  }
  [1] => array(6) {
    ["url"] => string(56) "ggsm.aspx?fbsj=2017-02-21 12:54:22&yxqx=2017-02-27&xh= "
    ["title"] => string(48) "退补选和重修选课开始时间延迟通知"
    ["unit"] => string(9) "教务处"
    ["publish_time"] => string(19) "2017-02-21 12:54:22"
    ["expire_time"] => string(10) "2017-02-27"
    ["detail"] => array(3) {
      ["title"] => string(48) "退补选和重修选课开始时间延迟通知"
      ["body"] => string(1651) "&lt;p&gt;同学们：&lt;br/&gt;..."
      ["attaches"] => array(0) {
      }
    }
  }
  ...
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
url | string | 通知链接
title | string | 通知标题
unit | string | 通知单位
publish_time | datetime | 发布时间
expire_time | date | 有效期
detail | array | 详情数组信息
detail.title | string | 通知标题
detail.body | string | 通知详情，HTML 字符串
detail.attaches | array | 附件信息数组，如果没有设置保存附件，改数组为空
detail.attaches.file_name | string | 附件原文件名
detail.attaches.save_name | string | 附件保存文件名
