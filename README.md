Spotify and Billboard Chart Success Analysis
Project Overview

This project investigates the relationship between Spotify audio features and Billboard Hot 100 chart performance. The main goal is to understand whether certain musical characteristics are associated with a track being charted, and whether those characteristics are also related to stronger Billboard success once a track appears on the chart.

The analysis combines Spotify track metadata and audio features with Billboard Hot 100 chart data. The final dataset includes both charted and non-charted songs, allowing comparison between the two groups. The project also explores how these relationships differ across decades and music genres.

Research Focus

The project examines several broad questions:

Do charted and non-charted songs have different Spotify audio-feature profiles?
Are features such as danceability, energy, loudness, acousticness, or instrumentalness associated with charted status?
Do the features linked to chart success change across decades?
Do different genres show different relationships between audio features and Billboard success?
Among charted songs, which features are associated with stronger normalized Billboard performance?
Datasets Used

The project uses three main data sources:

Spotify tracks dataset
Spotify 160k tracks dataset
Billboard Hot 100 dataset

These datasets are cleaned, normalized, merged, and transformed into one final analysis dataset.

Main Variables
Spotify Audio Features
popularity: Spotify popularity score of the track.
danceability: How suitable the track is for dancing.
energy: How intense and active the track feels.
loudness: Overall volume of the track in decibels.
speechiness: Presence of spoken-word content.
acousticness: Probability that the track sounds acoustic.
instrumentalness: Probability that the track is instrumental.
liveness: Probability that the track contains live-performance characteristics.
valence: Musical positivity or brightness of the track.
tempo: Speed of the track in beats per minute.
Billboard Variables
charted_binary: Binary chart status, where 1 = Charted and 0 = Non-Charted.
charted_label: Text version of chart status.
peak_rank: Best Billboard rank achieved by the track.
weeks_on_board: Number of weeks the track stayed on the chart.
CSS: Custom Chart Success Score.
CSS_normalized: Standardized version of the Chart Success Score.
Time and Genre Variables
year: Year associated with the track or chart record.
decade: Numeric decade.
decade_label: Readable decade label, such as 1980s or 2010-20s.
track_genre: Assigned music genre.
Chart Success Score

A custom Chart Success Score, called CSS, is created from Billboard weekly ranking data. Each weekly Billboard record receives a score based on rank:

weekly_score = (101 - rank) / 100

The total CSS for a song is then calculated by summing its weekly scores across all chart appearances.

A normalized version, CSS_normalized, is also created using z-score standardization:

CSS_normalized = zscore(CSS) * 100

This allows Billboard chart performance to be compared more easily across tracks.

Data Preparation Workflow

The project follows these main preparation steps:

Load Spotify and Billboard datasets.
Select relevant columns.
Rename columns for consistency.
Combine Spotify datasets.
Clean and normalize track names and artist names.
Remove duplicates and missing values.
Calculate weekly Billboard scores.
Create summarized Billboard chart-success table.
Merge Spotify and Billboard data.
Create charted and non-charted labels.
Add decade labels.
Merge genre reference data.
Export the final dataset.
Exploratory Data Analysis

The exploratory analysis includes:

Standardized mean audio features by chart status.
Distributions of Spotify audio features.
Audio-feature trends by decade.
Correlation heatmaps for charted status by decade.
Correlation heatmaps for normalized Billboard success by decade.
Correlation heatmaps for charted status by genre.
Correlation heatmaps for normalized Billboard success by genre.
Genre feature-profile heatmaps.
Appendix heatmaps for more detailed genre-decade analysis.
Statistical Methods

The project uses several statistical methods:

Welch’s t-test

Used to compare mean audio-feature values between charted and non-charted songs.

Mann-Whitney U test

Used as a non-parametric robustness check for differences between charted and non-charted songs.

Point-biserial correlation

Used when the dependent variable is binary, such as charted_binary.

Example use:

audio feature vs charted_binary
Spearman correlation

Used when analyzing relationships with CSS_normalized, because chart success is likely skewed and may contain outliers.

Example use:

audio feature vs CSS_normalized
Main Findings

The analysis finds that charted and non-charted songs differ significantly across all tested Spotify audio features. Charted songs tend to be:

More popular
Louder
More energetic
More danceable
Less acoustic
Less instrumental

However, most correlations are modest. This suggests that Spotify audio features are related to Billboard chart performance, but they do not fully explain chart success by themselves.

The results also show that genre and decade matter. A feature that is associated with chart success in one genre or decade may be weaker, irrelevant, or even opposite in another. Therefore, Billboard success is best understood as a combination of audio characteristics, genre conventions, historical period, and external factors.

Limitations

This project has several limitations:

The analysis is observational, so it shows association but not causation.
Billboard success is influenced by non-audio factors such as marketing, radio airplay, playlists, artist popularity, and social media.
Dataset merging depends on cleaned track and artist names, so some mismatches may remain.
Genre labels may simplify songs that belong to multiple styles.
Some genre-decade groups have smaller sample sizes, so minimum sample thresholds are used.
Future Research

Future research could explore the more detailed appendix heatmaps. These allow investigation of specific genre-decade combinations, such as whether danceability matters more in certain genres or whether instrumentalness reduces chart success in specific historical periods.

Further work could also include:

Artist popularity
Playlist placement
Radio airplay
Social media activity
Lyrics and sentiment analysis
Release timing
Music-label information
Predictive machine-learning models
Project Files

Typical project structure:

project/
│
├── initial_data/
│   ├── spotify_tracks.csv
│   ├── spotify_160k_dataset.csv
│   ├── billboard_hot_100.csv
│   └── genre_reference_table.csv
│
├── intermediary_data/
│   ├── spotify_combined_df.csv
│   ├── merged_df_billboard_spotify.csv
│   └── spotify_cleaned_combined.csv
│
├── final_data/
│   └── final_df.csv
│
├── Spotify_Billboard_DataScienceProject.ipynb
└── README.md
Requirements

The project uses Python and the following libraries:

pandas
numpy
matplotlib
seaborn
scipy
statsmodels
sklearn

Install them with:

pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn

or with Conda:

conda install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn

How to Run
Open the notebook in Jupyter Notebook or JupyterLab.
Make sure the datasets are placed in the correct folders. Namely the project should be one level lower than the three folders initial_data, intermediary_data, final_data
Run the data preparation cells first from Appendix A.
Run the exploratory analysis cells.
Run the hypothesis-testing cells.
Review the results, discussion, conclusion, and appendix sections.
