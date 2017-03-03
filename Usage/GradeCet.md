# 四六级

## 获取实例

```
$cet = $zCrawler->cet;
```


## 查询四六级成绩

### 方法

```
$cet->grade() : array
```

### 功能

查询四六级考试成绩，限在教务网能查询到的成绩

### 参数

无

### 返回值

array
```
array(2) {
  [0] => array(10) {
    ["year"] => string(9) "2015-2016"
    ["term"] => string(1) "2"
    ["name"] => string(12) "英语四级"
    ["number"] => string(15) "11047216xxxxxxxx"
    ["date"] => string(10) "2016-06-18"
    ["grade_all"] => string(3) "xxx"
    ["grade_listening"] => string(3) "xxx"
    ["grade_reading"] => string(3) "xxx"
    ["grade_writing"] => string(3) "xxx"
    ["grade_synthesizing"] => string(1) "0"
  }
  [1] => array(10) {
    ["year"] => string(9) "2016-2017"
    ["term"] => string(1) "1"
    ["name"] => string(4) "CET6"
    ["number"] => string(15) "1104721xxxxxxxx"
    ["date"] => string(10) "2016-12-17"
    ["grade_all"] => string(3) "xxx"
    ["grade_listening"] => string(3) "xxx"
    ["grade_reading"] => string(3) "xxx"
    ["grade_writing"] => string(3) "xxx"
    ["grade_synthesizing"] => string(1) "0"
  }
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
year | string | 学年
term | string | 学期
name | string | 等级考试名称
number | string | 准考证号
date | date | 考试日期
grade_all | float | 成绩
grade_listening | float | 听力成绩
grade_reading | float | 阅读成绩
grade_writing | float | 写作成绩
grade_synthesizing | float | 综合成绩

## 四六级报名展示

### 方法

```
$cet->page($photoSavePath = '', $saveName = '') : array
```

### 功能

获取四六级报名学期、可报名项目、已报名项目、学生报名信息

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$photoSavePath | string | N | 学生照片保存路径，例如 'storage/'，必须以 `/` 结尾，如果为空表示不下载学生照片
$saveName | string | N | 学生照片保存文件名，如果设置必须包含文件扩展名，文件扩展名可以为 .png, .jpg, 不设置自动生成

### 返回值

array
```
array(4) {
  ["info"] => array(3) {
    ["year"] => string(9) "2016-2017"
    ["term"] => string(1) "2"
    ["remark"] => string(173) "*** 务必核查本人身份证号、照片等个人信息，若有错误，东校区到办公楼108，北校区到教学楼105办理更正手续。注意缴费时间。 ***"
  }
  ["list"] => array(8) {
    ...
    [6] => array(9) {
      ["chk"] => string(22) "DBGrid:_ctl8:chkSelect"
      ["name"] => string(12) "英语六级"
      ["type"] => string(7) "类别1"
      ["can_apply"] => string(12) "允许报名"
      ["require"] => string(45) "(英语四级And 英语四级&gt;=2004-20...."
      ["fit"] => string(2) " "
      ["limit"] => string(142) ",2002级,2003级,2004级,2005级,俄语,日语,本科2006级,2006级,2007级,本科2008级,旁听,2009级,2010级,本科2011级,本科2012级,"
      ["remark"] => string(2) " "
      ["markup"] => string(2) " "
    }
    [7] => array(9) {
      ["chk"] => string(22) "DBGrid:_ctl9:chkSelect"
      ["name"] => string(12) "英语四级"
      ["type"] => string(7) "类别1"
      ["can_apply"] => string(12) "允许报名"
      ["require"] => string(2) " "
      ["fit"] => string(2) " "
      ["limit"] => string(142) ",2004级,2003级,2002级,2001级,日语,2005级,本科2006级,2007级,本科2008级,旁听,2009级,2010级,本科2011级,俄语,本科2012级,"
      ["remark"] => string(2) " "
      ["markup"] => string(2) " "
    }
  }
  ["applied"] => array(1) {
    [0] => array(8) {
      ["no"] => string(1) "1"
      ["name"] => string(12) "英语六级"
      ["id_card"] => string(18) "xxxxxxxxxxx"
      ["is_pay"] => string(2) " "
      ["original_no"] => string(2) " "
      ["reserve_type"] => string(24) "国家英语等级考试"
      ["reserve_grade"] => string(2) " "
      ["delete_id"] => string(22) "DBGridInfo:_ctl2:_ctl1"
    }
  }
  ["student"] => array(3) {
    ["photo"] => string(30) "readimagexs.aspx?xh=xxxxx"
    ["id_card"] => string(18) "xxxxxxxxxxxxxx"
    ["photo_save"] => string(xx) "/path/to/file.png"
  }
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
info | array | 四六级报名信息数组
info.year | string | 报名学年
info.term | string | 报名学期
info.remark | string | 教务处备注
list | array | 可报名项目列表
list.chk | string | 复选框的 name 值，报名时需提交此值
list.name | string | 名称
list.type | string | 类别
list.can_apply | string | 是否可以报名
list.require | string | 等级考试要求
list.fit | string | 面向对象
list.limit | string | 限制对象
list.remark | string | 备注
list.markup | string | 是否补考
applied | array | 已报名信息数组
applied.no | string | 序号
applied.name | string | 名称
applied.id_card | string | 身份证号
applied.is_pay | string | 是否缴费
applied.original_no | string | 原准考证号
applied.reserve_type | string | 保留成绩类型
applied.reserve_grade | string | 保留成绩分数
applied.delete_id | string | 删除id，用于删除时所传的参数值
student | array | 学生信息
student.photo | string | 学生照片地址
student.id_card | string | 学生身份证号
student.photo_save | string | 保存后的照片地址，只有 $photoSavePath 不为空时才有此字段


## 四六级报名提交

### 方法

```
$cet->submit($itemName, $idCard, $photoSavePath = '', $saveName = '') : array
```

### 功能

提交四六级报名信息

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$itemName | string | Y | $cet->page() 方法返回的 list.chk 的值
$idCard | string | Y | 学生身份证号
$photoSavePath | string | N | 学生照片保存路径，例如 'storage/'，必须以 `/` 结尾，如果为空表示不下载学生照片
$saveName | string | N | 学生照片保存文件名，如果设置必须包含文件扩展名，文件扩展名可以为 .png, .jpg, 不设置自动生成

## 返回值

同 [四六级报名展示] 方法返回值


## 四六级报名退选

### 方法

```
$cet->delete($itemName, $photoSavePath = '', $saveName = '') : array
```

### 功能

删除已报名的记录

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$itemName | string | Y | $cet->page() 方法返回的 applied.delete_id 的值
$photoSavePath | string | N | 学生照片保存路径，例如 'storage/'，必须以 `/` 结尾，如果为空表示不下载学生照片
$saveName | string | N | 学生照片保存文件名，如果设置必须包含文件扩展名，文件扩展名可以为 .png, .jpg, 不设置自动生成

## 返回值

同 [四六级报名展示] 方法返回值
