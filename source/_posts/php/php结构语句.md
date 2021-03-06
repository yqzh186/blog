---
title: php结构语句
date: 2016-10-14 09:51:50
categories: [php]
---
顺序结构 条件结构 循环结构 
<!-- more -->

<h2>顺序结构</h2>
顺序结构就像一条直线，按着顺序一直往下执行。我们编写的代码默认都是按照顺序结构执行的。

<h2>条件结构</h2>

<h3>if else</h3>
```php
<?php
if(条件){
     //分配服务器干的任务A
}else{
     //分配服务器干的任务B
}
?>

<?php
if(条件一){
     //分配服务器干的任务A
}else if(条件二){
     //分配服务器干的任务B
}
?>

<?php
if(条件一){
     //分配服务器干的任务A
}else if(条件二){
     //分配服务器干的任务B
}else{
     //分配服务器干的任务C
}
?>
```
<h3>switch</h3>
```php
<?php
switch (条件)
{
case 条件值一:
  //任务一
  break; 
case 条件值二:
  //任务二
  break;
default:
  //默认任务
}
?>
break的作用是阻止代码进入下一个case 中继续执行
```

<h2>循环结构</h2>

<h3>while</h3>
```php
<?php
while(条件){ 
     //执行任务
}
?>
```
<h3>do while</h3>
```php
<?php
do{ 
     //执行任务
}while(条件)
?>
```
<h3>for</h3>
```php
<?php
for(初始化;循环条件;递增项){
      //执行任务
}
?>
```

<h3>foreach</h3>
在PHP中foreach循环语句，常用于遍历数组，一般有两种使用方式:
+ 不取下标
+ 取下标

```php
（1）只取值，不取下标
<?php
 foreach (数组 as 值){
//执行的任务
}
?>
（2）同时取下标和值
<?php
foreach (数组 as 下标 => 值){
 //执行的任务
}
?>
```
```php
<?php
$students = array(
'2010'=>'令狐冲',
'2011'=>'林平之',
'2012'=>'曲洋',
'2013'=>'任盈盈',
'2014'=>'向问天',
'2015'=>'任我行',
'2016'=>'冲虚',
'2017'=>'方正',
'2018'=>'岳不群',
'2019'=>'宁中则',
);//10个学生的学号和姓名，用数组存储

//使用循环结构遍历数组,获取学号和姓名  
foreach($students as  $v)
{ 
    echo $v;//输出（打印）姓名
	echo "<br />";
}
?>

结果
令狐冲
林平之
曲洋
任盈盈
向问天
任我行
冲虚
方正
岳不群
宁中则
```

```php
<?php
$students = array(
'2010'=>'令狐冲',
'2011'=>'林平之',
'2012'=>'曲洋',
'2013'=>'任盈盈',
'2014'=>'向问天',
'2015'=>'任我行',
'2016'=>'冲虚',
'2017'=>'方正',
'2018'=>'岳不群',
'2019'=>'宁中则',
);//10个学生的学号和姓名，用数组存储

//使用循环结构遍历数组,获取学号和姓名  
foreach($students as $key =>$v)
{ 
    echo $key.":".$v;//输出（打印）学号：姓名
	echo "<br />";
}
?>

结果
2010:令狐冲
2011:林平之
2012:曲洋
2013:任盈盈
2014:向问天
2015:任我行
2016:冲虚
2017:方正
2018:岳不群
2019:宁中则
```



<!--<img src="/images/6.png" width="800" height="263" />-->
<!--<font color=#FF6666></font>-->
