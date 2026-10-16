# MOSS-Image for ComfyUI

English | [中文](./README_ZH.md)

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



## Model Files

| Component        | File                                                       | Size    | Format                                          |
| ---------------- | ---------------------------------------------------------- | ------- | ----------------------------------------------- |
| **DiT**          | `diffusion_models/moss_image_sft_int8_convrot.safetensors` | 5.25 GB | INT8 ConvRot (Modulation, Layer 0 & 41 in BF16) |
| **Text Encoder** | `text_encoders/qwen35_moss_int8_convrot.safetensors`       | 8.65 GB | INT8 ConvRot (SSM & Layer 31 in BF16)           |
| **VAE**          | `vae/flux2-vae.safetensors`                                | 238 MB  | FP32 (FLUX.2 Small Decoder, 384ch)              |

Download: [Quark Pan](https://pan.quark.cn/s/2c5661248312) (国内加速)

Place the files in your ComfyUI directories:

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

## Recommended Settings

| Setting                 | Value                     | Notes                                                     |
| ----------------------- | ------------------------- | --------------------------------------------------------- |
| **Sampler**             | `euler`                   | Flow-matching Euler                                       |
| **Scheduler**           | `sgm_uniform`             | Pairs with flow-matching shift                            |
| **Steps**               | `50`                      | 30–50 steps                                               |
| **CFG**                 | `3.0`                     | 2.5–3.5                                                   |
| **Shift**               | `5.0`                     | Set in `ModelSamplingSD3` node                            |
| **Skip Layer Guidance** | `22`                      | In `SkipLayerGuidanceDiTSimple`, set `single_layers="22"` |
| **Resolution**          | `1024×1024` or widescreen | Multiples of 16                                           |



## Documentation

See the upstream [installation and usage guide](https://github.com/OpenMOSS/MOSS-Image/blob/main/comfyui/README.md).

The example workflow lives at [`example_workflows/image_moss_sft_int8_t2i.json`](example_workflows/image_moss_sft_int8_t2i.json).



## License

This project is available under the Apache-2.0 license, same as the upstream [OpenMOSS/MOSS-Image](https://github.com/OpenMOSS/MOSS-Image) repository.
