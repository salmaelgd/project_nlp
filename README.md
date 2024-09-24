# project_nlp
# Sentiment Analysis of Tweets

## Data Preprocessing

### Database Description
The project uses the **Sentiment140 dataset** from Kaggle, containing **1.6 million tweets** for sentiment analysis on social media, specifically Twitter. Each tweet is labeled with a polarity (0 for negative, 4 for positive).

| Sentiment | Number of Rows |
|-----------|----------------|
| Positive  | 800,000        |
| Negative  | 800,000        |

#### Columns in the Database:
- **target**: polarity of the tweet
- **ids**: unique identifiers for tweets
- **date**: date and time of publication (UTC)
- **flag**: source of the request
- **user**: username of the person who tweeted
- **text**: content of the tweet (used for sentiment analysis)

### Data Preprocessing
- **Text Cleaning**:
  - Removal of links and mentions
  - Standardization (lowercase)
  - Elimination of stop words
  - Application of lemmatization
  - Removal of specific words without meaning for the analysis

### Data Visualization
- Analysis of Frequent Words with CountVectorizer
- Histogram of the 20 most frequent words
- Word clouds for positive and negative sentiments
- Temporal visualization of the number of tweets

## CNN Model for Sentiment Analysis

### Data Preparation for the Model
- Data Split: 60% training, 20% validation, 20% test

| Data            | Size    |
|------------------|---------|
| Training          | 960,000 |
| Validation        | 320,000 |
| Test              | 320,000 |

### Hyperparameters
- **Activation Function**: ReLU and Sigmoid
- **Loss Function**: Binary Crossentropy
- **Optimizer**: Adam
- **Batch Size**: defined based on the dataset size
- **Epochs**: 25

### Model Architecture
- Embedding Layer
- Three 1D Convolutional Layers
- GlobalMaxPooling1D Layer
- Three Dense Layers

### Model Training and Evaluation
- Confusion matrix to measure accuracy, precision, recall, and F1-score

| Data             | Accuracy | Recall | Precision | F1-score |
|------------------|----------|--------|-----------|----------|
| Train data       | 0.9741   | 0.9771 | 0.9708    | 0.9739   |
| Validation data   | 0.7297   | 0.7324 | 0.7251    | 0.7279   |
| Test data        | 0.7293   | 0.7310 | 0.7260    | 0.7219   |

## Trend Analysis

### LDA Model
- Use of Latent Dirichlet Allocation (LDA) for trend analysis

### Results Exploration
- Extraction and display of keywords for each topic
- Graphical visualization of topic distribution

| Topic | Keywords                               |
|-------|----------------------------------------|
| 1     | wow, tonight, looking, just, thank    |
| 2     | today, days, bed, school, got         |
| 3     | birthday, sure, cool, sick, need      |
| 4     | hair, cute, check, www, hot           |
| 5     | sleep, need, yeah, don, new           |

### Topic Analysis by Class
- Distribution of topics based on sentiment classes (positive and negative)
