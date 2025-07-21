# Moosic Case Study

## Overview

In this case study Moosic is a little start-up that creates playlists curated by music experts and specialists in old and new trends. Users can subscribe to their website and listen to these playlists through their preferred Music App (be it Spotify, Apple Music, Youtube Music…). Business is scaling up fast and the music experts are slow in creating new playlists. They want to use Data Science to add a degree of automatisation to the creation of playlists. The goal is to keep the size of all the playlists between 50 and 250 songs. The dataset has roughly 5000 songs, meaning the target amount of clusters is between 20 and 100 clusters.

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white) 
![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)
![scikit-learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google%20Colab-%23F9A825.svg?style=for-the-badge&logo=googlecolab&logoColor=white) 
![Jupyter Notebook](https://img.shields.io/badge/jupyter-%23FA0F00.svg?style=for-the-badge&logo=jupyter&logoColor=white)

## Data Sources

For this case study a dataset with roughly 5000 Spotify songs including their audio features is given:

- **Base dataset (CSV file)**:
  - `3_spotify_5000_songs.csv`
  

## Methodology

- **Data Cleaning & Preparation**:
  Non-numerical features ('name', 'artist','type', 'id', 'html"') were removed from the data set as K-Measn only works with numerical features.

- **Exploring the effects of different scaling methods**:
  A comparison of five different scaling methods (MinMaxScaler, StandardScaler, RobustScaler, QuantileTransformer, PowerTransformer) was conducted to explore the impacts of the scalers on the suggested ideal K-Value (number of clusters/playlists). The KneeLocator function was used to   determine the K-Value.

- **Principal Component Analysis**:
  PCA was used to reduce noise and the dimensionality of the Spotify dataset before clustering the songs. This helped to identify the most important features of the songs, and it also made the clustering process more efficient. The PowerTransformer was used to scale the features     before PCA transformation. Principal components (PCs) were selected based on highest variance, retaining those that cumulatively explained 95% of the total variance.

- **K-Value**:
  The selected random seed has a significant impact on the clustering of the K_Means algorithm. Therefore the average K-Value (48) of 100 random seed values was selected as the best K-Value to move forward.

- **Creation of Spotify Playlists**:
  For demonstration purposes two example playlists were selected and uploaded to Spotfy using a Spotfy API.

## Results

- With the determined K-Value of 48 the K-Means algorithm was able to create playlists with the desired size of 50 to 250 songs with only one exception.
- The composition of the majority of songs within a playlist appear cohesive to a human listener, but there are exceptions in each playlist that seem iappropriate or misplaced.
- Recommendations were formulated on Exploring Other Algorithms like HDBSCAN, adding selection layers to throw out misfits or use a supervised ML model to learn music genres with labeled data.

## Tools & Technologies

- Python (Pandas, NumPy, Sklearn) for data manipulation, analysis and clustering
- Jupyter Notebook for an integrated code and report environment
- Seaborn (Matplotlib) for data visualization
- Spotify API for upload of playlists

## Repository Contents

- `Scaler_Comparison`: Jupyter notebook comparing different scaling methods
- `Playlist_Creation_with_PCA`: Jupyter notebook scaling the data, feature reduction and selection using PCA, K_Value selection using KneeLocator function and averaging over 100 random seed values, uploading example playlists to Spotify
- `Spotify_Data/`: Folder containing the CSV data file used in the project.
- `Case_study_Moosic.pdf`: A detailed PDF report summarizing the findings (optional).

## Environment Variables
Your `.env` file should include:

```
usernameSpo=YOUR_SPOTIFY_USER_NUMBER
redirectUri=YOUR_REDIRECTURI
client_id=YOUR_CLIENT_ID
client_secret=YOUR_CLIENT_SECRET
```
See also the `exmple_variables.env` file.
For guidance how to get your Redirect URI, Client ID, Client Secret and Username take a look at `Spotify_App_Guide`.


## How to Run

1. Clone the repository.
2. Ensure the CSV file is in the `Spotify_Data` directory.
3. Open the Jupyter notebook `Playlist_Creation_with_PCA`.
4. Run the cells sequentially to reproduce playlist creation.
5. (Optional) Open the Jupyter notebook `Scaler_Comparison` in case you are interested in how the different scalers perform.


## License
This project is open-source and available under the MIT License.
