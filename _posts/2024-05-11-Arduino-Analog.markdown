---
layout:     post
title:      "Arduino 模拟输入输出"
subtitle:   " \"Hello World, Hello GitheBlog\""
date:       2024-05-11 23:00:00
author:     "Githe"
header-img: "img/post-bg-2015.jpg"
catalog: true
tags: 
    - C++学习笔记
    - Arduino
    - Analog
    - analogWrite
    - analogRead
---



## 正文

<p>
    模拟输入和模拟输出端口，在使用前不需要通过`pinMode()`函数初始化；另外，如果模拟输入端口悬空，那么`analogRead()`函数读取到的值将是随机的。
</p>

```c++
#include <Arduino.h> // 引入Arduino库，才能在程序中使用Arduino提供的方法；

void loop(){
    int val = analogRead(A5); //   模拟输入端口，会将0-5v的电压转换为0-1023的数值;
    Serial.println(val);  // 通过串口打印val的值;
    map(val, 0, 1023, 0, 255);  //   map 等比映射函数，将变量val数值从 0 － 1023 区间等比映射到 0 － 255区间;
    analogWrite(6, val);   // analogWrite, 会将0-255的值通过PWM波的形式输出;
    delay(100);  // 使Arduino暂停100ms;
}
```
<p>
此案例的电路图如下：
</p>
![analog示例电路](../img/posts_image/analog.png "利用电位器调节LED的亮度")
