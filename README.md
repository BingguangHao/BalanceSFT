# BalanceSFT: Improving LLM Function Calling with Balanced Training Signals and Data Hardness

<p align="center">
         &nbsp&nbsp🤗 <a href="https://modelscope.cn/models/hbg400/Open-Agentic-tool-use">Dataset</a>&nbsp&nbsp | &nbsp&nbsp🤗 <a href="https://huggingface.co/Bingguang/FunReason">Model</a>&nbsp&nbsp | &nbsp&nbsp 📑 <a href="https://arxiv.org/pdf/2505.20192">Paper</a> &nbsp&nbsp ｜ &nbsp&nbsp📖 <a href="https://github.com/BingguangHao/FunReason">Github</a>
</p>

> [!IMPORTANT]
> 
> - **We have released our training dataset!**
> 
> - **We will release the code, waiting the confidential review of Ant Group.**
> 
> - **Please give a ⭐️ to follow the update which is also an incentive for us.**



## Abstract

> While Supervised Fine-Tuning (SFT) is the prevailing method for equipping Large Language Models (LLMs) with function calling capabilities, its effectiveness is often compromised by two critical challenges: 1) **Imbalanced Training Signals**, where lengthy Chain-of-Thought (CoT) reasoning tokens dominate the training signals over concise function calls in the learning objective, and 2) **Imbalanced Data Hardness**, characterized by a scarcity of hard training examples. To overcome these limitations, we propose Balanced Supervised Fine-tuning (**BalanceSFT**), a novel framework incorporates two key components: a Self-adjusted Signal Balancing (SSB) loss that employs a learnable hyperparameter to dynamically adjust the token contributions of CoT reasoning and function calls, together with a Hard Data Re-sampling (HDR) strategy that establishes a feedback loop to selectively generate new, high-quality complex data guided by model errors. Extensive experiments demonstrate the effectiveness of our proposed BalanceSFT framework. With BalanceSFT, a 7B model achieves function calling performance on par with state-of-the-art giants like GPT-4o. Our code, models, and dataset are open-sourced.
>

## FunReason

<p align="center">
<img src="./img/datamake.png" width="100%" alt="thinking_template" />
</p>

**Overview of FunReason's data refinement pipeline.** The pipeline consists of five stages: Function Call Classification, Query and Tool Identification, CoT Identification, Function and Parameter Identification, and Format Identification. Each stage ensures specific aspects of data quality, with failing examples either being discarded or regenerated.

**We will release all the data that refined in this process, whcih contains 60k high quality CoT data for function call.**


<p align="center">
<img src="./img/MSL.png" width="100%" alt="thinking_template" />
</p>

**Self-Refinement Multiscale Loss.** Traditional loss functions often overemphasize the lengthy reasoning process at the expense of function call accuracy. The inherent trade-off between reasoning quality and function call correctness, leading to the development of our balanced approach.

<p align="center">
<img src="./img/training.png" width="100%" alt="thinking_template" />
</p>

**Self Refinement Strategy.** Following the MSL training, we employ a Self-Refinement strategy to further enhance the model capabilities. In this phase, the MSL-trained model samples from the original xLAM dataset, generating its own Chain-of-Thought reasoning and corresponding function calls. Subsequently, this self-generated data is fed into the data refinement pipeline for automated inspection and improvement. Only the refined data, having passed the rigorous quality checks of the data refinement, is then used to further update the model's parameters. This iterative process allows the model to learn from its own improved outputs, leading to continuous self-enhancement of its function calling and reasoning abilities.

## Main Result
<p align="center">
<img src="./img/result.png" width="100%" alt="thinking_template" />
</p>


<p align="center">
<img src="./img/code.png" width="100%" alt="thinking_template" />
</p>


## Citation
```md
@article{FunReason,
  title={FunReason: Enhancing Large Language Models' Function Calling via Self-Refinement Multiscale Loss and Automated Data Refinement},
  author={Bingguang Hao, Maolin Wang, Zengzhuang Xu, Cunyin Peng, Yicheng Chen, Xiangyu Zhao, Jinjie Gu, Chenyi Zhuang},
  journal={arXiv preprint arXiv:2505.20192},
  year={2025}
}
```
