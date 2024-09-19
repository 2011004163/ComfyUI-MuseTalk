# ComfyUI-MuseTalk
解决MuseTalkComfyui节点安装困难的问题
你需要先下载一个全新的comfyui
## 以下这些都要确保你是在你的comfyui的环境中安装,而不是安装在了根环境
你需要使用以下类似的安装命令,先指定你的comfyui的python解释器路径再使用pip命令
ComfyUI_windows_portable\python_embeded\python.exe -m pip install aliyun-python-sdk-core-v3==2.13.10

在安装之前,你可能需要调整comfyui的环境版本
使用类似命令D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip list
查看你目前的包的版本
首先你需要确保你的torch是2.0.1,cuda是11.8,也就是以下版本
torch==2.0.1+cu118
torchaudio==2.0.2+cu118
torchvision==0.15.2+cu118
如果不是,你需要先卸载你现有的版本
```
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip uninstall torch
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip uninstall cuda
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip uninstall transformers
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip uninstall torchaudio
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip uninstall torchvision
```
## 在你安装依赖之前你需要确保安装了这个输入以下类似命令
``` D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip install aliyun-python-sdk-core==2.13.10 ```


接下来要安装包,确保你把原有版本都卸载了,输入类似命令
```
D:\StableDiffusion\ComfyUI_MuseTalk\python_embeded\python.exe -m pip uninstall torch torchvision torchaudio diffusers accelerate tensorflow tensorboard opencv-python soundfile transformers gdown requests imageio omegaconf ffmpeg-python gradio spaces moviepy
```

然后你可以使用我已经打包的新requirements.txt安装依赖
你可以只下载这个文件,把这个文件放到D:\StableDiffusion\ComfyUI_MuseTalk\ComfyUI\custom_nodes\ComfyUI-MuseTalk类似的目录
在此目录打开cmd,输入
```
..\..\..\python_embeded\python.exe -m pip install -r requirements.txt
```
,你即可使用你的comfyui的python解释器安装这些依赖

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

###  然后你需要下载模型 Download weights
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
