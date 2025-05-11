# Gendered Text Generation with Fine-Tuned GPT-2 Models

This project explores gendered language generation by fine-tuning GPT-2 models on male and female subsets of the Switchboard Dialog Act Corpus (SwDA). The models are evaluated for gender distinctiveness (using a classifier) and diversity (using self-BLEU).

## Dataset

- **Source:** [Switchboard Dialog Act Corpus (SwDA)](https://catalog.ldc.upenn.edu/LDC97S62)
- **Format:** Prompt-response pairs, split by speaker gender.
- **Sample:** See `genderBERT_test_clean.csv` for generated responses.

## Model Training

- **Base model:** GPT-2 (`gpt2` from Hugging Face)
- **Fine-tuning:** Separate models for male and female datasets, 3 epochs, learning rate 5e-5.


## Text Generation

- **Prompts:** 30 neutral prompts.
- **Sampling:** `top_k=50`, `top_p=0.95`, `temperature=0.8`, `max_length=60`.
- **Output:** 5 responses per prompt per model.

## Evaluation

- **Classifier:** [padmajabfrl/Gender-Classification](https://huggingface.co/padmajabfrl/Gender-Classification)
- **Metrics:** Accuracy, precision, recall, F1-score, confusion matrix, self-BLEU.

## Results

| Model        | Mean Self-BLEU | Classifier Accuracy |
|--------------|---------------|--------------------|
| Male Model   | 5.39          | 58%                |
| Female Model | 2.99          | 58%                |

## Usage

1. **Install dependencies:**
   ```bash
   pip install transformers pandas sacrebleu scikit-learn
