# 考试查询

## 获取实例

```
$exam = $zCrawler->exam;
```


## 查询当前学期考试

### 方法

```
$exam->current() : array
```

### 功能

查询当前学期考试

### 参数

无

### 返回值

array
```
array(4) {
  [0] => array(8) {
    ["code"] => string(36) "(2015-2016-2)-xxx-2000500068-1"
    ["name"] => string(15) "xxx"
    ["student_name"] => string(6) "xxx"
    ["time"] => string(30) "2016年06月21日(10:30-12:30)"
    ["location"] => string(6) "北401"
    ["form"] => string(2) " "
    ["seat"] => string(2) "19"
    ["campus"] => string(6) "xxx"
  }
  [1] => array(8) {
    ["code"] => string(36) "(2015-2016-2)-PHY34400T-2011500066-1"
    ["name"] => string(12) "固体物理"
    ["student_name"] => string(6) "xxx"
    ["time"] => string(30) "2016年06月22日(10:30-12:30)"
    ["location"] => string(6) "教507"
    ["form"] => string(2) " "
    ["seat"] => string(1) "8"
    ["campus"] => string(6) "东区"
  }
  ...
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
code |string | 选课课号
name | string | 课程名称
student_name | string | 学生姓名
time | string | 考试时间
location | string | 考试地点
form | string | 考试形式
seat | string | 座位号
district | string | 校区


## 根据学年学期查询考试

### 方法

```
$exam->getTyTerm() : array
```
### 功能

根据指定的学年学期查询考试，如果是当前学期，不可使用该方法，否则获取不到数据

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$year | string | Y | 学年，例如 '2016-2017'
$term | int | Y | 学期，例如 1

### 返回值

同 [查询当前学期考试] 接口返回值


## 查询当前学期补考

### 方法

```
$exam->currentMakeUp() : array
```

### 功能

查询当前学期补考

### 参数

无

### 返回值

array
```
array(4) {
  [0] => array(7) {
    ["code"] => string(36) "(2015-2016-2)-xxx-2000500068-1"
    ["name"] => string(15) "xxx"
    ["student_name"] => string(6) "xxx"
    ["time"] => string(30) "2016年06月21日(10:30-12:30)"
    ["location"] => string(6) "北401"
    ["seat"] => string(2) "19"
    ["form"] => string(2) " "
  }
  [1] => array(7) {
    ["code"] => string(36) "(2015-2016-2)-PHY34400T-2011500066-1"
    ["name"] => string(12) "固体物理"
    ["student_name"] => string(6) "xxx"
    ["time"] => string(30) "2016年06月22日(10:30-12:30)"
    ["location"] => string(6) "教507"
    ["seat"] => string(1) "8"
    ["form"] => string(2) " "
  }
  ...
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
code |string | 选课课号
name | string | 课程名称
student_name | string | 学生姓名
time | string | 考试时间
location | string | 考试地点
seat | string | 座位号
form | string | 考试形式


## 根据学年学期查询补考

### 方法

```
$exam->getMakeUpByTerm() : array
```
### 功能

根据指定的学年学期查询补考，如果是当前学期，不可使用该方法，否则获取不到数据

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$year | string | Y | 学年，例如 '2016-2017'
$term | int | Y | 学期，例如 1

### 返回值

同 [查询当前学期补考] 接口返回值
