# 用户主页

## 获取实例

```
$userMain = $zCrawler->user_main;

```


## 获取用户菜单

### 方法

```
$userMain->menu() : array;
```

### 功能

获取用户教务网所有可用菜单，可以用于实时控制哪些功能可用，例如教务网关闭成绩查询功能时获取到的菜单里就没有成绩查询的菜单，此时可以控制应用关闭相应的功能

### 参数

无

### 返回值

array
```
array(2) {
  ["menu"] => array(21) {
    [0] => array(3) {
      ["url_raw"] => string(48) "xsxk.aspx?xh=2013016077&xm=田片&gnmkdm=N121101"
      ["url_base"] => string(9) "xsxk.aspx"
      ["title"] => string(51) "选修课、双语课、特殊课程（研讨课）"
    }
    [1] => array(3) {
      ["url_raw"] => string(53) "xf_xstyxk.aspx?xh=2013016077&xm=田片&gnmkdm=N121102"
      ["url_base"] => string(14) "xf_xstyxk.aspx"
      ["title"] => string(18) "体育项目选课"
    }
    ...
  }
  ["info"] => array(2) {
    ["student_number"] => string(10) "2013016077"
    ["student_name"] => string(6) "田片"
  }
}
```

参数名称 | 参数类型 | 说明
:--- | :--- | :---
menu | array | 菜单列表数组
menu.url_raw | string | 菜单完整链接
menu.url_base | string | 菜单简化链接
menu.title | string | 菜单名称
info | array | 学生信息数组
info.student_number | string | 学号
info.student_name | string | 姓名
