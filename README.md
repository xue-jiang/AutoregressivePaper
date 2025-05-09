# Paper List --> Autoregressive Image Generation
ICCV, CVPR, ECCV，AAAI, NIPS, ICLR  
Summary of recent papers on Autoregressive Image Generation, continuously updated ......

- [Autoregressive Image Generation Method](#1)
- [Autoregressive model efficiency and component improvements](#2)
- [Unified and Multimodal Autoregressive Models](#3)
- [Specific visual tasks based on autoregressive models](#4)
- [Others](#5)

<a name="1"></a>
## Autoregressive Image Generation Method
> This type of paper focuses on improving the basic methods, architectures, and training strategies of autoregressive models for image generation.

| title | paper | code | tips | dataset |
| ------------- | ------------- | ------------- | ------------- | ------------- |
|Autoregressive Image Generation without Vector Quantization|[NeurIPS-2024](https://arxiv.org/pdf/2406.11838) | [MAR](https://github.com/LTH14/mar) |提出使用扩散过程在连续值空间中建模每个 token 的概率分布，定义 Diffusion Loss 函数，消除对离散 tokenizer 的需求。| ImageNet |
|Visual Autoregressive Modeling: Scalable Image Generation via Next-Scale Prediction| [NeurIPS-2024](https://arxiv.org/pdf/2404.02905) | [VAR](https://github.com/FoundationVision/VAR) | 提出 Visual Autoregressive modeling (VAR)，将图像上的自回归学习重新定义为 coarse-to-fine 的“下一尺度预测”。 | ImageNet|
|FAR: Frequency Autoregressive Image Generation with Continuous Tokens | [2025](https://arxiv.org/pdf/2503.05305) | [FAR](https://yuhuustc.github.io//projects/FAR.html) | 提出 Frequency Autoregressive (FAR) 范式，使用连续 token 进行图像生成。定义频谱依赖作为回归方向，高频分量基于低频分量构建图像。探索 FAR 与连续 tokenizer 的集成。| |

<a name="2"></a>
##  Autoregressive model efficiency and component improvements
> These papers focus on increasing the speed of generating autoregressive models, reducing computing resource consumption, or improving key components such as tokenizers and latent spaces.

| title | paper | code | tips | dataset | key points |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
|SimpleAR: Pushing the Frontier of Autoregressive Visual Generation through Pretraining, SFT, and RL | [2025](https://arxiv.org/pdf/2504.11455) | [SimpleAR](https://github.com/wdrink/SimpleAR)| 提出 SimpleAR，一个没有复杂架构修改的普通自回归视觉生成框架。通过优化训练和推理流程，结合预训练、监督微调 (SFT) 和强化学习 (RL) 提升性能。|text-to-image benchmarks (e.g., GenEval, DPG), COCO, ImageNet| SFT & RL |
|SWITTI: Designing Scale-Wise Transformers for Text-to-Image Synthesis|[CVPR-2025](https://arxiv.org/pdf/2412.01819)| [SWITTI](https://arxiv.org/pdf/2412.01819) | 提出 SWITTI，一个用于 text-to-image 生成的 scale-wise transformer。调整现有的 next-scale prediction AR 架构，解决训练稳定性并提高采样效率。|使用 LLaVA-v1.4-13B, LLaVA-v1.6-34B 和 ShareGPT4V 模型进行了重新配文，并根据 OpenCLIP ViT-G/14 选择了最佳标题| |
|Improving Autoregressive Image Generation through Coarse-to-Fine Token Prediction | [2025](https://arxiv.org/pdf/2503.16194) | [link](https://github.com/GzyAftermath/CTF) | 提出粗到细 (CTF) token 预测方法，分两阶段预测：先预测粗略标签（聚类索引），再根据粗略标签预测精细标签（码本索引）。利用大型 codebook 中的冗余简化 AR 建模。| | CFT & 聚类 |
|E-CAR: Efficient Continuous Autoregressive Image Generation via Multistage Modeling| [2024](https://arxiv.org/pdf/2412.14170) |  |提出 E-CAR，通过多阶段建模实现高效连续自回归图像生成。采用阶段式连续 token 生成策略和多阶段 flow-based 分布建模方法。|| next-scale |
|FastVAR: Linear Visual Autoregressive Modeling via Cached Token Pruning | [2025](https://arxiv.org/pdf/2503.23367) | [FastVAR](https://github.com/csguoh/FastVAR) | 提出 FastVAR，一种用于加速视觉自回归 (VAR) 模型分辨率缩放的后训练方法。开发缓存 token 剪枝策略，仅转发关键 token，使用之前尺度的缓存 token 恢复剪枝位置。 | ImageNet| 剪枝|
|Head-Aware KV Cache Compression for Efficient Visual Autoregressive Modeling|[2025](https://arxiv.org/pdf/2504.09261) | |提出 Head-Aware KV Cache Compression (HACK)，通过根据注意力头的不同行为和重要性，剪枝 KV cache 中不重要的 token 来提高 VAR 模型效率。|Infinity-2B| Attention Head |
|LazyMAR: Accelerating Masked Autoregressive Models via Feature Caching | [2025](https://arxiv.org/pdf/2503.12450) | [LazyMAR](https://github.com/feihongyan1/LazyMAR) |旨在加速 Masked Autoregressive (MAR) 模型。通过利用 Token Redundancy (相邻解码步中的相似 token 表示) 和 Condition Redundancy (classifier-free guidance 中的条件和无条件输出的相似差异) 来研究缓存机制。| | 缓存 |
|Numerical Pruning for Efficient Autoregressive Models| [AAAI-2025](https://arxiv.org/pdf/2412.12441) | | 通过结构化权重剪枝压缩 decoder-only transformer-based 自回归模型，提高语言和图像生成任务的效率。| | 剪枝|
|Stabilize the Latent Space for Image Autoregressive Modeling: A Unified Perspective | [NeurIPS-2024](https://arxiv.org/pdf/2410.12490) | [DiGIT](https://github.com/DAMO-NLP-SG/DiGIT) | 研究自回归模型在图像生成方面落后于 latent diffusion models 和 masked image models 的原因。提出统一的视角分析 latent space 与生成模型的关系。| | |
|Scalable Autoregressive Image Generation with Mamba | [2025](https://arxiv.org/pdf/2408.12245) | [AiM](https://github.com/hp-l33/AiM) | 引入 AiM，一个基于 Mamba 架构的自回归图像生成模型。使用 Mamba 代替 Transformer，旨在提高生成质量和推理速度。直接使用 next-token prediction 范式。| ImageNet | Mamba|
| Parallelized Autoregressive Visual Generation| [CVPR-2025](https://arxiv.org/pdf/2412.15119) | [PAR](https://yuqingwang1029.github.io/PAR-project/) |提出一种并行化自回归视觉生成方法，利用视觉 token 之间的弱依赖性，并行生成远距离 token，同时顺序生成强依赖的局部 token。|ImageNet, UCF-101|并行推理|
|LANTERN: Accelerating Visual Autoregressive Models with Relaxed Speculative Decoding| [ICLR-2025](https://arxiv.org/pdf/2410.03355) | [LANTERN](https://github.com/jadohu/LANTERN)|提出 LANTERN，一种用于加速视觉自回归模型推断的宽松推测解码接受条件，利用潜在空间中 token 的可互换性。|MS-COCO (validation captions)|token |
|Direction-Aware Diagonal Autoregressive Image Generation| [2025](https://arxiv.org/pdf/2503.11129) | [DAR](https://arxiv.org/pdf/2503.11129) | 提出使用对角扫描顺序生成图像 token，确保相邻 token 在空间上接近。引入方向感知模块 (4D-ROPE 和方向嵌入) 处理生成方向变化。使用图像 tokenizer 的 codebook 作为 token 嵌入。| ImageNet| 对角扫描|
|Customize Your Visual Autoregressive Recipe with Set Autoregressive Modeling | [2024](https://arxiv.org/pdf/2410.10511) | [SAR](https://github.com/poppuppy/SAR) | 提出集合自回归建模 (SAR)，将 AR 从固定栅格顺序的下一 token 预测推广到“下一集合”预测，允许更灵活的生成。| | 集合预测|

<a name="3"></a>
## Unified and Multimodal Autoregressive Models
> These papers explore applying autoregressive models to unified vision and language tasks, or to handle multimodal data.

| title | paper | code | tips | dataset |
| ------------- | ------------- | ------------- | ------------- | ------------- |
|Generative Multimodal Pretraining with Discrete Diffusion Timestep Tokens| [CVPR-2025](https://arxiv.org/pdf/2504.14666) | [DDT-LLAMA](https://ddt-llama.github.io/) | 通过利用扩散时间步学习离散的、递归的视觉 token 来统一视觉理解和生成。提出的 token 递归地补偿噪声图像中属性的逐步损失。引入 DDT-LLaMA 模型。| ImageNet|
|JanusFlow: Harmonizing Autoregression and Rectified Flow for Unified Multimodal Understanding and Generation| [CVPR-2025](https://arxiv.org/pdf/2411.07975) | [Janus](https://github.com/deepseek-ai/Janus) | 提出 JanusFlow 框架，将图像理解和生成统一在一个模型中。将自回归语言模型与 rectified flow 集成。解耦理解和生成编码器并在统一训练期间对齐它们的表示。| |
|UGen: Unified Autoregressive Multimodal Model with Progressive Vocabulary Learning| [2025](https://arxiv.org/pdf/2503.21193) | | 提出 UGen，一个统一的自回归多模态模型，用于同时进行文本处理、图像理解和图像生成。将文本和图像转换为离散 token 序列，使用单个 transformer 自回归生成。采用渐进式词汇学习机制。| |
|Unified Autoregressive Visual Generation and Understanding with Continuous Tokens | [2025](https://arxiv.org/pdf/2503.13436) | | 提出 UniFluid，一个使用连续视觉 token 进行联合视觉生成和理解的统一自回归框架。处理多模态图像和文本输入，生成离散文本 token 和连续图像 token。| |
|VARGPT-v1.1: Improve Visual Autoregressive Large Unified Model via Iterative Instruction Tuning and Reinforcement Learning | [2025](https://arxiv.org/pdf/2504.02949) | [VARGPT-v1.1](https://github.com/VARGPT-family/VARGPT-v1.1) |提出 VARGPT-v1.1，一个改进的统一视觉自回归模型。保留 next-token prediction for visual understanding 和 next-scale generation for image synthesis 的双重范式。整合迭代视觉指令微调和强化学习 (DPO)。| |
|TIGeR: Unifying Text-to-Image Generation and Retrieval with Large Multimodal Models | [ICLR-2025](https://arxiv.org/pdf/2406.05814) | [TIGeR](https://tiger-t2i.github.io/) | 提出 TIGeR，一个使用单一大型多模态模型 (LMM) 统一 text-to-image 生成和检索的框架。探索 LMM 的判别能力实现无需训练的生成式检索，并提出自主决策机制选择生成或检索。| TIGeR-Bench |

<a name="4"></a>
## Specific visual tasks based on autoregressive models
> This type of paper applies autoregressive models to solve specific visual problems beyond image generation, such as image editing, conditional generation, style transfer, etc.

| title | paper | code | tips | dataset | key points |
| ------------- | ------------- | ------------- | ------------- | ------------- | ------------- |
|A Training-Free Style-aligned Image Generation with Scale-wise Autoregressive Model | [2025](https://arxiv.org/pdf/2504.06144) | |提出一种无需训练的风格对齐图像生成方法，利用 scale-wise 自回归模型。包括初始特征替换、关键特征插值和动态风格注入。| |风格对齐|
|Anchor Token Matching: Implicit Structure Locking for Training-free AR Image Editing| [2025](https://arxiv.org/pdf/2504.10434) | [ATM](https://github.com/hutaiHang/ATM) | 提出隐式结构锁定 (ISLock)，一种无需训练的自回归 (AR) 图像编辑方法。使用“锚点 token 匹配”来隐式锁定结构，在注意力图过程中确保对齐。| PIE-Bench|图像编辑|
|Autoregressive Omni-Aware Outpainting for Open-Vocabulary 360-Degree Image Generation| [AAAI-2024](https://arxiv.org/pdf/2309.03467) | [AOG-NET-360](https://github.com/zhuqiangLu/AOG-NET-360) | 提出自回归全景感知外绘 (AOGNet) 模型，用于从窄视场 (NFoV) 图像逐步合成 360 度图像，结合 NFoV 和文本指导。| |360度图像|
|ControlAR: Controllable Image Generation with Autoregressive Models | [ICLR-2025](https://arxiv.org/pdf/2410.02705) | [ControlAR](https://arxiv.org/pdf/2410.02705) | 探索自回归模型中的控制到图像生成。引入轻量级控制编码器将空间输入 (边缘图、深度图) 转换为控制 token。采用条件解码方法生成图像 token。| | |
|EditAR: Unified Conditional Generation with Autoregressive Models | [2025](https://arxiv.org/pdf/2501.04699) |[EditAR](https://jitengmu.github.io/EditAR/) | 提出 EditAR，一个用于各种条件图像生成任务的统一条件自回归模型 (图像编辑、深度图到图像、边缘图到图像、分割图到图像)。|PIE-Bench| 图像编辑|
|Fine-Tuning Visual Autoregressive Models for Subject-Driven Generation|[2025](https://arxiv.org/pdf/2504.02612)|[link](https://github.com/jiwoogit/ARBooth) | 专注于调整视觉自回归 (VAR) 模型用于主体驱动的图像生成，即根据少量示例和文本提示生成特定主体的图像。| | |
|MultiDiff: Consistent Novel View Synthesis from a Single Image | [CVPR-2024](https://arxiv.org/pdf/2406.18524) | [MultiDiff](https://sirwyver.github.io/MultiDiff/) |引入 MultiDiff，通过结合单目深度预测器和视频扩散先验，从单张 RGB 图像合成一致的新视角。|RealEstate10K, ScanNet|多视角图像生成|
|VIewDiff: 3D-Consistent Image Generation with Text-to-Image Models | [CVPR-2024](https://arxiv.org/pdf/2403.01807) | [ViewDiff](https://lukashoel.github.io/ViewDiff/) | 提出 ViewDiff，一种使用预训练 text-to-image 扩散模型进行 3D 一致图像生成的方法。将 3D 体积渲染和跨帧注意力层集成到 U-Net 中。设计自回归生成方案。| ScanNet, RealEstate10K| 3D视角|
|Autoregressive Video Generation without Vector Quantization| [ICLR-2025](https://arxiv.org/pdf/2412.14169) | [NOVA](https://github.com/baaivision/NOVA) | 提出 NOVA，一种用于高效灵活的无矢量量化自回归视频生成方法。将视频生成重新定义为时间上的逐帧和空间上的逐集合预测的无量化自回归建模。| | 视频生成|
|Make Autoregressive Great Again: Diffusion-Free Graph Generation with Next-Scale Prediction| [2025](https://arxiv.org/pdf/2503.23612) | |提出 MAG，一个基于 next-scale prediction 的无扩散图生成框架，灵感来自视觉自回归方法。利用潜在表示的层次结构逐步生成整个图的尺度，无需显式节点排序。| generic graph datasets, molecular graph datasets| 图生成|
|OctGPT: Octree-based Multiscale Autoregressive Models for 3D Shape Generation | [2025](https://arxiv.org/pdf/2504.09975) | [OctGPT](https://github.com/octree-nn/octgpt) |提出 OctGPT，一个用于 3D 形状生成的新型多尺度自回归模型。采用序列化八叉树表示捕获 3D 形状的层次和空间结构。使用八叉树编码粗略几何，使用 VQ-VAE 生成的二元 token 表示精细细节。 | ShapeNet、Objaverse| 3D|
|Provably Secure Robust Image Steganography via Cross-Modal Error Correction| [AAAI-2025](https://arxiv.org/pdf/2412.12206) | | 提出一种基于状态最优自回归图像生成模型的高质量、可证明安全且鲁棒的图像隐写术。利用 VQ tokenizers 生成 stego 图像。采用跨模态纠错框架生成 stego 文本以辅助恢复和提取信息。| |图像隐写|
|Scenario Dreamer: Vectorized Latent Diffusion for Generating Driving Simulation Environments| [CVPR-2025](https://arxiv.org/pdf/2503.22496) | [Scenario Dreamer](https://princeton-computational-imaging.github.io/scenario-dreamer/) | 引入 Scenario Dreamer，一个数据驱动的自动驾驶规划生成模拟器，生成初始交通场景和逼真智能体行为。使用矢量化潜在扩散模型生成初始场景，自回归 Transformer 模拟智能体行为。支持通过扩散 inpainting 进行场景外推。| | 驾驶场景|
|Topic-VQ-VAE: Leveraging Latent Codebooks for Flexible Topic-Guided Document Generation | [AAAI-2024](https://arxiv.org/pdf/2312.11532) | [Topic-VQ-VAE](https://github.com/clovaai/TVQ-VAE) | 提出 Topic-VQ-VAE (TVQ-VAE)，一个利用 VQ-VAE 潜在 codebooks 的生成式主题模型，用于灵活的主题引导文档生成。将潜在 codebooks 和嵌入解释为概念上的词袋。| | |
|Diffusion Beats Autoregressive: An Evaluation of Compositional Generation in Text-to-Image Models| [NeurIPS-2024](https://arxiv.org/pdf/2410.22775) | | 评估和比较扩散模型 (FLUX, Stable Diffusion) 和自回归 (AR) 模型 (LlamaGen) 在 text-to-image 合成中的组合生成能力，专注于准确渲染复杂的组合。| T2I-CompBench |分析|

<a name="5"></a>
## Others
| title | paper | code | tips | dataset |
| ------------- | ------------- | ------------- | ------------- | ------------- |
|GigaTok: Scaling Visual Tokenizers to 3 Billion Parameters for Autoregressive Image Generation | [2025](https://arxiv.org/pdf/2504.08736) | [GigaTok](https://silentview.github.io/GigaTok/) | 专注于缩放视觉 tokenizer，解决缩放 tokenizer 提高重建质量但可能降低下游生成质量的问题。提出 GigaTok，通过语义正则化对齐 tokenizer 特征和语义一致特征。探索缩放 tokenizer 的实践。| |
|Autoregressive Distillation of Diffusion Transformers | [CVPR-2025](https://arxiv.org/pdf/2504.11295) | [ARD](https://github.com/alsdudrla10/ARD) |引入 Autoregressive Distillation (ARD)，一种将 Diffusion Transformer 模型蒸馏成少步骤学生模型的新方法。利用 Probability Flow ODE 的历史轨迹预测未来步骤，减轻曝光偏差。 | ImageNet 256p|
|Safe-VAR: Safe Visual Autoregressive Model for Text-to-Image Generative Watermarking | [2025](https://arxiv.org/pdf/2503.11324) | | 提出 Safe-VAR，第一个专为视觉自回归 (VAR) text-to-image 生成模型设计的数字水印框架。研究水印注入时机的影响，提出 Adaptive Scale Interaction Module 动态确定水印嵌入策略。| |




