# Reddit Webscraping & NLP

### Description


This project involves scraping through two subreddits(r/declutter and r/minimalism) and applyting Natural language Processing (NLP) techniques. Both the subreddits have similar theme of intention lifestyle, yet they are different in the practices they use. 

Declutter fouses on reducing clutter  and organising spaces whereas Minimalism focuses on living with less.



Problem Statement : This project aims to scrap through two subreddits(Declutter and Minimalism) and apply Natural language Processing (NLP) techniques to build a supervised ML model that predicts if the post belongs to subreddit Declutter or Minimalism, with high accuracy, despite their similarities and differences. 

This is for my fellow data scientists to show the steps I have taken in order to come to the conclusion.
The key steps are listed below:


1. [Data Collection](#Data-Collection)
2. [Data Preprocessing](#Data-Preprocessing)
3. [Feature Extraction](#Feature-Extraction)
4. [Model Building and Evaluation](#Model-Building-and-Evaluation)
5. [Conclusion](#Conclusion)


The success of my project will be evaluated based on accuracy score.

## Data Collection
The data is collected using PRAW; Reddit's own webscraper. The goal was to get 1000 posts from each subreddit. I used .new method to get all data from the year 2024 to present. This resulted in data just shy of 1000. I then scraped through top post in previous years to get the data. Once that was done, I created a 2000 line csv file by filtering the data based on the time posted i.e. taking the most recent ones. I used the text part for all of my analysis and none of the title. 

# Data Dictionary


| Column                                                | Dtype   | Description                                                                                  |
| ----------------------------------------------------- | ------- | -------------------------------------------------------------------------------------------- |
| title                                    | object  | The title of reddit post                                         |
| text                                        | object  | The body of the post                                         |
| subreddit                                       | object  | The name of subreddit                                          |
| created_utc                                        | float64   | Timestamp when the post was created in UTC       |                                          

---

## Data Preprocessing
My preprocessing included finding the top words from each of the subreddit. They mostly included common englis words demonstrating the need for stemming or lemmatizing and also using stop words. I used WordNetLemmatizer to lemmatize the text and checked the new top words. I then created a new csv with added column of those lemmatized words. My preprocessing also involved checking for nulls, which I removed. 

---

## Feature Extraction
I used TF-IDF (Term Frequency-Inverse Document Frequency) Vectorizer for feature engineering to transform the text data to transform into numerical data. This will measure how frequently the word appears in the document and show the importance of the words. 

---

## Model Building and Evaluation

I built 2 models, one Logistic Regression Model and a Multinomial Naive Bayes (MultinomialNB) model both tested with GridSearch. 
My logistic Regression Model has an accuracy of 77% i.e. my model correctly predicted the subreddit that it belongs to 77% of the time.
With that I also found out the precision ,recall and f1-score.
precision: When the model predicted Declutter, it was correct 76% of the time i.e. 14% of time it belonged to minimalism(False Positives). When the model predicted Minimalism, it was correct 80% of the time i.e. 20% of time it belonged to declutter(False Positives)

---

## Conclusion and Recommendation

1. I suggest using Logistic Regression to see top words used in predicting.
2.  To further refine the model, we could use PorterStemmer instead to bring words to it's root form aggressively, this would allow words like e.g. minimalism, minimalist, minimal to bring to one root form for better count.
3. Exploring other techniques like Random Forest, Gradient Boosting or SVM to check for better accuracy.
   
---

