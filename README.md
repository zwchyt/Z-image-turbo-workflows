Z-Image-Turbo`文生图`基本安装流程的工作流。
=
`所需模型流程`(请手动放入对应文件夹)

| 节点 | 文件名 | 放置路径 | 下载文件链接 |
|------|--------|----------|---------------------|
| UNet模型加载器 | `z_image_turbo_bf16.safetensors/z-image-turbo-fp8-e4m3fn.safetensors` | `ComfyUI\models\diffusion_models\` | https://huggingface.co/Comfy-Org/z_image_turbo/blob/main/split_files/diffusion_models/z_image_turbo_bf16.safetensors/ https://huggingface.co/T5B/Z-Image-Turbo-FP8/blob/main/z-image-turbo-fp8-e4m3fn.safetensors|
| CLIP加载器 | `qwen_3_4b.safetensors` | `ComfyUI\models\text_encoders\` | https://huggingface.co/Comfy-Org/z_image_turbo/blob/main/split_files/text_encoders/qwen_3_4b.safetensors |
| VAE加载器 | `ae.safetensors`| `ComfyUI\models\vae\` | https://huggingface.co/Comfy-Org/z_image_turbo/blob/main/split_files/vae/ae.safetensors/ |

安装插件节点
=
1.建议使用`git clone`命令安装，GitHub插件主页-Code-HTTPS复制-粘贴到你的comfyui文件目录-`ComfyUI\custom_nodes>git clone 插件HTTPS 回车`,在插件目录下安装插件所需依赖`pip install -r requirements.txt`(仔细查看插件依赖文件`requirements.txt`，避免安装破坏你的`comfyui环境`)。

2.使用ComfyUI-Manager 一键安装-打开 ComfyUI → Manager  → 搜索插件名 → Install → 重启 ComfyUI 即可。

|节点包名称| GitHub 仓库地址|主要作用|必装/可选|
|--------|-----|------|-------|
| Efficiency Nodes | https://github.com/LucianoCirino/efficiency-nodes-comfyui | `高效K采样器` `高效加载器`|可选|
| ComfyUI-Easy-Use | https://github.com/yolain/ComfyUI-Easy-Use | `高清修复` `细节修复`|可选|
| rgthree-comfy | https://github.com/rgthree/rgthree-comfy | `图片对比（滑动对比）`|可选|
| prompt-assistant | https://github.com/yawiii/comfyui_prompt_assistant | [百度](https://fanyi-api.baidu.com/) [智谱](https://www.bigmodel.cn/) `图反推中英文提示词`|可选|
| comfyui-show-text | https://github.com/fairy-root/ComfyUI-Show-Text | `实时图片反推显示生成的提示`|可选|
| ComfyUI-Impact-Pack | https://github.com/ltdrdata/ComfyUI-Impact-Pack | `更多高级功能`|可选|

工作流使用方法
=

1. 将本仓库中的 `z-image.json` 拖入 ComfyUI 界面
2. 第一次运行会自动提示缺失模型(`如果你前面安装全部完成的话`)，按提示下载或手动放入对应目录
3. 双击画布搜索 `Load Image` 节点，上传你的人像原图(`反推图片所需`)
4. 修改右侧提示词`或`直接使用自动反推的中文 Tag
5. 生成图片结果自动保存在 `ComfyUI\output\`文件内

推荐内容
=
注意力机制加速wel推荐:
-
[wel轮子集合](https://github.com/wildminder/AI-windows-whl) 

[flash-attn2](https://huggingface.co/Wildminder/AI-windows-whl/tree/main) `快速、内存高效的精确注意力机制，支持 I/O 感知`

[sageattention2](https://huggingface.co/Wildminder/AI-windows-whl/tree/main) `高效的注意力机制，具有彻底的异常值平滑和线程级 INT4 量化功能`

[spas_sage_attn](https://github.com/woct0rdho/SpargeAttn/releases) `一种无需训练的稀疏注意力机制，可加速任何模型推理`

Lora推荐：
-
[Midjourney Luneva Cinematic Lora](https://civitai.green/models/2185167/midjourney-luneva-cinematic-lora-and-workflow) `添加电影般的氛围和细节`

[Luneva Cyber + HD Enhancer](https://civitai.green/models/2215818/luneva-cyber-hd) `添加逼真的赛博朋克风格服饰`

图片细节和种子多样性插件推荐：
-
[ComfyUI-Detail-Daemon](https://github.com/Jonseed/ComfyUI-Detail-Daemon)

[Capitan-ConditioningEnhancer](https://github.com/capitan01R/Capitan-ConditioningEnhancer)

[SeedVarianceEnhancer](https://github.com/ChangeTheConstants/SeedVarianceEnhancer)

缓存模型加速：
-
[comfyui-cache-dit](https://github.com/xlite-dev/comfyui-cache-dit)

推荐参数（已预设，可自行微调）
----
- 步数：4-8 步
- CFG：1
- 采样器：dpmpp_2m_sde
- 调度器：sgm_uniform
- 降噪：1

工作流演示
![Z-Image 完整工作流](samples/Z-image.png)
效果图
![Z-Image 一键增强](samples/X-image.png)
