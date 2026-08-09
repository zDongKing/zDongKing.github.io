---
title: 执法记录仪系统
date: 2025-08-01
summary: Qt + FFmpeg 客户端项目，覆盖摄像头采集、实时预览、H.264 录像、本地回放、SQLite 与 MVC 分层。
tags:
  - C++
  - Qt
  - FFmpeg
  - QThread
  - H.264
  - SQLite
---

执法记录仪系统是一个 Qt + FFmpeg 客户端项目，实现摄像头采集、实时预览、录像、抓拍、视频查询、本地回放和日志查看等功能。视频处理逻辑封装在线程中，主界面通过 Qt 信号槽接收图像帧，避免采集、编码和文件处理阻塞界面交互。

## 技术栈

- C++ / Qt Widgets / QThread / 信号槽
- FFmpeg / DirectShow / RGB32 / YUV420P / H.264
- SQLite / MVC 分层 / SingletonDB

## 核心实现

- 封装 VideoProcessingThread，通过 FFmpeg DirectShow 打开本机摄像头并循环读取视频帧。
- 将解码帧转换为 RGB32 用于 Qt 实时预览，同时转换为 YUV420P 交给 H.264 编码模块写入录像。
- 录像过程按 1500 帧自动切分，保存首帧封面，并将视频路径、时间等元数据写入 SQLite。
- 使用独立播放线程解码本地录像，支持播放、暂停和三档速度切换，降低长时间视频处理对主界面的影响。
- 项目按 View、Controller、model 分层组织，使用 SingletonDB 管理本地数据库连接，降低界面逻辑与数据访问耦合。

## 面试可讲点

这个项目可以重点讲 Qt 多线程和 FFmpeg 处理链路：输入端使用 DirectShow 采集摄像头，显示端转 RGB32，编码端转 YUV420P 并写入 H.264。项目里的 MP4/AVI 处理更适合描述为“封装导出”或“容器转换”，不要夸成完整转码系统。
