# UNDP WG 3 SDG Classificaion 
<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/original-15.jpg" width="480"></img>

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

**LDA and Word Cloud:**

     
     
## Modeling 

**Log Reg TFIDF:**

* [Note Book](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Models/Log%20Reg%20Model/Log%20Reg%20Classification.ipynb)

**Log Reg Word2Vec:**

* [Note Book](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Models/Word2vec%20Log%20Reg/word2vec%20Logreg.ipynb)

**BERT Transfer Learning with Hugging Face:**

* [Note Book](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Models/BERT%20Classification/SDG%20BERT%20Classification.ipynb)

## Results

## Author


* Justin Huang
  Into anime, finance computer vision, and NLP.
  [GitHub: Jvhuang1786](https://jvhuang1786.github.io/)

