# Named-Entity-Recognition
Implementation of three different models for the Binary Name Entity Recognition task on tweets data set:  
Simple machine learning model – SVM model  
Simple neural network model  
Bidirectional LSTMs inspired by ELMo  
## Preprocessing: 
In order to give the tweets as an input to our models the words of the tweet should be represented as vectors, therefore every word got vector embedding by using genism’s pre-trained GloVe model.
## Simple machine learning model 
Sklearn SVM with kernel = RBF. 
This model had an F1 score of 0.55 on the dev data set.
## Simple neural network model 
Simple neural network with two hidden layers. The input size is two hundred, the size of the first hidden layer is eighty, the size of the second is twenty and the output size is one (Binary Name Entity Recognition). The activation function is ReLU and the prediction function is Sigmoid for getting the probability. The batch size is 64 and the network is trained for 10 epochs.
This model had an F1 score of 0.5467 on the dev data set.
## Bidirectional LSTMs inspired by ELMo: 
Two layers of bidirectional LSTM. The LSTM network receives as an input the words’ embeddings of the tweet sequences. The idea behind it is to give contextual representations for each word in the tweet because a single word can have different tags depending on its context. Because the context can be either after the word or before the word using bidirectional LSTM helps to catch both contexts. 
After every word got its contextual embedding the LSTM model passes the new representation to a fully connected network with two output layers. For better results, the model tries to predict the exact entity of the word and from it the binary entity. 
### Loss function:
 A weighted combination of two-loss functions, the Cross-Entropy for predicting the exact entity and the Binary Cross-Entropy to predict the binary prediction. The weighted combination is ƛ*CE + BCE and after a lot of tries, the conclusion is that ƛ=2e-1 performs the best.
### F1 score: 
This model had an F1 score of 0.65 on the dev data set.
