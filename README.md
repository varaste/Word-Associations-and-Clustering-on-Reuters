# Word-Associations-and-Clustering-on-Reuters

In this project, we use a part of the Reuters news dataset. This collection contains 5501 news documents, each of which is placed in one of the ten categories below.
- acquisitions
- corn 
- crude 
- earn 
- grain 
- interest 
- money-fx 
- ship
- trade 
- wheat

The given file format is CSV. Each line contains ID, news text and news category.

# Word Associations

Here, the goal is to extract syntagmatic and paradigmatic relationships between words using Mutual Information (MI). We first extract (MI with smoothing) between words to implement these relationships. Cosine similarity is used for vector similarity measurement. 

To find the paradigmatic relationship, we obtain the context vector of the words using Mutual Information. Then we obtain the similarity of the context vector of the words (cosine similarity).

First, we perform the pre-processing steps as follows and show the steps with an example on document number 8710:
First, we tokenize the input text, which is as follows, using the nltk library:

![Tokenization](https://github.com/varaste/Word-Associations-and-Clustering-on-Reuters/blob/main/assets/Arya-Varaste-8710.png)

To be as follows:

![Tokenization](https://github.com/varaste/Word-Associations-and-Clustering-on-Reuters/blob/main/assets/Arya-Varaste-Tokenization.png)

After removing the stop words, we write the letters in small letters and perform stemming with PorterStemmer using the nltk library to get the following text:

![Tokenization](https://github.com/varaste/Word-Associations-and-Clustering-on-Reuters/blob/main/assets/Arya-Varaste-Stemm-Stop-word.png)

After we convert the data of all the documents into bags of words, we obtain Syntagmatic Associations for the words using the commands available in the scikit-learn library.
The 30 most repeated words in the entire text can be seen in the chart below:


![Tokenization](https://github.com/varaste/Word-Associations-and-Clustering-on-Reuters/blob/main/assets/Arya-Varaste-30-most-frequent-words-in-text.png)



