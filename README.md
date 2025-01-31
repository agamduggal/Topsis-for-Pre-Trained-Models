# 📚 Text Summarization Model Selection using TOPSIS

## 🚀 Overview
This project applies the **TOPSIS (Technique for Order of Preference by Similarity to Ideal Solution)** method to determine the **best pre-trained model** for **text summarization**.

Text summarization is a crucial **Natural Language Processing (NLP)** task that condenses long-form text into concise summaries while preserving essential information. Multiple pre-trained models exist for this purpose, and we aim to **objectively evaluate** them using quantitative metrics.

---

## 🛠 Methodology

### 1️⃣ Selected Pre-Trained Models
We compare the following **transformer-based models**:
- `facebook/bart-large-cnn`
- `google/pegasus-xsum`
- `t5-small`

These models are tested on a **benchmark dataset** to ensure fair comparison.

---

### 2️⃣ Dataset Used
The dataset chosen for this evaluation is **CNN/DailyMail**, a widely used dataset for abstractive summarization.

> 📌 **Dataset Source:** `cnn_dailymail` from Hugging Face `datasets` library

---

### 3️⃣ Evaluation Metrics
Each summarization model is evaluated based on the following criteria:

| **Metric**         | **Description**                                      | **Preference** |
|-------------------|------------------------------------------------|-------------|
| **ROUGE-1**       | Measures overlap of unigrams between generated and reference summaries | Higher is better |
| **ROUGE-2**       | Measures overlap of bigrams (two-word sequences) | Higher is better |
| **ROUGE-L**       | Measures longest common subsequence overlap | Higher is better |
| **Inference Time** | Time taken by the model to generate a summary | Lower is better |

---

### 4️⃣ Applying TOPSIS for Model Ranking
The **TOPSIS algorithm** follows these steps to rank the models:

1. **Normalize the dataset** to ensure all metrics are on the same scale.
2. **Determine the ideal best and worst solutions**:
   - **Best Solution:** Highest ROUGE scores, lowest inference time.
   - **Worst Solution:** Lowest ROUGE scores, highest inference time.
3. **Compute Euclidean distance** of each model from the ideal best and worst.
4. **Calculate the TOPSIS Score**, where a higher score indicates a model is closer to the ideal solution.
5. **Rank the models** based on their TOPSIS scores.

---

### 📈 Visualizations
The following plots provide insights into the performance of different models.

#### 1️⃣ ROUGE Score Comparison
![rouge_scores](https://github.com/user-attachments/assets/a148c486-7b52-41fa-83a6-b3261d03223c)

#### 2️⃣ Inference Time Comparison
![inference_time](https://github.com/user-attachments/assets/f5d073f5-2724-4a0a-8b0a-a9727bd248dd)

#### 3️⃣ TOPSIS Score Ranking
![topsis_scores](https://github.com/user-attachments/assets/5fd8c64a-cf0b-49cc-8a76-b4dfae24ed06)

---

### 📊 Results
The models are ranked based on their **TOPSIS** Score.

| Model                   | ROUGE-1     | ROUGE-2     | ROUGE-L     | Inference Time | TOPSIS Score | Rank |
|-------------------------|------------|------------|------------|---------------|--------------|------|
| facebook/bart-large-cnn | 0.418919719 | 0.377941511 | 0.392419849 | 1.760554695   | 0.945898567  | 1    |
| t5-small               | 0.379326317 | 0.334881592 | 0.360968365 | 1.048615646   | 0.560245128  | 2    |
| google/pegasus-xsum    | 0.274686191 | 0.161131482 | 0.207986797 | 1.849757051   | 0.366025404  | 3    |

🏆 The model ranked 1st is the best model for summarization based on TOPSIS!
