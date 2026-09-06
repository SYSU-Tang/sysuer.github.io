---
sidebar_position: 1
title: 开发文档
description: 开发文档
---

> 该文档未完善

# 开发文档

欢迎来到**中大儿**开发者文档！本部分内容专为希望了解中大儿工作原理以及参与开发的用户设计。

## <svg xmlns="http://www.w3.org/2000/svg" height="24px" viewBox="0 -960 960 960" width="24px" fill="#005826"><path d="M40-240q9-107 65.5-197T256-580l-74-128q-6-9-3-19t13-15q8-5 18-2t16 12l74 128q86-36 180-36t180 36l74-128q6-9 16-12t18 2q10 5 13 15t-3 19l-74 128q94 53 150.5 143T920-240H40Zm275.5-124.5Q330-379 330-400t-14.5-35.5Q301-450 280-450t-35.5 14.5Q230-421 230-400t14.5 35.5Q259-350 280-350t35.5-14.5Zm400 0Q730-379 730-400t-14.5-35.5Q701-450 680-450t-35.5 14.5Q630-421 630-400t14.5 35.5Q659-350 680-350t35.5-14.5Z"/></svg> 项目


中大儿是一个基于 Java/Kotlin + Jetpack Compose 开发的Android应用，使用[Android Studio](https://developer.android.com/studio)作为开发工具，采用MVVM的思想，通过viewModel将view和model连接。

## <svg xmlns="http://www.w3.org/2000/svg" height="24px" width="24px" fill="#005826" viewBox="0 0 24 24"><title>github</title><path d="M12,2A10,10 0 0,0 2,12C2,16.42 4.87,20.17 8.84,21.5C9.34,21.58 9.5,21.27 9.5,21C9.5,20.77 9.5,20.14 9.5,19.31C6.73,19.91 6.14,17.97 6.14,17.97C5.68,16.81 5.03,16.5 5.03,16.5C4.12,15.88 5.1,15.9 5.1,15.9C6.1,15.97 6.63,16.93 6.63,16.93C7.5,18.45 8.97,18 9.54,17.76C9.63,17.11 9.89,16.67 10.17,16.42C7.95,16.17 5.62,15.31 5.62,11.5C5.62,10.39 6,9.5 6.65,8.79C6.55,8.54 6.2,7.5 6.75,6.15C6.75,6.15 7.59,5.88 9.5,7.17C10.29,6.95 11.15,6.84 12,6.84C12.85,6.84 13.71,6.95 14.5,7.17C16.41,5.88 17.25,6.15 17.25,6.15C17.8,7.5 17.45,8.54 17.35,8.79C18,9.5 18.38,10.39 18.38,11.5C18.38,15.32 16.04,16.16 13.81,16.41C14.17,16.72 14.5,17.33 14.5,18.26C14.5,19.6 14.5,20.68 14.5,21C14.5,21.27 14.66,21.59 15.17,21.5C19.14,20.16 22,16.42 22,12A10,10 0 0,0 12,2Z" /></svg> 开源

中大儿使用了以下开源项目：

- [Material3](https://github.com/material-components/material-components-android)
- [androidX](https://developer.android.com/jetpack/androidx)
- [fastjson2](https://github.com/alibaba/fastjson2)
- [okHttp](https://square.github.io/okhttp/)
- [Shizuku](https://github.com/RikkaApps/Shizuku)
- [Kotlin](https://kotlinlang.org/)
- [Glide](https://github.com/bumptech/glide)
- [RikkaX](https://github.com/RikkaApps/RikkaX)
- [Markwon](https://github.com/noties/Markwon)
- [Shizuku](https://github.com/RikkaApps/Shizuku)
- [Navigation3]
- [Room3]
- [Compose]
- [DataStore]
- [Miuix]

## 开发流程

网络请求$\rightarrow$数据处理$\rightarrow$UI渲染$\rightarrow$界面过渡

## 网络请求

本软件使用okhttp进行网络请求，okhttp的使用文档参考()[]

为了方便调用okhttp，对okhttp常见的方法封装到`com.sysu.edu.api.HttpManager`，HttpManager的各函数及说明参考()[]

同时整理不同域名下的网络请求，在基于`com.sysu.edu.model.BaseModel`继承基于`jwxt`、`xgxt`、`portal`、`zhny`、`pay`等域名开发的model，统一处理登录请求时需要的必要参数（如`Cookie、Authorization、Token、UA、Referer`）以及响应数据的统一处理，model的使用方法参考()[]

绝大部分请求需要使用NetID登录后的Cookie，同时不同域名下NetID登录的逻辑是不同的，本软件将部分域名的登录逻辑统一到`com.sysu.edu.api.LoginManager`，具体已经实现登录的域名详见`com.sysu.edu.api.TargetUrl`，LoginManager的文档详见()[]

Cookie、Token、Authorization数据统一在`com.sysu.edu.api.CookieManager`、`com.sysu.edu.api.Authorization`

## 数据处理

鉴于网络请求返回的数据多数为json和html格式，因此本软件使用fastjson2和jsoup处理数据，fastjson2的使用文档参考()[]，jsoup的使用文档参考()[]

存储在本地的数据主要使用Datastore和Room3进行管理

## UI渲染

本软件目前使用compose进行UI渲染，使用MaterialExpreessive作为主题，并且使用Material Componet作为组件，具体组件参考()[]

同时为了统一界面风格，本软件将常用的视图和控件整合到`com.sysu.edu.view`下

## 界面过渡

为实现更优雅的过渡效果，本软件采用Navigation3作为导航，Navigation3的使用文档参考()[]

本软件将NavKey整合在`com.sysu.edu.nav.NavKey`下，命名为各个服务对应的Activity前缀

 