# MOSS-Image for ComfyUI

[English](./README.md) | 中文

![version](https://img.shields.io/badge/version-v0.1.1-blue)
![python](https://img.shields.io/badge/python-%3E%3D3.10-blue)
![comfyui](https://img.shields.io/badge/ComfyUI-native-green)
![license](https://img.shields.io/badge/license-Apache--2.0-green)

ComfyUI 原生 MOSS-Image 加载器，输出标准的 MODEL、CLIP、VAE 对象，可直接复用 ComfyUI 自带的采样、引导与显存管理节点。

Fork 自 [OpenMOSS/MOSS-Image](https://github.com/OpenMOSS/MOSS-Image)（原仓 `comfyui/` 子树），作为独立 custom node 重新发布。

## 安装

```bash
cd ComfyUI/custom_nodes
git clone https://github.com/wanaigc/comfyui-moss-Image.git
```

重启 ComfyUI 即可。插件复用 ComfyUI 自带的 Python 依赖，无需额外安装。

## 文档

使用说明请参考上游的[安装与使用指南](https://github.com/OpenMOSS/MOSS-Image/blob/main/comfyui/README.md)。

示例工作流见 [`example_workflows/moss-image.json`](example_workflows/moss-image.json)。

## 模型权重

权重需单独从 [MOSS-Image-Base](https://huggingface.co/OpenMOSS-Team/MOSS-Image-Base) 下载。将 HF Loader 的 `model_path` 指向包含 `transformer/`、`text_encoder/`、`tokenizer/`、`vae/` 的本地目录。

## 许可证

本项目采用 Apache-2.0 许可证，与上游 [OpenMOSS/MOSS-Image](https://github.com/OpenMOSS/MOSS-Image) 仓库保持一致。
