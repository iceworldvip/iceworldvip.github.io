---
layout: post
title: "单例模式衍化"
date: 2017-03-18 23:15:30 +0800
tags: Design patterns
categories: Pattern
comments: true
published: true
---

## 概述
单例模式确保某一个类只有一个实例，而且自行实例化并向整个系统提供这个实例，这个类称为单例类，它提供全局访问的方法。

**三要素**
> 1. 某个类只能有一个实例
> 2. 它必须自行创建这个实例
> 3. 它必须自行向整个系统提供这个实例

单例模式是一种对象创建型模式。单例模式又名单件模式或单态模式。

## java实现

* 懒汉，线程不安全

```java
    public class Singleton {
        private static Singleton instance;
        private Singleton (){}
        public static Singleton getInstance() {
            if (instance == null) {
                instance = new Singleton();
            }
            return instance;
        }
    }
```

* 懒汉，线程安全

```java
    public class Singleton {
        private static Singleton instance;
        private Singleton (){}
        public static synchronized Singleton getInstance() {
            if (instance == null) {
                instance = new Singleton();
            }
            return instance;
        }
    }
```

* 饿汉

```java
    public class Singleton {
        private static Singleton instance = new Singleton();
        private Singleton (){}
        public static Singleton getInstance() {
            return instance;
        }
    }
```

* 饿汉，变种

```java
    public class Singleton {
        private Singleton instance = null;
        static {
            instance = new Singleton();
        }
        private Singleton (){}
        public static Singleton getInstance() {
            return this.instance;
        }
    }
```

* 静态内部类

```java
    public class Singleton {
        private static class SingletonHolder {
            private static final Singleton INSTANCE = new Singleton();
        }
        private Singleton (){}
        public static final Singleton getInstance() {
            return SingletonHolder.INSTANCE;
        }
    }
```

* 枚举

```java
    public enum Singleton {
        INSTANCE;
        public void whateverMethod() {
        }
    }
```

* 饿汉，线程安全高级版

```java
    public class Singleton {
        private volatile static Singleton singleton;
        private Singleton (){}
        public static Singleton getSingleton() {
            if (singleton == null) {
                synchronized (Singleton.class) {
                    if (singleton == null) {
                        singleton = new Singleton();
                    }
                }
            }
            return singleton;
        }
    }
```