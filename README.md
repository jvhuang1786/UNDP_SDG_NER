# UNDP WG 3 SDG Classificaion 
<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/original-15.jpg" width="700"></img>

## Introduction

This project in partnershp with SDG AI Labs aims to use supervised learning models to classify text/articles into the 17 SDGs. 

### Libraries Used


<table>

<tr>
  <td>Data Collection</td>
  <td>Tweepy, Pygoogle, GPT2, GPTNEO</td>
</tr>

<tr>
  <td>Data Visualization</td>
  <td>PyCaret LDA, WordCloud</td>
</tr>

<tr>
  <td>Modeling</td>
  <td>Sklearn Logistic Regression, Word2Vec, Hugging Face, Pytorch</td>
</tr>

</table>


## Data Collection 

Steps of Collected the Data: 

   * GPT2/Neo/Xlmnet Sentence Generation using Hugging Face 
      * [Code](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Sentence_Generation/GPT%20Sentence%20Generation.ipynb)
      * [Data](https://github.com/jvhuang1786/UNDP_SDG_NER/tree/main/Sentence_Generation)
   * Twitter API using Tweepy to collect Tweets #/@ using Keyword List from Ontology 
      * [Code](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Twitter/undpkeywordstwitter.py)
      * [Data](https://github.com/jvhuang1786/UNDP_SDG_NER/tree/main/Twitter/Tweets)
   * Google News Scrape using pygoogle collected news on 17 SDGs 2018-2020
      * [Code](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/SDGGOGNEWSSCRAPER/SDG_news%20Scraper.ipynb)
      * [Data](https://github.com/jvhuang1786/UNDP_SDG_NER/tree/main/SDGGOGNEWSSCRAPER)
  



## Data Visualization and Findings

**Text Preprocessing:**

**Data Distribution**

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Unknown-4.png" width="480"></img>

*TFIDF

*Word2Vec

*BERT

**LDA and Word Cloud:**

* [LDA PyCaret Model](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Twitter/EDA/Cluster_Topic_exploration.ipynb)

* [KMeans Clustering WordCloud](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Twitter/EDA/Kmeans%20Clustering%20of%20Topics.ipynb)

## Modeling 

**Log Reg TFIDF:**

* [Note Book](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Models/Log%20Reg%20Model/Log%20Reg%20Classification.ipynb)

**Log Reg Word2Vec:**

* [Note Book](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Models/Word2vec%20Log%20Reg/word2vec%20Logreg.ipynb)

**BERT Transfer Learning with Hugging Face:**

**Token Distribution**

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Unknown-8.png" width="480"></img>

* [Note Book](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Models/BERT%20Classification/SDG%20BERT%20Classification.ipynb)

## Results

**Log Reg TFIDF:**

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Screen%20Shot%202021-05-11%20at%207.06.20%20PM.png" width="480"></img>

**Log Reg Word2Vec:**

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Screen%20Shot%202021-05-11%20at%207.06.39%20PM.png" width="480"></img>

**BERT Transfer Learning with Hugging Face:**

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Unknown-5.png" width="480"></img>

## Author
* Justin Huang
  Into anime, finance computer vision, and NLP.
  [GitHub: Jvhuang1786](https://jvhuang1786.github.io/)

