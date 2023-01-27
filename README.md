# Hungry Hungry Hippos (H3)

This repository provides the official implementation of H3 from the
following paper.

**Hungry Hungry Hippos: Towards Language Modeling with State Space Models**  
Tri Dao\*, Daniel Y. Fu\*,  Khaled K. Saab, Armin W. Thomas, Atri Rudra, Christopher Ré  
International Conference on Learning Representations, 2023. Notable top-25% (spotlight).  
Paper: https://arxiv.org/abs/2212.14052

# Abstract
State space models (SSMs) have demonstrated state-of-the-art sequence modeling performance in some modalities, but underperform attention in language modeling. Moreover, despite scaling nearly linearly in sequence length instead of quadratically, SSMs are still slower than Transformers due to poor hardware utilization. In this paper, we make progress on understanding the expressivity gap between SSMs and attention in language modeling, and on reducing the hardware barrier between SSMs and attention. First, we use synthetic language modeling tasks to understand the gap between SSMs and attention. We find that existing SSMs struggle with two capabilities: recalling earlier tokens in the sequence and comparing tokens across the sequence. To understand the impact on language modeling, we propose a new SSM layer, H3, that is explicitly designed for these abilities. H3 matches attention on the synthetic languages and comes within 0.4 PPL of Transformers on OpenWebText. Furthermore, a hybrid 125M-parameter H3-attention model that retains two attention layers surprisingly outperforms Transformers on OpenWebText by 1.0 PPL. Next, to improve the efficiency of training SSMs on modern hardware, we propose FlashConv. FlashConv uses a fused block FFT algorithm to improve efficiency on sequences up to 8K, and introduces a novel state passing algorithm that exploits the recurrent properties of SSMs to scale to longer sequences. FlashConv yields 2× speedup on the long-range arena benchmark and allows hybrid language models to generate text 1.6× faster than Transformers. Using FlashConv, we scale hybrid H3-attention language models up to 1.3B parameters on the Pile and find promising initial results, achieving lower perplexity than Transformers and outperforming Transformers in zero- and few-shot learning on a majority of tasks in the SuperGLUE benchmark.


![H3](assets/banner.png)

# Code & model release

You can find model weights on the Hugging Face Hub here (under "Files and Versions" for each model):
* [125M](https://huggingface.co/danfu09/H3-125M)
* [355M](https://huggingface.co/danfu09/H3-355M)
* [1.3B](https://huggingface.co/danfu09/H3-1.3B)
* [2.7B](https://huggingface.co/danfu09/H3-2.7B)

An example of how to load the weights is given in `benchmarks/benchmark_generation.py`.
More examples coming soon!

## Acknowledgments
Some of the files related to S4D and HiPPO initialization are
adapted from the https://github.com/HazyResearch/state-spaces.

## Citation
If you use this codebase, or otherwise found our work valuable, please cite:
```
@inproceedings{dao2023hungry,
  title={Hungry {H}ungry {H}ippos: Towards Language Modeling with State Space Models},
  author={Dao, Tri and Fu, Daniel Y. and Saab, Khaled K. and Thomas, Armin W.
  and Rudra, Atri and R{\'e}, Christopher},
  booktitle={International Conference on Learning Representations},
  year={2023}
}
```
