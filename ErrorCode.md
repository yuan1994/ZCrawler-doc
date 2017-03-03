# 返回码参照

在使用过程中，可能因为一些意外情况抛出异常，一般异常都设置了返回码，请根据返回码进行相应的异常处理：
```
use ZCrawler\Foundation\ZCrawler;
use ZCrawler\Core\Exception;

$zCrawler = new ZCrawler($username, $password, $config);

$login = $zCrawler->login;

try {
    $login->noCode();
} catch (Exception $e) {
    if ($e->getCode() == 10002) {
        // 帐号或密码错误
    }
} catch (\InvalidArgumentException $e) {
    // 返回的 HTML 文件结构和预期不同，说明出现了错误，请进行相应异常处理
    // 该异常不带返回码，为 Symfony\Component\DomCrawler\Crawler 对象解析 HTML 文件时抛出的异常
}
```


## ZCrawler\Core\Exception 异常返回码参照

返回码 | 说明
:---: | :---
10001 | 获取参数V失败
10002 | 帐号或密码不正确
10003 | 登录失败
10004 | 登录过程中发生错误，例如验证码错误或者不可预期的错误
10005 | 获取验证码失败
10006 | 修改密码过程中发生错误
10007 | 修改密码失败（未知错误）
10008 | 四六级协议同意失败
