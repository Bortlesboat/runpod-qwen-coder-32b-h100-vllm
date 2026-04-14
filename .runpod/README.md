# Qwen 2.5 Coder 32B H100 vLLM Worker

Deploy `Qwen/Qwen2.5-Coder-32B-Instruct` on RunPod Hub with an OpenAI-compatible `vLLM` worker tuned for premium coding and H100-class inference.

## Best for

- stronger repo copilots and code-review assistants,
- teams that want a deployable coding-tuned 32B model,
- users searching for `Qwen Coder 32B`, `H100`, or premium coding inference on RunPod Hub.

## Request shapes

- `prompt` for `/v1/completions`
- `messages` for `/v1/chat/completions`
- `route` + `body` for explicit OpenAI-compatible requests

## Main knobs

- `MODEL_NAME`
- `MAX_MODEL_LEN`
- `GPU_MEMORY_UTILIZATION`
- `MAX_NUM_SEQS`
- `DEFAULT_MAX_TOKENS`
- `MAX_CONCURRENCY`

The smoke test uses a smaller coder-family model on easier-to-find GPU capacity, but the deployment presets stay centered on H100-class coding use.
