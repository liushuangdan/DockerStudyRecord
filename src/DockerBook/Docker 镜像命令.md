<!--
 * @Author: liushuangdan
 * @Date: 2020-08-28 13:23:13
 * @LastEditTime: 2020-08-28 16:34:35
 * @LastEditors: VScode
 * @Description: 
 * @FilePath: \DockerBook\Docker 镜像命令.md
-->
## Docker 的镜像命令

- dockers images    列出本地主机上的所有的镜像
    - options说明 常见参数
    - -a: 列出本地所有的镜像（含有中间映像层）
    - -q： 只显示镜像ID
    - --digests： 显示镜像的摘要信息
    - --no-trunc: 显示完成的镜像信息
- docker search 某个镜像的名字
    - docker search [options] 镜像名字  查找镜像
    - options 说明
    - --no-trunc: 显示完整的镜像描述
    - -s：列出收藏数不小于指定值的镜像
    - --automated： 只列出automated build类型的镜像
- docker pull 某个镜像的名字
    - docker pull [options] 镜像名字：[TAG]  下载镜像

    eg: docker pull tomcat 等价于 docker pull tomcat:latest
    
    docker pull tomcat:3.2 

- docker rmi 某个镜像的名字ID
    - -f 强制删除 
    - docker rmi -f 镜像ID   删除单个
    - docker rmi -f 镜像名1:TAG 镜像名2:TAG 删除多个  (空格分隔，删除多个)
    - docker rmi -f $(docker images -qs) 删除所有镜像
  

