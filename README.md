# 张东项目作品集

这是用于 zDongking.github.io 的 GitHub Pages 静态项目展示页面，内容根据本地两个 C++ 项目源码整理。

## 项目内容

- 智慧停车系统：Linux C++ 服务端，覆盖 Socket、epoll、pthread、IPC、MySQL、自定义协议与文件分片传输。
- 执法记录仪系统：Qt + FFmpeg 客户端，覆盖摄像头采集、实时预览、H.264 录像、本地回放、SQLite 与 MVC 分层。

## 页面结构

- index.html：作品集首页
- projects/stopcar.html：智慧停车系统详情页
- projects/bodycam.html：执法记录仪系统详情页

## 上传命令

如果本地能访问 GitHub，可以在该目录执行这些命令：

    git init
    git branch -M main
    git remote add origin https://github.com/zDongking/zDongking.github.io.git
    git add .
    git commit -m "Add C++ project portfolio pages"
    git push -u origin main

如果远程仓库已有内容，先 pull 再 push。
