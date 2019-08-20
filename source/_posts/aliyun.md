---
title: 在阿里云上搭建回国翻墙服务器
toc: true
date: 2019-08-20 16:42:21
tags: ssr, vps
categories: ssr
---

## 翻墙回国的必要性

出国之后，我们会有打开优酷，爱奇艺看视频，使用网易云听歌等需求。然而经常发生的一个现象是“版权受限”，所以我们需要有一个国内的 IP 来越过这个限制。这里介绍一种在阿里云服务器上搭建 SSR 翻墙回国内的方法。

## 服务器设置

阿里云有着著名的[云翼计划](https://promotion.aliyun.com/ntms/act/campus2018.html),对于学生（24 岁以下免认证）来说，可以使用学生优惠价，一年只需 114 元人民币，拿到一个 2G 内存 5M 带宽的服务器（不要选 1G 带宽不限流量的那一个）。购买之后可以登录服务器，
之后下载 ssr。ssr 可以使用[一键安装脚本](https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-all.sh)来自动下载安装。默认情况下服务器只开放 80，443，22 号端口，
而我们的 ssr 服务之前另外设置了一个端口，所以我们需要开放这个端口。具体操作起来就是打开管理界面的防火墙，添加规则，协议设为 TCP，端口设为之前自己设置的 ssr 端口。

## 客户端设置

在 mac 上，可以使用[ShadowsocksX-NG-R8](https://github.com/qinyuhang/ShadowsocksX-NG-R/releases/download/1.4.4-r8/ShadowsocksX-NG-R8.dmg)。在 IOS 上，则建议使用 potatso（不能在国区 store 下载）。
对于其他系统，因为很久没碰了，所以暂且不做推荐。有一个[electron-ssr](https://github.com/qingshuisiyuan/electron-ssr-backup/releases),用户体验很好。可惜因为政策原因，原作者不再维护更新，但是应该还是可以使用的。
