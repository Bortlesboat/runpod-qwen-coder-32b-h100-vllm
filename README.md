# Qwen 2.5 Coder 32B H100 Worker For RunPod Hub

This repo packages an OpenAI-compatible `vLLM` worker around `Qwen/Qwen2.5-Coder-32B-Instruct` for H100-class RunPod Serverless deployments.

It is meant for heavier coding use cases:

- premium code assistant endpoints,
- repo copilots that need stronger code reasoning than 7B models,
- teams that want a deployable 32B coding model without building a worker from scratch.

## Positioning

This listing is the premium coding lane in the portfolio:

- H100-focused hardware targeting,
- coding-tuned Qwen defaults instead of generic chat defaults,
- long-context presets for more demanding code workflows.

The handler still forwards plain completions, chat completions, and explicit OpenAI-style routes through the local `vLLM` server inside the worker container.

## Presets

The Hub metadata ships with presets tuned for H100-class coding deployment:

- `Balanced Coder 32B`
- `Long Context Coder 32B`
- `High Throughput Coder 32B`

The default model is:

- `Qwen/Qwen2.5-Coder-32B-Instruct`

## Important note about automated tests

The Hub submission smoke test intentionally uses a much smaller coder-family model than the default deployment model. That keeps automated validation fast and cheap while still proving the worker boots, serves requests, and routes payloads correctly.

User-facing deployment defaults in `.runpod/hub.json` remain centered on `Qwen/Qwen2.5-Coder-32B-Instruct`.

## Local verification

```bash
python -m unittest discover -s tests -v
python -m json.tool .runpod/hub.json
python -m json.tool .runpod/tests.json
python -m py_compile handler.py tests/test_handler.py
```

## Publish flow

1. Cut a GitHub release.
2. Submit the repo to RunPod Hub.
3. Let RunPod build and test the release.
4. Iterate by publishing new releases rather than rewriting old tags.
