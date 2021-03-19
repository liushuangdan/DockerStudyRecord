<!--
 * @Author: liushuangdan
 * @Date: 2020-08-28 16:35:24
 * @LastEditTime: 2021-03-19 15:33:08
 * @LastEditors: Please set LastEditors
 * @Description: 
 * @FilePath: \DockerBook\Docker容器命令.md
-->
## Docker 的容器命令

有镜像才能创建容器，这是根本前提

- 新建并启动容器
    - docker run [option] IMAGE [COMMAND] [ARG...]
    - options 说明 有些是一个减号 有些是两个
    - --name="容器新名字"： 为容器指定一个名称， 没有指定docker会随机分配一个名字
    - -d： 后台运行容器，并返回容器ID，也即启动守护式容器
    - -t：为容器重新分配一个伪输入终端，通常与 -i同时 使用
    - -i：以交互模式运行容器，通常与-t同时使用
    - -P：随机端口映射
    - -p：指定端口映射，有以下4种格式
        - ip:hostPort:containerPort
        - ip::containerPort
        - hostPort:containerPort
        - containerPort

`docker run -it centos /bin/bash` 使用镜像centos：latest 以交互模式启动一个容器，在容器内执行/bin/bash 命令。


- 列出当前所有**正在运行**的容器
    - docker ps [options]
      - -a： 列出当前所有正在运行的容器 + 历史上运行过的
      - -l：显示最近创建的容器
      - -n: 显示最近n个创建的容器
      - -q：静默模式，只显示容器编号
      - --no-trunc： 不截断输出
  
- 退出容器
  - 两种方法
    - exit 容器停止退出
    - ctrl+P+Q 容器不停止退出
  
- 启动容器
  - docker start 容器id 或者容器名称
- 重启容器
- docker restart 容器id 或者容器名称
- 停止容器
  - docker stop 容器id或者容器名称
- 强制停止容器
  - docker kill 容器id或者容器名称
- 删除已停止的容器
  - docker rm 容器id 
  - docker rm -f 容器id 强制删除容器
  - docker rm -f $(docker ps -a -q) 删除多个容器
  - docker ps -a -q | xargs docker rm 删除多个容器
- 重点：
  - 启动守护式容器
    - docker run -d 容器名称或者容器id
    #使用镜像centos：latest 以后台模式启动一个容器
    docker run -d centos
    
##### 问题： 然后 docker ps -a 进行查看， 会发现容器已经退出

    很重要的要说明一点，**Docker容器后台运行，就必须有一个前台进程。**
容器运行的命令如果不是那些 一直挂起的命令 (比如运行top，tail)，就是会自动退出的。

这个是docker的机制问题，比如你的web容器，我们以nginx为例，正常情况下，我们配置启动服务只需要启动响应的service即可，例如service nginx start
但是，这样做，nginx在后台进程模式运行，就导致docker前台没有运行的应用，
这样的容器后台启动后，会立即自杀，因为他觉得他没事可做了。
所以，最佳的解决方案是，将你要运行的程序以前台进程的形式运行。

  - 查看容器日志
    - docker logs -f -t --tail 容器id
      - -t 是加入时间戳
      - -f 跟随最新的日志打印
      - --tail数字显示最后多少条 默认10条
  - 查看容器内运行的进程
    - docker top 容器id
  - 查看容器内部细节
    - docker inspect 容器id
  - 进入正在运行的容器并以命令行交互【ctrl+P+Q 容器不停止退出后】
    - docker exec -it 容器id bashShell
    - 重新进入docker attach 容器id
    - 上述两个区别
      - attach
        - 直接进入容器启动命令的终端，不会启动新的进程
      - exec
        - 是在容器中打开新的终端，并且可以启动新的进程
  
  - 从容器内拷贝文件到主机上
    - docker cp 容器id：容器内路径 目的主机路径