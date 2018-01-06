---
layout: post
title: "Java设计模式——单例模式"
date: 2017-03-18 23:15:30 +0800
tags: Design patterns
categories: Pattern
comments: true
published: true
---

# Java设计模式

> 设计模式是被反复使用且被广泛验证的优秀的设计理念的总结，经过分类和归纳后，更容易被人们接受并使用在工程学中。
---
**设计模式分类**

| 范围 | 创建模式 | 结构模式 | 行为模式 |
| :----: | :----------- |  :----------  | :----------- |
| 类 | 工厂方法（Factory Method） | 适配器（Adapter） | 解释器（Interpreter） |
| 类 |         |         | （Template Method） |
| 对象 | 抽象工厂（Abstract Factory） | 适配器（Adapter） | 责任链（Chain of Responsibility） |
| 对象 | 生成器（Builder） | 桥接（Bridge） | 命令（Command） |
| 对象 | 原型（Prototype） | 组成（Composite） | 迭代器（Iterator） |
| 对象 | 单例（Singleton） | 装饰器（Decorator） | 中介者（Mediator）|
| 对象 |    | 外观（Facade） | 备忘录（Memento）|
| 对象 |    | 享元（Flyweight） | 观察者（Observer）|
| 对象 |    | 代理（Proxy） | 状态（State）|
| 对象 |    |    | 策略（Strategy）|
| 对象 |    |    | 访问者（Visitor）|

**设计模式原则**
> 1. 开闭原则（Open Close Principle）
       对扩展开放，对修改关闭
> 2. 里氏替换原则（Liskov Substitution Principle）
        开闭原则的扩展
> 3. 依赖倒置原则（Dependence Inversion Principle）
        对接口编程，依赖于抽象
> 4. 接口隔离原则（Interface Segregation Principle）
        多接口实现，避免单一接口集中定义方法抽象
> 5. 迪米特法则（Demeter Principle）
        最少知道原则
> 6. 合成复用原则（Composite Reuse Principle）
        尽量使用组合，聚合等方式，替代继承

## 单例模式

> 这期介绍常用的单例模式

**三要素**
> 1. 类只能有一个实例
> 2. 必须由自身创建对象实例
> 3. 必须由自身向调用方提供这个实例

单例模式是一种对象创建型模式。单例模式又名单件模式或单态模式。

## java实现
**解释**
1. 懒汉——懒加载方式，在使用的时候，如果不存在则创建
2. 饿汉——饥饿家在方式，在未使用的时候，直接创建等待使用，始终线程安全
3. 线程安全——单线程与多线程执行预期始终一致

* 懒汉方式，线程不安全

![](http://upload-images.jianshu.io/upload_images/2307987-e6d3d25c1e0bd857.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 懒汉方式，线程安全

![](http://upload-images.jianshu.io/upload_images/2307987-e828050c3a454b5c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 懒汉方式，线程安全高级版
> 该方式锁定的是实例引用资源，而不是类对象，这样该类的其他静态方法就不会收到影响。
![](http://upload-images.jianshu.io/upload_images/2307987-81153e06a3ac9203.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 饿汉方式

![](http://upload-images.jianshu.io/upload_images/2307987-38931f9433037f35.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 饿汉，变种

![](http://upload-images.jianshu.io/upload_images/2307987-8818d6dc8ac39d24.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 静态内部类

![](http://upload-images.jianshu.io/upload_images/2307987-5c88af269f64a73c.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

* 枚举

![](http://upload-images.jianshu.io/upload_images/2307987-355dba0044a43412.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

## 总结
> 这里由很多单例的实现，线程安全的不安全的，懒汉模式，饿汉模式等组合。需要大家关注的是这里面所用到的Java特性。这里推荐静态内部类和枚举的方式来实现。

## 常见面试问题
> 1. 使用过哪些设计模式
> 2. 手写单例模式
> 3. 怎么做到线程安全
> 4. 如何更优雅的实现单例模式