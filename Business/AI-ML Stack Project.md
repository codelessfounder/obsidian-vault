---

---

AI/ML stack:

- Python
- C & C++


Future proofing myself because I’m bullish on AI:



### *One-sentence summary*

*Double down on ****Python for modelling and experimentation****, learn ****C++/CUDA**** for high-performance kernels and production inference, and invest time in ****systems, compilers, and MLOps**** (profiling, deployment, distributed training) so you can own the full stack from prototype to production.*

---

## *Priority roadmap (practical, ordered)*

1. ***Core foundations (mandatory)***
    - *Linear algebra, probability/statistics, optimisation (gradients, SGD, Adam).*
    - *Python fluency — idiomatic code, virtualenv/venv/poetry, typing (mypy).*
2. ***Python ML stack (fast wins)***
    - *NumPy, pandas, and data pipelines.*
    - *One major DL framework deeply: ****PyTorch**** (autograd, modules, custom *`*Dataset*`*/*`*DataLoader*`*, training loop). Learn a second (TensorFlow/JAX) at a surface level.*
    - *HuggingFace Transformers and tokenisation if you care about LLMs.*
3. ***Practical model engineering & infra***
    - *Experimentation: Jupyter/Colab, logging/visualisation (TensorBoard/Weights & Biases).*
    - *Versioning: git, DVC/MLflow for datasets/experiments.*
    - *Containerisation: Docker, simple Kubernetes basics.*
4. ***Performance & production (systems + C/C++)***
    - *Modern C++ (C++17/20 basics) and idiomatic memory management.*
    - ***CUDA**** fundamentals: kernels, memory transfers, streams, basic optimisation patterns.*
    - *How Python ↔ C++ bridging works: CPython C API, ****PyBind11****, and writing a custom C++ op for PyTorch.*
5. ***Advanced system tooling***
    - *Profiling and optimisation: *`*nvprof*`*/nsight, PyTorch profiler, CPU profilers.*
    - *Model compilers and runtimes: ONNX, TorchScript/TorchServe, TensorRT, XLA, and an understanding of what MLIR is trying to solve.*
    - *Distributed training: PyTorch DDP, Horovod, basics of data vs model parallelism.*
6. ***Edge, inference & specialised hardware***
    - *Quantisation, pruning, int8 optimisations, and how to convert a model to run on CPU/mobile/edge.*
    - *Awareness of TPUs and other accelerators (how they change compilation/deployment).*
7. ***Long-term / future-proofing research areas***
    - *Learn compiler concepts (IRs, graph lowering) and keep an eye on ****Mojo/Triton/MLIR**** — these are where languages meet high performance.*
    - *Get comfortable reading and implementing ideas from research papers.*

---

## *Concrete learning projects (do these in order)*

8. ***End-to-end notebook****: clean dataset → train small CNN/Transformer in PyTorch → evaluate → push to a simple Flask/FastAPI endpoint.*
9. ***Custom op****: implement a tiny tensor op in C++ (or CUDA) and bind it into Python with PyBind11; call it from PyTorch and benchmark.*
10. ***Profile & optimise****: take a training loop, profile GPU/CPU usage, then optimise memory transfers and batch sizes.*
11. ***Export & serve****: convert that model to ONNX/TorchScript, run inference with ONNX Runtime / TorchServe, and compare latency.*
12. ***Distributed experiment****: run a multi-GPU training job with PyTorch DDP; understand bottlenecks and batch scaling.*
13. ***Tiny tensor library****: (advanced) implement a minimal NumPy-like tensor with autodiff in Python (or C++) to internalise how autograd works.*
14. ***Edge deploy****: quantise and deploy a model to a phone or low-power device (TFLite or ONNX on edge).*

---

## *Tech stack you should be comfy with*

- ***Language / frameworks:**** Python (primary), PyTorch (primary), JAX/TensorFlow (familiarity).*
- ***Systems / performance:**** C++17/20, CUDA (or HIP for AMD), PyBind11, Triton (optional but useful).*
- ***Deployment / infra:**** Docker, Kubernetes basics, FastAPI, TorchServe/ONNX Runtime, TensorRT.*
- ***Tools:**** git, CI/CD, Weights & Biases or TensorBoard, profiling (nsight, perf), DVC/MLflow.*
- ***Cloud:**** at least one of AWS/GCP/Azure for GPUs (know how to spin up GPU instances and S3-like storage).*
- ***MLOps:**** experiment tracking, reproducibility, dataset management, tests and model validation.*

---

## *Practical learning schedule (rough, flexible)*

- ***0–3 months:**** Python + NumPy + PyTorch basics + small projects (notebook + simple model).*
- ***3–6 months:**** Deepen PyTorch, HuggingFace, basic Docker, start one C++/PyBind11 tutorial.*
- ***6–12 months:**** CUDA basics + write a custom C++/CUDA op; export and serve models; profiling.*
- ***12+ months:**** Distributed training, compilers/IRs (ONNX/MLIR/XLA), production optimisation, hardware-specific runtimes.*

*(Do not over-optimise the timeline — ship small projects and iterate.)*

---

## *Mindset & habits that actually future-proof you*

- ***Read code, not just papers**** — inspect PyTorch, ONNX, or Triton source to see real patterns.*
- ***Contribute to open-source**** — even small fixes teach binding, build systems, and CI.*
- ***Benchmark obsessively**** — learn to measure before you optimise.*
- ***Automate reproducibility**** — scripts that rebuild the environment, seed RNGs, and fetch data.*
- ***Network in communities**** — PyTorch Forums, HuggingFace, CUDA developer forums, relevant GitHub projects.*
- ***Stay curious about compilers**** — the next big improvements come from IRs, not prettier Python syntax.*

---

## *What to avoid early on*

- *Premature optimisation in C++ before you understand hotspots.*
- *Reinventing generic infra — use proven tools (ONNX, TorchServe) instead of bespoke servers.*
- *Chasing every new language hype without an ecosystem (unless you’re experimenting).*

---

## *Quick checklist you can use right away*

- *Can you train a model in PyTorch and save it? ✅*
- *Can you profile a training run and see GPU utilisation? ✅*
- *Can you write a C++ extension for Python with PyBind11? ✅*
- *Can you export to ONNX/TorchScript and run inference? ✅*
- *Can you scale a job to multiple GPUs and measure speedup? ✅*

*If you can answer yes to most of those, you’re already in the top tier of practical ML engineers.*

---
