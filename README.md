Z-Image 工作流（中文｜English）
=

一个专为`文生图`打造的一键式高质量人像图像工作流
A one-click high-quality portrait image enhancement workflow based on Z-Image-Turbo + SeedVR2 Upscaler.

功能 | Features

| 功能 | 说明 |
|------|------|
| prompt-assistant (智谱/百度) | 上传任意人像图 → 自动反推中英文 Tag |
| Z-Image-Turbo（fp8 / bf16）极快初代 | 4步极速生成 1080p 级人像，保留完美面部细节 |
| SeedVR2 图像超分率 | 支持单张超分（真实电影感） |
| Hires-Fix + 4x-UltraSharp 最终精修 | 30% 上采 + 最锐细节恢复 |
| ComfyUI-Easy-Use 一键清理显存节点 | 防止爆显存，显存占用峰值仅） |
| rgthree-comfy 完整输出对比（Image Comparer） | 实时滑动对比原图 vs 最终结果 |

所需模型（请手动放入对应文件夹）| Required Models
=

| 节点 | 文件名 | 放置路径 | 下载链接（建议使用） |
|------|--------|----------|---------------------|
| Z-Image - UNet模型加载器 | `z_image_turbo_bf16.safetensors/z-image-turbo-fp8-e4m3fn.safetensors` | `ComfyUI\models\diffusion_models\` | https://huggingface.co/Comfy-Org/z_image_turbo/blob/main/split_files/diffusion_models/z_image_turbo_bf16.safetensors/ https://huggingface.co/T5B/Z-Image-Turbo-FP8/blob/main/z-image-turbo-fp8-e4m3fn.safetensors|
| Z-Image CLIP加载器 | `qwen_3_4b.safetensors` | `ComfyUI\models\text_encoders\` | https://huggingface.co/Comfy-Org/z_image_turbo/blob/main/split_files/text_encoders/qwen_3_4b.safetensors |
| Z-Image VAE加载器 | `ae.safetensors`| `ComfyUI\models\vae\` | https://huggingface.co/Comfy-Org/z_image_turbo/blob/main/split_files/vae/ae.safetensors/ |
| SeedVR2 DiT Model | `seedvr2_ema_3b_fp16.safetensors` | `ComfyUI\models\SEEDVR2\` | https://huggingface.co/numz/SeedVR2_comfyUI/tree/main|
| SeedVR2 VAE Model | `ema_vae_fp16.safetensors` | `ComfyUI\models\SEEDVR2\` | https://huggingface.co/numz/SeedVR2_comfyUI/blob/main/ema_vae_fp16.safetensors |
| 任意超分模型 | `4x-UltraSharp.pth` | `ComfyUI\models\upscale_models\` | https://huggingface.co/lokCX/4x-Ultrasharp/blob/main/4x-UltraSharp.pth|

必装自定义节点（强烈建议使用 ComfyUI-Manager 一键安装）Required Custom Nodes
=
安装方法
-

打开 ComfyUI → Manager  → 搜索插件名 → Install → 重启 ComfyUI 即可。

|节点包名称| GitHub 仓库地址|主要作用|必装/可选|
|--------|-----|------|-------|
| Efficiency Nodes | https://github.com/LucianoCirino/efficiency-nodes-comfyui | `高效K采样器` `高效加载器`|必装|
| ComfyUI-Easy-Use | https://github.com/yolain/ComfyUI-Easy-Use | `高清修复` `细节修复`|必装|
| rgthree-comfy | https://github.com/rgthree/rgthree-comfy | `图片对比（滑动对比）`|必装|
| SeedVR2 Video Upscaler | https://github.com/numz/ComfyUI-SeedVR2_VideoUpscaler | `图像超分节点`|必装|
| prompt-assistant | https://github.com/yawiii/comfyui_prompt_assistant | `智谱` `百度` `图生中英文提示词`|必装|
| comfyui-show-text | https://github.com/fairy-root/ComfyUI-Show-Text | `实时图片反推显示生成的提示`|必装|
| ComfyUI-Impact-Pack | https://github.com/ltdrdata/ComfyUI-Impact-Pack | `更多高级功能`|可选|


工作流使用方法 | How to Use
=

1. **将本仓库中的 `z-image.json` 拖入 ComfyUI 界面**
2. **第一次运行会自动提示缺失模型(`如果你前面安装全部完成的话`)，按提示下载或手动放入对应目录**
3. **双击画布搜索 `Load Image` 节点，上传你的人像原图(`反推图片所需`)**
4. **修改右侧提示词`或`直接使用自动反推的中文 Tag**
5. **生成图片结果自动保存在 `ComfyUI\output\`文件内**

推荐参数（已预设，可自行微调）
----

- 初代步骤：仅 4-8 步（极快）
- SeedVR2 分辨率：1024（可改 1440/4K，但显存会显著上升）
- Batch Size：5（时间与显存平衡最佳）
- Color Correction：Lab（最自然色彩）

示例效果 | Samples

工作流演示

![Z-Image 完整工作流](samples/Z-image.png)

| 原图 | 最终输出 `1920x1080` +`4步` + `dempp_2m_sde`+`sgm_uniform`|

![Z-Image 一键增强](samples/X-image.png)
