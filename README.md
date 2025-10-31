# Azerbaijani-Text-Preprocessing
Data cleaning, sentiment labeling, domain awareness, corpus merging, word embedding, some analysis to gain insight.




# Contents
- [DATA & GOAL](#datagoal)
- [PREPROCESSING](#preprocessing)
- [DOMAIN AWARE](#domainaware)
- [EMBEDING](#embeding)
- [REPRODUCIBILITY](#reproducibility)
- [CONCLUTION](#conclution)
- [CONTRIBUTORS](#contributers)
- [ACKNOWLEDGMENT](#acknowledgment)

## DATA & GOAL
The purpose of this work is to understand the basics of Natural Language Processing (NLP). In this project, we gained experience in data preprocessing, sentiment annotation, and word embedding. We used two different embedding models and analyzed their outputs on Azerbaijani language datas.

	•	Data cleaning, normalization, and sentiment labeling
	•	Domain-aware preprocessing (news, social, reviews)
	•	Merging datasets into a single corpus
	•	Training Word2Vec and FastText models
	•	Comparing their performance using lexical coverage, synonym/antonym similarity, and nearest-neighbor quality

Data:

        https://drive.google.com/file/d/1_nLlOQV1cYFHyN69fkYnnA5Grq-TvPtY/view?usp=sharing


## PREPROCESSING
> Text Normalization :

In this part we gain to make a text meaningful and consistent . So model can train it easly. In this way  kind a models like Word2Vec, FastText etc. can established semantic relationship. We also create a domain awareness in this section to help the model detect and distinguish different contexts such as “news language,” “social media language,” and “product review language.”


## DOMAIN AWARE

Domain Detection: The model learns the meanings of words based on the text type.
Domain-Specific Normalization: This allows the model to recognize semantics, not numerical or formal meanings. This allows the model to match hints with emotional meanings.
Domain Label Symbol: This helps understand the different meanings of words, as sometimes the same words have different meanings (e.g., negative or positive).

We used the different datasets and than standardizes labels from different datasets into a uniform numeric sentiment value  (Negative = 0.0, Neutral = 0.5, Positive = 1.0) for training.



        Saved: data/clean/labeled-sentiment_2col.xlsx (rows=2955)
        Saved: data/clean/test__1__2col.xlsx (rows=4198)
        Saved: data/clean/train__3__2col.xlsx (rows=19557)
        Saved: data/clean/train-00000-of-00001_2col.xlsx (rows=41756)
        Saved: data/clean/merged_dataset_CSV__1__2col.xlsx (rows=55662)
        Wrote data/clean/corpus_all.txt with 124353 lines

> Per-File Processing & Corpus Builder: 

We read the data files and performed the necessary cleaning, normalization, and labeling. As a result, we obtained the cleaned_text and sentiment_value values. To prevent the model from learning the same data over and over, we remove useless columns, null cells and duplicates to create a single corpus. This resulted in a clean and consistent text for model training.



## EMBEDING

We trained Word2vec (Skip-gram) and FasTest models using this dataset. The analysis shows that FastTest is better at grouping synonyms, but both models still struggle to distinguish antonyms.

        Exception ignored in: 'gensim.models.word2vec_inner.our_dot_float'
        Exception ignored in: 'gensim.models.word2vec_inner.our_dot_float'
        Exception ignored in: 'gensim.models.word2vec_inner.our_dot_float'
        Exception ignored in: 'gensim.models.word2vec_inner.our_dot_float'
        Exception ignored in: 'gensim.models.word2vec_inner.our_dot_float'
        Exception ignored in: 'gensim.models.word2vec_inner.our_dot_float'
        Exception ignored in: 'gensim.models.word2vec_inner.our_dot_float'
        Exception ignored in: 'gensim.models.word2vec_inner.our_dot_float'
        Saved Word2Vec model


        Exception ignored in: 'gensim.models.word2vec_inner.our_dot_float'
        Exception ignored in: 'gensim.models.word2vec_inner.our_dot_float'
        Exception ignored in: 'gensim.models.word2vec_inner.our_dot_float'
        Exception ignored in: 'gensim.models.word2vec_inner.our_dot_float'
        Saved FaxtText model

        == Lexical coverage (per dataset) ==
        data/clean/labeled-sentiment_2col.xlsx: W2V=0.932, FT(vocab)=0.932
        data/clean/test__1__2col.xlsx: W2V=0.987, FT(vocab)=0.987
        data/clean/train__3__2col.xlsx: W2V=0.990, FT(vocab)=0.990
        data/clean/train-00000-of-00001_2col.xlsx: W2V=0.943, FT(vocab)=0.943
        data/clean/merged_dataset_CSV__1__2col.xlsx: W2V=0.949, FT(vocab)=0.949


                == Similarity ==
                
        Synonyms: W2V=0.364, FT=0.439
        Antonyms: W2V=0.328, FT=0.408
        Separation: W2V=0.036, FT=0.032

                == Nearest Neighbors ==
        W2V NN for 'yaxşı': ['yaxshi', '<RATING_POS>', 'iyi', 'yaxsı', 'artsa']
        FT NN for 'yaxşı': ['yaxşıı', 'yaxşıkı', 'yaxşıca', 'yaxş', 'yaxşıya']
        W2V NN for 'pis': ['bugunki', 'günd', '<RATING_NEG>', 'yaxşıdır_NEG', 'xalçalardan']
        FT NN for 'pis': ['piis', 'pi', 'pisdii', 'pixlr', 'pisleşdi']
        W2V NN for 'çox': ['çoox', 'çöx', 'gözəldir', 'bəyənilsin', 'cooxx']
        FT NN for 'çox': ['çoxçox', 'çoxx', 'çoxh', 'ço', 'çoh']
        W2V NN for 'bahalı': ['villaları', 'portretlerinə', 'yaxtaları', 'metallarla', 'radiusda']
        FT NN for 'bahalı': ['bahalıı', 'bahalısı', 'bahalıq', 'baharlı', 'pahalı']
        W2V NN for 'ucuz': ['şeytanbazardan', 'düzəltdirilib', 'qiymete', 'elektik', 'qiymətə']
        FT NN for 'ucuz': ['ucuzu', 'ucuza', 'ucuzdu', 'ucuzluğa', 'ucuzdur']
        W2V NN for 'mükəmməl': ['kəliməylə', 'möhtəşəmm', 'mukəmməl', 'tamamlayır', 'süjetli']
        FT NN for 'mükəmməl': ['mükəmməll', 'mükəməl', 'mukəmməl', 'mükəmməldi', 'mükəmməlsiz']
        W2V NN for 'dəhşət': ['xalçalardan', 'birda', 'ayranları', 'yelləndi', 'treylerdə']
        FT NN for 'dəhşət': ['dəhşətdü', 'dəhşətə', 'dəhşəti', 'dəhşətizm', 'dəhşətdi']
        W2V NN for '<PRICE>': []
        FT NN for '<PRICE>': ['cruise', 'recebzade', 'reeceep', 'light', 'cokubse']
        W2V NN for '<RATING_POS>': ['deneyin', 'uyqulama', 'internetli', 'uygulama', 'hak']
        FT NN for '<RATING_POS>': ['<RATING_NEG>', 'süperr', 'çookk', 'cöx', 'süper']

Word2Vec works by looking at how often words occur in text. 

![Word2Vec Model Architecture](word2vec.png)
FastText, on the other hand, breaks words into smaller parts (subwords). 
![FastText Model Illustration](fastText.png)
![FastText vs Word2Vec Comparison](fastText-vs.-Word2Vec.png)

FastText works better in agglutinative languages ​​like Azerbaijani.

## REPRODUCIBILITY


[Last version](#lastversion):  

    git clone https://github.com/isoatalay/Ceng442-assignment1-Ismail.git

- Python 3
- pandas
- regex
- unicodedata
- ftfy
- gensim
- openpyxl


        python3.12
        gensim-4.4.0
        openpyxl-3.1.5
        ftfy-6.3.1
        seed = 42



    
Uploaded the Data folder: inputs in data/raw/, outputs in data/clean/.
Updated all paths to match the data/... structure.
Installed requirements:

        pip install pandas gensim openpyxl regex ftfy scikit-learn

Ran preprocessing to produce data/clean/*_2col.xlsx and data/clean/corpus_all.txt.
Trained Word2Vec and FastText; saved models under embeddings/.

## CONTRIBUTORS
- [@Beyhan Kandemir](https://github.com/Beykn) 
- [@İsmail Atalay](https://github.com/isoatalay)



## ACKNOWLEDGMENT

This project is part of the Natural Language Processing course.

We would like to thank  Yusuf Evren AYKAÇ for his guidance . We also referred to the paper “The Art of Natural Language Processing: Classical, Modern and Contemporary Approaches to Text Document Classification” for theoretical background and help to understanding NLP fundemantals.
