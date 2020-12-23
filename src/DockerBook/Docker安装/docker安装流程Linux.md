## docker安装流程Linux

#### centos6版本安装

1. `yum install -y epel-release`
2. `yum install -y docker-io`

3. 安装后的配置文件`/etc/sysconfig/docker`

4. 启动Docker后台服务`service docker start`

5. docker version 验证



---

#### centos7版本安装 

文档 https://docs.docker.com

卸载老版本： 假如之前安装过。

```python
$ sudo yum remove docker \
                  docker-client \
                  docker-client-latest \
                  docker-common \
                  docker-latest \
                  docker-latest-logrotate \
                  docker-logrotate \
                  docker-engine
```

---



```
yum install -y yum-utils
yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo
yum-config-manager --enable docker-ce-nightly
yum-config-manager --enable docker-ce-test
yum install docker-ce docker-ce-cli containerd.io
systemctl start docker
docker run hello-world

配置文件：
/etc/docker/daemon.json
```