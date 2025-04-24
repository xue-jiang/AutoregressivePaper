# Paper List --> Autoregressive Model
ICCV, CVPR, ECCV，AAAI, NIPS, ICLR

## Autoregressive Image Generation Method
This type of paper focuses on improving the basic methods, architectures, and training strategies of autoregressive models for image generation.
| title | paper | link | tips | dataset |
| ------------- | ------------- | ------------- | ------------- | ------------- |
|Autoregressive Image Generation without Vector Quantization|[NIPS-2024](https://arxiv.org/pdf/2406.11838) | [link](https://github.com/LTH14/mar) |提出使用扩散过程在连续值空间中建模每个 token 的概率分布，定义 Diffusion Loss 函数，消除对离散 tokenizer 的需求。| ImageNet |
|Direction-Aware Diagonal Autoregressive Image Generation| [2025](https://arxiv.org/pdf/2503.11129) | [DAR](https://arxiv.org/pdf/2503.11129) | 提出使用对角扫描顺序生成图像 token，确保相邻 token 在空间上接近。引入方向感知模块 (4D-ROPE 和方向嵌入) 处理生成方向变化。使用图像 tokenizer 的 codebook 作为 token 嵌入。| ImageNet|
|Improving Autoregressive Image Generation through Coarse-to-Fine Token Prediction | [2025](https://arxiv.org/pdf/2503.16194) | [link](https://github.com/GzyAftermath/CTF) | 提出粗到细 (CTF) token 预测方法，分两阶段预测：先预测粗略标签，再根据粗略标签预测精细标签。利用大型 codebook 中的冗余简化 AR 建模。| |
|SimpleAR: Pushing the Frontier of Autoregressive Visual Generation through Pretraining, SFT, and RL | [2025](https://arxiv.org/pdf/2504.11455) | [SimpleAR](https://github.com/wdrink/SimpleAR)| 提出 SimpleAR，一个没有复杂架构修改的普通自回归视觉生成框架。通过优化训练和推理流程，结合预训练、监督微调 (SFT) 和强化学习 (RL) 提升性能。|text-to-image benchmarks (e.g., GenEval, DPG), COCO, ImageNet (基于相关研究惯例)|
|Customize Your Visual Autoregressive Recipe with Set Autoregressive Modeling | [2024](https://arxiv.org/pdf/2410.10511) | [SAR](https://arxiv.org/pdf/2410.10511) | 提出集合自回归建模 (SAR)，将 AR 从固定栅格顺序的下一 token 预测推广到“下一集合”预测，允许更灵活的生成。| |
|Visual Autoregressive Modeling: Scalable Image Generation via Next-Scale Prediction| [2024](https://arxiv.org/pdf/2404.02905) | [VAR](https://arxiv.org/pdf/2404.02905) | 提出 Visual Autoregressive modeling (VAR)，将图像上的自回归学习重新定义为 coarse-to-fine 的“下一尺度预测”。 | ImageNet, (也提到了 zero-shot 图像编辑结果，暗示使用了用于预训练和编辑能力评估的数据集，如 COCO, LAION)|

## Specific visual tasks based on autoregressive models
This type of paper applies autoregressive models to solve specific visual problems beyond image generation, such as image editing, conditional generation, style transfer, etc.
| title | paper | link | tips | dataset |
| ------------- | ------------- | ------------- | ------------- | ------------- |
|A Training-Free Style-aligned Image Generation with Scale-wise Autoregressive Model | [2025](https://arxiv.org/pdf/2504.06144) | |提出一种无需训练的风格对齐图像生成方法，利用 scale-wise 自回归模型。包括初始特征替换、关键特征插值和动态风格注入。| |
|Anchor Token Matching: Implicit Structure Locking for Training-free AR Image Editing| [2025](https://arxiv.org/pdf/2504.10434) | [ATM](https://github.com/hutaiHang/ATM) | 提出隐式结构锁定 (ISLock)，一种无需训练的自回归 (AR) 图像编辑方法。使用“锚点 token 匹配”来隐式锁定结构，在注意力图过程中确保对齐。| PIE-Bench, (也集成了 LlamaGen 和 Lumina-mGPT，暗示使用了这些模型所用的数据集如 LAION, COCO 等)|
|Autoregressive Omni-Aware Outpainting for Open-Vocabulary 360-Degree Image Generation| [AAAI-2024](https://arxiv.org/pdf/2309.03467) | [AOG-NET-360](https://github.com/zhuqiangLu/AOG-NET-360) | 提出自回归全景感知外绘 (AOGNet) 模型，用于从窄视场 (NFoV) 图像逐步合成 360 度图像，结合 NFoV 和文本指导。| |
|ControlAR: Controllable Image Generation with Autoregressive Models | [2025](https://arxiv.org/pdf/2410.02705) | [ControlAR](https://arxiv.org/pdf/2410.02705) | 探索自回归模型中的控制到图像生成。引入轻量级控制编码器将空间输入 (边缘图、深度图) 转换为控制 token。采用条件解码方法生成图像 token。| |
|EditAR: Unified Conditional Generation with Autoregressive Models | [2025](https://arxiv.org/pdf/2501.04699) |[EditAR](https://jitengmu.github.io/EditAR/) | 提出 EditAR，一个用于各种条件图像生成任务的统一条件自回归模型 (图像编辑、深度图到图像、边缘图到图像、分割图到图像)。|PIE-Bench, (也提到了基线模型 InstructPix2Pix, MagicBrush, 暗示使用了这些模型所用的数据集如 COCO, ImageNet, LAION 等)|
|Fine-Tuning Visual Autoregressive Models for Subject-Driven Generation|[2025](https://arxiv.org/pdf/2504.02612)|[link](https://github.com/jiwoogit/ARBooth) | 专注于调整视觉自回归 (VAR) 模型用于主体驱动的图像生成，即根据少量示例和文本提示生成特定主体的图像。| |
|SWITTI: Designing Scale-Wise Transformers for Text-to-Image Synthesis|[CVPR-2025](https://arxiv.org/pdf/2412.01819)| [SWITTI](https://arxiv.org/pdf/2412.01819) | 提出 SWITTI，一个用于 text-to-image 生成的 scale-wise transformer。调整现有的 next-scale prediction AR 架构，解决训练稳定性并提高采样效率。|MS-COCO (validation captions), (也提到了人体偏好研究和自动化评估，与现有 T2I AR 和扩散模型比较，暗示使用了标准 T2I 基准数据集)|

##  Autoregressive model efficiency and component improvements
These papers focus on increasing the speed of generating autoregressive models, reducing computing resource consumption, or improving key components such as tokenizers and latent spaces.
| title | paper | link | tips | dataset |
| ------------- | ------------- | ------------- | ------------- | ------------- |
|E-CAR: Efficient Continuous Autoregressive Image Generation via Multistage Modeling| [2024](https://arxiv.org/pdf/2412.14170) |  |提出 E-CAR，通过多阶段建模实现高效连续自回归图像生成。采用阶段式连续 token 生成策略和多阶段 flow-based 分布建模方法。||
|FastVAR: Linear Visual Autoregressive Modeling via Cached Token Pruning | [2025](https://arxiv.org/pdf/2503.23367) | [FastVAR](https://github.com/csguoh/FastVAR) | 提出 FastVAR，一种用于加速视觉自回归 (VAR) 模型分辨率缩放的后训练方法。开发缓存 token 剪枝策略，仅转发关键 token，使用之前尺度的缓存 token 恢复剪枝位置。 | ImageNet, (也提到了 zero-shot generation，暗示使用了用于预训练的数据集如 COCO, LAION 等)|
|Head-Aware KV Cache Compression for Efficient Visual Autoregressive Modeling|[2025](https://arxiv.org/pdf/2504.09261) | |提出 Head-Aware KV Cache Compression (HACK)，通过根据注意力头的不同行为和重要性，剪枝 KV cache 中不重要的 token 来提高 VAR 模型效率。|Infinity-2B, (也提到了 VAR-d30 模型，可能在大规模数据集如 ImageNet, OpenImages 等上训练)|

