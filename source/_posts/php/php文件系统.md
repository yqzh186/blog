---
title: php文件系统
date: 2016-10-17 12:38:53
categories: [php]
---
php文件系统
<!-- more -->

<h2>读取文件内容</h2>
PHP具有丰富的文件操作函数，最简单的读取文件的函数为file_get_contents，可以将整个文件全部读取到一个字符串中。

```php
$content = file_get_contents('./test.txt');
```
file_get_contents也可以通过参数控制读取内容的开始点以及长度。

```php
$content = file_get_contents('./test.txt', null, null, 100, 500);
```
PHP也提供类似于C语言操作文件的方法，使用fopen，fgets，fread等方法，fgets可以从文件指针中读取一行，freads可以读取指定长度的字符串。

```php
$fp = fopen('./text.txt', 'rb');
while(!feof($fp)) {
    echo fgets($fp); //读取一行
}
fclose($fp);
 
$fp = fopen('./text.txt', 'rb');
$contents = '';
while(!feof($fp)) {
    $contents .= fread($fp, 4096); //一次读取4096个字符
}
fclose($fp);
```
使用fopen打开的文件，最好使用fclose关闭文件指针，以避免文件句柄被占用。

<h2>判断文件是否存在</h2>
一般情况下在对文件进行操作的时候需要先判断文件是否存在，PHP中常用来判断文件存在的函数有两个is_file与file_exists.

```php
$filename = './test.txt';
if (file_exists($filename)) {
    echo file_get_contents($filename);
}
```
如果只是判断文件存在，使用file_exists就行，file_exists不仅可以判断文件是否存在，同时也可以判断目录是否存在，从函数名可以看出，is_file是确切的判断给定的路径是否是一个文件。

```php
$filename = './test.txt';
if (is_file($filename)) {
    echo file_get_contents($filename);
}
```
更加精确的可以使用is_readable与is_writeable在文件是否存在的基础上，判断文件是否可读与可写。

```php
$filename = './test.txt';
if (is_writeable($filename)) {
    file_put_contents($filename, 'test');
}
if (is_readable($filename)) {
    echo file_get_contents($filename);
}
```

<h2>取得文件的修改时间</h2>
文件有很多元属性，包括：文件的所有者、创建时间、修改时间、最后的访问时间等。
+ fileowner：获得文件的所有者
+ filectime：获取文件的创建时间
+ filemtime：获取文件的修改时间
+ fileatime：获取文件的访问时间
其中最常用的是文件的修改时间，通过文件的修改时间，可以判断文件的时效性，经常用在静态文件或者缓存数据的更新。

```php
$mtime = filemtime($filename);
echo '修改时间：'.date('Y-m-d H:i:s', filemtime($filename));
```

<h2>取得文件的大小</h2>
通过filesize函数可以取得文件的大小，文件大小是以字节数表示的。

```php
$filename = '/data/webroot/usercode/resource/test.txt';
$size = filesize($filename);
```
如果要转换文件大小的单位，可以自己定义函数来实现。

```php
function getsize($size, $format = 'kb') {
    $p = 0;
    if ($format == 'kb') {
        $p = 1;
    } elseif ($format == 'mb') {
        $p = 2;
    } elseif ($format == 'gb') {
        $p = 3;
    }
    $size /= pow(1024, $p);
    return number_format($size, 3);
}

$filename = '/data/webroot/usercode/code/resource/test.txt';
$size = filesize($filename);

$size = getsize($size, 'kb'); //进行单位转换
echo $size.'kb';
```
值得注意的是，没法通过简单的函数来取得目录的大小，目录的大小是该目录下所有子目录以及文件大小的总和，因此需要通过递归的方法来循环计算目录的大小。









<!--<img src="/images/6.png" width="800" height="263" />-->
<!--<font color=#FF6666></font>-->
