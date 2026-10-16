# MOSS-Image for ComfyUI

[English](./README.md) | 中文

![version](https://img.shields.io/badge/version-v0.1.1-blue)
![python](https://img.shields.io/badge/python-%3E%3D3.10-blue)
![comfyui](https://img.shields.io/badge/ComfyUI-native-green)
![license](https://img.shields.io/badge/license-Apache--2.0-green)

ComfyUI 原生 MOSS-Image 加载器，输出标准的 MODEL、CLIP、VAE 对象，可直接复用 ComfyUI 自带的采样、引导与显存管理节点。

Fork 自 [OpenMOSS/MOSS-Image](https://github.com/OpenMOSS/MOSS-Image)（原仓 `comfyui/` 子树），作为独立 custom node 重新发布。

## 安装

**方式一：Comfy CLI / ComfyUI-Manager（推荐）**

```bash
comfy node install comfyui-moss-Image
```

或在 ComfyUI-Manager → Custom Nodes → Install 中搜索 `comfyui-moss-Image`。

**方式二：手动 git clone**

```bash
cd ComfyUI/custom_nodes
git clone https://github.com/wanaigc/comfyui-moss-Image.git
```

重启 ComfyUI 即可。插件复用 ComfyUI 自带的 Python 依赖，无需额外安装。

## 模型文件

| 组件             | 文件                                                          | 大小    | 格式                                            |
| ---------------- | ------------------------------------------------------------- | ------- | ----------------------------------------------- |
| **DiT**          | `diffusion_models/moss_image_sft_int8_convrot.safetensors`    | 5.25 GB | INT8 ConvRot（Modulation、Layer 0 & 41 为 BF16） |
| **Text Encoder** | `text_encoders/qwen35_moss_int8_convrot.safetensors`         | 8.65 GB | INT8 ConvRot（SSM、Layer 31 为 BF16）           |
| **VAE**          | `vae/flux2-vae.safetensors`                                    | 238 MB  | FP32（FLUX.2 Small Decoder，384ch）             |

下载地址：[夸克网盘](https://pan.quark.cn/s/2c5661248312)（国内加速） · [HuggingFace](https://huggingface.co/XCEED123/MOSS-Image-SFT-INT8-ComfyUI)

将文件放到 ComfyUI 对应目录：

```
📂 ComfyUI/
├── 📂 models/
│   ├── 📂 diffusion_models/
│   │   └── moss_image_sft_int8_convrot.safetensors
│   ├── 📂 text_encoders/
│   │   └── qwen35_moss_int8_convrot.safetensors
│   └── 📂 vae/
│       └── flux2-vae.safetensors
```

## 推荐参数

| 设置                    | 值                       | 备注                                                |
| ----------------------- | ------------------------ | --------------------------------------------------- |
| **采样器 (Sampler)**    | `euler`                  | Flow-matching Euler                                  |
| **调度器 (Scheduler)**  | `sgm_uniform`            | 与 flow-matching shift 配对                         |
| **步数 (Steps)**        | `50`                     | 建议 30–50 步                                       |
| **CFG**                 | `3.0`                    | 建议 2.5–3.5                                        |
| **Shift**               | `5.0`                    | 在 `ModelSamplingSD3` 节点中设置                    |
| **Skip Layer Guidance** | `22`                     | 在 `SkipLayerGuidanceDiTSimple` 中设 `single_layers="22"` |
| **分辨率 (Resolution)** | `1024×1024` 或宽屏       | 需为 16 的倍数                                      |

## 文档

使用说明请参考上游的[安装与使用指南](https://github.com/OpenMOSS/MOSS-Image/blob/main/comfyui/README.md)。

示例工作流见 [`example_workflows/image_moss_sft_int8_t2i.json`](example_workflows/image_moss_sft_int8_t2i.json)。

## 许可证

本项目采用 Apache-2.0 许可证，与上游 [OpenMOSS/MOSS-Image](https://github.com/OpenMOSS/MOSS-Image) 仓库保持一致。
