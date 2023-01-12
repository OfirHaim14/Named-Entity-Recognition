Implementation of three different modes for the Binary Name Entity Recognition task on tweets data set: 
Simple machine learning model – SVM model 
Simple neural network model 
Bidirectional LSTMs inspired by ELMo
# Preprocessing: 
In order to give the tweets as input to our models the words should be represent as vectors, so every word got embedding by using genism’s pretrained GloVe model.
# Simple machine learning model 
Sklearn SVM with kernel = RBF. 
This model had F1 score of 0.55 on the validation data set.
# Simple neural network model 
Simple neural network with two hidden layers. The input size is two hundred, the first hidden layer size is eighty, the second is twenty and the output size is one (Binary Name Entity Recognition). The activation function is ReLU and the prediction function is Sigmoid to get the probability. The batch size is 64 and the network trained for 10 epochs.
This model had F1 score of 0.5467 on the validation data set.
# Bidirectional LSTMs inspired by ELMo: 
Two layers of bidirectional LSTM which received as input the word embeddings of tweet sequences. The idea behind it is to give contextual representations for each word in the tweet, because a single word can have different tags depending on it’s context. Because the context can be either after the word or before the word using bidirectional LSTM helps to catch both of the contexts. 
After every word got it’s contextual embedding the LSTM model pass the new representation to a fully connected network with two output layers. For better results the model try to predict the exact entity of the word and from it the binary entity. 
# Loss function:
 Weighted combination of two-loss functions, the Cross-Entropy for predicting the exact entity and the Binary Cross-Entropy to predict the binary prediction. The weighted combination is : ƛ*CE + BCE and after a lot of tries the conclusion is that ƛ=2e-1 performs the best.
# F1 score: 
This model had F1 score of 0.65 onthe validation data set.
