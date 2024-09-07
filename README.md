# Clustering Network Traffic Data for Anomaly Detection
This project focuses on identifying unusual patterns in network traffic that could indicate cyber threats or failures. The project includes multiple .ipynb files, each handling a different aspect of the process, from data cleaning to model evaluation.

## Table of Contents
- [Project Structure](#project-structure)
- [How to Use](#how-to-use)
- [Key Libraries](#key-libraries)
- [Dataset](#dataset)
- [Notes](#notes)
- [Conclusion](#conclusion)

## Project Structure
The following .ipynb files are included in the project:
1. network_anamoly_detection_data_cleaning.ipynb
   * **Purpose:** This notebook handles missing data, outlier detection, and any issues with the dataset. It ensures the data is in a clean state before further analysis.
   * **Key Steps:**
        * Identifies and removes missing or irrelevant data.
        * Handles outliers using methods such as z-score or IQR.
        * Validates data integrity.
        * Applies basic visualizations to understand data distribution.
  * **Outputs:** Cleaned dataset ready for preprocessing.
3. network_anamoly_detection_data_preprocessing.ipynb
   * **Purpose:** This notebook prepares the data for clustering algorithms. It handles the transformation of data into a suitable format for modeling.
   * **Key Steps:**
        * Converts data types where necessary.
        * Checks for normalization or scaling (if required, based on the dataset’s distribution).
        * PCA (Principal Component Analysis) for dimensionality reduction.
        * The transformed data is saved and ready for model building.
  * **Outputs:** Preprocessed dataset with optional PCA applied.
4. network_anamoly_detection_model_building.ipynb
   * **Purpose:** This notebook builds and trains the clustering models on the preprocessed data.
   * **Key Steps:**
        * Uses both KMeans and DBSCAN clustering algorithms.
        * Applies PCA for dimensionality reduction within a Pipeline to streamline preprocessing and modeling.
        * For KMeans, tries different numbers of clusters (n_clusters) and compares results.
        * For DBSCAN, tunes parameters like eps and min_samples.
        * KMeans is used to identify structured clusters, while DBSCAN is used for identifying noise and irregularly shaped clusters.
  * **Outputs:** Trained KMeans and DBSCAN models along with their clustering labels.
5. network_anamoly_detection_model_evaluation.ipynb
   * **Purpose:** This notebook evaluates the clustering models using various metrics to determine the quality of the clusters.
   * **Key Steps:**
        * **Davies-Bouldin Index (DBI):** Measures intra-cluster similarity vs. inter-cluster differences (lower is better).
        * Compares clustering performance between KMeans and DBSCAN.
        * For KMeans, tries different numbers of clusters (n_clusters) and compares results.
        * For DBSCAN, tunes parameters like eps and min_samples.
        * KMeans is used to identify structured clusters, while DBSCAN is used for identifying noise and irregularly shaped clusters.
  * **Outputs:** Evaluation metrics for both KMeans and DBSCAN

## How to use
1. Run data_cleaning.ipynb first to clean the dataset and remove any anomalies or missing values.
2. Next, run data_preprocessing.ipynb to transform the data and reduce its dimensions using PCA if needed.
3. Then, proceed to model_building.ipynb to train the clustering models on the preprocessed data.
4. Finally, run evaluation.ipynb to evaluate the performance of the models using clustering evaluation metrics.

## Key Libraries
* pandas: For data handling and manipulation.
* numpy: For numerical operations.
* scikit-learn: For clustering algorithms, PCA, and evaluation metrics.
* matplotlib/seaborn: For visualizing clusters and results.

## Dataset
The dataset consists of network traffic data with the following features:
* **SourceIP, DestinationIP, SourcePort, DestinationPort**: Identifiers for network traffic.
* **Protocol, BytesSent, BytesReceived, PacketsSent, PacketsReceived, Duration:** Traffic characteristics.
* **IsAnomaly:** A flag indicating if the data point is an anomaly (0 or 1).

## Notes
* Make sure to adjust parameters like n_clusters for KMeans and eps/min_samples for DBSCAN based on your dataset.
* If you have a large dataset (e.g., 1,000,000 records), consider using mini-batch KMeans or experimenting with eps and min_samples to optimize DBSCAN for scalability.

## Conclusion
This project helps in identifying unusual network traffic patterns using clustering techniques, aiming to detect anomalies that could indicate cyber threats or failures. The combination of KMeans and DBSCAN ensures both structured and unstructured anomalies are captured.
