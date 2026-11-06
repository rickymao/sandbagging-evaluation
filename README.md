# sandbagging-evaluation

Sandbagging evals using [Inspect](https://inspect.aisi.org.uk/) (UK AISI). Models answer the same
multiple-choice questions under different system-prompt conditions; the accuracy gap vs. `baseline`
is the sandbagging signal.

## Setup

```bash
uv sync
touch .env   # add API keys: ANTHROPIC_API_KEY, OPENAI_API_KEY, GOOGLE_API_KEY, XAI_API_KEY
uv run jupyter lab notebooks/sandbagging_eval.ipynb
```

## Notebook layout

1. Setup
2. **Config** (`EvalConfig` — models, dataset, conditions, limits)
3. Dataset (toy / WMDP / MMLU / GPQA)
4. Tasks (one per condition)
5. Run (`eval_set`, resumable)
6. Results (accuracy + gap)
7. Per-sample flips

Supported providers include `anthropic/`, `openai/`, `google/` (Gemini) and `grok/` (xAI), e.g.
`models=["google/gemini-2.5-pro", "grok/grok-4"]`.

Smoke test with `models=["mockllm/model"], dataset="toy"` (no API cost).

## Viewing logs


In the root of this repository run:

```bash
uv run inspect view --log-dir logs/
```
