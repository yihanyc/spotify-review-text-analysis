# Spotify Review Text Analysis

This project analyzes over 60,000 Spotify user reviews from the Google Play Store using text-as-data methods. It explores emotional tone, feature feedback, and platform engagement behavior through classification, topic modeling, and logistic regression.

## 📁 Project Structure

### 🔹 Inputs

- `reviews.csv`: The original raw dataset of 61,594 Spotify user reviews from the Google Play Store.
- `processed_reviews.csv`: Cleaned and tokenized version of the raw data used for feature extraction and modeling.
- `predicted_reviews_tfidf_lasso.csv`: TF-IDF-based classification results (App Experience vs. Other) from the Lasso model.
- `newreview_with_lda_labels.csv`: The full review dataset merged with topic labels from LDA modeling.
- `app_reviews_with_topic.csv`: Subset of reviews classified as App Experience, used for topic modeling.
- `lda_beta_terms.csv`: Beta term matrix output from the LDA model, listing word-topic probabilities.
- `lda_topic_keywords_top.csv`: Top keywords per topic extracted from the LDA model.
- `human_label_checked.xlsx`: Manually labeled sample of 2,000 reviews used for training supervised classifiers.
- `sampled_reviews_by_topic.xlsx`: Sample of representative reviews per topic, used for interpretation and validation.
- `data/glove.6B.300d.txt` *(not included)*: Pre-trained GloVe embeddings originally used in the classification model. Due to GitHub’s file size restrictions, this file is excluded. It can be downloaded from the [official GloVe repository](https://nlp.stanford.edu/projects/glove/).

### 🔧 Functionality

The analysis pipeline includes the following steps:

- **Data Cleaning**: Lowercasing text, handling duplicates and special characters.
- **Manual Annotation**: A sample of 2,000 reviews was manually labeled as App Experience vs. Other for supervised training.
- **Feature Engineering**: Flags for reply status and competitor mentions; word count calculated for each review.
- **Supervised Classification**: TF-IDF and word embeddings used to train models (Lasso, SVM, Naïve Bayes) to classify user concerns.
- **Topic Modeling**: LDA applied to App Experience reviews to extract major sub-themes such as Technical Fixes and Account Issues.
- **Sentiment & Emotion Scoring**: NRC lexicon used to score 10 emotion categories (e.g., joy, trust, disgust).
- **Logistic Regression**: Models platform reply behavior using emotion, topic, word count, and competitor mentions.
- **SMOTE Balancing**: Synthetic oversampling applied to adjust for the extremely low reply rate and improve regression robustness.
- **Visualization**: Emotion, topic, and model results visualized using `ggplot` and integrated in the final report.

### 📤 Outputs

- `figures/`: Contains generated figures for sentiment distribution, emotion scores, topic labeling, and regression results.
- `Spotify.html`: Final Quarto-based report summarizing the analysis.
- `README.md`: Project documentation and guide (this file).

### 🧠 Code Files

- `Spotify.qmd`: Main Quarto file containing the entire analysis workflow.
- `model/`: Includes modeling code for classification, topic modeling, and logistic regression.
- `data/`: Folder for input datasets (excluding large files).
- `slide/`: Optional slides for presentation.
- `document/`: Supporting documentation for project submission or review.

---

## 🔗 References

- Dataset: [Kaggle - Spotify Google Play Reviews (2022)](https://www.kaggle.com/datasets/mfaaris/spotify-app-reviews-2022)
- GloVe Embeddings: [Stanford GloVe Project](https://nlp.stanford.edu/projects/glove/)

---

## ⚠️ Notes

- The GloVe file is not included due to GitHub's 100MB file limit. You can download it externally and place it in the `/data` directory if needed.
- Ensure required packages are installed using `requirements.txt` for reproducibility.
