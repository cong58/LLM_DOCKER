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

## 在docker部署InstantID模型

* 下载[InstantID源码](https://github.com/InstantID/InstantID),下载[Huggingface上的模型](https://hf-mirror.com/InstantX/InstantID)并放在源码的checkpoints目录下，下载antelopev2模型(百度网盘https://pan.quark.cn/s/ddcd385cd661
提取码：cgDt)并放在源码的models目录下。

* 下载[Diffusion基础模型](https://hf-mirror.com/wangqixun/YamerMIX_v8)并放在源码下的的wangqixun/YamerMIX_v8目录中

* 下载[lora模型](https://hf-mirror.com/latent-consistency/lcm-lora-sdxl)并放在源码下的的latent-consistency/lcm-lora-sdxl目录中

* 下载[openpose模型](https://hf-mirror.com/thibaud/controlnet-openpose-sdxl-1.0)并放在源码下的thibaud/controlnet-openpose-sdxl-1.0目录中

* 下载[canny模型](https://hf-mirror.com/diffusers/controlnet-canny-sdxl-1.0)并放在源码下的diffusers/controlnet-canny-sdxl-1.0目录中

* 下载[depth模型](https://hf-mirror.com/diffusers/controlnet-depth-sdxl-1.0-small)并放在源码下的diffusers/controlnet-depth-sdxl-1.0-small目录中

* 下载[hybrid模型](https://hf-mirror.com/Intel/dpt-hybrid-midas)并放在源码下的Intel/dpt-hybrid-midas目录中

* 下载[lllyasviel模型](https://hf-mirror.com/lllyasviel/ControlNet)并放在源码下的lllyasviel/ControlNet目录中

* 下载[Annotators模型](https://hf-mirror.com/lllyasviel/Annotators)并放在源码下的lllyasviel/Annotators目录中