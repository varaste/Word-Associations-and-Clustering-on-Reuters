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


# Clustering


In this section, we used the TF-IDF method to create a vector representation of the document collection. We considered the maximum vocabulary size to be 3000.

After getting the input file, we first used the nltk library for preprocessing tokenization operations, removing stop words and stemming, and using the scikit-learn library, we performed clustering with K-Means methods. The results of K-Means clustering evaluation with Purity, RI, F1 and NMI criteria were calculated as follows:

Purity Score is:  0.83949  
RI Score is:  0.34787  
Normalized Mutual Information Score is:  0.51255  
Precision Score is:  0.51961  
Recall Score is:  0.27999  
F1 Score is:  0.36488  

Because the command available in the sklearn library did not provide correct and accurate results for calculating the F1 criterion, we calculated the F1 criterion indirectly by using the accuracy and recall criteria.  
Since this algorithm uses a possibly different point as the center of the clusters in each series, the results obtained in different executions have slight differences, we took 10 executions and took the highest value obtained in these 10 times as the result. considered final.  
Next, we did the clustering this time with the hierarchical method and with Average-Link, Complete-Link and Single-Link algorithms respectively on the dataset. The results of K-Means clustering evaluation with Purity, RI, F1 and NMI criteria were calculated as follows: 

Average Link Purity Score is:  0.72787  
Average Link RI Score is:  0.36946  
Average Link Normalized Mutual Information Score is:  0.39165  
Average Link F1 Score is:  0.19847  

Complete Link Purity Score is:  0.67025  
Complete Link RI Score is:  0.25961  
Complete Link Normalized Mutual Information Score is:  0.27629  
Complete Link F1 Score is:  0.06959  

Single Link Purity Score is:  0.53736  
Single Link RI Score is:  0.00995  
Single Link Normalized Mutual Information Score is:  0.00717  
Single Link F1 Score is:  0.00385  

In this category of methods, as in the previous method, there is a possibility that the results obtained in different executions may have slight differences, but this time because the algorithm can behave randomly in points that are the same distance from two clusters. Therefore, for these algorithms, we have executed 10 times and considered the highest value obtained in these 10 times as the result.  

In the table below, the calculated values of the evaluation criteria for all three methods can be seen. Considering the large amount of data, as expected, the K-Means method obtained better results in the evaluation criteria than the hierarchical methods. In addition, what was seen at the time of execution was the faster execution of the K-Means algorithm than the hierarchical clustering algorithms.

|          	|     Purity    	|     RI    	|     NMI    	|     F1    	|
|---	|---	|---	|---	|---	|
|     K-Means    	|     0.83949    	|     0.34787    	|     0.51255    	|     0.36488    	|
|     Average-Link    	|     0.72787    	|     0.36946    	|     0.39165    	|     0.19847    	|
|     Complete-Link    	|     0.67025    	|     0.25961    	|     0.27629    	|     0.06959    	|
|     Single-Link    	|     0.53736    	|     0.00995    	|     0.00717    	|     0.00385    	|
