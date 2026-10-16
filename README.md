# MOSS-Image for ComfyUI

![version](https://img.shields.io/badge/version-v0.1.1-blue)
![python](https://img.shields.io/badge/python-%3E%3D3.10-blue)
![comfyui](https://img.shields.io/badge/ComfyUI-native-green)
![license](https://img.shields.io/badge/license-Apache--2.0-green)

Native MOSS-Image loaders for ComfyUI that output standard MODEL, CLIP and VAE objects, so you can use ComfyUI's own sampling, guidance and memory management nodes.

Forked from [OpenMOSS/MOSS-Image](https://github.com/OpenMOSS/MOSS-Image) (the `comfyui/` subtree), republished as a standalone custom node.

## Installation

```bash
cd ComfyUI/custom_nodes
git clone https://github.com/wanaigc/comfyui-moss-Image.git
```

Restart ComfyUI. The plugin uses ComfyUI's bundled Python dependencies, no extra install step is required.

## Documentation

See the upstream [installation and usage guide](https://github.com/OpenMOSS/MOSS-Image/blob/main/comfyui/README.md).

The example workflow lives at [`example_workflows/moss-image.json`](example_workflows/moss-image.json).

## Model weights

Download the weights separately from [MOSS-Image-Base](https://huggingface.co/OpenMOSS-Team/MOSS-Image-Base). Point the HF Loader's `model_path` at the local directory containing `transformer/`, `text_encoder/`, `tokenizer/` and `vae/`.

## License

This project is available under the Apache-2.0 license, same as the upstream [OpenMOSS/MOSS-Image](https://github.com/OpenMOSS/MOSS-Image) repository.
