## 🧠 Background

This project explores the use of language models to automate policy enforcement for e-commerce product listings. Specifically, it focuses on identifying safety violations related to **drawstrings on children's upper-body clothing**, which can present choking or entanglement hazards.

The goal is to simulate real-world compliance classification using GPT-4.1, based on a well-defined policy.

---

## 🎯 Task Overview

The objective is to:

- **Write prompts** to classify listings as either policy-violating (`etsy.childrens_drawstrings`) or not (`out_of_scope`).
- **Run evaluations** to calculate **precision** and **recall** using a labeled dataset.

The dataset includes:

- `reviewInput`: product listing content (text and images)
- `expectedOutcome`: the correct classification

---

## 🪜 Steps

1. Read the policy guidelines.
2. Load the dataset from `drawstrings_labeled_data.json`.
3. Build an end-to-end classification pipeline using GPT-4.1.
4. Calculate precision and recall based on model output vs. labeled data.
5. Iterate to improve classification quality.

---

## 📌 Key Notes

- Use GPT-4.1 for all LLM calls.
- Follow the classification rules carefully:
  - Focus on **upper-body garments** for **children (14 or younger)** with **drawstrings or cords**.
  - Err on the side of safety: prefer false positives over false negatives.
- Use `o3-mini` or similar smart models to speed up dev work.
- When no images are provided, text must still be sufficient to classify.

---

## 📂 Materials

- 📘 [Children's Drawstrings Guidelines.pdf](attachment:f61e9482-852e-463b-8942-3ec0d433e253:Childrens_Drawstrings_Guidelines.pdf)
- 📊 [drawstrings_labeled_data.json](attachment:19b92ed5-5d85-4e6a-b42b-67a1b15b2caf:drawstrings_labeled_data.json)

---

## 🧪 Evaluation Metrics

- **Precision** = `TP / (TP + FP)`
- **Recall** = `TP / (TP + FN)`

Where:
- **TP**: True Positives (correctly flagged violations)
- **FP**: False Positives (incorrectly flagged as violations)
- **FN**: False Negatives (missed actual violations)

---

## 🚀 Running the Classifier

To evaluate the model, run:

```bash
python classify_drawstrings.py
