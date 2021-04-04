# BR Fake News Detection
Fake news detection with deep learning on texts written in Brazilian Portuguese. All the data used to train and test the models was obtained at: https://github.com/roneysco/Fake.br-Corpus. Three different approaches were tested: one using bag-of-words, another using GloVe word embeddings and another based on the fine-tuning of a *Bidirectional Encoder Representations from Transformers* (BERT) model. 

### Methodology
In the bag-of-words approach, each text was represented by a vector containing the frequecies of the top 1000 most frequent words in the training corpus. Before being processed, the texts were normalized (lowercasing and stemming) and had their stopwords removed. The learning algorithm used was a MLP and the average accuracy of the models in the 10-fold cross-validation was 88,65%.

In the word embeddings approach, each text was represented by a sequence of 100-dimensional GloVe word vectors. The maximum number of tokens allowed in each text was set to 200 - larger texts were truncated. The learning algorithm used was a deep BiLSTM neural network and the average accuracy of the models in the 10-fold cross-validation was 93,56%.

In the BERT approach, a pre-trained BERT model called [BERTimbau](https://github.com/neuralmind-ai/portuguese-bert) (trained on the Portuguese language) was fine-tuned. The BERT model was responsible for encoding each text in a 768-dimensional vector, while a fully-connected layer with linear activation was responsible for predicting (generating the *logits*) the text's class based on the text's encoding. To train the model (BERT + classifier), 75% of the data (5400 texts) was used. The validation and testing of the model were performed on, respectively, 12.5% (900 texts) and 12.5% (900 texts) of the data. The model was able to achieve an accuracy of 98.44% on the test dataset.

### Results

| Methodology           | Accuracy     | Acc. standard deviation |
| :-------------------: | :----------: | :---------------------: |
| BoW + MLP             |    88.65%    |         1.61%           |
| GloVe 100D + BiLSTM   |    93.56%    |         0.85%           |
| BERTimbau fine-tuned  |  **98.44%**  |           -             |

### References:

Monteiro R.A., Santos R.L.S., Pardo T.A.S., de Almeida T.A., Ruiz E.E.S., Vale O.A. (2018) Contributions to the Study of Fake News in Portuguese: New Corpus and Automatic Detection Results. In: Villavicencio A. et al. (eds) Computational Processing of the Portuguese Language. PROPOR 2018. Lecture Notes in Computer Science, vol 11122. Springer, Cham

Souza, F., Nogueira, R., & Lotufo, R. (2020). BERTimbau: pretrained BERT models for Brazilian Portuguese. In 9th Brazilian Conference on Intelligent Systems, BRACIS, Rio Grande do Sul, Brazil, October 20-23 (to appear).


