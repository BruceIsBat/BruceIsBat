# Ibrahim Keji Awotedu

**Applied AI/ML Engineer (Early Career) with an Industrial & Production Engineering Background**
I work on machine learning for manufacturing operations (predictive maintenance, scheduling, dynamic control), resilient backend and ML serving systems, and speech/NLP pipelines for low-resource African languages. I operate by one rule: **no receipts, no claim.**

Ogun State, Nigeria · [awoteduibrahim@gmail.com](mailto:awoteduibrahim@gmail.com) · [LinkedIn](https://www.linkedin.com/in/ibrahim-awotedu) · [GitHub](https://github.com/BruceIsBat)

**Open to:** Junior AI/ML engineering roles, internships, and funded Master's/PhD programs in Machine Learning, Cyber-Physical Systems, and Industrial AI (2027 intake).

---

## Background

- **B.Eng. Industrial and Production Engineering**, Federal University of Technology, Akure (FUTA), 2024.  
  *CGPA: 4.33 / 5.00 (Second Class Upper Division, top 10% of department). Recipient of the Dean's Honour Award across 3 consecutive academic sessions.*
- **Back-End AI Engineering Intern**, FlyRank (2026 – Present): Building backend services, asynchronous worker task queues, and persistent data layers for AI-driven products.
- **AI Intern (Predictive Maintenance Focus)**, SkillBoost Africa (Oct 2024 – Aug 2025): Developed automated log-parsing scripts and predictive anomaly detection models flagging equipment failure risk 48 hours in advance (~12% reduction in unplanned downtime).
- **Production Systems Manager**, Razlab Sand & Blocks (2020 – 2022): Built discrete-event simulation models to resolve production bottlenecks and reorganized operational dispatching, improving daily throughput by 20%.
- **Software Engineering Trainee**, ALX Africa (2023 – 2024): Intensive low-level systems programming in C, dynamic memory allocation, and Linux/Bash infrastructure.
- **Fellowships:** Google DeepMind AI Research Foundations Scholar (2026), AWS AI & ML Scholar (2026).
- **Certifications:** CS50's Introduction to AI with Python (HarvardX), AWS AI Practitioner Challenge (Udacity), AI Engineering Certification (TechCrush), AI Fluency (Anthropic).

---

## Current Research: #90DaysOfAI

A public, preregistered 90-day empirical study (Oct 2 – Dec 31, 2026) investigating which machine learning methods yield verifiable gains in industrial and production engineering environments. Repository: [90-days-ai-industrial-engineering](https://github.com/BruceIsBat/90-days-ai-industrial-engineering)

| Research Question | Experimental Setup | Evaluation Window |
|---|---|---|
| Do deep sequence models (LSTM, 1D-CNN, Transformer) outperform a tuned gradient-boosted baseline for remaining-useful-life (RUL) prediction? | NASA C-MAPSS FD001 (FD002 secondary), engine-grouped cross-validation, piecewise RUL target capped at 125 cycles, fixed 50-trial tuning budget, paired bootstrap CIs over distinct engines. | Oct 18 – Nov 11 |
| Does a physics-informed loss (PINN prior) improve generalization when domain physical equations are partially misspecified? | Controlled degradation dataset with systematic misspecification of physical constants against unconstrained neural baselines. | Nov 12 – Dec 6 |
| Under what operational conditions does Reinforcement Learning dispatching beat classical Operations Research heuristics? | Gymnasium job-shop environment comparing PPO against classical dispatching rules (SPT, MWKR, FIFO) and exact CP-SAT solvers across Taillard benchmark instances. | Dec 7 – Dec 23 |

Hypotheses and evaluation protocols are preregistered before running experiments. Every public update carries an empirical receipt: a plot, benchmark table, commit hash, or documented failure mode.

**Status:** In progress. Deterministic seed harnesses, experiment run-logging, and engine-grouped validation splits with unit tests are in place.

---

## Selected Systems & Research Projects

### [Agricultural Extension Retrieval (Kaggle: Smart Retrieval for Farmers)](https://github.com/BruceIsBat/agri-extension-rag)
*Two-stage hybrid retrieval and cross-encoder re-ranking architecture for domain-specific agronomic advisory.*
- **Pipeline:** Established a sparse BM25 baseline (score 0.48), then engineered a hybrid retrieval system blending dense embeddings (`BAAI/bge-large-en-v1.5`) with BM25 (0.6 / 0.4 min-max scaled). Re-ranked candidates using a `BAAI/bge-reranker-large` cross-encoder to achieve an absolute score improvement of +0.3.
- **Ablations:** Implemented secondary LLM verification using Qwen2.5-7B-Instruct as a binary relevance filter, logging runtime latency trade-offs against candidate recall depth.
- **Stack:** Python, PyTorch, Sentence-Transformers, Rank-BM25, Hugging Face Transformers.

### [Sentinel-Ledger](https://github.com/BruceIsBat/sentinel-ledger)
*Empirical concurrency and contention study analyzing transaction isolation invariants under high contention.*
- **Architecture:** Process-local Token Bucket rate limiter positioned in front of ACID transactions executed on MySQL InnoDB using pessimistic row-level locking (`SELECT ... FOR UPDATE`, `DECIMAL` precision, and balance `CHECK` constraints), served via Flask.
- **Contention Findings:** Under 50 concurrent workers hitting a single hot account pair, transfers queued on the database row lock with median latencies between 1.7–2.2 s. Under restrictive throttling, the limiter shed 80% of excess traffic in milliseconds while accepted transfers completed in ~1.1 s median. Zero lost updates, negative balances, or deadlocks were detected.
- **Documented Trade-offs:** The project explicitly documents real-world constraints: lack of distributed state sync, process-local rate tracking, and absence of idempotency keys.
- **Stack:** Python, Flask, MySQL (InnoDB), Threading Load Tests, Pytest.

### [Yoruba-Ubuntu Storyteller](https://github.com/BruceIsBat/yoruba-ubuntu-storyteller)
*End-to-end pipeline for low-resource Yoruba speech recognition, narrative generation, and speech synthesis.*
- **Pipeline:** Tone-aware automatic speech recognition fine-tuned on the WAXAL corpus (MMS / Wav2Vec2-XLSR), retrieval-augmented story generation using a QLoRA-adapted LLaMA-3-8B model, and neural speech synthesis via VITS.
- **Engineering:** Diacritic normalization preprocessing, DVC data versioning, modular FastAPI microservice endpoints, and Docker containerization.
- **Stack:** PyTorch, Hugging Face (Transformers, PEFT/QLoRA), FastAPI, DVC, Docker.

### [Fairness–Accuracy Trade-Offs in Employee Loan Approval](https://github.com/BruceIsBat/Loan_Approval_-Status)
*Systems-level model evaluation auditing algorithmic fairness constraints in financial loan allocation.*
- **System Role:** Built the model serving and evaluation infrastructure (team of 6). Benchmarked five model architectures (Logistic Regression, Random Forest, XGBoost, Neural Network, SHAP-constrained Random Forest) across demographic parity, equalized odds, and calibration error.
- **Deployment:** Mitigated class imbalance using SMOTE, extracted feature-level disparity drivers via SHAP, and deployed real-time explainable inference via FastAPI with an interactive Gradio diagnostic interface.
- **Stack:** Scikit-learn, XGBoost, Imbalanced-learn, SHAP, FastAPI, Pydantic, Gradio, Pytest.

---

## Other Technical Work

- **[XRL-Ops](https://github.com/BruceIsBat/xrl-ops):** Explainable reinforcement learning framework for industrial continuous control environments, wrapping policy state-action trajectories with attribution logging and MLflow tracking.
- **Pre-Trained CNN Architecture Diagnostic:** Evaluated transfer learning representations across ResNet, AlexNet, and VGG on 40 labelled pet images (100% species detection; VGG achieved 93.3% breed accuracy vs. ResNet 90.0% and AlexNet 80.0%). Documented edge failure cases, such as an AlexNet failure labeling a rotated canine image as "custard apple".
- **Pandas to Polars Lazy Streaming:** Refactored data pipeline execution from Pandas eager loading to Polars lazy execution, reducing processing latency on a 3 GB telemetry file from 12.4 s to 0.08 s via memory mapping and query optimization.
- **Mechanical Cassava Mesh-Sieving Machine (B.Eng. Capstone):** Designed and fabricated an agro-processing prototype; applied Design of Experiments (DOE) for mesh throughput optimization and Python-based Fast Fourier Transform (FFT) vibration signal analysis to map mechanical wear signatures.
- **[100 Days of ML Engineering](https://github.com/BruceIsBat/100-days-of-ml-engineering):** Daily technical practice migrating experimental code toward structured, reproducible ML pipelines.

---

## Skills

- **Used in Projects:** Python, PyTorch, Scikit-learn, XGBoost, SHAP, Hugging Face (Transformers, PEFT/QLoRA), Sentence-Transformers, Flask, FastAPI, Pydantic, MySQL, Docker, DVC, Pytest, NumPy, Pandas, Polars.
- **Working Knowledge:** TensorFlow, MLflow, MATLAB, AWS (EC2, SageMaker), C, Linux/Bash.
- **Learning & Expanding:** Kubernetes, CI/CD GitHub Actions, Production Model Drift Monitoring.

---

## Research Focus Areas

- **Smart Manufacturing & Industry 4.0:** Predictive maintenance, vibration signal analysis, and cyber-physical systems.
- **Data-Driven Operations Research & Control:** Explainable reinforcement learning, combinatorial scheduling, and dynamic dispatching.
- **Reliable ML & Concurrency Engineering:** Robust serving layers, contention mitigation, and efficient model fine-tuning.
- **Low-Resource Speech & Language Technologies:** Diacritic-aware ASR and localized generative language models.

---

## Contact & Profiles

- **Email:** [awoteduibrahim@gmail.com](mailto:awoteduibrahim@gmail.com)
- **LinkedIn:** [linkedin.com/in/ibrahim-awotedu](https://www.linkedin.com/in/ibrahim-awotedu)
- **GitHub:** [@BruceIsBat](https://github.com/BruceIsBat)