# 运行instantid的容器instantid

* 生成容器，在wsl执行：

    ```bash
    docker run -it --name instantid --hostname instantid -v ~/InstantID:/root/InstantID  -e NVIDIA_DRIVER_CAPABILITIES=compute,utility -e NVIDIA_VISIBLE_DEVICES=all --privileged=true --net=host --gpus=all llm:1.0
    ```

* 重启ssh，在docker里执行：

    ```bash
        service ssh --full-restart
    ```

* 安装gcc,在docker里执行：

    ```bash
        apt update
        apt install build-essential
    ```

* 安装cv2依赖,在docker里执行：

    ```bash
        apt update
        apt install libgl1-mesa-glx
    ```

* 安装适用于cuda 12.x版本的onnxruntime-gpu,在docker里执行：

    ```bash
        pip uninstall onnxruntime-gpu
        pip install onnxruntime-gpu --extra-index-url https://aiinfra.pkgs.visualstudio.com/PublicPackages/_packaging/onnxruntime-cuda-12/pypi/simple/
    ```

* 安装依赖库,在docker里执行：

    ```bash
        pip install mediapipe
    ```

* 安装python库，在docker里执行：

    ```bash
        pip install --default-timeout=50 -r /root/InstantID/gradio_demo/requirements.txt
    ```
