# ZCrawler

## ZCrawler 是什么？

ZCrawler 是一个优雅、高效、功能强大的【正方教务】爬虫程序，支持成绩查询、考试查询、课表查询、四六级成绩查询、四六级报名、选课查询、修改密码、获取用户菜单等功能，并且能将数据解析成易读格式，是一个强大的【正方教务】爬虫的 PHP 类库。


## 项目地址

ZCrawler：[https://github.com/yuan1994/ZCrawler](https://github.com/yuan1994/ZCrawler)

文档：[http://zcrawler.yuan1994.com](http://zcrawler.yuan1994.com)

文档仓库：[https://github.com/yuan1994/ZCrawler-doc](https://github.com/yuan1994/ZCrawler-doc)


## 使用示例

```
use ZCrawler\Foundation\ZCrawler;

$config = include '/path/to/config.php';

// 实例化
$zCrawler = new ZCrawler($username, $password, $config);

// 查成绩
$grade = $zCrawler->grade;
// 历年成绩
$grade->history();
// 成绩统计
$grade->state();
// 培养计划
$grade->trainingPlan();

// 四六级
$cet = $zCrawler->cet;
// 四六级成绩
$cet->grade();
// 四六级报名
$cet->page();
$cet->submit();
$cet->delete();

// 查询课表
$schedule = $zCrawler->schedule;
// 当前学期课表
$schedule->current();
// 2015-2016学年第2学期课表
$schedule->getByTerm('2016-2017', 2);
```

更多使用方法请参考 [基本使用](Usage.md)


## 适合那些人用？

适合在校大学生，并且能熟练编写 PHP 代码，教务系统使用的【正方教务】的人使用，由于 PC 端教务网使用不方便，如果将教务网做成 App 或者微信公众号等适用于移动端的网页就方便多了。


## 有什么特点？

* 代码遵守 psr 规范，优雅整洁
* 专注于业务，不用考虑登录问题，自动缓存 cookie, 按需自动刷新 cookie
* 直接绕过验证码登录教务网帐号
* 如果免验证码登录入口关闭，可以抓取验证码然后使用验证码识别 + 手工填写验证码方式登录
* 支持网络代理，学校 VPN 也墙不了在校外的服务器
* 支持除选课、学生个人信息抓取之外的大部分功能，功能齐全


## 环境需求

* [PHP](http://php.net) >= 5.5.9
* [cUrl](http://php.net/manual/en/book.curl.php) 扩展
* [fileinfo](http://php.net/manual/en/book.fileinfo.php) 拓展（教务通知自动生成附件名需要）
