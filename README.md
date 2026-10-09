# bert-lora-placement-selection
A comparative study of BERT fine-tuning methods with automatic LoRA placement selection for news topic classification.
BERT Fine-Tuning with Automatic LoRA Placement Selection
## Overview
This project compares four BERT fine-tuning methods for news topic classification: Frozen BERT, Full Fine-Tuning, Standard LoRA, and Automatically Selected LoRA.
The main contribution is an Automatic LoRA Placement Selection Module, which evaluates eight LoRA configurations and selects the best one based on validation Macro-F1.
## Dataset and Methods
•	Dataset: AG News (4 news categories)
•	Base model: bert-base-uncased
•	Placement search: 8 candidates using QV/QKV projections and different encoder layer groups
•	Final comparison: 4 methods × 5 random seeds
•	Evaluation: Accuracy and Macro-F1
## Results
| Method | Test Macro-F1 (Mean ± SD) | Trainable Parameters |
|---|---|---:|
| Frozen BERT | 0.7828 ± 0.0008 | 3,076 |
| Full Fine-Tuning | 0.9231 ± 0.0019 | 109,485,316 |
| Standard LoRA | 0.9218 ± 0.0024 | 297,988 |
| Selected LoRA | 0.9221 ± 0.0008 | 445,444 |

The automatic search selected QKV_all. Selected LoRA achieved performance close to Full Fine-Tuning while updating approximately 0.41% of the model parameters. Its improvement over Standard LoRA was small.
## How to Run
Install the dependencies:
```bash
pip install -r requirements.txt
```
Open the Jupyter Notebook and run the cells in order. The full experiment includes eight placement-search runs and twenty final comparison runs, which may require substantial GPU time.
Project
AIML339 — Machine Learning Project.
