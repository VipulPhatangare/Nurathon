
# Nerathon

This repository contains a solution for the **Nerathon NLP Challenge**, an exciting Natural Language Processing competition designed for AI/ML students to tackle real-world problems such as Named Entity Recognition (NER), text classification, and sentiment analysis on noisy financial service data.

---

## Project Overview

In this project, we build an NLP model using:
- **Logistic Regression** for classification
- **TF-IDF Vectorization** for text
- **Ordinal Encoding** for categorical features
- **Feature Engineering** to process dates and metadata

The objective is to classify customer complaints based on their textual descriptions and metadata into correct **Product Categories**.

---

## Dataset Description

The dataset contains customer complaints related to financial services with the following columns:

- `Complaint_Description`: Raw text describing the complaint
- `Company`: Name of the company
- `Region`: Customer's region (may contain null values)
- `Location_Code`: Geographical code (may contain null values)
- `Time_Logged`: Date the complaint was filed (in mixed formats: `DD-MM-YYYY` and `MM/DD/YYYY`)
- `Issue_Category`: Issue classification
- `Product_Category`: Target label (only in train data)

### Files:
- `train.csv`: Labeled training data
- `test.csv`: Unlabeled test data
- `submission.csv`: Output file containing predicted categories for test data

---


## Steps Performed

1. **Data Cleaning**
   - Handled null values by replacing them with `'Unknown'`
   - Standardized the date format and extracted `Day`, `Month`, and `Year` from `Time_Logged`

2. **Feature Engineering**
   - Used all columns for model input, including both categorical and numerical
   - Applied `OrdinalEncoder` to handle unseen categories gracefully in the test set

3. **Text Vectorization**
   - Converted `Complaint_Description` using `TfidfVectorizer` with a max of 5000 features

4. **Modeling**
   - Combined text and metadata features
   - Trained a `LogisticRegression` model
   - Evaluated on validation split using accuracy and classification report

5. **Prediction**
   - Predicted `Product_Category` on the test set
   - Generated submission file

---

## Evaluation Metrics

The model is evaluated based on:
- **Accuracy** – Percentage of correctly classified complaints
- **F1-score** – Harmonic mean of precision and recall

---
