# Song Clustering and Feature Analysis Using Unsupervised Learning

## Project Motivation

The objective of this project is to investigate the relationships between various attributes of songs and identify the key features that effectively differentiate between genres. Given that the dataset lacks explicit genre labels, we will employ unsupervised learning methods, specifically clustering algorithms, to organize the songs into distinct groups. These groups, formed based on similarities in their musical attributes, will serve as proxies for genres. Through this approach, we aim to uncover the underlying patterns in the data that signal genre distinctions, despite the absence of pre-defined genre classifications.

## Libraries Used

- **Pandas**: For data cleaning, manipulation, and preprocessing.
- **Seaborn**: For creating data visualizations.
- **Matplotlib**: For plotting charts and graphs.
- **Scikit-learn**: For implementing clustering algorithms like K-means, PCA, and data preprocessing using StandardScaler.
  
## Dat

The dataset consists of various musical features for each song, including:
- Acousticness
- Danceability
- Duration
- Energy
- Instrumentalness
- Key
- Liveness
- Loudness
- Mode
- Speechiness
- Tempo
- Time Signature
- Valence

These features are used to cluster the songs into groups that likely correspond to different genres or musical styles.

## Data Cleaning and Preprocessing

1. **Loading the Data**: The dataset was loaded using `pandas` from a CSV file. An unnecessary column was dropped, and duplicate rows based on song title and artist were removed.
2. **Handling Missing Data**: Checked for missing values, ensuring there were no NaNs.
3. **Feature Selection**: Only relevant features were selected for clustering.
4. **Normalization**: Data was scaled using `StandardScaler` to ensure that all features contribute equally to the clustering process.

## Exploratory Data Analysis

### Correlation Matrix and Heatmap

A correlation matrix was created to identify the relationships between the musical features. Key insights include:
- **Energy and Loudness**: Strong positive correlation (0.762), suggesting that higher energy tracks tend to be louder.
- **Acousticness and Energy**: Strong negative correlation (-0.646), indicating that more acoustic tracks have lower energy levels.
- **Danceability and Valence**: Moderate positive correlation (0.442), suggesting that more danceable tracks tend to have a happier mood.

A heatmap was generated to visually represent these correlations.

### Scatter Plot Matrix (SPLOM)

A scatter plot matrix was created to examine relationships between key features such as energy, loudness, acousticness, danceability, and valence.

## K-Means Clustering

1. **Feature Selection**: Features such as acousticness, danceability, energy, instrumentalness, and others were selected for clustering.
2. **Normalization**: The data was normalized using `StandardScaler`.
3. **Optimal Number of Clusters (K)**: The Elbow Method and Silhouette Score were used to determine the optimal number of clusters, with K=5 chosen as the best fit.

### Results

Cluster distribution:
- Cluster 0: 760 tracks
- Cluster 1: 171 tracks
- Cluster 2: 211 tracks
- Cluster 3: 621 tracks
- Cluster 4: 219 tracks

## PCA and Cluster Visualization

To visualize the clusters in a 2D space, **PCA** was applied to reduce the dimensions of the data. A scatter plot was generated, where each point represents a song, colored by its cluster label. 

### PCA Loadings

The PCA loadings were examined to understand how the original features contribute to the principal components:
- **PCA Component 1**: Strong positive loading for acousticness, strong negative loadings for energy and loudness.
- **PCA Component 2**: Strong negative loading for danceability, positive loadings for liveness and tempo.

These components help explain the variability in the dataset and the differences between clusters.

### Biplot

A biplot was created to visualize both the PCA components and the original features, showing how the features align with the clustered data points.

## Variance Across Clusters

To identify the most distinguishing features, the variance of each feature across the clusters was calculated:
- **Tempo**: Shows the highest variance, suggesting that it plays a significant role in differentiating between clusters.
- **Loudness**: Also shows high variance, indicating it is a key factor in distinguishing tracks.
- **Acousticness and Instrumentalness**: Play a notable role in separating different types of music.
  
Lower variance was observed for features such as speechiness and danceability, which contribute more subtly to cluster differentiation.

## Insights

- **High Energy and Loudness Cluster**: Likely represents intense and powerful tracks, possibly genres like dance, electronic, or rock music.
- **High Acousticness Cluster**: Likely corresponds to more acoustic genres like folk or classical.
- **High Danceability and Valence Cluster**: Suggests upbeat and rhythmically engaging genres like pop or electronic dance music.
- **Instrumental and Long Duration Cluster**: Likely represents ambient or instrumental genres such as classical or jazz.
- **Balanced Feature Cluster**: Represents tracks with a balanced mix of acoustic and electronic elements, spanning across genres like pop, rock, or hip-hop.
