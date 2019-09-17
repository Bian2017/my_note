## Jenkins 踩坑指南

**参考：**

[Jenkins 上踩过的那些坑](https://www.jianshu.com/p/d9191eed6950)

### 1. Failed to connect to repository

为项目设置 git repository 的时候报“Failed to connect to repository”

解决办法：在 ECS 服务器上安装 git 客户端。

### 2. node: command not found

Jenkins 提供了[Nodejs Plugin 插件](https://wiki.jenkins.io/display/JENKINS/NodeJS+Plugin)，按照官方提示安装插件即可。

第一步：点击系统管理，在插件管理中安装 NodeJS Plugin 插件；

第二步：点击系统管理，在全局工具配置中配置 NodeJS 安装(参照官方提示) ；

第三步：点击具体项目的配置选项，将 NodeJS 的 bin 文件添加到 PATH 中；
