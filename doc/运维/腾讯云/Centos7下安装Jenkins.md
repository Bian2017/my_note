**参考：**

[Centos7 下 Jenkins 安装](https://blog.csdn.net/linjingke32/article/details/77799878)

### 1. 首先安装好 Java(JAVA_HOME)

> java -version

### 2. 获取 jenkins 安装源文件

> wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat/jenkins.repo

### 3. 导入公钥

> rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key

### 4. 安装 Jenkins

> yum install -y jenkins

### 5. 配置文件修改(可选: 这里修改默认端口为 8787)

配置文件位于：/etc/sysconfig/jenkins

```
## Type:        integer(0:65535)
## Default:     8080
## ServiceRestart: jenkins
#
# Port Jenkins is listening on.
# Set to -1 to disable
#
JENKINS_PORT="8787"
```

注意：记得云服务需对**安全组**设置下 8787 端口。

### 6. 启动: http://{IP地址}:8787

> service jenkins start

### 7. 浏览器访问 Jenkins 主页

输入如下地址：http://{IP地址}:8787，即可访问Jenkins主页。启动后第一次打开这个链接，会出现“解锁 Jenkins”页面。

此时只需按照提示，去那个文件下拿到超级管理员的密码填写即可。

### 8. 接着会提示安装插件

可以选择建议插件，也可以选择自定义要安装插件，进入 jenkins 后也可以进行插件安装的。

这里先默认，后面再按需安装吧:

### 9.插件安装完，进入主页

后面再自行修改相关用户信息等操作即可。

### 11.卸载(按需，可选)

- 卸载软件：rpm -e jenkins

- 删除遗留文件: find / -iname jenkins | xargs -n 1000 rm -rf
