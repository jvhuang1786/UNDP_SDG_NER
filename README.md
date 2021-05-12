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


**Data Distribution**

Tweet Distribution collection of the SDGs

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Unknown-4.png" width="550"></img>


**Text Preprocessing:**

  **TFIDF**

```python

def clean_tweet(df):
    """function first creates a copy. Then cleans up text for http, @, ampersands, and clears for punctuations.  Then lemmatizes, tokenizes.
    """
    import re 
    
    df = df.copy()
    
    #decontract
    df = df.apply(decontracted)
    #clean up https,@, &amp
    df = df.apply(lambda x: re.sub(r"http\S+","", x.lower()),1)\
    .apply(lambda i: " ".join(filter(lambda x: x[0]!="@", i.split())),1)\
    .apply(lambda x: re.sub(r"&amp", "",x),1)\
    .apply(lambda x: re.sub(r"&amp;","",x))\
    .apply(lambda x: re.sub(r'[_"\-;%()|+&=*%.,!?:#$@\[\]/]', ' ', x),1)
    
    #lemmatize
    df = df.apply(lambda x: lemm.lemmatize(x))
    
    #tokenize
    df = df.apply(lambda x: tknzr.tokenize(x))
    df = df.apply(lambda x: ' '.join(x))
    return df

```


  **Word2Vec**

```python

def clean_text(df):
    import re
    df = df.copy().reset_index(drop = True)
     
    #decontract
    df = df.apply(decontracted)
    
    df = df.apply(lambda x: re.sub(r"http\S+", "", x), 1)\
.apply(lambda i: " ".join(filter(lambda x:x[0]!="@", i.split())), 1)\
.apply(lambda x: re.sub(r"&amp", "",x),1)\
.apply(lambda x: re.sub(r"&amp;", "",x),1)\
.apply(lambda x: str(x).lower()).replace('\\', '').replace('_', ' ')\
.apply(lambda x: re.sub(r'[_"\-;%()|+&=*%.,!?:#$@\[\]/]', ' ', x),1)

    return df

```

  **BERT**

```python

def clean_text(df):
    import re
    df = df.copy().reset_index(drop = True)
    df = df.apply(lambda x: re.sub(r"http\S+", "", x), 1)\
.apply(lambda i: " ".join(filter(lambda x:x[0]!="@", i.split())), 1)\
.apply(lambda x: re.sub(r"&amp", "",x),1)\
.apply(lambda x: re.sub(r"&amp;", "",x),1)
    return df

```

**LDA and Word Cloud:**

* [LDA PyCaret Model](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Twitter/EDA/Cluster_Topic_exploration.ipynb)

* [KMeans Clustering WordCloud](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Twitter/EDA/Kmeans%20Clustering%20of%20Topics.ipynb)

Kmeans Word Cloud 17 SDGS

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Unknown.png" width="400"></img>

Industry and Infrastructure SDG 9 WordCloud

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Unknown-2.png" width="300"></img>

Responsible Consumption and Production SDG 12 WordCloud

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Unknown-3.png" width="300"></img>


## Modeling 

**Log Reg TFIDF:**

* [Note Book](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Models/Log%20Reg%20Model/Log%20Reg%20Classification.ipynb)

**Log Reg Word2Vec:**

* [Note Book](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Models/Word2vec%20Log%20Reg/word2vec%20Logreg.ipynb)

**BERT Transfer Learning with Hugging Face:**

**Token Distribution** - 100 Tokens used for Tweet BERT model with Case since HI!!! and hi. could mean different things. 

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Unknown-8.png" width="480"></img>

* [Note Book](https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/Models/BERT%20Classification/SDG%20BERT%20Classification.ipynb)

## Results

**Log Reg TFIDF:**

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Screen%20Shot%202021-05-11%20at%207.06.20%20PM.png" width="200"></img>

**Log Reg Word2Vec:**

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Screen%20Shot%202021-05-11%20at%207.06.39%20PM.png" width="200"></img>

**BERT Transfer Learning with Hugging Face:**

BERT SDG Confusion Matrix


<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Unknown-5.png" width="600"></img>


Tweet:

    You have to agree with The on this, I DON'T agree on EVERYTHING the
    GOP has to say much ANYMORE. But I have to admit that condemning China
    for what they're currently going would've been a lot BETTER than what
    he said that day.

    True SDG: 14
    
Prediction:

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Unknown-6.png" width="400"></img>

Tweet:

Prediction:

<img src="https://github.com/jvhuang1786/UNDP_SDG_NER/blob/main/images/Unknown-7.png" width="400"></img>



## Author
* Justin Huang
  Into anime, finance computer vision, and NLP.
  [GitHub: Jvhuang1786](https://jvhuang1786.github.io/)

