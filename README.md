## **Spotify_Analysis_Project**

### **Introduction**
Spotify’s Popularity Index is a metric introduced by Spotify to quantify the popularity of a song relative to others on the platform. However, the exact methodology behind this index remains undisclosed. Our goal is to demystify this "black box" by constructing models that predict a song’s Spotify Popularity Index based on factors such as streaming metrics, genre, and audio features. Additionally, we analyze song lyrics' evolution over time and user sentiment to explore their influence on popularity.

This study is structured into two parts:
1. **Predicting Popularity Scores** using regression models, random forests, and neural networks.
2. **Analyzing Lyrical Themes and Sentiment** across the top songs from 2018 to 2023.

---

## **Data Collection**
We collected data from multiple sources:
- **Spotify API**: Extracted song attributes, including valence, danceability, and tempo.
- **Kworb.net**: Scraped top 1000 streamed songs per year (2018-2023) to obtain **total stream count**.
- **Last.fm API**: Retrieved song-level genre tags.
- **Lyrics.ovh & Genius API**: Obtained lyrics for sentiment and topic modeling.
- **YouTube API**: Scraped top user comments for selected songs to analyze listener sentiment.

We used **Python’s BeautifulSoup** for web scraping and managed API rate limits with request batching.

---

## **Methodology**

### **Part 1: Predicting Popularity Scores**
We built models to predict Spotify’s Popularity Index using:
- **Multiple Linear Regression** (Spotify audio features only) → *Low predictive accuracy (R² ~ 0.0022).*
- **Random Forest & Lasso Regression** → *Slight improvement, but still poor performance.*
- **Including Stream Count in Regression** → *Significant accuracy boost (R² ~ 0.29).*
- **Neural Network with Yamnet Audio Embeddings** → *Best performance, R² ~ 0.5.*

**Key Findings:**
- **Streaming volume has an outsized impact on popularity**, far more than genre or individual song attributes.
- **Direct audio embeddings improve predictive accuracy**, capturing richer feature representation than standard Spotify features.

---

### **Part 2: Lyrics and Sentiment Analysis**
We conducted a **Latent Semantic Indexing (LSI)** analysis to detect lyrical theme shifts and **NRC emotion scoring** to assess sentiment trends.

**Findings:**
- **Lyrics themes evolved from romantic idealism (2018) → introspection & perseverance (2019-2021) → symbolic, sensual imagery (2022-2023).**
- **Positive sentiment peaked in 2021, possibly due to social optimism post-pandemic.**
- **Genre had minimal impact on popularity.**

Additionally, we performed case studies on **Taylor Swift** and **Billie Eilish**, comparing their song popularity to listener sentiment from YouTube comments. Results showed a **high correlation for Billie Eilish but inconsistencies for Taylor Swift**, suggesting differences in audience engagement across platforms.

---

## **Conclusion**
Our study revealed that:
- **Streaming count is the strongest predictor of popularity**, explaining why Spotify does not publicly disclose streaming data.
- **Lyrical sentiment has shifted over time, but core emotional themes (love, struggle, joy) remain consistent.**
- **Neural network models using direct audio embeddings offer the best predictive accuracy.**

Future work could expand this research to include **TikTok virality metrics, emerging genres, and artist collaborations** to further refine the understanding of music popularity.

---

## **Repository Structure**
```
Spotify_Analysis_Project/
│── Code/
│   ├── Neural_Network/
│   ├── Sentiment_Analysis/
│   ├── Webscraping_and_Others/
│── Data/
│   ├── spotify_2018.csv
│   ├── spotify_2019.csv
│   ├── ...
│── Reports/
│   ├── Data_Analytics_Project_Report.pdf
│   ├── Presentation_Slides.pdf
│── README.md
```

---
