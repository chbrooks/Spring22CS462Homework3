### Assignment 3: Natural Language Processing.

#### Due Thursday, March 24, start of class.

The first portions of this assignment are written in a lab format, with a number of tasks to provide you with exposure to NLTK.  Folloeing that are two machine learning problems
to implement.

In order to complete this assignment, you will need NLTK (https://www.nltk.org) (it’s in conda, if you use that).

We’ll be reading from the NLTK book, which can be found here: https://www.nltk.org/book/ (Links to an external site.)

To submit: add code and documents to your GitHub repo for this assignment, along with a submission.py file that  runs your code. There are several places where you're asked to  measure or compare performance.
Please add a document called HW3.pdf to  your repo containing the answers to these questions.

Part 1.  Getting warmed up. These tasks are intended to get you started with NLTK. 

(5 points) Please read chapter 1, sections 1 and 3. Please feel free to skim the parts about Python as necessary. Choose one of the intro texts and compute its lexical diversity.

(5 points) Generate the bigrams for this text.

(10 points) Generate a FreqDist for this text to identify the 50 most common words. Filter the text to lower case, remove non-words and stopwords to see if you can generate a more informative distribution.

(10 points) Please read chapter 2, sections 1 and 2. Choose one of the Gutenberg texts and create a FreqDist with it as you did above.
    Be sure to remove stop words, convert to lower case and remove non-words.

(10 points) Next, create a ConditionalFreqDist (CFD), where the conditions are the fileids in the Gutenberg corpus and the events are the words in Gutenberg.words(), filtered as above to convert to lower case, and remove stop words and non-words.

Part 2: Document clustering. 

In this part, you'll implement the k-means algorithm and use it to classify documents.

We'll use the Brown corpus for this task. 

To begin, select at least 5 categories from the Brown corpus. 

Using the FreqDist object, construct a word vector for each document (strip punctuation, convert to lowercase, and remove stopwords). 
Write a function called k_means that takes as input a list of FreqDist objects and a number (k) of clusters and returns a list of five lists, 
one for each cluster, containing the documents in each cluster, using Euclidean distance as your metric. 

Compute your performance. What fraction of the articles were placed in the proper clusters?  To measure this, for each cluster determine the 
most common category, and then count the fraction of articles in that category.

Compare your performance to that of the [nltk.cluster](https://www.nltk.org/api/nltk.cluster.html) package. 

Part 3: Supervised learning with Naive Bayes.

Clustering is an *unsupervised* algorithm. It constructs a hypothesis using only the relationships within the data.

On the other hand, Naive Bayes is a *supervised* algorithm. It uses labeled training data to try to make generalizations.

Using the same five categories as above, construct a Naive Bayes classifier. You will probably want to re-use your FreqDist vectors from before.

Your program should:
Pre-process all the data for each category as above - remove stopwords, punctuation, and convert to lower case.

For each category, construct a FreqDist. You'll use this to compute P(word | category).

Then, implement a function called classify. It should take as input a vector representing an unknown document, and our FreqDists for each  category. 
(Please feel free to use a ConditionalFreqDist here to make things easier.)
It should then compute P(category | word1, word2, ..., wordn) for each category, and return the most likely category.

To test your performance, you'll implement five-fold cross-valudation. (please implement this by hand. I know that sklearn has it built in,
but it's good to do it yourself once.)

Split your articles into five bins, arranged randomly. for i = 1 to 5:
train on 4 bins
test on the 5th bin. What percentage of the articles were classified correctly?
Average these five percentages to get an average accuracy. Report this in your document.
Also, compare your algorithm's performance to the [Naive Bayes classifier included with NLTK:](https://www.nltk.org/api/nltk.classify.naivebayes.html)

Part 4: CS686 students only: Please read [this article](https://thegradient.pub/machine-learning-wont-solve-the-natural-language-understanding-challenge/)
And answer the following questions:
- According to the author, what is the difference between natural language processing and natural language understanding?
- Why  does the author feel that data-driven approaches are not suitable for NLU?
- If we accept the author's premise, what sorts of tasks are then best suited for data-driven approaches to NLP?


