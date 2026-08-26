# Amazon-Music-Clustering-
Amazon Music Clustering - To group songs with similar audio characteristics using K-Means clustering and identify meaningful audio-profile clusters without using predefined genre labels.
# Amazon Music Clustering

## Project Overview

This project uses **unsupervised machine learning** to group songs with similar audio characteristics. The goal is to identify meaningful audio-profile clusters without using predefined genre labels.

The project applies **K-Means clustering** to selected audio features and uses evaluation metrics, PCA, cluster profiling, and genre analysis to interpret the results.

---

## Problem Statement

With millions of songs on music platforms, manually categorizing them is difficult. This project uses unsupervised machine learning to group similar songs based on audio features such as danceability, energy, acousticness, speechiness, valence, tempo, and duration.

---

## Objectives

- Analyze and preprocess Amazon Music song data.
- Select and standardize relevant audio features.
- Apply **K-Means clustering** to group similar songs.
- Determine the optimal number of clusters using the **Elbow Method and Silhouette Score**.
- Evaluate and visualize the resulting clusters.
- Interpret cluster characteristics and associated genres.
- Provide business insights for playlist curation and song discovery.

---

## Tech Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Google Colab
- K-Means Clustering
- PCA

---

## Dataset Description

**Dataset:** `single_genre_artists.csv`

- **Total Records:** 95,837 songs
- **Total Columns:** 23

### Selected Audio Features

- Danceability
- Energy
- Loudness
- Speechiness
- Acousticness
- Instrumentalness
- Liveness
- Valence
- Tempo
- Duration

Song and artist identification fields were retained for reference but were not used as clustering features.

c

## Project Workflow

```text
Data Loading
      ↓
Data Exploration
      ↓
Data Cleaning
      ↓
Feature Selection
      ↓
Feature Scaling
      ↓
Elbow Method
      ↓
Silhouette Analysis
      ↓
K-Means Clustering
      ↓
Cluster Evaluation
      ↓
PCA Visualization
      ↓
Cluster Profiling
      ↓
Genre Inference
      ↓
Business Insights
      ↓
Final Clustered Dataset

---

# 🔍 Data Exploration & Preprocessing

The dataset was analyzed to understand its structure and quality.

## Data Quality Results

- Missing values: **0**
- Duplicate rows: **0**
- Records analyzed: **95,837**

The selected audio features were standardized using **StandardScaler** because K-Means clustering is distance-based.

---

# 🎧 Feature Selection

The following 10 audio features were selected for clustering:

- danceability
- energy
- loudness
- speechiness
- acousticness
- instrumentalness
- liveness
- valence
- tempo
- duration_ms

These features represent rhythm, mood, energy, instrumentation, and other characteristics of a song.

---

# 📐 Choosing the Number of Clusters

## Elbow Method

K values from **2 to 10** were tested using inertia (SSE) to analyze cluster compactness.
<img width="856" height="536" alt="image" src="https://github.com/user-attachments/assets/582216d9-793e-4277-9002-1f4e200de57e" />


## Silhouette Analysis

A random sample of **10,000 songs** was used to compare silhouette scores efficiently.
<img width="772" height="502" alt="image" src="https://github.com/user-attachments/assets/1f776b74-ac94-4ec8-918a-ee859b7c7ed2" />


The highest silhouette score was obtained at:

**K = 3 → 0.2364**

Therefore, **3 clusters** were selected for the final K-Means model.
