Solving the issue of difficulty installing MuseTalkComfyUI nodes
解决MuseTalkComfyui节点安装困难的问题

You need to first download a fresh version of ComfyUI
你需要先下载一个全新的comfyui

Ensure that the following installations are done within your ComfyUI environment, not the root environment
以下这些都要确保你是在你的comfyui的环境中安装,而不是安装在了根环境
You need to use installation commands like the following, first specifying the path to your ComfyUI Python interpreter, then using the pip command
你需要使用以下类似的安装命令,先指定你的comfyui的python解释器路径再使用pip命令
```
ComfyUI_windows_portable\python_embeded\python.exe -m pip install aliyun-python-sdk-core-v3==2.13.10
```

Before installation, you may need to adjust the ComfyUI environment version
在安装之前,你可能需要调整comfyui的环境版本

Use a similar command to check your current package versions
使用类似命令查看你目前的包的版本
```
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip list
```
Make sure your torch version is 2.0.1 and CUDA is 11.8, as follows
首先你需要确保你的torch是2.0.1,cuda是11.8,也就是以下版本
```
torch==2.0.1+cu118
torchaudio==2.0.2+cu118
torchvision==0.15.2+cu118
```
If they are not the correct versions, uninstall the current ones
如果不是,你需要先卸载你现有的版本
```
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip uninstall torch
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip uninstall cuda
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip uninstall transformers
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip uninstall torchaudio
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip uninstall torchvision
```
Update your pip
更新你的pip
```
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip install --upgrade pip
```

## Before installing openmim dependencies, make sure to install the following first 在你安装openmim依赖之前你需要确保安装了这个,输入以下类似命令!!!!!!!!必须安装
``` D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip install aliyun-python-sdk-core==2.13.10 ```

Next, uninstall the previous versions of the packages
接下来要安装包,确保你把原有版本都卸载了,输入类似命令
```
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip uninstall torch torchvision torchaudio diffusers accelerate tensorflow tensorboard opencv-python soundfile transformers gdown requests imageio omegaconf ffmpeg-python gradio spaces moviepy
```

Use the new requirements.txt to install dependencies
然后你可以使用我已经打包的新requirements.txt安装依赖

You can download this file and place it in a similar directory:D:\StableDiffusion\ComfyUI_MuseTalk\ComfyUI\custom_nodes\ComfyUI-MuseTalk
你可以只下载这个文件,把这个文件放到D:\StableDiffusion\ComfyUI_MuseTalk\ComfyUI\custom_nodes\ComfyUI-MuseTalk类似的目录
Open CMD in this directory and enter the following command 在此目录打开cmd,输入:
```
..\..\..\python_embeded\python.exe -m pip install -r requirements.txt
```
This will install the dependencies using your ComfyUI Python interpreter.Here are the dependencies to be installed
你即可使用你的comfyui的python解释器安装这些依赖:

```
torch==2.0.1  
torchvision==0.15.2  
torchaudio==2.0.2  
diffusers==0.27.2  
accelerate==0.28.0  
tensorflow==2.12.0  
tensorboard==2.12.0  
opencv-python==4.9.0.80  
soundfile==0.12.1  
transformers==4.39.2  
gdown==5.2.0  
requests==2.32.3  
imageio[ffmpeg]==2.35.1  
omegaconf==2.3.0  
ffmpeg-python>=0.2.0  
gradio==4.44.0  
spaces==0.30.2  
moviepy==1.0.3  
mmpose==1.1.0  
numpy==1.23.5  
tqdm==4.66.5  
more-itertools==10.5.0  
pydub==0.25.1  
openmim==0.3.9  
mmengine==0.10.4  
mmcv==2.0.1
mmdet==3.1.0
```
这些依赖

Make sure you've installed these dependencies correctly after installation
安装完上述再次确保你已经正常安装这些依赖
cmd输入
```
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip install --no-cache-dir -U openmim
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m mim install mmengine
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m mim install "mmcv>=2.0.1"
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip install "mmdet>=3.1.0"
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m mim install "mmpose>=1.1.0"
```
### At this point, you should have successfully installed all dependencies 到这里你应该全部依赖安装成功了


###  然后你需要下载模型 Finally, you need to download the model weights
You can download weights manually as follows:

1. Download our trained [weights](https://huggingface.co/TMElyralab/MuseTalk).

2. Download the weights of other components:
   - [sd-vae-ft-mse](https://huggingface.co/stabilityai/sd-vae-ft-mse)
   - [whisper](https://openaipublic.azureedge.net/main/whisper/models/65147644a518d12f04e32d6f3b26facc3f8dd46e5390956a9424a650c0ce22b9/tiny.pt)
   - [dwpose](https://huggingface.co/yzd-v/DWPose/tree/main)
   - [face-parse-bisent](https://github.com/zllrunning/face-parsing.PyTorch)
   - [resnet18](https://download.pytorch.org/models/resnet18-5c106cde.pth)


Finally, these weights should be organized in `models` as follows:
```
ComfyUI/models/diffusers/TMElyralab/MuseTalk/
├── musetalk
│   └── musetalk.json
│   └── pytorch_model.bin
├── dwpose
│   └── dw-ll_ucoco_384.pth
├── face-parse-bisent
│   ├── 79999_iter.pth
│   └── resnet18-5c106cde.pth
├── sd-vae-ft-mse
│   ├── config.json
│   └── diffusion_pytorch_model.bin
└── whisper
    └── tiny.pt
```
