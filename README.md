# Text to Number

Since most of the statistical algorithms, e.g machine learning and deep learning techniques, work with numeric data, therefore we have to convert text into numbers. Several approaches exist in this regard. 

The most famous ones are Bag of Words, TF-IDF, and word2vec. 

Though several libraries exist, such as Scikit-Learn and NLTK, I implemented these techniques from scratch for proper understanding.

## Bag of Words
1. Scrape data
2. Tokenize to sentences and preprocess
3. Tokenize to words, remove stopwords, and create a dictionary of word frequency
4. Fetch 200 most frequent words
5. Vectorize sentences and Create bag of words
    * **Idea**: For each word in the mostfreq dictionary, if the word exists in the sentence, a 1 will be added for the word, else 0 will be added.

### Problem with Bag of Words
It assigns equal value to the words, irrespective of their importance. <br>
For instance, a word appearing in multiple sentences makes it very common. On the other hand, words that only appear in one sentence/document are not. 
<br>
But, essentially, the words that are rare have more classifying power compared to the words that are common, which BOW fails to take into account.

## TF-IDF
**Idea**: The words that are more common in one sentence/document and less common in other sentences/documents should be given higher weights.<br>
**TF** = (Frequency of the word in the sentence) / (Total number of words in the sentence)<br>
**IDF** = log(Total number of sentences (documents))/(Number of sentences (documents) containing the word)<br>

1. Scrape data
2. Tokenize to sentences and preprocess
3. Tokenize to words, remove stopwords, and create a dictionary of word frequency
4. Fetch 200 most frequent words 
5. Find the IDF values for the words
6. Find the TF values for the words
7. Find the TF-IDF values for the words


