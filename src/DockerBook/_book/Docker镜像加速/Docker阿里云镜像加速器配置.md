## Docker阿里云镜像加速器配置

#### 阿里云镜像加速

1. 是什么？

​       https://dev.aliyun.com/search.html

2. 注册一个属于自己的阿里云账户（可以复用淘宝账号）

3. 获得加速器地址连接

   1. 登陆阿里云开发平台
   2. 获得加速器地址

4. 配置本机Docker运行镜像加速器

5. 重新启动Docker后台服务：systemctl start docker

6. Linux系统下配置完成加速器需要检查是否生效

   ps -ef|grep docker

---

#### 网易云加速



"https://hub-mirror.c.162.com"

同下，json文件中加速地址改为 上述，即为网易云加速。 建议使用阿里云加速器。 更全面。 



----

### 配置本机Docker运行镜像加速器

鉴于国内网络问题，后续拉取Docker镜像十分缓慢，我们可以配置加速器来解决。

我使用的是阿里云的本人账号的镜像地址（需要自己注册有一个属于自己的）：https://xxx.mirror.aliyuncs.com

* vim /etc/sysconfig/docker centos6.8修改这个配置文件

  将获得的自己的账户下的阿里云加速地址配置进  other_args="--registry-mirror=https://自己的账号加速信息.mirror.aliyun.com"

* vim /etc/docker/daemon.json centos7 修改这个配置文件

  如果没有这个文件需要创建一个： sudo mkdir -p /etc/docker
  sudo tee /etc/docker/daemon.json <<-'EOF'
  {
  "registry-mirrors": ["https://9luj2x1c.mirror.aliyuncs.com"]
  }
  EOF

  重启配置文件： sudo systemctl daemon-reload
  重启docker服务： sudo systemctl restart docker

  

