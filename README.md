# BR Fake News Detection
Fake news detection with deep learning on texts written in Brazilian Portuguese. All the data used to train and test the models was obtained at: https://github.com/roneysco/Fake.br-Corpus. Two different approaches were tested: one using bag-of-words and another using GloVe word embeddings. 

In the bag-of-words approach, each text was represented by a vector containing the frequecies of the top 1000 most frequent words in the training corpus. Before being processed, the texts were normalized (lowercasing and stemming) and had their stopwords removed. The learning algorithm used was a MLP and the average accuracy of the models in the 10-fold cross-validation was 88,65%.

In the word embeddings approach, each text was represented by a sequence of 100-dimensional GloVe word vectors. The maximum number of tokens allowed in each text was set to 200 - larger texts were truncated. The learning algorithm used was a deep BiLSTM neural network and the average accuracy of the models in the 10-fold cross-validation was 93,56%. Attempts to use the full version of the texts as well as word embeddings of higher dimensions failed due to lack of RAM.

Final results (average performance computed by 10-fold cross-validation):


References:

Monteiro R.A., Santos R.L.S., Pardo T.A.S., de Almeida T.A., Ruiz E.E.S., Vale O.A. (2018) Contributions to the Study of Fake News in Portuguese: New Corpus and Automatic Detection Results. In: Villavicencio A. et al. (eds) Computational Processing of the Portuguese Language. PROPOR 2018. Lecture Notes in Computer Science, vol 11122. Springer, Cham

