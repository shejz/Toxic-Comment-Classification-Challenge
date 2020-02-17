# [Toxic Comment Classification](https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge)
Identify and classify toxic online comments.

## Data Description

Competition data set is available at [Kaggle](https://www.kaggle.com/c/jigsaw-toxic-comment-classification-challenge). A large number of Wikipedia comments are provided which have been labeled by human raters for toxic behavior.  The problem has only one predictor variable, `comment_text`, which is to be labeled or classified with respect to six target variables.

**The target variables are the following types of toxicity:**
- toxic
- severe toxic
- obscene
- threat
- insult
- identity hate

The training set consists of labeled **159,571** comments (observations) and the test set consists of **153,164** comments to be labeled.

## Problem Definition
- Toxic comment classification is a multi-label text classification problem with a highly imbalanced dataset.
- Build a multi-labeled model that's capable of detecting different types of toxicity like threats, obscenity, insults, and identity-based hate. We need to create a model which predicts a probability of each type of toxicity for each comment.


## Evaluation Metric
Due to changes in the competition data set, the evaluation metric of the competition has been changed and updated on Jan 30, 2018.      -  Submissions are evaluated on the mean column-wise **ROC AUC** score (the Area computed Under the Receiver Operating Characteristic Curve from prediction scores). In other words, the score is the average of the individual AUCs of each predicted column.

## Hyperparameters and preprocessing
- Batch size: 512. Bigger batch size makes results more stable.
- 10 Fold CV
- Epochs: 15.
- Sequence length: 900.
- Optimizer: Adam with clipped gradient (clipvalue=1.0)
- Preprocessing: Unidecode library (https://pypi.python.org/pypi/Unidecode) to convert text to ASCII first and after that filtering everything except letters and some punctuation.

The max_features in the embedding layer is the vocabulary size. Setting `maxfeatures = 283759`.


**Text normalization**
- Fixed some misspellings with word2vec.
- Excluding all punctuations special_character_removal = re.compile(r'[^A-Za-z\.\-\?\!\,\#\@\% ]',re.IGNORECASE)

**Pre-trained word embeddings**:
- FastText (crawl-300d-2M.vec)
- GloVe (glove.twitter.27B.200d.txt)

## Models
- Logistic Regression
- BERT-Fast.ai
- Bidirectional-LSTM
- Bidirectional-GRU

**NOTE**: About ~5-6 hours timeline was for 10 Fold CV with 15 epochs in each fold.


## Submissions & Leaderboard Scores

|Models |Public score|Private score|Final rank| 
|------|--------|--------|---|
|Logistic Regression |0.98022 |0.98048|   |
|BERT with fast.ai |0.98553 |0.98578 |   |
|Bidirectional-GRU-LSTM  | 0.98673 |0.98634 |723/4550 ([Top 16%](https://www.kaggle.com/shielaj/competitions)) |


