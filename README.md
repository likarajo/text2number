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

### Problems with TF-IDF and Bag of Words Approach
* Words are treated individually and every single word is converted into its numeric counterpart. 
* The context information of the word is not retained. <br>

For instance: Consider two sentences "big red machine and carpet" and "big red carpet and machine". If you use a bag of words approach, you will get the same vectors for these two sentences. However, we can clearly see that in the first sentence we are talking about a "big red machine", while the second sentence contains information about the "big red carpet". Hence, context information is very important.

## N-grams
**Idea**: Capture the context information. 
* A contiguous sequence of N items from a given sample of text or speech. 
* An item can be a character, a word or a sentence and N can be any integer. 
* When N is 2, we call the sequence a bigram. Similarly, a sequence of 3 items is called a trigram, and so on.

### Connection of N-Grams with Markov Chains
A **Markov chain** is a sequence of states. 
* With 2 states, X and Y, in a Markov chain, you can either stay at one state or move to the other state. The probability of moving from X to Y is 50% and similarly, the probability of staying at X is 50%. Likewise, the probability of staying at Y is 50% while the possibility of moving back to X is also 50%. This way a Markov sequence can be generated, such as XXYX, etc.
* In an N-Grams model, an item in a sequence can be treated as a Markov state.

1. Scrape data
2. Only keep letters, periods, and spaces
3. Create N-grams dictionary
    * character tri-gram (3-gram)
    * Ngrams as keys, and the corresponding characters which occur after the ngrams in the text, as values.