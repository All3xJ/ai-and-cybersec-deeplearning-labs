# 🤖 AI & Cybersecurity – Deep Learning Labs
**Politecnico di Torino** | Course: AI and Cybersecurity

> A collection of four hands-on labs exploring deep learning, NLP, and anomaly detection applied to cybersecurity scenarios.

---

## 📁 Repository Structure

```
.
├── Lab_1/   # Feed Forward Neural Network (FFNN)
├── Lab_2/   # Model Engineering – FFNN, RNN, GNN
├── Lab_3/   # Natural Language Processing (NLP)
└── Lab_4/   # Supervised vs Unsupervised Anomaly Detection
```

---

## 🔬 Lab Overview

### Lab 1 – Introduction to Deep Learning with FFNN
**Dataset:** Network traffic (Benign, PortScan, DoS Hulk, Brute Force)

A step-by-step introduction to building Feed Forward Neural Networks for network intrusion detection.

**Key topics:**
- Data preprocessing: deduplication, standardization, train/val/test split
- Shallow neural network training with early stopping
- Impact of activation functions (Linear vs ReLU)
- Feature analysis and class imbalance (weighted loss)
- Deep neural network design: architecture comparison, batch size, optimizer tuning (SGD, AdamW)
- Overfitting and regularization: Dropout, Batch Normalization, weight decay

**Best result:** ~95.6% accuracy using a 5-layer DNN with ReLU and AdamW optimizer.

---

### Lab 2 – Model Engineering: FFNN, RNN & GNN
**Dataset:** Malware API call sequences (binary classification: Benign vs Malware)

A comparative study of three neural network families for malware detection from sequences of system API calls.

**Key topics:**
- Bag-of-Words preprocessing with `CountVectorizer` + Logistic Regression baseline
- FFNN with sequential IDs vs learnable embeddings
- Recurrent Neural Networks: Monodirectional RNN, Bidirectional RNN, LSTM
- Graph Neural Networks: GCN, GraphSAGE, GAT
- Handling variable-length sequences (padding, packing)
- Class imbalance mitigation with threshold tuning

**Best result:** GraphSAGE (Benign F1 = 50.00 on test), LSTM competitive at 41.85. GNNs outperform RNNs by leveraging graph structure.

---

### Lab 3 – NLP: Malicious SSH Log Analysis with Pre-trained Language Models
**Dataset:** SSH honeypot bash session logs labeled with MITRE ATT&CK tactics

Fine-tuning and comparing pre-trained language models for Named Entity Recognition (NER) on malicious shell commands.

**Key topics:**
- Dataset exploration: 7 MITRE tactics (Discovery, Execution, Persistence, etc.)
- Tokenization comparison: BERT vs Unixcoder
- End-to-end fine-tuning: BERT, Naked BERT, Unixcoder, Secure-Shell-BERT
- Lightweight fine-tuning: frozen layers vs full fine-tuning
- Inference analysis: command-level tactic prediction and fingerprint temporal analysis

**Best result:** Secure-Shell-BERT (E2E) — 86.09% token accuracy, 67.94% F1, 85% session fidelity.

---

### Lab 4 – Supervised vs Unsupervised Anomaly Detection
**Dataset:** KDD-style network intrusion dataset (Normal, DoS, Probe, R2L)

A broad comparison of shallow and deep anomaly detection methods, from One-Class SVMs to Autoencoders and clustering.

**Key topics:**
- Domain-expert feature analysis via statistical heatmaps
- One-Class SVM: normal-only training, nu/gamma tuning, robustness testing
- Deep Autoencoder with mixed loss (MSE + Cross-Entropy) and threshold selection
- Representation learning: AE bottleneck + OC-SVM, PCA + OC-SVM
- Unsupervised clustering: K-Means + t-SNE visualization, DBSCAN anomaly analysis

**Best result:** OC-SVM on raw features (78% accuracy, macro F1 = 0.75). Surprisingly, shallow methods matched or outperformed deep ones on this dataset.

---

## 🛠️ Tech Stack

| Library | Usage |
|---|---|
| `PyTorch` | FFNN, RNN, LSTM training |
| `PyTorch Geometric` | GCN, GraphSAGE, GAT |
| `scikit-learn` | OC-SVM, PCA, preprocessing, metrics |
| `HuggingFace Transformers` | BERT, Unixcoder, Secure-Shell-BERT fine-tuning |
| `matplotlib` / `seaborn` | Visualization |
| `pandas` / `numpy` | Data manipulation |

---

## 📊 Results Summary

| Lab | Task | Best Model | Test Accuracy |
|---|---|---|---|
| Lab 1 | Network Intrusion (4-class) | 5-layer DNN + ReLU + AdamW | ~95.6% |
| Lab 2 | Malware Detection (binary) | GraphSAGE | 96.57% |
| Lab 3 | SSH Tactic NER (7-class) | Secure-Shell-BERT (E2E) | 86.09% token acc. |
| Lab 4 | Anomaly Detection (binary) | OC-SVM (normal data only) | 78% |

---

## 🚀 Getting Started

Each lab is self-contained. Navigate to the respective folder and open the Jupyter notebook:

```bash
cd Lab_1
jupyter notebook Lab_1.ipynb
```

> **Note:** Some labs require a GPU for reasonable training times (especially Lab 2 – LSTM and GNN, and Lab 3 – transformer fine-tuning).

---

## 📄 Reports

Each lab folder contains a PDF report with detailed answers to all lab questions, analysis of results, and discussion of design choices.
