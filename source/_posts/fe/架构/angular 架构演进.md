---
title: 组件&库 架构方案
date: 2018-12-28 16:22:22
tags:
- 架构
---

## 最原始方案

所有组件库各自独立维护，独立演进。
搭建私有`npm`，业务项目独立引用组件库对应版本。

- 优势

组件之间相互独立，各自互补相干。

- 劣势

组件库的研发比较麻烦，需要写独立demo。
如果在业务项目中发现组件库出现问题，调试极其麻烦。

- 适用
大型团队，组件与业务彻底分离，各自独立演进。

- 不适用
小型团队使用成本极大，业务产出低。

