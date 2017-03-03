# 助手函数

## 解析课表

### 方法

```
use ZCrawler\Support\Parser;

Parser::schedule($body, $selector = '#Table1') : array
```

### 功能

将课表成易读的数组格式，使用了 Symfony 框架的组件 DomCrawler ，详情请参考 [http://symfony.com/doc/current/components/dom_crawler.html](http://symfony.com/doc/current/components/dom_crawler.html)

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$body | string\Crawler | Y | HTML 代码字符串或者 `Symfony\Component\DomCrawler\Crawler` 对象
$selector | string | N | 选择器，请参考 DomCrawler 文档

### 返回值

array
```
array(13) {
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
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
0 | string | 时间，上午；中午；下午
1 | string | 节数，第几节
2-8 | string | 周一 - 周日的课程


## 解析表格

### 方法

```
use ZCrawler\Support\Parser;

Parser::table($body, $selector = '#DataGrid1', $header = [], $columnCount = 0, $startLine = 1, $getValueMethod = 'html') : array
```

### 功能

快速解析一个表格里的数据，将其转化为数组，使用了 Symfony 框架的组件 DomCrawler ，详情请参考 [http://symfony.com/doc/current/components/dom_crawler.html](http://symfony.com/doc/current/components/dom_crawler.html)

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$body | string\Crawler | Y | HTML 代码字符串或者 `Symfony\Component\DomCrawler\Crawler` 对象
$selector | string | N | 选择器，请参考 DomCrawler 文档
$header | array | N | 设置此项，可以将本来输出的索引数组转化为关联数组，例如原来返回的结果为 $result = ['a', 'b', 'c'], 设置 $header = ['field1', 'field2', 'field3'] 后，返回结果为 $newResult = ['field1' => 'a', 'field2' => 'b', 'field3' => 'c']
$columnCount | int | N | 列的数量大于等于此值时才输出，防止设置 $header 后因某些行的列数不够喝抛出异常，所以设置了 $header 后此值一定要设置，如果为0，表示不受限制，默认为 0
$startLine | int | N | 从哪一行（索引）开始读取，默认是第 1 行（索引），自动过滤掉第 0 行的表头
$getValueMethod | string | N | 获取值的方法，html - 获取值的 html；text - 获取值的纯文本，默认为 html

### 返回值

array
```
// 假设不设置 $header 输出
array(6) {
    [0] => array(4) {
      [0] => string(18) "第一列"
      [1] => string(1) "第二列"
      [2] => string(1) "这一列不要了"
      [3] => string(1) "第四列"
    }
    [1] => array(4) {
      [0] => string(18) "第一列"
      [1] => string(1) "第二列"
      [2] => string(1) "这一列不要了"
      [3] => string(1) "第四列"
    }
    [2] => array(3) {
      [0] => string(18) "第一列"
      [1] => string(1) "第二列"
      [2] => string(1) "不同凡响，少一列"
    }
    ...
}

// 设置 $header = ['header1', 'header2', '', 'header4'], $column = 4
// 因为 $header 的第三项为空，所以结果的第三列被过滤了，因为 $column 为 4，所以第三行被过滤了
array(5) {
    [0] => array(4) {
      ['header1'] => string(18) "第一列"
      ['header2'] => string(1) "第二列"
      ['header4'] => string(1) "第四列"
    }
    [1] => array(4) {
      ['header1'] => string(18) "第一列"
      ['header2'] => string(1) "第二列"
      ['header4'] => string(1) "第四列"
    }
    ...
}
```


## 获取表单控件的值

### 方法

```
use ZCrawler\Support\Parser;

Parser::fieldName($body, $fieldName, $attr = 'value') : string

```

### 功能

快速获取 HTML 里 input[name="$fieldName"] 的值，例如获取 __VIEWSTATE 的方法为 Parser::fieldName($body, '__VIEWSTATE')

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$body | string\Crawler | Y | HTML 代码字符串或者 `Symfony\Component\DomCrawler\Crawler` 对象
$fieldName | string | Y | 表单控件 name 值
$attr | string | N | 属性名，一般为 value

### 返回值

string 获取表单控件的值


## 解析课表上课时间

### 方法

```
use ZCrawler\Support\Parser;

Parser::scheduleClassHour($str) : array
```

### 功能

将课表中的上课时间解析成数组

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$str | string | Y | 上课时间字符串

### 返回值

array
```
// $str = '大学英语B<br>周四第6,7节{第1-17周|单周}<br>陈雪峰<br>北809<br>2017年06月27日(13:30-15:30)<br><br>大学英语B<br>周四第6,7节{第2-18周|双周}<br>陈雪峰<br>北613<br>2017年06月27日(13:30-15:30)';

array(2) {
  [0] => array(11) {
    ["name"] => string(13) "大学英语B"
    ["week"] => string(3) "四"
    ["time_section"] => string(3) "6,7"
    ["week_section"] => string(4) "1-17"
    ["week_remark"] => string(3) "单"
    ["teacher"] => string(9) "陈雪峰"
    ["location"] => string(6) "北809"
    ["exam_y"] => string(4) "2017"
    ["exam_m"] => string(2) "06"
    ["exam_d"] => string(2) "27"
    ["exam_h"] => string(11) "13:30-15:30"
  }
  [1] => array(11) {
    ["name"] => string(13) "大学英语B"
    ["week"] => string(3) "四"
    ["time_section"] => string(3) "6,7"
    ["week_section"] => string(4) "2-18"
    ["week_remark"] => string(3) "双"
    ["teacher"] => string(9) "陈雪峰"
    ["location"] => string(6) "北613"
    ["exam_y"] => string(0) ""
    ["exam_m"] => string(0) ""
    ["exam_d"] => string(0) ""
    ["exam_h"] => string(0) ""
  }
}

```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
name | string | 课程名称
week | string | 周几，一 - 六、日
time_section | string | 从第几节课到第几节课
week_section | string | 从第几周到第几周
week_remark | string | 是否单周、双周、或者为空字符串 - 不限单双周，也有特殊情况：3节/，详情请看后面备注
teacher | string | 教师名称
location | string | 上课地点
exam_y | string | 考试时间 - 年，yyyy 格式
exam_m | string | 考试时间 - 月，mm 格式
exam_d | string | 考试时间 - 日，dd 格式
exam_h | string | 考试时间 - 小时时间范围，hh:mm-hh:mm 格式


## 解析考试时间

### 方法

```
use ZCrawler\Support\Parser;

Parser::examTime($str) : array
```

### 功能

将考试时间解析成数组

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$str | string | Y | 考试时间字符串

### 返回值

array
```
// $str = '2016年06月24日(10:30-12:30)';

array(2) {
  ["date"] => string(10) "2016-06-24"
  ["time"] => string(11) "10:30-12:30"
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
date | date | 考试日期，yyyy-mm-dd 格式
time | string | 考试时间范围，hh:mm-hh:mm 格式


## 选课时间解析

### 方法

```
use ZCrawler\Support\Parser;

Parser::scheduleSelectTime($str) : array
```

### 功能

将选课时间解析成数组

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$str | string | Y | 选课时间字符串

### 返回值

array
```
// $str = '周二第11,12,13节{第3-10周|单周}';

array(4) {
  ["week"] => string(3) "二"
  ["time_section"] => string(8) "11,12,13"
  ["week_section"] => string(4) "3-10"
  ["week_remark"] => string(3) "单"
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
week | string | 周几，一 - 六、日
time_section | string | 从第几节课到第几节课
week_section | string | 从第几周到第几周
week_remark | string | 是否单周、双周、或者为空字符串 - 不限单双周，也有特殊情况：3节/，详情请看后面备注


## 解析有多个选课时间组合的时间

### 方法

```
use ZCrawler\Support\Parser;

Parser::multiScheduleSelectTime($str) : array
```

### 功能

将多个选课时间组合的时间解析成数组

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$str | string | Y | 选课时间字符串

### 返回值

array
```
// $str = '周日第3,4,5节{第3-10周};周日第8,9,10节{第3-10周|单周}';

array(2) {
  [0] => array(4) {
    ["week"] => string(3) "日"
    ["time_section"] => string(5) "3,4,5"
    ["week_section"] => string(4) "3-10"
    ["week_remark"] => string(0) ""
  }
  [1] => array(4) {
    ["week"] => string(3) "日"
    ["time_section"] => string(6) "8,9,10"
    ["week_section"] => string(4) "3-10"
    ["week_remark"] => string(3) "单"
  }
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
week | string | 周几，一 - 六、日
time_section | string | 从第几节课到第几节课
week_section | string | 从第几周到第几周
week_remark | string | 是否单周、双周、或者为空字符串 - 不限单双周，也有特殊情况：3节/，详情请看后面备注


## 解析长课程代码为详细的课程代码

### 方法

```
use ZCrawler\Support\Parser;

Parser::courseCode($str) : array
```

### 功能

解析长课程代码为详细的课程代码

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$str | string | Y | 参数代码

### 返回值

array
```
// $str = '(2015-2016-2)-EEE21503T-2010500001-1';

array(5) {
  ["year"] => string(9) "2015-2016"
  ["term"] => string(1) "2"
  ["code"] => string(9) "EEE21503T"
  ["teacher_job_number"] => string(10) "2010500001"
  ["no"] => string(1) "1"
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
year | string | 学年
term | string | 学期
code | string | 课程代码
teacher_job_number | string | 教师工号
no | string | 序号


## 备注

### 特殊课表上课时间解析

课表中上课时间有一种特殊格式：`经济学原理<br>{第3-18周|3节/周}<br>高歌<br>电110<br>`，上述解析方法返回的数组值 `week_remark` 的可能值不仅仅只有 `单`；`双`；`空字符串`，还有 `3节/`，根据其中的数字以及当前是周几、第几节课解析出该课是在周几第几节课到第几节课之间上，该格式字符串返回值请自行测试
