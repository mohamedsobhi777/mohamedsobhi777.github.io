---
layout: page
title: LLM Reasoning with GRPO
description: Reinforcement learning for language-model reasoning on a single GPU.
importance: 2
category: research
---

I post-trained Qwen3.5-0.8B Base with GRPO using BF16 LoRA and Hugging Face TRL on a single 16 GB GPU. After 300 steps, held-out greedy exact-solve accuracy increased from 0% to 33.2% (85 of 256), without supervised fine-tuning.

[View the project on GitHub](https://github.com/mohamedsobhi777/countdown-grpo).
