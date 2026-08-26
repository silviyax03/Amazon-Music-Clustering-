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
```
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

---

# 🤖 K-Means Clustering

The final K-Means model was trained using:

- **Number of Clusters:** 3
- **Random State:** 42
- **n_init:** 10

Each of the **95,837 songs** was assigned to one of the three clusters.

---

# 📊 Cluster Evaluation

| Metric | Result |
|---|---:|
| Number of Clusters | **3** |
| Songs Analyzed | **95,837** |
| Silhouette Score | **0.2423** |
| Davies-Bouldin Index | **1.5702** |
| Inertia | **658,335.08** |

The results indicate moderate separation between the clusters.

---

# 📊 Cluster Distribution

| Cluster | Number of Songs |
|---|---:|
| Cluster 0 | **12,513** |
| Cluster 1 | **30,807** |
| Cluster 2 | **52,517** |
<img width="591" height="381" alt="image" src="https://github.com/user-attachments/assets/c001e67e-93f1-491c-a312-0b50d988a2f6" />

---

# 🧩 PCA Analysis

PCA was used for visualization by reducing the 10 standardized audio features to **2 principal components**.

- **PC1:** 27.08%
- **PC2:** 18.82%
- **Total explained variance:** **45.90%**

PCA was used only for visualization; the original standardized features were used for K-Means clustering.

<img width="701" height="470" alt="image" src="https://github.com/user-attachments/assets/0abf59f3-1c00-4396-8840-e2956ab037d8" />

---

# 🔎 Cluster Profiling

## Cluster 0 — Speech / Spoken-Content Profile

- Very high speechiness
- Higher liveness
- Shorter average duration
- Strong association with spoken-content genres

## Cluster 1 — Acoustic / Instrumental Profile

- Highest acousticness
- Highest instrumentalness
- Lower energy
- Lower valence
- More acoustic and instrumental characteristics

## Cluster 2 — Energetic / Upbeat Profile

- Highest energy
- Highest loudness
- Highest valence
- Higher tempo
- More energetic and upbeat characteristics

The clusters represent **audio profiles rather than guaranteed musical genres**.

<img width="1107" height="542" alt="image" src="https://github.com/user-attachments/assets/fdfb546c-8caa-4bca-8d51-d24823179fc8" />
<img width="969" height="683" alt="image" src="https://github.com/user-attachments/assets/357c70b8-31dc-4230-987c-a11991699e50" />

---

# 🎼 Genre Inference

Genre information was analyzed **after clustering** to help interpret the resulting audio profiles.

Genre labels were **not used as input features for K-Means**.

The analysis showed that songs from different genres can belong to the same cluster when they have similar audio characteristics.

### Cluster 0

- Dominated by **Hoerspiel** and **Kleine Hoerspiel**
- Strong association with speech-heavy content
<img width="582" height="367" alt="image" src="https://github.com/user-attachments/assets/a591427b-75c9-40cf-a38a-5a7ce85c3b5c" />

### Cluster 1

- Major genres include **Vintage Taiwan Pop, Classic Israeli Pop, Chanson, and Classic Soundtrack**
- Consistent with its more acoustic and instrumental profile
<img width="564" height="367" alt="image" src="https://github.com/user-attachments/assets/b1592f10-fbd4-4aa9-a07b-2717e45c1079" />

### Cluster 2

- Major genres include **J-Pop, Turkish Pop, Classic Thai Pop, and Thai Pop**
- Consistent with its more energetic and upbeat profile
<img width="583" height="374" alt="image" src="https://github.com/user-attachments/assets/90f6808e-39a9-434a-a5bb-2c94cdf01cc7" />

---

# 💼 Business Use Cases

## Personalized Playlist Curation

Group songs with similar audio characteristics to create targeted playlists.

## Improved Song Discovery

Recommend songs from similar audio-profile clusters based on user preferences.

## Artist Analysis

Compare songs with tracks that have similar audio characteristics.

## Music Content Segmentation

Separate different types of music and spoken content based on their audio profiles.

---

# 📋 Final Results

The project successfully grouped **95,837 songs into three audio-profile clusters** using K-Means clustering.

## Final Cluster Summary

| Cluster | Profile |
|---|---|
| Cluster 0 | Speech / Spoken-Content |
| Cluster 1 | Acoustic / Instrumental |
| Cluster 2 | Energetic / Upbeat |

## Final Model Metrics

- **Silhouette Score:** 0.2423
- **Davies-Bouldin Index:** 1.5702
- **Inertia:** 658,335.08

---

# 📁 Project Outputs

- `Amazon_Music_Clustering.ipynb`
- `amazon_music_clustered.csv`
- `visualizations/`

## Final CSV

The final dataset contains the original song information along with the assigned **cluster label**.

---

# ✅ Conclusion

The Amazon Music Clustering project demonstrates how unsupervised machine learning can organize a large music catalog based on audio characteristics.

Using K-Means clustering with three clusters, the project identified distinct speech-oriented, acoustic/instrumental, and energetic/upbeat audio profiles. These results can support playlist curation, song discovery, artist analysis, and music-content segmentation.

---

# 👩‍💻 Author

**Silviya X**
