# Evaluating Open-Source LLMs for Named Entity Recognition in Law Enforcement Cybercrime Contexts

A Business & IT bachelor's thesis project evaluating Large Language Models for intelligent extraction of cyber Indicators of Compromise from unstructered cybercrime text.

**Author:** Tim Angevare
**Institution:** University of Twente
**Contact:** t.p.angevare@student.utwente.nl

## Overview

This research investigates the effectiveness of various LLMs and prompt engineering strategies for automatically extracting cyber-related indicators from unstructured text. The project compares traditional methods (regex, NLP, GLiNER-PII) with modern LLM approaches and explores fine-tuning techniques for improved performance.

### Entity Types Extracted

- **EMAIL** - Email addresses
- **IP** - IP addresses v4 and v6
- **BTC** - Bitcoin wallet addresses
- **IBAN** - Bank account numbers
- **PERSON** - Human names
- **LOCATION** - Geographic locations
- **PHONE** - Phone numbers
- **URL** - Web addresses/domains
- **TOX** - Tox messenger IDs

## Repository Structure

```
├── IoC_Extraction.ipynb      # Baseline comparison (Regex, NLP, GLiNER)
├── LLM_Extraction.ipynb      # Comprehensive LLM evaluation
├── Qwen_finetuning.ipynb     # LoRA fine-tuning experiments
├── Cipher/                   # The Cipher Trail annotated dataset
├── results/                  # Evaluation metrics and visualizations
```

## Notebooks

### IoC_Extraction.ipynb
Main notebook for NER extraction:
1. traditional NLP extraction
  - Regex-based pattern matching
  - spaCy NLP entity recognition
  - GLiNER-PII specialized NER model
2. LLM extraction with Qwen 2.5
3. LoRA fine-tuned extraction
4. Hybrid pipeline extraction
  - On Cipher e-mails dataset
  - On 500 annotated leaked conti ransomeware messages

### LLM_Extraction.ipynb
1.Comprehensive evaluation of 19 LLM models via Ollama, testing 5 prompt strategies:
  - Role and task
  - Role, task, and format
  - One-shot example
  - With chain of verification steps
  - Pseudo code instruction
2. Also evaluates context chunking strategies (sentence, paragraph, section level).

### Qwen_finetuning.ipynb
Fine-tuning Qwen 2.5 14B using LoRA (Low-Rank Adaptation) on the ai4privacy/pii-masking-300k dataset with 4-bit quantization.

## Datasets

### The Cipher Trail
A custom dataset of 13 annotated JSON documents containing fictional cybercrime narratives with embedded realistic IoCs. Located in `/Cipher/`.

### ContiLeaks
Real-world data from ransomware gang communications, used for validating model performance on authentic cybercrime text. 500 messages annotated

## Technical Stack

- **ML/NLP:** Transformers, PEFT (LoRA), Ollama, spaCy, GLiNER
- **Models:** Qwen 2.5, Gemma 3, Phi 4, Llama 3, Mistral, Deepseek, etc
- **Experiment Tracking:** Weights & Biases
- **Infrastructure:** CUDA GPU computing, 4-bit quantization

## Requirements

- Python 3.10+
- Ollama (for local LLM inference)
- CUDA-capable GPU (recommended for fine-tuning)

## Usage

1. Install Ollama and run with `ollama serve`

2. Run the notebooks in order:
   - `LLM_Extraction.ipynb` for LLM evaluation
   - `Qwen_finetuning.ipynb` for fine-tuning experiments
   -  `IoC_Extraction.ipynb` for total multi method extraction

## License

This project is part of academic research at the University of Twente.
