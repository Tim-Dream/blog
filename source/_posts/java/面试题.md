---
title: JAVA面试题
date: 2025-04-02 22:10:06
index_img: /img/java.png
categories:
- JAVA
tags:
- 面试题
---

#### JAVA
##### JAVA基础
###### Java基础数据类型
- 整数类型
    - `byte` 8 位，范围 -128 到 127
    - `short` 16 位，范围 -32,768 到 32,767
    - `int` 32 位，范围 -2³¹ 到 2³¹-1（约 ±21 亿）
    - `long` 64 位，范围 -2⁶³ 到 2⁶³-1
- 浮点类型
    - `float` 32 位单精度浮点数
    - `double` 64 位双精度浮点数
- 字符类型
    - `char` 16 位 Unicode 字符，范围 '\u0000' 到 '\uffff'（0 到 65,535）
- 布尔类型
    - `boolean` 只有 true 和 false 两个值

###### ==和equals的区别
- `==`在比较基本数据类型的时候，比较值。比较对象的时候，比较对象的内存地址，就是判断两个对象是否为同一个对象
- `equals`  是Object类中的一个方法，默认比较对象的内存地址，但很多类都会重写这个方法，一般用来比较对象的值是否相同

###### String,StringBuffer,StringBuilder的区别
- `String`是不可变的，创建一个String之后，将存放与常量池中。再次创建相同的String，将指向同一内存地址。
- `StringBuffer` 可变的，线程安全的。大多方法加了synchronized关键字，效率低一些
- `StringBuilder` 可变的，线程不安全的。效率高一点

  

