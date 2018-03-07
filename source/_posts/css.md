---
title: CSS知识
tags: css
categories: css
date: 2018-01-24 7:07:20
---

## css基础

**CSS盒模型**:每个HTML元素都是长方形盒子。 

1. 盒子模型有两种：IE盒子模型、标准W3C盒子模型；IE的content部分包含了border和pading。 
2. 标准W3C盒模型包含：内容(content)、填充(padding)、边界(margin)、边框(border)。

**CSS选择器**，

1. 伪类：id选择器（# myid） 

2. 类选择器（.myclassname）

3.  标签选择器（div、h1、p） 

4. 相邻选择器（h1 + p） 

5. 子选择器（ul < li） 

6. 后代选择器（li a）

7.  通配符选择器（ * ） 

8. 属性选择器（a[rel = "external"]） 

9. 伪类选择器（a: hover, li: nth - child）

**优先级就近原则**，样式定义最近者为准，载入样式以最后载入的定位为准。

 **优先级为：** !important > id > class > tag 

**CSS3新增伪类举例：** 

1. p:first-of-type 选择属于其父元素的首个<p>元素的每个<p>元素。 
2. p:last-of-type 选择属于其父元素的最后<p>元素的每个<p>元素。
3.  p:only-of-type 选择属于其父元素唯一的<p>元素的每个<p>元素。 
4. p:only-child 选择属于其父元素的唯一子元素的每个<p>元素。 
5. p:nth-child(2) 选择属于其父元素的第二个子元素的每个<p>元素。 
6. :enabled、:disabled 控制表单控件的禁用状态。 
7. :checked 单选框或复选框被选中。

**可继承**： font-size font-family color, UL LI DL DD DT; 

**不可继承** ：border padding margin width height ; 

