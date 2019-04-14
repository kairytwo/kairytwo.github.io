---
layout: post
title:  "Dockerfile中使用Cmd做為Entrypoint的參數且使用環境變數"
date:   2019-04-13 22:14:59 +0800
categories: docker
---

# Entrypoint & Cmd

之前已經知道在`docker run`的時候可以設定`entrypoint`來做為執行的主要程式，而`cmd`則是餵給主程式的參數

舉例來說，我們可以寫一個`Dockerfile`

```Dockerfile
FROM ubuntu:latest

ENTRYPOINT ["ls"]
```

我們把它建立成docker image

```bash
docker build test:latest .
```

然後在執行的時候餵入cmd, 

```bash
# 列出 container 內 /var 中的檔案
docker run --rm test:latest -l /var
```

會顯示結果

<pre>
➜  test docker run --rm test:latest -l /var/
total 36
drwxr-xr-x 2 root root  4096 Apr 24  2018 backups
drwxr-xr-x 5 root root  4096 Mar  7 21:01 cache
drwxr-xr-x 1 root root  4096 Apr  5  2018 lib
drwxrwsr-x 2 root staff 4096 Apr 24  2018 local
lrwxrwxrwx 1 root root     9 Mar  7 21:00 lock -> /run/lock
drwxr-xr-x 3 root root  4096 Mar  7 21:00 log
drwxrwsr-x 2 root mail  4096 Mar  7 21:00 mail
drwxr-xr-x 2 root root  4096 Mar  7 21:00 opt
lrwxrwxrwx 1 root root     4 Mar  7 21:00 run -> /run
drwxr-xr-x 2 root root  4096 Mar  7 21:00 spool
drwxrwxrwt 2 root root  4096 Mar  7 21:01 tmp
</pre>

應該就可以知道，真正 container 執行的內容就是 `ls -l /var`，將/var下的內容列出

## 如果需要解析環境變數?

但之前遇到的一個情況是我需要執行 java 且餵入環境變數時就遇到個問題

我想執行的是

```bash
java $JAVA_OPTS -jar app.jar 2019-04-10 2019-04-11
```

在執行 app.jar 時會餵入 $JAVA\_OPTS 去設定JVM的參數，而app.jar 又接受從 command line 輸入的兩個日期參數

我先寫了第一版的`Dockerfile`

```Dockerfile
FROM openjdk:8

RUN mkdir -p /app
COPY app.jar /app/app.jar
WORKDIR /app

ENTRYPOINT ["java", "$JAVA_OPTS", "-jar", "app.jar"]
```

建立docker image`docker build -t app:latest .`後，然後執行

```bash
docker run --rm -e JAVA_OPTS=-Xmx1024m app:latest 2019-04-10 2019-04-11
```

結果回傳給我錯誤

<pre><font color="#8AE234"><b>➜  </b></font><font color="#34E2E2"><b>app</b></font> docker run --rm app:latest 2019-04-10 2019-04-11
Error: Could not find or load main class $JAVA_OPTS
</pre>

咦！！環境變數怎麼無法解析

後來去看一下Dockerfile中[Entrypoint的說明](https://docs.docker.com/engine/reference/builder/#entrypoint)，才知道Entrypoint有分為*exec form* 和 *shell form*

```Dockerfile
# exec form
ENTRYPOINT ["java", "$JAVA_OPTS", "-jar", "app.jar"]
```

```Dockerfile
# shell form
ENTRYPOINT java $JAVA_OPTS -jar app.jar
```

然後**只有shell form**能夠解析環境變數，所以我就將Entrypoint的寫法改為*shell form*，再試一次

這次環境變數的問題好像解決了，但是卻帶來新的問題

<pre>Caused by: java.lang.ArrayIndexOutOfBoundsException: 0
</pre>

這次則是吃不到我docker run 餵進去的參數，看一下文件，才又看到

> The shell form prevents any CMD or run command line arguments from being used

哎呀，文件應該好好仔細看的

## 解決方案

**把要執行的Entrypoint先寫在.sh裡，然後使用shell的參數接受Cmd的參數**

先把要執行的指令寫在`entrypoint.sh`中

```bash
#! /usr/bin/env bash
# entrypoint.sh

# 在bash裡可以解析 $JAVA_OPTS
# $1 $2 表示執行shell的第一與第二個參數
java $JAVA_OPTS -jar app.jar $1 $2
```

然後稍微調整一下`Dockerfile`，將`entrypoint.sh` COPY進 docker image，然後設定對應的 Entrypoint


```Dockerfile
FROM openjdk:8

RUN mkdir -p /app
COPY app.jar /app/app.jar
# copy entrypoint.sh 進到 image 中
COPY entrypoint.sh /app/entrypoint.sh
# 給予 /app/entrypoint.sh 可執行權限
RUN chmod +x /app/entrypoint.sh
WORKDIR /app

# 讓Entrypoint以exec form執行 entrypoint.sh
ENTRYPOINT ["/app/entrypoint.sh"]
```

接著再執行docker run

```bash
docker run --rm -e JAVA_OPTS=-Xmx1024m app:latest 2019-04-09 2019-04-10
```

這樣就順利執行包含環境變數的指令又能從 Cmd 餵入參數了
