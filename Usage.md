# 基本使用

## 基本使用

```
use ZCrawler\Foundation\ZCrawler;

// 载入配置项，详情请参考 [配置]
$config = [
    ...
];

// 学生帐号、密码
$username = '2016066666';
$password = 'your password';

// 实例化对象
$zCrawler = new ZCrawler($username, $password, $config);

// 实例化成绩查询应用
$grade = $zCrawler->grade;

// 返回结果
$result = $grade->getByTerm('2016-2017', 1);

// 打印出结果
echo '<pre>';
var_dump($result);
echo '</pre>';

```
