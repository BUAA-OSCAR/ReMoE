# DeepSeek-V2-Lite-Chat-ReMoE-GGUF

This repository provides a GGUF release of **DeepSeek-V2-Lite-Chat-ReMoE**, a ReMoE-adapted Mixture-of-Experts (MoE) model for memory-constrained and edge-oriented LLM inference.

ReMoE is a router-only fine-tuning method designed to improve short-horizon expert reuse during autoregressive decoding. Instead of changing the model architecture, expert weights, inference kernels, or runtime cache policy, ReMoE fine-tunes only the MoE router/gate parameters. The goal is to make adjacent tokens reuse experts more often, improving expert-cache locality and reducing expert offloading overhead.

This GGUF version is intended for local inference with **Ollama** and GGUF-compatible runtimes.

## Project Links

* GitHub: [BUAA-OSCAR/ReMoE](https://github.com/BUAA-OSCAR/ReMoE)
* Hugging Face: [Zhu149248/DeepSeek-V2-Lite-Chat-ReMoE-GGUF](https://huggingface.co/Zhu149248/DeepSeek-V2-Lite-Chat-ReMoE-GGUF)

## Usage with Ollama

Install Ollama from the official website, then run the model directly from Hugging Face:

```bash
ollama run hf.co/Zhu149248/DeepSeek-V2-Lite-Chat-ReMoE-GGUF
```

To specify a quantization tag or a full GGUF filename:

```bash
ollama run hf.co/Zhu149248/DeepSeek-V2-Lite-Chat-ReMoE-GGUF:Q4_K_M
```

or:

```bash
ollama run hf.co/Zhu149248/DeepSeek-V2-Lite-Chat-ReMoE-GGUF:YOUR_MODEL_FILE.gguf
```

Example prompt:

```bash
ollama run hf.co/Zhu149248/DeepSeek-V2-Lite-Chat-ReMoE-GGUF \
  "Explain ReMoE in one paragraph."
```

Ollama downloads the GGUF file on first use and caches it locally.

## Use and Limitations

This model is mainly intended for local MoE inference, expert-offloading experiments, and ReMoE-related routing-locality research. Its efficiency benefit is most relevant when expert weights are constrained by cache capacity, memory bandwidth, or storage bandwidth.

This release inherits the capabilities, limitations, and license restrictions of `deepseek-ai/DeepSeek-V2-Lite-Chat`. GGUF quantization and runtime configuration may affect quality and latency.

## License and Attribution

This repository is a ReMoE-adapted GGUF derivative of `deepseek-ai/DeepSeek-V2-Lite-Chat`. The original model weights are subject to the DeepSeek Model License.

Original model copyright notice:

```text
Copyright (c) 2023 DeepSeek
```

## Citation

```bibtex
@inproceedings{
zhu2026remoe,
title={ReMoE: Boosting Expert Reuse through Router Fine-Tuning in Memory-Constrained MoE {LLM} Inference},
author={Xiongwei Zhu and Xiaojian Liao and Tianyang Jiang and Yusen Zhang and Liang Wang and Limin Xiao},
booktitle={Forty-third International Conference on Machine Learning},
year={2026},
url={https://openreview.net/forum?id=ylAhgNb2ak}
}
```

## Acknowledgements

This release builds on `deepseek-ai/DeepSeek-V2-Lite-Chat` by DeepSeek and the GGUF/Ollama inference ecosystem.
