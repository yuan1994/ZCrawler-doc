# 全校课表

## 获取实例

```
$scheduleSchool = $zCrawler->schedule_school;
```


## 保存课表到缓存

### 方法

```
$scheduleSchool->saveDataToCache($cachePath) : int
```

### 功能

保存课表到指定缓存路径，由于全校课表数据量大，不适合直接一次性解析，保存的缓存文件都是 `/path/to/cache/1.html`, `/path/to/cache/2.html`, 其中数字代表页码

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$cachePath | string | Y | 缓存路径，例如 'storage/'，必须以 `/` 结尾

### 返回值

`int` 全校课表总页数


## 解析课表成数组

### 方法

```
$scheduleSchool->parseHtml($html) : array

```

### 功能

将保存到本地的 HTML 缓存文件解析成数组

### 参数

参数名称 | 参数类型 | 是否必须 | 说明
:--- | :--- | :---: | :---
$html | string | Y | 缓存到本地的 html

### 使用示例

```
$scheduleSchool = $zCrawler->schedule_school;

$cachePath = '/path/to/cache/';

$pageCount = $schedule->saveDataToCache($cachePath);

for ($page = 1; $page <= $pageCount; $page ++) {
    $filePath = $cachePath . $page . '.html';
    $dataList = $scheduleSchool->parseHtml(file_get_content($filePath));
    // TODO 保存数据到数据库 and so on
}

```

### 返回值

array
```
array(14) {
  [0] => array(12) {
    ["status"] => string(6) "已开"
    ["name"] => string(12) "基础摄影"
    ["credit"] => string(3) "2.0"
    ["examination"] => string(6) "考查"
    ["property"] => string(12) "专业选修"
    ["teacher"] => string(9) "王一珉"
    ["code"] => string(36) "(2016-2017-2)-ART24200E-1987500023-2"
    ["week"] => string(5) "02-09"
    ["hour"] => string(2) " "
    ["place"] => string(2) " "
    ["campus"] => string(18) "机电工程学院"
    ["class"] => string(10) "数媒1601"
  }
  [1] => array(12) {
    ["status"] => string(6) "已开"
    ["name"] => string(18) "物流系统规划"
    ["credit"] => string(3) "2.0"
    ["examination"] => string(6) "考试"
    ["property"] => string(12) "专业必修"
    ["teacher"] => string(6) "吴军"
    ["code"] => string(36) "(2016-2017-2)-BUS34227C-2013500015-1"
    ["week"] => string(5) "03-18"
    ["hour"] => string(27) "周三第3,4节{第3-18周}"
    ["place"] => string(6) "教602"
    ["campus"] => string(18) "经济管理学院"
    ["class"] => string(21) "物流1401,物流1402"
  }
  ...
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
status | string | 开课状态
name | string | 课程名称
credit | float | 学分
examination | string | 考核方式
property | string | 课程性质
teacher | string | 任课教师
code | string | 选课课号
week | string | 起止周
hour | string | 上课时间
place | string | 上课地点
campus | string | 开课学院
class | string | 合班信息
