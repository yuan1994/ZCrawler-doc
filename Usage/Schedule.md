# 个人课表

## 获取实例

```
$schedule = $zCrawler->schedule;
```


## 获取当前学期课表

### 方法

```
$schedule->current() : array
```

### 功能

获取当前学期课表


### 参数

无

### 返回值

array
```
array(3) {
  ["normal"] => array(13) {
    [0] => array(9) {
      [0] => string(6) "上午"
      [1] => string(7) "第1节"
      [2] => string(2) " "
      [3] => string(2) " "
      [4] => string(2) " "
      [5] => string(2) " "
      [6] => string(2) " "
      [7] => string(2) " "
      [8] => string(70) "形势与政策<br>周日第1,2节{第12-13周}<br>王俊琪<br>电110"
    }
    [1] => array(9) {
      [0] => string(6) "上午"
      [1] => string(7) "第2节"
      [2] => string(2) " "
      [3] => string(2) " "
      [4] => string(2) " "
      [5] => string(2) " "
      [6] => string(2) " "
      [7] => string(2) " "
      [8] => string(70) "形势与政策<br>周日第1,2节{第12-13周}<br>王俊琪<br>电110"
    }
    ...
  }
  ["no_time"] => array(2) {
    [0] => array(5) {
      ["year"] => string(9) "2016-2017"
      ["term"] => string(1) "2"
      ["name"] => string(35) "毕业环节：毕业设计(论文)"
      ["teacher"] => string(9) "冯志芳"
      ["credit"] => string(4) "16.0"
    }
    [1] => array(5) {
      ["year"] => string(9) "2016-2017"
      ["term"] => string(1) "2"
      ["name"] => string(12) "社会实践"
      ["teacher"] => string(9) "丁贞栋"
      ["credit"] => string(3) "2.0"
    }
  }
  ["student"] => array(5) {
    ["number"] => string(10) "2013016077"
    ["name"] => string(6) "田片"
    ["campus"] => string(9) "理学院"
    ["major"] => string(21) "电子科学与技术"
    ["class"] => string(10) "电科1303"
  }
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
normal | array | 正常教学课表，具有具体上课时间、地点
normal.0 | string | 时间，上午；中午；下午
normal.1 | string | 节数，第几节
normal.2-8 | string | 周一 - 周日的课程
no_time | array | 未安排上课时间的课程
no_time.year | string | 学年
no_time.term | int | 学期，1 - 3
no_time.name | string | 课程名称
no_time.teacher | string | 教师姓名
no_time.credit | float | 学分
student | array | 学生信息数组
student.number | string | 学号
student.name | string | 姓名
student.campus | string | 学院
student.major | string | 专业
student.class | string | 班级


## 根据学年学期获取课表

### 方法

```
$schedule->getByTerm($year, $term) : array
```
### 功能

根据指定的学年学期获取课表，如果是当前学期，不可使用该方法，否则获取不到数据

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$year | string | Y | 学年，例如 '2016-2017'
$term | int | Y | 学期，例如 1

### 返回值

同 [获取当前学期课表] 接口返回值
