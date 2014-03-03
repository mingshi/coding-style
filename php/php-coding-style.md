#PHP源代码规范

## 编辑器设置
 * 字符集使用 **UTF-8**
 * 缩进使用 **4个字符的空格**, 不实用TAB制表符
 * 使用'\n'作为行结束符

## Naming conventions

### 变量
  * 名词，全部使用小写字符
  * 使用驼峰风格
  * 循环可以使用简单变量名

```php
<?php
$debugLevel = 3;

for ($i = 0; $i < 10; $i++) {
}
```

### Class
  * 名词，大写字母开始
  * 多个单词组成的，每个单词的第一个字母大写
  * 命名空间之间用下划线分割

```php
<?php
class Model_Order_Info {
}
```

### Function/Method Name
  * 动词，全部使用小写字符
  * 单词之间使用下划线分割

```php
<?php
/**
 * @param ...
 */
 function get_user_info($uid) {
 }

 class Adeaz {
    /**
     * return Adeaz
     */
     public static function get_instance() {
     }
 }
```

### Parameter
同变量

### Constant
 * 名词，全部使用大写字符
 * 单词之间用下划线分割

```php
<?php
define('BASE_INFO', 'Test')

class Foo {
    const FOO_BAR = "test";
}
```

## Coding Style

### PHP Tag

 * 在`*.php`的源代码文件里不使用`?>`关闭标签

```php
<?php
// 正确

// do something awesome
```

```php
<?php
// 错误

// do something awesome, but minor bad?

?>
```

 * 在(P)HTML模板里输出变量时推荐使用`<?= ?>`，其他情况仍使用`<?php ?>`。
    * **注意，需要打开`php.ini`里`short_open_tag`的选项**
    * PHP 5.4开始 `<?= ?>`的用法和`short_open_tag`选项无关可以直接使用

```phtml
<!-- 正确 -->
<?= $foo ?>
<?php $bar = 1; ?>

<!-- 错误 -->
<?php echo $foo ?>
<? $bar = 1; ?>
```

### Braces
 * 强制使用花括号，即使不需要使用
 * 起始花括号在一行的最后，结束花括号独立一行

```php
<?php
// 正确
if ($foo == $bar) {
    echo 'equals';
}

// 错误
if ($foo == $bar) echo 'equals';
if ($foo == $bar)
    echo 'equals';
```


### Spaces

 * 缩进使用 **4个字符的空格** ，不使用TAB制表符。建议使用anyedit插件，可以方便的将tab缩进转换为空格缩进
 * 标识符之间使用一个空格区分
 * 行尾去掉无用的空格

```php
<?php
// 正确
$i = 0;
if (($i < 2) || ($i > 5)) {
}
foo($a, $b, $c);
$i = ($j < 5) ? $j : 5;

// 错误
$i=0;
if(( $i<2 )||( $i>5 )) {
}
foo ( $a,$b,$c );
$i=($j<5)?$j:5;
```

### Quotes

  * 缺省 **使用单引号**
  * ***需要转义或内嵌变量时*** **使用双引号**

```php
<?php
// 正确
echo 'Hello, World!';
echo "Hello, {$name}";

// 错误
echo "Hello, World!";
echo 'Hello, ' . $name;
```

### SQL
SQL关键字使用大写，数据库对象使用小写。

```sql
SELECT id, name FROM foobar WHERE updated < :updated ORDER BY display_order;
```

### 换行
一行不要太长到难以阅读。

### Comment
提供给其他开发人员调用的代码，建议使用phpdoc格式的注释，特别是函数的返回类型。

