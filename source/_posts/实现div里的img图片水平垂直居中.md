---
title: 实现div里的img图片水平垂直居中
date: 2018-09-27 19:10:32
tags:
    - css
categories:
    - 前端
    - 技术
---

在不清楚图片图片或元素的真实宽高情况下,实现div里的img图片水平垂直居中

<!-- more -->

### 通过position定位来实现

``` css     
        img {
                width: 50px;
                height: 50px;
                position: absolute;
                top: 0;
                left: 0;
                right: 0;
                bottom: 0;
                margin: auto;
            }
```

``` css     
         img {
             width: 50px;
             height: 50px;
             position: absolute;
             top: 0;
             left: 0;
             right: 0;
             bottom: 0;
             margin: auto;
         }
        
```

### 布局flex
``` css     

    *{margin: 0;padding:0;}
    div{
        width:150px;
        height: 100px;
        border:1px solid #000;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    img {
        width: 50px;
        height: 50px;
    }

```
