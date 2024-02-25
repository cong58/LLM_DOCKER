# 运行ChatGLM3的容器glm3

* 生成容器，在wsl执行：

    ```bash
    docker run -it --name glm3 --hostname glm3 -v ~/LLM_MODEL:/root/LLM_MODEL -e MODEL_PATH=/root/LLM_MODEL/THUDM/chatglm3-6b/ -e EMBEDDING_PATH=/root/LLM_MODEL/BAAI/bge-large-zh-v1.5/ -e NVIDIA_DRIVER_CAPABILITIES=compute,utility -e NVIDIA_VISIBLE_DEVICES=all --privileged=true --net=host --gpus=all llm:1.0
    ```

* 拷贝代码工程至docker，在wsl执行：

    ```bash
    docker cp ~/PyQt_ChatGLM3/LLM/ChatGLM3 glm3:/root/ChatGLM3
    ```

* 重启ssh，在docker里执行：

    ```bash
        service ssh --full-restart
    ```

* 安装python库，在docker里执行：

    ```bash
        pip install --default-timeout=50 -r /root/ChatGLM3/requirements.txt
    ```

* 设置全局永久的环境变量，在docker的`/root/.bashrc`文件尾追加：

    ```bash
    export MODEL_PATH="/root/LLM_MODEL/THUDM/chatglm3-6b/"
    export EMBEDDING_PATH="/root/LLM_MODEL/BAAI/bge-large-zh-v1.5/"
    export NVIDIA_DRIVER_CAPABILITIES="compute,utility"
    export NVIDIA_VISIBLE_DEVICES="all"
    ```

    重载`/root/.bashrc`，在docker里执行：

    ```bash
        source /root/.bashrc
    ```
