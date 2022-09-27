# noisy-enhanced-finance-sentiment

bert-base-finance-sentiment-noisy-search

This model is a fine-tuned version of bert-base-uncased on Kaggle finance news sentiment analysis with data enhancement using noisy search. The process is explained below:

First "bert-base-uncased" was fine-tuned on Kaggle's finance news sentiment analysis https://www.kaggle.com/ankurzing/sentiment-analysis-for-financial-news dataset achieving accuracy of about 88%

We then used a logistic-regression classifier on the same data. Here we looked at coefficients that contributed the most to the "Positive" and "Negative" classes by inspecting only bi-grams.

Using the top 25 bi-grams per class (i.e. "Positive" / "Negative") we invoked Bing news search with those bi-grams and retrieved up to 50 news items per bi-gram phrase.
We called it "noisy-search" because it is assumed the positive bi-grams (e.g. "profit rose" , "growth net") give rise to positive examples whereas negative bi-grams (e.g. "loss increase", "share loss") result in negative examples but note that we didn't test for the validity of this assumption (hence: noisy-search)

For each article we kept the title + excerpt and labeled it according to pre-assumptions on class associations.

We then trained the same model on the noisy data and apply it to an held-out test set from the original data set split.

Training with couple of thousands noisy "positives" and "negatives" examples yielded a test set accuracy of about 95%.

It shows that by automatically collecting noisy examples using search we can boost accuracy performance from about 88% to more than 95%.

Accuracy results for Logistic Regression (LR) and BERT (base-cased) are shown in the attached pdf:

https://drive.google.com/file/d/1MI9gRdppactVZ_XvhCwvoaOV1aRfprrd/view?usp=sharing
