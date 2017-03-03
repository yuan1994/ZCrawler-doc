# 选课

## 获取示例

```
$scheduleSelect = $zCrawler->schedule_select;
```


## 全校性选修课（通识课）列表

### 方法

```
$scheduleSelect->schoolWide($district = 2) : array
```

### 功能

获取全校性选修课（通识课）列表及全校性选修课（通识课）列表已选

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$district | string | N | 校区，可选值请参考该接口返回值，默认为教务网设置的默认校区

### 返回值

array
```
array(3) {
  ["list"] => array(30) {
    [0] => array(15) {
      ["name"] => string(16) "艺术与审美	"
      ["code"] => string(9) "ART10100G"
      ["teacher"] => string(9) "刘春梅"
      ["time"] => string(2) " "
      ["location"] => string(2) " "
      ["credit"] => string(3) "1.5"
      ["hour"] => string(7) "3.0-0.0"
      ["week"] => string(5) "03-14"
      ["volume"] => string(4) "2000"
      ["volume_surplus"] => string(4) "1970"
      ["affiliation"] => string(15) "人文社科类"
      ["property"] => string(18) "通识教育课程"
      ["district"] => string(6) "东区"
      ["campus"] => string(9) "教务处"
      ["exam_time"] => string(2) " "
    }
    [1] => array(15) {
      ["name"] => string(15) "声乐与合唱"
      ["code"] => string(9) "ART11000G"
      ["teacher"] => string(6) "马梅"
      ["time"] => string(32) "周二第11,12,13节{第3-12周}"
      ["location"] => string(6) "电110"
      ["credit"] => string(1) "1"
      ["hour"] => string(7) "3.0-0.0"
      ["week"] => string(5) "03-12"
      ["volume"] => string(3) "214"
      ["volume_surplus"] => string(3) "202"
      ["affiliation"] => string(9) "艺术类"
      ["property"] => string(18) "通识教育课程"
      ["district"] => string(6) "东区"
      ["campus"] => string(12) "文法学院"
      ["exam_time"] => string(2) " "
    }
    ...
  }
  ["selected"] => array(0) {
  }
  ["district"] => array(2) {
    [0] => array(2) {
      ["text"] => string(6) "东区"
      ["value"] => string(1) "1"
    }
    [1] => array(2) {
      ["text"] => string(6) "北区"
      ["value"] => string(1) "2"
    }
  }
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
list | array | 通识课信息列表
list.name | string | 课程名称
list.code | string | 课程代码
list.teacher | string | 教师姓名
list.time | string | 上课时间
list.location | string | 上课地点
list.credit | float | 学分
list.hour | string | 周学时
list.week | string | 起始结束周
list.volume | int | 容量
list.volume_surplus | int | 余量
list.affiliation | string | 课程归属
list.property | string | 课程性质
list.district | string | 校区代码
list.campus | string | 开课学院
list.exam_time | string | 考试时间
selected | array | 已选课列表
selected.name | string | 课程名称
selected.teacher | string | 教师名称
selected.credit | float | 学分
selected.week | string | 周学时
selected.week_start_to_end | string | 起始结束周
selected.district | string | 校区
selected.hour | string | 上课时间
selected.location | string | 上课地点
selected.affiliation | string | 课程归属
selected.property | string | 课程性质
selected.code | string | 校区代码
district | array | 校区列表
district.text | string | 校区名称
district.value | string | 校区代码，用于该接口查询时校区筛选


## 已选课列表

### 方法

```
$scheduleSelect->selected() : array
```

### 功能

查询学生已选课列表

### 参数

无

### 返回值

array
```
array(4) {
  [0] => array(8) {
    ["code"] => string(9) "MXI42200E"
    ["name"] => string(15) "形势与政策"
    ["property"] => string(18) "公共基础必修"
    ["direction"] => string(9) "无方向"
    ["credit"] => string(3) "2.0"
    ["hour"] => string(7) "0.0-4.0"
    ["exam_time"] => string(2) " "
    ["status"] => string(6) "已选"
  }
  [1] => array(8) {
    ["code"] => string(9) "HSS39000P"
    ["name"] => string(12) "社会实践"
    ["property"] => string(18) "实践环节必修"
    ["direction"] => string(9) "无方向"
    ["credit"] => string(3) "2.0"
    ["hour"] => string(7) "0.0-0.0"
    ["exam_time"] => string(2) " "
    ["status"] => string(6) "已选"
  }
  ...
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
code | string | 课程代码
name | string | 课程名称
property | string | 课程性质
direction | string | 专业方向
credit | float | 学分
hour | string | 周学时
exam_time | string | 考试时间 
status | string | 选课状态


## 专业可选课列表

### 方法

```
$scheduleSelect->major() : array
```

### 功能

获取专业可选课列表

### 参数

无

### 返回值

array
```
array(4) {
  [0] => array(8) {
    ["code"] => string(9) "MXI42200E"
    ["name"] => string(15) "形势与政策"
    ["property"] => string(18) "公共基础必修"
    ["direction"] => string(9) "无方向"
    ["credit"] => string(3) "2.0"
    ["hour"] => string(7) "0.0-4.0"
    ["exam_time"] => string(2) " "
    ["status"] => string(6) "已选"
  }
  [1] => array(8) {
    ["code"] => string(9) "HSS39000P"
    ["name"] => string(12) "社会实践"
    ["property"] => string(18) "实践环节必修"
    ["direction"] => string(9) "无方向"
    ["credit"] => string(3) "2.0"
    ["hour"] => string(7) "0.0-0.0"
    ["exam_time"] => string(2) " "
    ["status"] => string(6) "已选"
  }
  ...
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
code | string | 课程代码
name | string | 课程名称
property | string | 课程性质
direction | string | 专业方向
credit | float | 学分
hour | string | 周学时
exam_time | string | 考试时间 
status | string | 选课状态


## 获取体育选课列表

### 方法

```
$scheduleSelect->physical() : array
```

### 功能

获取体育选课列表及已选体育课列表

### 参数

无

### 返回值

array
```
array(2) {
  ["list"] => array(17) {
    [0] => array(8) {
      ["name"] => string(6) "健美"
      ["teacher"] => string(6) "刘俭"
      ["hour"] => string(27) "周一第6,7节{第1-16周}"
      ["location"] => string(14) "北体育馆18"
      ["credit"] => string(3) "1.0"
      ["week"] => string(7) "2.0-0.0"
      ["volume"] => string(2) "35"
      ["volume_surplus"] => string(2) "35"
    }
    [1] => array(8) {
      ["name"] => string(9) "健美操"
      ["teacher"] => string(9) "孙伟庆"
      ["hour"] => string(27) "周一第6,7节{第1-16周}"
      ["location"] => string(14) "北体育馆16"
      ["credit"] => string(3) "1.0"
      ["week"] => string(7) "2.0-0.0"
      ["volume"] => string(2) "35"
      ["volume_surplus"] => string(2) "35"
    }
    ...
  }
  ["selected"] => array(1) {
    [0] => array(8) {
      ["code"] => string(36) "(2016-2017-2)-ty0000004-1997500023-2"
      ["name"] => string(9) "健美操"
      ["teacher"] => string(9) "孙伟庆"
      ["credit"] => string(3) "1.0"
      ["week"] => string(7) "2.0-0.0"
      ["hour"] => string(27) "周一第6,7节{第1-16周}"
      ["location"] => string(14) "北体育馆16"
      ["limit"] => string(2) " "
    }
  }
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
list | array | 通识课信息列表
list.name | string | 课程名称
list.teacher | string | 教师姓名
list.hour | string | 周学时
list.location | string | 上课地点
list.credit | float | 学分
list.week | string | 起始结束周
list.volume | int | 容量
list.volume_surplus | int | 余量
selected | array | 已选课列表
selected.code | string | 课程代码
selected.name | string | 课程名称
selected.teacher | string | 教师名称
selected.credit | float | 学分
selected.week | string | 周学时
selected.hour | string | 上课时间
selected.location | string | 上课地点
selected.limit | string | 年级、专业限制
