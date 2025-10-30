# Azerbaijani-Text-Preprocessing
Data cleaning, sentiment labeling, domain awareness, corpus merging, word embedding, some analysis to gain insight.

## ABSTRACT
The purpose of this work is to understand the basics of Natural Language Processing (NLP). In this project, we gained experience in data preprocessing, sentiment annotation, and word embedding. We used two different embedding models and analyzed their outputs on Azerbaijani language datas.

	•	Data cleaning, normalization, and sentiment labeling
	•	Domain-aware preprocessing (news, social, reviews)
	•	Merging datasets into a single corpus
	•	Training Word2Vec and FastText models
	•	Comparing their performance using lexical coverage, synonym/antonym similarity, and nearest-neighbor quality

# Contents
- [SETUP](#setup)
- [DATASETS](#datasets)
- [DOCUMENTATION](#documentation)
- [CONTRIBUTORS](#contributers)
- [ACKNOWLEDGMENT](#acknowledgment)

## SETUP 
[Last version](#lastversion):  

    git clone https://github.com/isoatalay/Ceng442-assignment1-Ismail.git

- Python 3
- pandas
- regex
- unicodedata
- ftfy
- gensim
- openpyxl

Install essentials:

    pip install pandas gensim openpyxl regex ftfy scikit-learn

## DATASETS
https://drive.google.com/file/d/1_nLlOQV1cYFHyN69fkYnnA5Grq-TvPtY/view?usp=sharing

## DOCUMENTATION
> Text Normalization: normalize_text_az()

> Domain Detection: detect_domain()

> Domain-Specific Normalization: domain_specific_normalize()

> Domain Tag Token: add_domain_tag()

> Sentiment Label Mapping: map_sentiment_value()

> Per-File Processing: process_file()

> Corpus Builder: build_corpus_txt()

> Embedding Training (Word2Vec & FastText)

> Model Comparison

![Word2Vec Model Architecture](word2vec.png)
![FastText Model Illustration](fastText.png)
![FastText vs Word2Vec Comparison](fastText-vs.-Word2Vec.png)
## CONTRIBUTORS
Beyhan Kandemir

İsmail Atalay

## ACKNOWLEDGMENT

This project is part of the Natural Language Processing course.

We would like to thank  Yusuf Evren AYKAÇ for his guidance . We also referred to the paper “The Art of Natural Language Processing: Classical, Modern and Contemporary Approaches to Text Document Classification” for theoretical background and help to understanding NLP fundemantals.
