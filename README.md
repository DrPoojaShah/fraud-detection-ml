# 📝 Evaluate Student Writing using Machine Learning

## 📌 Project Overview
This project focuses on classifying discourse elements in student essays using machine learning techniques. The goal is to automatically identify different types of argumentative components such as claims, evidence, and rebuttals.

The project is based on the **Feedback Prize 2021 dataset** and demonstrates an end-to-end machine learning pipeline including data preprocessing, feature engineering, model training, and evaluation.

---

## 📊 Dataset
- Source: Kaggle – Feedback Prize 2021  
- Data: Student essays with labeled discourse segments  
- Target Variable: `discourse_type`

### Discourse Classes
- Lead  
- Position  
- Claim  
- Counterclaim  
- Rebuttal  
- Evidence  
- Concluding Statement  

---

## ⚙️ Methods Used

### 🔹 Text Features
- TF-IDF Vectorization (Unigrams + Bigrams)

### 🔹 Feature Engineering
- Relative position in essay  
- Word count and character length  
- Sentence count  
- Essay length  
- Normalized rank  
- Position-based features  

### 🔹 Models Implemented
- Logistic Regression  
- Linear SVM  
- Random Forest  
- Dummy Classifier (Baseline)

---

## 📈 Evaluation Strategy
- Used **GroupKFold Cross Validation** to avoid data leakage  
- Primary metric: **Macro F1 Score** (due to class imbalance)

---

## 📊 Results

### 🔥 Best Model: Logistic Regression
- Accuracy: ~0.83  
- Macro F1 Score: ~0.74  

### 📌 Key Insights
- Combining TF-IDF with engineered features improved performance significantly  
- Position-based features were highly informative  
- Model performed well on structured classes like *Lead* and *Concluding Statement*  
- Lower performance on *Counterclaim* and *Rebuttal* due to class imbalance  

---

## 📂 Project Structure

.
├── evaluate-student-writing.ipynb
└── README.md


---

## 🚀 How to Run
1. Download dataset from Kaggle (Feedback Prize 2021)
2. Open notebook in Jupyter Notebook or Google Colab
3. Upload dataset
4. Run all cells

---

## 🛠️ Skills Demonstrated
- Python (Pandas, NumPy, Scikit-learn)
- Machine Learning
- Natural Language Processing (NLP)
- Feature Engineering
- Model Evaluation
- Cross Validation

---

## 👩‍💻 Author
**Pooja Shah**  
MS Data Analytics Engineering, George Mason University
