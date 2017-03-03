# 成绩查询

## 获取实例

```
$grade = $zCrawler->grade;
```

## 成绩统计

### 方法

```
$grade->state() : array
```

### 功能

查询成绩统计

### 参数

无

### 返回值

array
```
array(4) {
  ["overview"] => array(4) {
    ["selected"] => string(6) "xxx"
    ["get"] => string(6) "xxx"
    ["restudy"] => string(5) "xxx"
    ["fail"] => string(2) "xxx"
  }
  ["property"] => array(6) {
    [0] => array(5) {
      ["item_name"] => string(18) "通识教育课程"
      ["require"] => string(1) "xxx"
      ["get"] => string(1) "xxx"
      ["fail"] => string(1) "xxx"
      ["need"] => string(1) "xxx"
    }
    [1] => array(5) {
      ["item_name"] => string(18) "公共基础必修"
      ["require"] => string(5) "73.50"
      ["get"] => string(5) "71.50"
      ["fail"] => string(1) "0"
      ["need"] => string(1) "2"
    }
    [2] => array(5) {
      ["item_name"] => string(18) "公共基础选修"
      ["require"] => string(1) "xxx"
      ["get"] => string(1) "xxx"
      ["fail"] => string(1) "xxx"
      ["need"] => string(1) "xxx"
    }
    [3] => array(5) {
      ["item_name"] => string(18) "实践环节必修"
      ["require"] => string(2) "xxx"
      ["get"] => string(2) "xxx"
      ["fail"] => string(1) "xxx"
      ["need"] => string(2) "xxx"
    }
    [4] => array(5) {
      ["item_name"] => string(12) "专业必修"
      ["require"] => string(2) "xxx"
      ["get"] => string(2) "xxx"
      ["fail"] => string(1) "xxx"
      ["need"] => string(1) "xxx"
    }
    [5] => array(5) {
      ["item_name"] => string(12) "专业选修"
      ["require"] => string(5) "xxx"
      ["get"] => string(2) "xxx"
      ["fail"] => string(1) "xxx"
      ["need"] => string(3) "xxx"
    }
  }
  ["affiliation"] => array(5) {
    [0] => array(5) {
      ["item_name"] => string(9) "管理类"
      ["require"] => string(1) "0"
      ["get"] => string(1) "0"
      ["fail"] => string(1) "0"
      ["need"] => string(1) "0"
    }
    [1] => array(5) {
      ["item_name"] => string(9) "科技类"
      ["require"] => string(1) "0"
      ["get"] => string(1) "4"
      ["fail"] => string(1) "0"
      ["need"] => string(1) "0"
    }
    [2] => array(5) {
      ["item_name"] => string(15) "人文社科类"
      ["require"] => string(1) "0"
      ["get"] => string(1) "0"
      ["fail"] => string(1) "0"
      ["need"] => string(1) "0"
    }
    [3] => array(5) {
      ["item_name"] => string(9) "体育类"
      ["require"] => string(1) "0"
      ["get"] => string(1) "0"
      ["fail"] => string(1) "0"
      ["need"] => string(1) "0"
    }
    [4] => array(5) {
      ["item_name"] => string(9) "艺术类"
      ["require"] => string(1) "0"
      ["get"] => string(1) "2"
      ["fail"] => string(1) "0"
      ["need"] => string(1) "0"
    }
  }
  ["info"] => array(4) {
    ["people"] => string(2) "xxx"
    ["gpa"] => string(4) "xxx"
    ["gp_sum"] => string(6) "xxx"
    ["update_time"] => string(19) "2016-11-30 14:13:39"
  }
}

```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
overview | array | 学分概览
overview.selected | float | 所选学分
overview.get | float | 获得学分
overview.restudy | float | 重修学分
overview.fail | float | 正考未通过学分
property | array | 课程性质信息
property.item_name | string | 课程性质名称	
property.require | float | 学分要求
property.get | float | 获得学分
property.fail | float | 未通过学分
property.need | float | 还需学分
affiliation | array | 课程归属信息
affiliation.item_name | string | 课程归属名称
affiliation.require | float | 学分要求
affiliation.get | float | 获得学分
affiliation.fail | float | 未通过学分
affiliation.need | float | 还需学分
info | array | 其他信息数组
info.people | int | 本专业总人数
info.gpa | float | 所有课程平均学分绩点
info.gp | float | 学分绩点总和
info.update_time | datetime | 统计时间


## 历年成绩

### 方法

```
$grade->history() : array
```

### 功能

获取学生历史以来所有的成绩，免去按学期查询的烦恼

### 参数

无

### 返回值

array
```
array(70) {
  [0] => array(15) {
    ["year"] => string(9) "2013-2014"
    ["term"] => string(1) "1"
    ["code"] => string(9) "CSE10300C"
    ["name"] => string(21) "大学计算机基础"
    ["property"] => string(18) "公共基础必修"
    ["affiliation"] => string(2) " "
    ["credit"] => string(3) "2.5"
    ["gp"] => string(7) "   4.33"
    ["grade"] => string(2) "A+"
    ["minor_flag"] => string(1) "0"
    ["make_up"] => string(2) " "
    ["restudy"] => string(2) " "
    ["campus"] => string(27) "信息科学与技术学院"
    ["remark"] => string(0) ""
    ["restudy_flag"] => string(0) ""
  }
  ...
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
year | string | 学年
term | string | 学期
code | string | 课程代码
name | string | 课程名称
property | string | 课程性质
affiliation | string | 课程归属
credit | float | 学分
gp | string | 绩点
grade | string | 成绩
minor_flag | string | 辅修标记
make_up | string | 补考成绩
restudy | string | 重修成绩
campus | string | 开课学院
remark | string | 备注
restudy_flag | string | 重修标记


## 培养计划

### 方法

```
$grade->trainingPlan() : array
```

### 功能

查询培养计划

### 参数

无

### 返回值

array
```
array(95) {
  [0] => array(14) {
    ["code"] => string(9) "CSE10300C"
    ["name"] => string(21) "大学计算机基础"
    ["credit"] => string(3) "2.5"
    ["hour"] => string(7) "2.5-1.0"
    ["examination"] => string(6) "考查"
    ["property"] => string(18) "公共基础必修"
    ["kind"] => string(12) "公共基础"
    ["term"] => string(1) "1"
    ["minor"] => string(2) " "
    ["direction"] => string(9) "无方向"
    ["group_code"] => string(2) " "
    ["module_code"] => string(2) " "
    ["status"] => string(3) "√"
    ["week"] => string(5) "01-18"
  }
  ...
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
code | string | 课程代码
name | string | 课程名称
credit | float | 学分
hour | string | 周学时
examination | string | 考核方式
property | string | 课程性质
kind | string | 课程类别
term | string | 建议修读学期
minor | string | 辅修标识
direction | string | 专业方向
group_code | string | 组代码
module_code | string | 模块代码
status | string | 通过情况
week | string | 起始结束周
