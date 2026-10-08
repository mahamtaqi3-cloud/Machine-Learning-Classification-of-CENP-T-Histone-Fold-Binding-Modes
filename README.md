# Machine Learning Classification of CENP-T Histone Fold Binding Modes

This project presents an end-to-end computational pipeline designed to classify adaptive evolutionary binding modes in centromeric protein T (CENP-T). Focusing on the C-terminal Histone Fold Domain (HFD), the model distinguishes between **Mouse-like weaker binding innovations** and **Rat/Ancestral stronger binding modes**.

---

## 📌 Project Overview

* **Domain:** Evolutionary centromere biology and structural kinetochore dynamics.
* **Objective:** Predict CENP-T binding phenotypes directly from primary sequence composition retrieved from NCBI.
* **Target Classes:**
  * **Class 1 (Weaker Binding):** Mouse innovation (*Mus* genus).
  * **Class 0 (Stronger Binding):** Rat/Ancestral state (*Rattus*, *Apodemus*, *Praomys*, etc.).

---

## ⚙️ Computational Pipeline Workflow

1. **Environment Setup & Dependencies:** Integrates `Biopython` for sequence retrieval, `pandas` for data manipulation, and `scikit-learn` for feature modeling.
2. **NCBI Entrez Sequence Retrieval:** Automatically queries and fetches rodent CENP-T sequences, slices the C-terminal ~100 amino acid Histone Fold Domain (HFD), and deduplicates exact sequence strings.
3. **Feature Extraction & Random Forest Training:** Calculates 20D amino acid composition (AAC) frequency vectors for each sequence and trains a class-weighted Random Forest classifier.
4. **Full-Length Sequence Inference:** Tests trained models on full-length domain sequences to evaluate prediction accuracy and class confidence scores.

---

## 📊 Results Summary

* **Dataset:** 300 initial NCBI records processed into 8 unique deduplicated HFD sequences (6 Mouse, 2 Rat).
* **Key Predictive Features:** Serine (S), Arginine (R), and Alanine (A) frequency distributions drive class separation.
* **Inference Accuracy:** Evaluated full-length HFD test domains accurately classified Mouse weaker binding (**93% confidence**) and Rat stronger binding (**68% confidence**).

---

## 🚀 Future Directions

* Transition from global amino acid composition percentages to position-specific sequence representations.
* Incorporate pre-trained protein language model embeddings (e.g., **ESM-2**) to capture critical local substitutions like the 4NS motif.
