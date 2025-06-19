# Deciphering Motion in Visual Dynamics: A Comprehensive Survey



## Full list

### Quick Links

- [Motion Estimation](#Motion Estimation)
  - [Estimation by Prediction](#Estimation by Prediction)
    - [Physics-Based Methods](#Physics-Based Methods)
    - [Sequential Modeling Networks](#Sequential Modeling Networks)
    - [Generative Models](#Generative Models)
  - [Estimation by Correlation](#Estimation by Correlation)
    - [Explicit Computation](#Explicit Computation)
    - [Two-Stream Architecture](#Two-Stream Architecture)
    - [Attention Mechanism](#Attention Mechanism)
    - [Implicit Learning](#Implicit Learning)
  - [Practical Strategies](#Practical Strategies)
    - [Iterative Refinement](#Iterative Refinement)
    - [Memory Augmentation](#Memory Augmentation)
    - [Online Update](#Online Update)
- [Motion Understanding](#Motion Understanding)
  - [Motion-Separated Modeling](#Motion-Separated Modeling)
    - [Intra-Block Separated Modeling](#Intra-Block Separated Modeling)
    - [Parallel Inter-Block Separated Modeling](#Parallel Inter-Block Separated Modeling)
    - [Sequential Inter-Block Separated Modeling](#Sequential Inter-Block Separated Modeling)
  - [Motion-Joint Modeling](#Motion-Joint Modeling)
    - [Local Operator](#Local Operator)
    - [Global Interaction](#Global Interaction)
    - [Local-Global Mechanism](#Local-Global Mechanism)
    - [LLM-based Modeling](#LLM-based Modeling)
  - [Context-Augmented Modeling](#Context-Augmented Modeling)
    - [Multimodal Fusion](#Multimodal Fusion)
    - [Cross-Modal Alignment](#Cross-Modal Alignment)
    - [Contextual Priors](#Contextual Priors)
- [Motion Generation](#Motion Generation)
  - [Explicit Motion Guidance](#Explicit Motion Guidance)
    - [Input-level Embedding](#Input-level Embedding)
    - [Latent-level Fusion](#Latent-level Fusion)
    - [Architecture-Level Integration](#Architecture-Level Integration)
  - [Implicit Motion Learning](#Implicit Motion Learning)
    - [Input-level Preparation](#Input-level Preparation)
    - [Architectural-level Refinement](#Architectural-level Refinement)
    - [Training Optimization](#Training Optimization)
  - [Practical Strategies](#Practical Strategies)
    - [Dynamic Condition](#Dynamic Condition)
    - [Frequency decomposition](#Frequency decomposition)
    - [Extract motion representation](#Extract motion representation)
    - [Autoregressive Generation](#Autoregressive Generation)

### Motion Estimation

#### Estimation by Prediction

##### Physics-Based Methods
16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32 33 34
| Title & Authors | Introduction | Links |
| ------------- | ------------- | ------------- |
|[An Introduction to the Kalman Filter](https://d1wqtxts1xzle7.cloudfront.net/52484748/Kalman_CoursePack_08-libre.pdf?1491379511=&response-content-disposition=inline%3B+filename%3DAn_Introduction_to_the_Kalman_Filter.pdf&Expires=1750353534&Signature=eCqfwl8yOdlKkJ249wukP8OUaorUeNjMB-SKiEAeqbIMT6EnQRQbx6UZ6jKUCQ5SdCV1CFghv6fNWXHGvduytueZ71b8EPx87Iwdi6CjCh8PZJPCSM47eDjYkJcR81FVMqQaDl9fjs50y1LlEN2HT6DwH4pc2ykGe3VdRdBNO7Cxs9mujCMeLu76RrWn53by5MYMI269-mG~k5br6rdhNxI23xFmVt16SceuaOkF3JN8TW3RXpwm7jESpLYovlDq3qTGejKEZ3zVlV5kOXw~wc8ZC9S7xy2bZJ9uF2WAWY0cQVMBal1XIPTqRdO8vpgPEtWOCg011L6mP4IZtC5dEA__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA) <br/> Greg Welch1 and Gary Bishop2 | ![image](images/16.png) | [Paper](https://d1wqtxts1xzle7.cloudfront.net/52484748/Kalman_CoursePack_08-libre.pdf?1491379511=&response-content-disposition=inline%3B+filename%3DAn_Introduction_to_the_Kalman_Filter.pdf&Expires=1750353534&Signature=eCqfwl8yOdlKkJ249wukP8OUaorUeNjMB-SKiEAeqbIMT6EnQRQbx6UZ6jKUCQ5SdCV1CFghv6fNWXHGvduytueZ71b8EPx87Iwdi6CjCh8PZJPCSM47eDjYkJcR81FVMqQaDl9fjs50y1LlEN2HT6DwH4pc2ykGe3VdRdBNO7Cxs9mujCMeLu76RrWn53by5MYMI269-mG~k5br6rdhNxI23xFmVt16SceuaOkF3JN8TW3RXpwm7jESpLYovlDq3qTGejKEZ3zVlV5kOXw~wc8ZC9S7xy2bZJ9uF2WAWY0cQVMBal1XIPTqRdO8vpgPEtWOCg011L6mP4IZtC5dEA__&Key-Pair-Id=APKAJLOHF5GGSLRBV4ZA) |
| [Simple Online and Realtime Tracking](https://arxiv.org/abs/1602.00763) <br/> Alex Bewley, Zongyuan Ge, Lionel Ott, Fabio Ramos, Ben Upcroft | ![image](images/17.png) | [Paper](https://arxiv.org/abs/1602.00763) |
| [Simple Online and Realtime Tracking with a Deep Association Metric](https://arxiv.org/abs/1703.07402) <br/> Nicolai Wojke, Alex Bewley, Dietrich Paulus | ![image](images/18.png) | [Paper](https://arxiv.org/abs/1703.07402) |
| [ByteTrack: Multi-Object Tracking by Associating Every Detection Box](https://arxiv.org/abs/2110.06864) <br/> Yifu Zhang, Peize Sun, Yi Jiang, Dongdong Yu, Fucheng Weng, Zehuan Yuan, Ping Luo, Wenyu Liu, Xinggang Wang | ![image](images/19.png) | [GitHub](https://github.com/FoundationVision/ByteTrack) <br/> [Paper](https://arxiv.org/abs/2110.06864) |
| [StrongSORT: Make DeepSORT Great Again](https://arxiv.org/abs/2202.13514) <br/> Yunhao Du, Zhicheng Zhao, Yang Song, Yanyun Zhao, Fei Su, Tao Gong, Hongying Meng | ![image](images/20.png) | [GitHub](https://github.com/dyhBUPT/StrongSORT) [ GitHub](https://github.com/open-mmlab/mmtracking) <br/> [Paper](https://arxiv.org/abs/2202.13514) |
| [BoT-SORT: Robust Associations Multi-Pedestrian Tracking](https://arxiv.org/abs/2206.14651) <br/> Nir Aharon, Roy Orfaig, Ben-Zion Bobrovsky | ![image](images/21.png) | [GitHub](https://github.com/NirAharon/BOT-SORT) <br/> [Paper](https://arxiv.org/abs/2206.14651) |
| [FeatureSORT: Essential Features for Effective Tracking](https://arxiv.org/abs/2407.04249) <br/> Hamidreza Hashempoor, Rosemary Koikara, Yu Dong Hwang | ![image](images/22.png) | [Paper](https://arxiv.org/abs/2407.04249) |
| [Hybrid-SORT: Weak Cues Matter for Online Multi-Object Tracking](https://arxiv.org/abs/2308.00783) <br/> Mingzhan Yang, Guangxin Han, Bin Yan, Wenhua Zhang, Jinqing Qi, Huchuan Lu, Dong Wang  | ![image](images/23.png) | [GitHub](https://github.com/ymzis69/HybridSORT) <br/> [Paper](https://arxiv.org/abs/2308.00783) |
| [Faster R-CNN: Towards Real-Time Object Detection with Region Proposal Networks](https://arxiv.org/abs/1506.01497) <br/> Shaoqing Ren, Kaiming He, Ross Girshick, Jian Sun | ![image](images/24.png) | [Paper](https://arxiv.org/abs/1506.01497) |
| [YOLOX: Exceeding YOLO Series in 2021](https://arxiv.org/abs/2107.08430) <br/> Zheng Ge, Songtao Liu, Feng Wang, Zeming Li, Jian Sun | ![image](images/25.png) | [GitHub](https://github.com/Megvii-BaseDetection/YOLOX) <br/> [Paper](https://arxiv.org/abs/2107.08430) |
| [The Hungarian method for the assignment problem](https://onlinelibrary.wiley.com/doi/abs/10.1002/nav.3800020109) <br/> H. W. Kuhn | ![image](images/26.png) | [Paper](https://www.math.toronto.edu/mccann/1855/KuhnNRL55.pdf) |


##### Sequential Modeling Networks
35 36 37 38 39 40 41 42 43 44 45 46 47 48 49 

##### Generative Models
50 51 34 52 53 54 55 56 57 58 59 60 49 61 62 63

#### Estimation by Correlation

##### Explicit Computation
64 65 66 67 68 69 70 71 72 73 74 75 76 77 78 

##### Two-Stream Architecture
79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96 

##### Attention Mechanism
97 98 99 100 101 102 103 104 105 106 107 108 109 110 111 112 113 114 115 44 93 49 45 116 117 

##### Implicit Learning
118 119 120 121 122 123 124 125 126 127 128

#### Practical Strategies

##### Iterative Refinement
129 121 122 123 130 102 95 96 41

##### Memory Augmentation
131 132 37 133 98 112 106 105 134 135 136

##### Online Update
64 65 118 137 121 122 123 138 139 140 141 98 99 112



### Motion Understanding

#### Motion-Separated Modeling

##### Intra-Block Separated Modeling

##### Parallel Inter-Block Separated Modeling

##### Sequential Inter-Block Separated Modeling

#### Motion-Joint Modeling

##### Local Operator

##### Global Interaction

##### Local-Global Mechanism

##### LLM-based Modeling

#### Context-Augmented Modeling

##### Multimodal Fusion

##### Cross-Modal Alignment

##### Contextual Priors

### Motion Generation

#### Explicit Motion Guidance

##### Input-level Embedding

##### Latent-level Fusion

##### Architecture-Level Integration

#### Implicit Motion Learning

##### Input-level Preparation

##### Architectural-level Refinement

##### Training Optimization

#### Practical Strategies

##### Dynamic Condition

##### Frequency decomposition

##### Extract motion representation

##### Autoregressive Generation

## Acknowledgement

## Citation
