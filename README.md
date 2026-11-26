# Can You Hear the Genre?

### Predicting Musical Genres Using Spotify Audio Features

**UC San Diego — DSC 80 Final Project**

## Introduction

Can we determine a song's musical genre based solely on its numerical audio characteristics?

Music genres are often distinguished by their instrumentation, rhythm, and overall sound. However, many genres share similar characteristics, making it difficult to establish clear boundaries between them.

This project explores whether numerical audio features such as energy, danceability, speechiness, and acousticness can distinguish between five musical genres: **classical, electronic, hip-hop, jazz, and rock**.

The goal is to identify which musical characteristics are most useful for genre classification and explore the limitations of categorizing music using numerical data alone.

## Dataset

This project uses a Spotify tracks dataset containing 114,000 entries across 114 musical genres.

For this analysis, I selected five genres representing different musical characteristics, resulting in an initial dataset of 5,000 entries.

The dataset includes numerical features such as:

- **Energy:** The perceived intensity and activity of a song.
- **Danceability:** How suitable a song is for dancing.
- **Speechiness:** The presence of spoken words within a recording.
- **Acousticness:** The confidence that a recording is acoustic.
- **Instrumentalness:** The likelihood that a track contains no vocals.
- **Loudness:** The overall loudness of a recording, measured in decibels.
- **Tempo:** The estimated speed of a song in beats per minute.

## Data Cleaning and Exploratory Analysis

During data cleaning, I identified repeated recordings, inconsistent release dates, and missing tempo values.

Some tracks were also assigned to multiple genres, highlighting the ambiguity of musical genre labels. These observations will be considered when preparing the data for classification.

Exploratory analysis revealed several interesting patterns:

- **Classical music** had substantially lower average energy and higher acousticness than most other genres.
- **Hip-hop** had the highest average danceability and speechiness.
- **Electronic and rock** had similar average energy scores but differed in danceability.
- **Hip-hop and electronic** shared several numerical characteristics, suggesting that additional features may be necessary to distinguish them.

These findings suggest that combining multiple audio characteristics may be more effective for genre classification than relying on individual features.

## Assessment of Missingness

The `tempo` column contained a substantial number of missing values.

A permutation test using Total Variation Distance (TVD) found evidence that tempo missingness was associated with musical genre.

A separate test examining musical mode produced a p-value of approximately 0.241, providing insufficient evidence to conclude that tempo missingness depends on mode.

These results suggest that missing tempo values may not occur completely at random. However, additional information would be needed to determine the underlying missingness mechanism.

## Hypothesis Testing

I investigated whether hip-hop songs have higher average speechiness scores than electronic songs.

**Null Hypothesis:** Hip-hop and electronic songs have equal mean speechiness.

**Alternative Hypothesis:** Hip-hop songs have higher mean speechiness than electronic songs.

Using a permutation test with 1,000 simulations, I obtained an observed difference in means of approximately 0.04861.

None of the simulated differences exceeded the observed difference, producing an estimated p-value below 0.001.

At a significance level of 0.05, I rejected the null hypothesis, finding strong evidence that hip-hop songs have higher average speechiness than electronic songs in the selected dataset.

## Baseline Model

*In progress*

The baseline model will use multiclass Logistic Regression to classify tracks into one of the five selected genres using energy and danceability.

Performance will be evaluated using accuracy and macro F1-score.

## Final Model

*In progress*

The final model will investigate additional audio features, feature engineering, and hyperparameter tuning to improve genre classification.

## Fairness Analysis

*In progress*

The fairness analysis will investigate whether classification performance differs between tracks with high and low acousticness.

## Conclusion

*To be completed after model evaluation.*

The project aims to demonstrate both the usefulness and limitations of numerical audio features in identifying musical genres.
