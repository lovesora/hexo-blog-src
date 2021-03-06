---
title: Spring Boot Building a RESTful Web Service
date: 2018-07-05 10:14:42
tags:
- spring boot
---

## 创建项目

`idea -> new project -> Spring Initializr -> check web/web dependency -> finish`

## 创建VO

```java
package com.sora.rest;

public class Greeting {
    private final long id;
    private final String content;

    public Greeting(long id, String content) {
        this.id = id;
        this.content = content;
    }

    public long getId() {
        return id;
    }

    public String getContent() {
        return content;
    }
}
```

## 创建Controller

```java
package com.sora.rest;

import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

import java.util.concurrent.atomic.AtomicLong;

@RestController
public class GreetingController {
    private static final String template = "Hello, %s! Your id is %s";

    private final AtomicLong counter = new AtomicLong();

    @RequestMapping
    public Greeting greeting(@RequestParam(value = "/greeting", defaultValue = "world") String name) {
        return new Greeting(counter.incrementAndGet(), String.format(template, name, counter.get()));
    }
}
```

## 调试

Press `Option + Control + D` ，编辑配置，如图所示

![configuration](/assets/images/spring/debug-configuration.jpg)

再次按下 `Option + Control + D` ，选择刚才配置的spring boot，启动。

## 构建

打开终端，进入项目目录，执行 `./mvnw clean package`

## 部署执行

1. 安装jre

```bash
yum install java-1.8.0-openjdk
```

2. 将 `target` 目录下的 `jar` 文件copy至服务器，执行 `java -jar xxxx.jar`即可。

```bash
scp target/xxx.jar user@ip:xxx.jar
java -jar xxx.jar
```

## Summery

1. 创建REST项目需要添加 `spring-boot-starter-web` 依赖

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

2. 通过注解的方式关联API请求

```java
@RestController

// 映射路径，方法，默认值等
@RequestMapping
@GetMapping
@PostMapping
@PutMapping
@DeleteMapping

// 映射参数
@RequestParam
@RequestBody

// 映射返回值
@ResponseBody
```

## Refs

-[How to install Java on CentOS 7](https://linuxize.com/post/install-java-on-centos-7/)
-[Building a RESTful Web Service](http://spring.io/guides/gs/rest-service/#initial)

