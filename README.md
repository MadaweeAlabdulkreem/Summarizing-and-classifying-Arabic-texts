# Classifying & Summarizing Arabic Text: Traditional vs. Modern NLP Approaches

## Project Overview
This project studies Arabic NLP through two core tasks:
- **Text Classification**
- **Text Summarization**

The goal is to compare **traditional methods** with **deep learning and transformer-based models** to analyze:
- Which approaches perform best on Arabic text
- Trade-offs between accuracy, speed, and computational cost

## Dataset
We use the **KALIMAT Arabic Corpus** , which contains newspaper articles: 
- Classified into **6 topics** (for classification)
- Each article includes a **human-written summary** (for summarization)

Using a single dataset enables fair comparison across all methods.

## Arabic NLP Challenges
Arabic presents several challenges:
- Rich morphology (roots and patterns)
- Undiacritized text requiring normalization
- Long and complex sentences, especially for summarization

These characteristics often limit traditional approaches and favor transformer-based models.

---

## Task 1: Text Classification

### Models Compared
- **SVM (TF-IDF)**
- **CNN**
- **AraBERT**

### Performance Summary
<img width="840" height="110" alt="image" src="https://github.com/user-attachments/assets/6a0bd7a9-50d8-4bb6-9f72-26558a3aaf3d" />


- Major classes (sports, religion) are classified well
- Minority classes (culture, international news) remain challenging

### Trade-offs
- **Best Accuracy:** AraBERT  
- **Fastest Training (CPU):** CNN (~2 min), SVM (~3 min)  
- **Longest Training:** AraBERT (10h CPU, ~45 min on T4 GPU)  
- **Most Interpretable:** SVM  

### Recommendations
- Use **SVM** when computational resources are limited
- Use **AraBERT** when accuracy and deep language understanding are required
- **Hybrid approach:** AraBERT embeddings + SVM classifier

---

## Task 2: Text Summarization

### Models Compared
- **TF-IDF (Extractive)**
- **mT5 (XL-Sum)**
- **AraT5**

### Performance Summary (BLEU / ROUGE-1)
<img width="1077" height="316" alt="image" src="https://github.com/user-attachments/assets/0646ede6-3aae-4378-a7a6-3a8bfb5c5357" />


- **TF-IDF** achieves the best automatic metrics and fastest runtime
- Transformer models generate more natural summaries but score lower

### Trade-offs
- **Best Metrics & Speed:** TF-IDF  
- **Best Linguistic Quality:** mT5 / AraT5  
- **Most Interpretable:** TF-IDF  
- **Most Computationally Expensive:** mT5  

### Recommendations
- Use **TF-IDF** for fast, structured news summarization
- Use **mT5 / AraT5** for abstractive and human-like summaries
- **Hybrid approach:** TF-IDF sentence selection → AraT5 rewriting

---

## Conclusion
- **Transformer models** (AraBERT, mT5) excel at capturing Arabic morphology and context
- **Traditional methods** (SVM, TF-IDF) remain fast, efficient, and competitive
- **Hybrid approaches** provide the best balance between performance and computational cost

Model choice should depend on:
- Task complexity
- Available computational resources
- Desired interpretability vs. language quality
