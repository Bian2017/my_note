## Centos7 下安装 Gitlab 服务器

**参考：**

[Centos 7 搭建 Gitlab 服务器超详细](https://blog.csdn.net/duyusean/article/details/80011540)

### 1. 添加 gitlab 镜像

> wget https://mirrors.tuna.tsinghua.edu.cn/gitlab-ce/yum/el7/gitlab-ce-10.0.0-ce.0.el7.x86_64.rpm

### 2. 安装 gitlab 

安装命令

> rpm -i gitlab-ce-10.0.0-ce.0.el7.x86_64.rpm

安装过程需要些时间，如果出现下图，则说明安装成功。

### 3. 修改 gitlab 配置文件指定服务器 ip 和自定义端口

> vim  /etc/gitlab/gitlab.rb

修改 external_url，指定服务器 IP 和端口。

```
external_url 'http://49.235.154.5:9797/'
```

注意：这里设置的端口不能被占用，默认是 8080 端口，如果 8080 已经使用，请自定义其它端口，并在防火墙设置开放相对应的端口(腾讯云 ECS 服务器安全组需设置相应端口)。

### 4. 重置并启动 GitLab

执行：

> gitlab-ctl reconfigure

> gitlab-ctl restart

提示"ok: run:"表示启动成功。

### 5. 访问 GitLab 页面

如果没有域名，直接输入服务器 ip 和指定端口进行访问。

第一次登录需设置密码。

### 6. 删除 gitlab

gitlab 太吃内存了，1 核 2G 的 ECS 服务器根本就跑不动 gitlab。

先停止运行 gitlab：

> gitlab-ctl stop

查看 gitlab 的 rpm 包：

```
> rpm -qa | grep gitlab
gitlab-ce-10.0.0-ce.0.el7.x86_64
```

删除软件包

> rpm -e gitlab-ce-10.0.0-ce.0.el7.x86_64
