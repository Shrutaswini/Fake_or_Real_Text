# 🕵️ Fake or Real: The Impostor Hunt (Kaggle NLP Competition)

This repository contains my solution to the Kaggle competition **[Fake or Real: The Impostor Hunt](https://www.kaggle.com/competitions/fake-or-real-the-impostor-hunt)**. The challenge involves detecting which of two nearly identical texts is closer to the original, aiming to spot subtle LLM-based edits.

---

## 🚀 Goal

> Build a model that identifies whether Text 1 or Text 2 is closer to the original source or **Real**.

---

## 🧠 Models and Results

| Model Variant                         | Features Used                                           | Macro F1 Score |
|--------------------------------------|---------------------------------------------------------|----------------|
| Random Forest                        | Readability, lexical, syntactic, sentiment              | 0.53           |
| XGBoost                              | Same as above                                           | 0.63           |
| SentenceTransformer + XGBoost        | Sentence embeddings + same handcrafted features         | 0.53           |
| ✅ Final XGBoost (Best)              | Expanded feature set (see below)                        | **0.75**       |

---

## 📊 Final Feature Set

Our best model used XGBoost trained on rich, interpretable features:

### 🧾 TextStat Readability
- Flesch Reading Ease
- Gunning Fog Index
- SMOG Index
- Lexicon Count

### 🔤 Lexical Features
- Word Count, Char Count
- Average Word Length
- Type-Token Ratio (TTR)

### 🧠 Syntactic Features (via SpaCy)
- Noun, Verb, Adjective Counts
- Noun/Verb/Adjective Ratios

### 🧠 Additional NLP Features
- Polarity and Subjectivity (TextBlob)
- Stopword Count
- Punctuation Count
- Numeric Token Count
- Named Entity Repetition Ratio
- Compression Ratio
- Speculative Cue Count (e.g., “maybe,” “possibly”)

---

## 🧪 Evaluation

- Evaluation Metric: **Macro F1 Score**
- Final Validation F1 (macro avg): **0.75**
- Top 15 features (by importance) were plotted using XGBoost’s `feature_importances_`.

---


---

## 📈 Submission & Inference

- Final model was run on the test set using the same feature pipeline.
- Predictions were formatted per Kaggle guidelines and saved in `submission.csv`.

---

## 💡 Key Takeaways

- Hand-crafted, interpretable features outperformed both transformers and embeddings.
- Readability + syntactic features provided strong signals for detecting LLM-edited text.
- Feature importance analysis helped guide iterative improvements.

---

## 📎 Author

**Shrutaswini Borkakoty**  


---

## 📘 License

This project is licensed under the MIT License.


