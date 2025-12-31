# LLM-Based Machine Learning Experiment Design Critic

## 1. Overview
This project implements an LLM-driven system that evaluates the **design and methodology of machine learning experiments**, independent of model performance or numerical results.

The system focuses on identifying conceptual and methodological flaws in an ML experiment before execution, helping ensure scientific validity, reproducibility, and trustworthy evaluation.

---

## 2. Problem Statement
Many machine learning projects fail due to **incorrect experimental design**, even when models achieve high accuracy. Common issues include:
- Data leakage caused by improper splitting strategies
- Misaligned evaluation metrics
- Missing or weak baseline comparisons
- Invalid hyperparameter tuning procedures
- Unsupported claims of generalization

These issues are difficult to detect using traditional automated tools and require **reasoning over methodology**, not computation.

---

## 3. Proposed Solution
The proposed system analyzes **structured metadata describing an ML experiment** and applies LLM-based reasoning to critique the experiment design.

The system evaluates:
- Dataset usage assumptions
- Validation and splitting strategies
- Metric suitability
- Experimental rigor and reproducibility
- Logical consistency of methodological choices

No model training or result evaluation is performed.

---

## 4. System Architecture

Experiment Description Input  
→ Schema Validation  
→ Risk Signal Extraction  
→ Prompt Construction  
→ LLM-Based Methodology Critique  
→ Structured Review Output  

---

## 5. Core Modules

### 5.1 Experiment Schema Parser
- Validates completeness of experiment metadata
- Normalizes dataset, model, and evaluation fields
- Flags missing or ambiguous information

### 5.2 Risk Signal Extractor
- Deterministically detects known methodological risk patterns
- Examples:
  - Temporal data with random splitting
  - High class imbalance with accuracy as sole metric
  - Preprocessing applied before train–test split
- Produces structured risk indicators for LLM conditioning

### 5.3 Prompt Builder
- Constructs a constrained, rule-augmented prompt
- Injects experiment summary and detected risks
- Restricts reasoning strictly to experimental design

### 5.4 LLM Critique Engine
- Performs contextual reasoning over experiment metadata
- Identifies methodological flaws and risks
- Produces structured, evidence-based critique

---

## 6. Reasoning Dimensions
The experiment is evaluated across fixed dimensions:
- Data leakage and split validity
- Metric–problem alignment
- Baseline adequacy
- Validation and tuning correctness
- Generalization validity
- Reproducibility and experimental rigor

---

## 7. Input Specification
The system accepts a structured experiment description containing:
- Dataset characteristics (type, size, imbalance, temporal nature)
- Train/validation/test split strategy
- Model and baseline selection
- Hyperparameter tuning protocol
- Evaluation metrics and testing methodology

---

## 8. Output Specification
The system produces a structured review including:
- Methodology risk level (Low / Medium / High)
- Identified critical and moderate issues
- Design-level recommendations
- Confidence level based on input completeness

---

## 9. Hallucination Control
- LLM reasoning constrained strictly to provided metadata
- Deterministic risk extraction limits free-form inference
- Missing information explicitly acknowledged
- Output format enforced using a fixed schema

---

## 10. Tech Stack
- Language: Python
- LLM: OpenAI / LLaMA / Mistral
- Backend API: FastAPI
- Prompt Templates: Version-controlled
- Frontend (optional): Streamlit

---

## 11. Evaluation Strategy
- Comparison with expert-reviewed ML experiment critiques
- Testing on known flawed and well-designed experiment setups
- Consistency checks across repeated LLM runs
- Alignment with established ML best practices

---

## 12. Limitations
- Dependent on completeness of experiment metadata
- No inspection of raw datasets or model outputs
- Cannot verify numerical performance
- Reasoning quality bounded by LLM capabilities

---

## 13. Expected Outcome
A deployable system that audits **methodological integrity** of machine learning experiments before execution, reducing silent failures and improving reproducibility and scientific rigor.
