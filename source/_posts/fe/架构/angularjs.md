---
title: 浅谈angularjs架构演进
date: 2018-06-25 21:48:06
layout: draft
tags:
- angularjs
- architecture
---

> 笔者大言不惭将其称为前端架构，各位大佬可直接略过

## 前言（纯属乱劈柴，可直接略过）

在公司工作快一年了，收获了很多东西，`学而不思则罔，思而不学则殆`。都明白，智者总是一语道天机，大道至简，很多核心的设计思想往往都是非常简洁，明了的。这一年做了太多的东西，却思考得太少，没有理解到技术的原理，深深地陷入了码农深渊，不知道为什么这么做，为什么这样设计（现在老是后悔以前上大学的时候没有好好学习理论知识，书到用时方恨少）。每次从需求到研发，都是拿着设计图，思考实现这个东西要怎么做，时间可控不，要花多少时间，有什么风险，需要什么依赖，哪些东西可以复用等等。但是，产品初衷是什么？解决了用户什么刚需？为什么设计师要这样子设计？后端数据库怎么设计的？为什么要给这样的数据结构？这些往往难以接触，即使有机会了解，也不太愿意花时间去做。很多时候都不清除源头，就开始草草动工，只着眼于自己领域的实现，结果往往就是各种返工。既然看不到原理，那就先从现象入手吧，透过现象看本质。现象都不知道，还鬼的个本质？

## 最原始架构

