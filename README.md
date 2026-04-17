# 🦥 Unsloth Compiled TRL Cache

Pre-compiled [Unsloth](https://github.com/unslothai/unsloth) TRL trainer cache files, ready to drop in and use — no recompilation needed.

---

## 📖 What Is This?

When you run [Unsloth](https://github.com/unslothai/unsloth) with [TRL](https://github.com/huggingface/trl), it dynamically compiles optimized trainer files (e.g. `UnslothSFTTrainer.py`, `UnslothGRPOTrainer.py`) into a local `unsloth_compiled_cache/` directory on first run.

This repository contains **pre-built versions of those compiled cache files**, so you can:

- ⚡ Skip slow first-run compilation
- 🔁 Share consistent trainer builds across machines / containers
- 🐛 Debug or inspect the generated trainer code
- 🚀 Speed up CI/CD pipelines and cloud training jobs

---

## 📁 Repository Structure
```
unsloth_compiled_TRL_cache/
├── README.md        # README File
├── UnslothSFTTrainer.py        # Compiled SFT Trainer
├── UnslothGRPOTrainer.py       # Compiled GRPO Trainer
├── UnslothDPOTrainer.py        # Compiled DPO Trainer
├── unsloth_compiled_module_*.py # Model-specific compiled modules
└── ...
```

---

## 🚀 Usage

### Option 1 — Clone directly as your cache folder
```bash
git clone https://github.com/alpha-ml/unsloth_compiled_TRL_cache unsloth_compiled_cache
```

Then run your training script from the same directory. Unsloth will detect and use the existing cache instead of recompiling.

### Option 2 — Copy into an existing project
```bash
cp -r unsloth_compiled_TRL_cache/* /path/to/your/project/unsloth_compiled_cache/
```

---

## ✅ Requirements

These compiled files are tied to specific package versions. Make sure your environment matches:

| Package        | Version |
|----------------|---------|
| `unsloth`      | See release notes |
| `unsloth_zoo`  | See release notes |
| `trl`          | `>=0.9.0` |
| `transformers` | `>=4.40.0` |
| `torch`        | `>=2.1.0` |

> ⚠️ **Important:** Using compiled files with mismatched package versions may cause errors or silent incorrect behavior. Always verify your environment.

---

## 🔄 Regenerating the Cache

If your package versions differ, regenerate the cache by simply running any Unsloth training script once:
```python
from unsloth import FastLanguageModel
from trl import SFTTrainer
# ... your training code
```

Unsloth will recompile and populate a fresh `unsloth_compiled_cache/` directory automatically.

---

## 🤝 Contributing

If you've generated a compiled cache for a new version combination, feel free to open a PR! Please include the exact package versions in your PR description.

---

## 📄 License

This repository contains auto-generated code derived from [Unsloth](https://github.com/unslothai/unsloth) (Apache 2.0) and [TRL](https://github.com/huggingface/trl) (Apache 2.0). See those projects for their respective licenses.

---

## 🔗 Related Projects

- [unslothai/unsloth](https://github.com/unslothai/unsloth) — The source of the compiled code
- [huggingface/trl](https://github.com/huggingface/trl) — Transformer Reinforcement Learning library
- [huggingface/transformers](https://github.com/huggingface/transformers)