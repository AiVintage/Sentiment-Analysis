# 📝 Sentiment Analysis on Amazon Reviews

## 📌 Project Overview
This project applies **Natural Language Processing (NLP)** techniques to analyze customer reviews from Amazon.  
The analysis covers two main tasks:
1. **Sentiment Analysis** – classifying reviews as Positive, Negative, or Neutral.  
2. **Similarity Analysis** – measuring semantic similarity between reviews using vector embeddings.  

---

## 📂 Dataset
- **Source:** Datafiniti Amazon Consumer Reviews of Amazon Products (May 2019)  
- **Size:** 24 columns (product info, brand, categories, customer reviews, ratings, etc.)  
- **Focus:** Only the `reviews.text` column was used for analysis (after dropping missing values).  

**Example Reviews:**
- “I order 3 of them and one of the item is bad quality.”  
- “Bulk is always the less expensive way to go for products.”  

---

## ⚙️ Approach
### 1. Sentiment Analysis
- Implemented using **spaCy** (`en_core_web_md`) + **spacytextblob**.  
- Rules:
  - Polarity > 0 → Positive  
  - Polarity < 0 → Negative  
  - Polarity = 0 → Neutral  

### 2. Similarity Analysis
- Used **word embeddings** from `en_core_web_md` to compute **cosine similarity** between reviews.  
- Helps identify reviews that discuss similar features (e.g., *quality* vs. *price*).  

---

## 📊 Results
### Sentiment Analysis (sample of 5 reviews):
- “Awesome tablet. Very fast, user friendly” → **Positive** ✅  
- “They don’t last. Duracell lasts 3x longer. Not worth the savings.” → **Positive** (⚠ misclassified, should be Negative)  
- “Thx.” → **Neutral**  
- “Kids love it, great quality, warranty included.” → **Positive** ✅  
- “Very kid friendly, safe content.” → **Positive** ✅  

**Observation:**  
- Most reviews skew **Positive**.  
- Model struggled with nuanced Negative reviews (limitation of simple polarity thresholding).  

### Similarity Analysis:
- Compared:  
  1. “I order 3 of them and one of the item is bad quality.”  
  2. “Bulk is always the less expensive way to go for products.”  
- **Similarity Score:** 0.95 → semantically very close.  

---

## 🔎 Key Challenges
- **Misclassifications:** Negative reviews misclassified as Positive.  
- **Model Limitations:** Small vs. medium spaCy models differ in embedding quality.  
- **Performance:** Large dataset processing is slow.  

---

## ✅ Conclusion
- Sentiment analysis revealed a **positive bias** in Amazon reviews.  
- Review similarity analysis successfully grouped related feedback.  

---

## 🚀 Future Improvements
- Use **transformer-based models** (BERT, RoBERTa) for better sentiment accuracy.  
- Balance dataset by including more Negative/Neutral examples.  
- Apply **clustering** to group reviews by product features (e.g., *price*, *quality*, *durability*).  
- Deploy as a **Streamlit/Flask web app** for interactive use.  

---

## 🛠️ Tech Stack
- **Language:** Python  
- **Libraries:** pandas, spaCy, spacytextblob, NumPy, scikit-learn, matplotlib  
- **Models:** `en_core_web_md` (spaCy embeddings)  

---

## 👨‍💻 Author
**AiVintage (Veli)**  
Data Science Graduate | Skilled in Python, Machine Learning, NLP, Data Analysis & Visualization, SQL  
[GitHub](https://github.com/AiVintage) | [LinkedIn](#)  

---
