# Qwen3-0.6B LoRA, 1914 Press Entity Extraction

LoRA adapters for `Qwen/Qwen3-0.6B` that the `press-extraction-lora-transformers` lab
trains to extract the people, places and organizations of a 1914 press passage as JSON:
the distillation of a larger model's labels into a small one. The lab loads them when it
runs without a GPU, where its own training is cut to a few examples.

## Files

- `fr/adapter_model.safetensors`, `fr/adapter_config.json`: trained with the French
  notebook's prompt.
- `en/adapter_model.safetensors`, `en/adapter_config.json`: trained with the English
  notebook's prompt (the passages and labels are the same, in French).

Rank 16, `lora_alpha` 32, dropout 0.05, on `q_proj`, `k_proj`, `v_proj` and `o_proj`.
Load one into the lab's PEFT model with `peft.set_peft_model_state_dict(model,
safetensors.torch.load_file("adapter_model.safetensors"))`, or onto the base model with
`peft.PeftModel.from_pretrained(model, "<lang>")`.

## Source

- Trained with the lab's own code (`trl.SFTTrainer`, one epoch over the 1,899 training
  examples of `press-1914-extraction/distill.jsonl` in shuuchuu/datasets, batches of 8
  with 2 accumulation steps, learning rate 2e-4, fp16, completion-only loss), on Colab's
  runtime image with an RTX A4000.
- Base model: Qwen3-0.6B, https://huggingface.co/Qwen/Qwen3-0.6B (Apache 2.0).
- Labels: `qwen3:4b-instruct-2507-q4_K_M`'s extractions (Apache 2.0) on public-domain
  passages of the BnF's 1914 press corpus.

## License

Apache 2.0, https://www.apache.org/licenses/LICENSE-2.0, like the base model.
