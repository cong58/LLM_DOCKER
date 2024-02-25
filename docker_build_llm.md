# 构建最小系统的镜像llm

* 根据Dockerfile构建镜像，在wsl执行：

    ```bash
    docker build --no-cache --network=host -t llm:1.0 -f ~/LLM_DOCKER/Dockerfile .
    ```

* 根据镜像生成容器，在wsl执行：

    ```bash
    docker run -it --name llm --hostname llm -e NVIDIA_DRIVER_CAPABILITIES=compute,utility -e NVIDIA_VISIBLE_DEVICES=all --privileged=true --net=host --gpus=all llm:1.0
    ```

* 在容器中，设置root用户密码为1997，在容器中执行：

    ```bash
    passwd root

    ```

* 将ssh的端口设置为1234，并开启root登录，在容器中的`/etc/ssh/sshd_config`文件添加：

    ```bash
    Port 1234
    PermitRootLogin yes
    ```

* 重启ssh，在容器中执行：

    ```bash
    service ssh --full-restart
    ```

* 查看端口号命令，在wsl执行：：

    ```bash
    netstat -ntlp
    ```

* 移除原来的镜像，在wsl执行：

    ```bash
    docker rmi llm:1.0
    ```

* 将容器生成镜像，在wsl执行：

    ```bash
    docker commit llm llm:1.0
    ```
