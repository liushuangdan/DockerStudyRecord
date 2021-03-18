## Docker 运行 hello-world 

```python
[root@IDAD-PublisherSystem01 ~]# docker run hello-world

Hello from Docker!
This message shows that your installation appears to be working correctly.

To generate this message, Docker took the following steps:
 1. The Docker client contacted the Docker daemon.
 2. The Docker daemon pulled the "hello-world" image from the Docker Hub.
    (amd64)
 3. The Docker daemon created a new container from that image which runs the
    executable that produces the output you are currently reading.
 4. The Docker daemon streamed that output to the Docker client, which sent it
    to your terminal.

To try something more ambitious, you can run an Ubuntu container with:
 $ docker run -it ubuntu bash

Share images, automate workflows, and more with a free Docker ID:
 https://hub.docker.com/

For more examples and ideas, visit:
 https://docs.docker.com/get-started/
```

 如果本地没有hello-world的这个镜像，所有会下载一个hello-world 镜像，并在容器内运行。 

Hello from Docker!
This message shows that your installation appears to be working correctly.

出现这个说明docker 运行hello world 成功。

输出这段文字提示以后，hello-world就会停止运行，容器自动中止。 


run都做了些什么，如下图所示：
![run干了什么](/./images/run干了什么.png)