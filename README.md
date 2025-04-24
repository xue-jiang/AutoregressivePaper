# Paper List --> Autoregressive Model
ICCV, CVPR, ECCV，AAAI, NIPS, ICLR

## Autoregressive Image Generation Method
| title | paper | link | tips | dataset |
| ------------- | ------------- | ------------- | ------------- | ------------- |
|Autoregressive Image Generation without Vector Quantization|[NIPS-2024](https://arxiv.org/pdf/2406.11838) | [link](https://github.com/LTH14/mar) |提出使用扩散过程在连续值空间中建模每个 token 的概率分布，定义 Diffusion Loss 函数，消除对离散 tokenizer 的需求。| ImageNet |
|Direction-Aware Diagonal Autoregressive Image Generation| [2025](https://arxiv.org/pdf/2503.11129) | [DAR](https://arxiv.org/pdf/2503.11129) | 提出使用对角扫描顺序生成图像 token，确保相邻 token 在空间上接近。引入方向感知模块 (4D-ROPE 和方向嵌入) 处理生成方向变化。使用图像 tokenizer 的 codebook 作为 token 嵌入。| ImageNet|
|Improving Autoregressive Image Generation through Coarse-to-Fine Token Prediction | [2025](https://arxiv.org/pdf/2503.16194) | [link](https://github.com/GzyAftermath/CTF) | |
|SimpleAR: Pushing the Frontier of Autoregressive Visual Generation through Pretraining, SFT, and RL | [2025](https://arxiv.org/pdf/2504.11455) | [SimpleAR](https://github.com/wdrink/SimpleAR)| text-to-image benchmarks (e.g., GenEval, DPG), COCO, ImageNet (基于相关研究惯例)|
|Customize Your Visual Autoregressive Recipe with Set Autoregressive Modeling | [2024](https://arxiv.org/pdf/2410.10511) | [SAR](https://arxiv.org/pdf/2410.10511) | 提出集合自回归建模 (SAR)，将 AR 从固定栅格顺序的下一 token 预测推广到“下一集合”预测，允许更灵活的生成。| |
|Visual Autoregressive Modeling: Scalable Image Generation via Next-Scale Prediction| [2024](https://arxiv.org/pdf/2404.02905) | [VAR](https://arxiv.org/pdf/2404.02905) | 提出 Visual Autoregressive modeling (VAR)，将图像上的自回归学习重新定义为 coarse-to-fine 的“下一尺度预测”。 | ImageNet, (也提到了 zero-shot 图像编辑结果，暗示使用了用于预训练和编辑能力评估的数据集，如 COCO, LAION)|
