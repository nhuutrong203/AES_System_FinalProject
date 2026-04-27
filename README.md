# AES System Final Project

A unified Automated Essay Scoring (AES) system for IELTS Writing assessment. This project focuses on building a data-driven pipeline to process IELTS Writing Task 1 and Task 2 essays, reconstruct criterion-level labels, complete missing criteria scores, and train prediction models for essay scoring.

## Project Overview

Automated Essay Scoring (AES) is an educational NLP task that aims to evaluate written responses using machine learning and deep learning methods. This project is designed around the IELTS Writing assessment framework, where essays are evaluated using four major criteria:

- Task Achievement / Task Response
- Coherence and Cohesion
- Lexical Resource
- Grammatical Range and Accuracy

Instead of predicting only one overall band score, this project focuses on multi-aspect scoring. This allows the system to provide a more detailed view of writing performance across different IELTS criteria.

## Main Objectives

The main objectives of this project are:

- Collect and organize multiple IELTS Writing datasets.
- Split mixed datasets into Task 1 and Task 2 subsets.
- Standardize inconsistent dataset formats into a unified schema.
- Reconstruct criterion-level scores from examiner comments.
- Validate and clean overall scores using IELTS rounding rules.
- Complete missing criterion scores using transformer-based models.
- Train score prediction models for IELTS Writing evaluation.
- Analyze model performance using quantitative metrics and visualizations.

## System Pipeline

The project follows a multi-stage pipeline:

1. **Raw Dataset Collection**  
   Six raw IELTS Writing datasets are collected from different sources. Some datasets contain both Task 1 and Task 2 essays, while others contain only one task type.

2. **Task Type Routing and Dataset Construction**  
   Mixed datasets are split by `task_type`. Task 1 data is processed separately, while Task 2 data is merged with additional independent Task 2 datasets.

3. **Schema Alignment and Exploratory Data Analysis**  
   All datasets are converted into a consistent format. Exploratory Data Analysis is used to inspect score distribution, essay length, missing values, and label consistency.

4. **Preprocessing and Label Reconstruction**  
   Text fields are cleaned and standardized. Criterion scores are extracted from examiner comments using regex-based rules, and overall scores are recalculated using IELTS rounding rules.

5. **Criteria Filling**  
   Missing criterion-level scores are completed using transformer-based models such as BERT, BERT with chunking, and XLNet.

6. **Score Prediction**  
   Completed datasets are used to train final scoring models for IELTS Writing Task 1 and Task 2.

7. **Evaluation and Result Analysis**  
   Model performance is evaluated using regression and agreement metrics. Visual analysis includes loss curves, scatter plots, error distributions, and criterion-level comparisons.

## Models and Techniques

### Criteria Filling Models

- BERT
- BERT with chunking
- XLNet

These models are used to complete missing criterion-level labels while maintaining consistency with the given overall score.

### Score Prediction Models

- RoBERTa
- MPNet
- DeBERTa
- Other baseline models where applicable

## Feature Engineering

The project includes several text-based features, including:

- Essay length
- Unique word count
- Type-token ratio
- Average word length
- Sentence count
- Average sentence length
- Sentence length variance
- Long-word ratio
- Short-word ratio
- Punctuation density

## Evaluation Metrics

The scoring models are evaluated using:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Pearson Correlation
- Quadratic Weighted Kappa (QWK)
- Within ±0.5 band accuracy

These metrics help evaluate both numerical prediction accuracy and agreement with human-like IELTS scoring behavior.

## Technologies Used

- Python
- Pandas
- NumPy
- Scikit-learn
- PyTorch
- Hugging Face Transformers
- Matplotlib
- Jupyter Notebook / Google Colab

## Expected Outputs

The expected outputs of this project include:

- Cleaned IELTS Writing Task 1 dataset
- Cleaned IELTS Writing Task 2 dataset
- Completed datasets with filled criterion scores
- Trained criteria filling models
- Trained score prediction models
- Evaluation tables and visualization figures
- Final report and project documentation

## Project Structure

```text
AES_System_FinalProject/
├── data/
│   ├── raw/
│   ├── processed/
│   └── processing/
├── notebooks/
│   ├── task1_preprocessing/
│   ├── task2_preprocessing/
├── models/
│   ├── criteria_filling/
│   └── score_prediction/
├── src/
└── README.md
