# 🎬 Phase-4-Project: Movie Recommendation System

**Authors:** Blex Olonde,Dennis Muriungi, Jasho Kiplangat, Shem Omondi and Valary Kones  
**Date:** February 3, 2026  

A production-style movie recommendation engine built using collaborative filtering algorithms to predict user preferences and generate personalized movie recommendations.

The system compares multiple approaches (KNN, Matrix Factorization, NMF) and selects the best performing model based on prediction accuracy.

---

## 📌 Project Overview

Streaming platforms face a major challenge: users cannot easily discover relevant content within massive catalogs.

This leads to:

- Decision fatigue
- Low engagement
- Poor retention
- Underutilized content

This project solves that problem by building a recommender system that predicts what a user will like and returns **Top-5 personalized movie recommendations**.

---

## 🎯 Business Objectives

### Primary Goal
Predict movie ratings and generate personalized recommendations.

### Target Performance
- RMSE < 0.90
- MAE < 0.70
- Real-time recommendation capability
- Handle cold-start users

---

## 📊 Dataset

MovieLens dataset:

| Metric | Value |
|------|------|
| Users | 610 |
| Movies | 9,742 |
| Ratings | 100,836 |
| Rating Range | 0.5 – 5.0 |
| Average Rating | 3.50 |
| Sparsity | 98.3% |

### Key Observations
- Most users rate few movies → cold start problem
- Most movies have very few ratings → long-tail distribution
- Ratings skew positive (users rate what they like)

---
## 🔍 Exploratory Data Analysis (EDA)

### Rating Distribution
![alt text](<Distribution of Users and Ratings.png>)

**Insight:**  
Ratings are skewed toward positive values (3–5 stars), confirming implicit positive feedback bias.
The rating distribution is heavily skewed toward higher ratings.  
Users are more likely to rate movies they enjoyed, which introduces **positive bias** in the dataset.

---

### User Activity Distribution
- Majority of users rated fewer than 100 movies
- Small minority of users are highly active
*Number of ratings per user*

![alt text](<image (1).png>)

**Insight:**  
Most users interact with very few movies, creating a cold-start challenge.

---

### Movie Popularity Distribution
- Most movies receive very few ratings
- A small number of blockbuster movies dominate the dataset

*Ratings per movie*

![alt text](<image (6).png>)

**Insight:**  
Few movies dominate interactions while most receive very few ratings — classic long-tail problem.

---

## 🧠 Methodology

### Algorithms Implemented

| Model | Type | Description |
|------|------|------|
| KNNBasic | User-based CF | Baseline similarity model |
| KNNWithMeans (User) | User CF | Adjusts rating bias |
| KNNWithMeans (Item) | Item CF | Uses movie similarity |
| SVD | Matrix Factorization | Learns hidden preferences |
| NMF | Matrix Factorization | Interpretable latent features |

### ⚙️ Training Process
- Train/Test Split: 80/20
- Cross Validation: 3-fold GridSearch

**Metrics**
- RMSE (accuracy)
- MAE (interpretability)

---

## 🏆 Results

| Rank | Model | RMSE | MAE | Improvement |
|----|----|----|----|----|
| 1 | SVD (Tuned) | 0.8602 | 0.6601 | +12.4% |
| 2 | NMF (Tuned) | 0.8961 | 0.6779 | +8.8% |
| 3 | KNNWithMeans (User) | 0.9077 | 0.6933 | +7.6% |
| 4 | KNNWithMeans (Item) | 0.9129 | 0.6953 | +7.1% |
| 5 | KNNBasic | 0.9823 | 0.7559 | Baseline |

### Key Insight
Matrix Factorization significantly outperforms similarity-based models.  
SVD captures hidden user preferences and generalizes best.

---

## 📈 Error Analysis

**Findings**
- Predictions unbiased (centered around zero error)
- Accurate for typical ratings (3–4 stars)
- Harder to predict extreme ratings (1 & 5 stars)

*Residual error plot*

![alt text](<ERROR ANALYSIS.png>)

**Insight:**  
Model performs well for common ratings but struggles with extreme preferences.

**Interpretation**
The model understands general taste patterns but struggles with very strong opinions — a common behavior in recommender systems.

---
## 🧾 Conclusion

This project demonstrates the effectiveness of collaborative filtering techniques for personalized recommendation systems in sparse real-world environments.

Traditional neighborhood-based models (KNN) provided a reasonable baseline but struggled with sparse interactions and limited user history. In contrast, matrix factorization approaches — particularly the tuned SVD model — successfully captured latent relationships between users and movies, leading to significantly improved prediction accuracy.

The model achieved strong performance (RMSE < 0.90) and generalized well across typical rating behavior. While extreme ratings (very low or very high) remained difficult to predict, this reflects natural human rating inconsistency rather than model failure.

Overall, the system proves that latent factor models are better suited for scalable recommendation systems and can substantially improve user engagement and content discovery.

---

## 💡 Recommendations

Based on the findings, the following strategies are recommended for production deployment:

- Use **SVD as the core recommendation engine**
- Combine collaborative filtering with content-based features for cold-start users
- Prioritize ranking quality over perfect rating prediction
- Introduce onboarding questionnaires to collect initial preferences
- Periodically retrain the model as new interactions are collected

These steps would improve recommendation relevance, user retention, and platform engagement.

---

## 🚀 Future Work

To further improve system performance and production readiness:

### Model Improvements
- Hybrid recommender (Collaborative + Content-Based)
- Deep learning embeddings (Neural Collaborative Filtering)
- Temporal dynamics (time-aware recommendations)

### Product Improvements
- Real-time recommendation API
- Online A/B testing framework
- Feedback loop from clicks & watch time
- Personalized homepage ranking

### Cold Start Solutions
- Preference onboarding survey
- Genre-based initialization
- Popularity-based fallback recommender

Implementing these enhancements would move the system from a predictive model to a fully production-ready personalization engine.


## Repository Structure
```
├── data/
├── images/
|   └── 
├── notebooks/
│   └── main.ipynb
|   ├── olonde.ipynb
|   ├──jasho.ipynb
|   ├──shem.ipynb
|   ├──vkones.ipynb
|   └── dennis.ipynb
└── README.md


