PEFT-QLoRA example for fine-tuning with the FreedomIntelligence/medical-o1-reasoning-SFT dataset. This code is inspired by community projects and uses the lightweight DeepSeek-R1-Distill-Qwen-1.5B model, making it efficient even on a free T4 GPU.

How It Works

Dataset Formatting: The medical-o1-reasoning-SFT dataset contains Question, Complex_CoT, and Response fields. The code formats these into a chat template that encourages step-by-step reasoning (...) before the final answer .

Efficient Training: QLoRA dramatically reduces memory usage by quantizing the base model to 4-bit, allowing this 1.5B parameter model to be trained on a standard T4 GPU . The SFTTrainer from the trl library handles the supervised fine-tuning loop

bitsandbytes - The 4-bit **Quantization Engine Purpose: Enables 4-bit quantization to dramatically reduce model memory usage.

Why You Need It:

Compresses a 1.5B parameter model from ~6GB (FP16) down to ~1.5GB (4-bit)

Allows training on free Colab GPUs (T4 with 16GB VRAM)

Libraries Used:

trl - Transformer Reinforcement Learning Purpose: Provides high-level trainers and utilities for fine-tuning language models, especially with RLHF and instruction tuning.
Why You Need It:

Provides SFTTrainer - the most convenient way to fine-tune on instruction datasets

Handles tokenization, batching, and training loop automatically

Built specifically for conversational/chat models
