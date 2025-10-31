# Azerbaijani-Text-Preprocessing
Data cleaning, sentiment labeling, domain awareness, corpus merging, word embedding, some analysis to gain insight.




# Contents
- [DATA & GOAL](#data--goal)
- [PREPROCESSING](#preprocessing)
- [MINI CHALLENGES](#mini-challenges)
- [DOMAIN AWARE](#domain-aware)
- [EMBEDDING](#embedding)
- [REPRODUCIBILITY](#reproducibility)
- [CONCLUSION](#conclusion)
- [CONTRIBUTORS](#contributors)
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

## MINI CHALLENGES
| Challenge | Implementation | Observation |
|------------|----------------|--------------|
| *Emoji mapping* | EMO_MAP dictionary | Adds emotional hints to text. |
| *Hashtag split* | Regex + camel-case | Handles the words with hastag also separate the words that are written in camelcase. |
| *Negation scope* | _NEG flag for next 3 tokens | Strengthens polarity marking which is also helpful for sentiment labeling|
| *Deasciify* | SLANG_MAP replacement | ≈3 % token correction. |
| *Stopwords* | Manually verified list | Some negative words saved from stopwords intentionally to save labeling accuracy. |


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



## EMBEDDING

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
		Synonyms: W2V=0.355, FT=0.442
		Antonyms: W2V=0.349, FT=0.436
		Separation: W2V=0.007, FT=0.005
		
		== Nearest Neighbors ==
		  W2V NN for 'yaxşı': ['<RATING_POS>', 'iyi', 'yaxshi', 'yaxsı', 'awsome']
		  FT NN for 'yaxşı': ['yaxşıı', 'yaxşıkı', 'yaxşıca', 'yaxş', 'yaxşıya']
		  W2V NN for 'pis': ['vərdişlərə', 'lire', 'kardeşi', 'xalçalardan', 'günd']
		  FT NN for 'pis': ['piis', 'pi', 'pisdii', 'pixlr', 'pisi']
		  W2V NN for 'çox': ['bəyənilsin', 'çoox', 'çöx', 'gözəldir', 'əladir']
		  FT NN for 'çox': ['çoxçox', 'çoxx', 'çoxh', 'ço', 'çoh']
		  W2V NN for 'bahalı': ['yaxtaları', 'metallarla', 'villaları', 'radiusda', 'portretlerinə']
		  FT NN for 'bahalı': ['bahalıı', 'bahalısı', 'bahalıq', 'baharlı', 'pahalı']
		  W2V NN for 'ucuz': ['düzəltdirilib', 'baha', 'qiymete', 'keyfiyetli', 'sududu']
		  FT NN for 'ucuz': ['ucuzu', 'ucuza', 'ucuzdu', 'ucuzluğa', 'ucuzdur']
		  W2V NN for 'mükəmməl': ['möhtəşəmm', 'kəliməylə', 'yaradilanlarin', 'mukəmməl', 'möhdəşəm']
		  FT NN for 'mükəmməl': ['mükəmməll', 'mükəməl', 'mükəmməldi', 'mukəmməl', 'mükəmməlsiz']
		  W2V NN for 'dəhşət': ['xalçalardan', 'birda', 'ayranları', 'açdıq', 'təsirlidi']
		  FT NN for 'dəhşət': ['dəhşətdü', 'dəhşətə', 'dəhşətizm', 'dəhşəti', 'dəhşətdi']
		  W2V NN for '<PRICE>': []
		  FT NN for '<PRICE>': ['cokubse', 'reeceep', 'engiltdere', 'ıngiltere', 'flight']
		  W2V NN for '<RATING_POS>': ['deneyin', 'uygulama', 'süper', 'çook', 'iternetsiz']
		  FT NN for '<RATING_POS>': ['<RATING_NEG>', 'çookk', 'süperr', 'çokk', 'çook']

Word2Vec works by looking at how often words occur in text. 

![Word2Vec Model Architecture](word2vec.png)


FastText, on the other hand, breaks words into smaller parts (subwords). 


![FastText Model Illustration](fastText.png)


![FastText vs Word2Vec Comparison](fastText-vs.-Word2Vec.png)


FastText works better in agglutinative languages ​​like Azerbaijani.

Embedings: 

		https://drive.google.com/drive/folders/1GpbKV5XZH6bMsABkZUf58VEupmi3c7L3?usp=sharing

## REPRODUCIBILITY


[Last version](#lastversion):  

    git clone https://github.com/isoatalay/Ceng442-assignment1-Ismail-Beyhan.git

	
Run Order  ① `data_processing.ipynb` → ② `embedding_training_evaulation.ipynb`.  
  
Why this Order?  
This two-step order enforces *clean data → deterministic training*.

1) **data_processing.ipynb**
   - Reads **data/raw/** and produces *outputs* in data/clean/:
     - Two-column files: cleaned_text, sentiment_value
     - Domain-tagged corpus_all.txt
   - Preprocess multiple Azerbaijani text datasets for sentiment analysis by cleaning, normalizing, and labeling data .
  

2) **embedding_training_evaluation.ipynb**
   - Take the files that are created in data/clean/ (5 Cleaned excel files and corpus_all.txt).
   - Trains Word2Vec/FastText using exactly the cleaned tokens
   - compare both model with some metrics (coverage, synonym/antonym separation, NN lists).
   - Uses fixed *seed (42)* and recorded library versions (Python, gensim, openpyxl, ftfy, Jupyter) for *reproducibility*.



  
- Python 3
- pandas
- regex
- unicodedata
- ftfy
- gensim
- openpyxl
- Jupyter NoteBook


        python3.12.3
        gensim-4.4.0
        openpyxl-3.1.2
        ftfy-6.3.1
        seed = 42
  		jupyter notebook 7.2.2



    
Uploaded the Data folder: inputs in data/raw/, outputs in data/clean/.
Updated all paths to match the data/... structure.
Installed requirements:

        pip install pandas gensim openpyxl regex ftfy scikit-learn

Ran preprocessing to produce data/clean/*_2col.xlsx and data/clean/corpus_all.txt.
Trained Word2Vec and FastText; saved models under embeddings/.

## CONCLUSION

In this project, we compare the Word2Vec and FastText models.
The results show that these two models have different characteristics in terms of word similarity and nearest neighbors.

The FastText model focuses on the roots and affixes of words, and it can easily capture variations such as “yaxşıı”, “pisdii”, and “çoxx”.
On the other hand, the Word2Vec model focuses on meaning and can easily capture semantically similar words like “iyi”, “süper”, and “gözəldir”.

When we look at the overall results, FastText gives slightly higher similarity values.
This shows that FastText is more sensitive to morphological and spelling differences.

In general:
	•	Word2Vec performs better at capturing semantic similarities.
	•	FastText performs better at capturing morphological variations in words.

At the end of the project, we can say that languages like Azerbaijani and Turkish are better suited to the FastText model.
The Word2Vec model, on the other hand, provides advantages in capturing meaningful relationships between words.

## CONTRIBUTORS
- [@Beyhan Kandemir](https://github.com/Beykn) 
- [@İsmail Atalay](https://github.com/isoatalay)



## ACKNOWLEDGMENT

This project is part of the Natural Language Processing course.

We would like to thank  Yusuf Evren AYKAÇ for his guidance . We also referred to the paper “The Art of Natural Language Processing: Classical, Modern and Contemporary Approaches to Text Document Classification” for theoretical background and help to understanding NLP fundemantals.
