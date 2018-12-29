# Machine-Translation-Based-On-RNN-Model
## Introduction
<br/>In this notebook, I will build a deep neural network that functions as part of an end-to-end machine translation pipeline. I completed pipeline will accept English text as input and return the French translation.
- **Preprocess** - I'll convert text to sequence of integers.
- **Models** Create models which accepts a sequence of integers as input and returns a probability distribution over possible translations. After learning about the basic types of neural networks that are often used for machine translation, you will engage in your own investigations, to design your own model!
- **Prediction** Run the model on English text.

## Dataset
<br/>We begin by investigating the dataset that will be used to train and evaluate the pipeline.  The most common datasets used for machine translation are from [WMT](http://www.statmt.org/).  However, that will take a long time to train a neural network on.  We'll be using a dataset we created for this project that contains a small vocabulary.  We'll be able to train our model in a reasonable time with this dataset.
<br/>For comparison, _Alice's Adventures in Wonderland_ contains 2,766 unique words of a total of 15,500 words.

## Preprocess
<br/>For this project, we won't use text data as input to our model. Instead, we'll convert the text into sequences of integers using the following preprocess methods:
<br/>1. Tokenize the words into ids
<br/>2. Add padding to make all the sequences the same length.

### Tokenize
<br/>For a neural network to predict on text data, it first has to be turned into data it can understand. Text data like "dog" is a sequence of ASCII character encodings.  Since a neural network is a series of multiplication and addition operations, the input data needs to be number(s).
<br/>We can turn each character into a number or each word into a number.  These are called character and word ids, respectively.  Character ids are used for character level models that generate text predictions for each character.  A word level model uses word ids that generate text predictions for each word.  Word level models tend to learn better, since they are lower in complexity, so we'll use those.

### Padding
<br/>When batching the sequence of word ids together, each sequence needs to be the same length.  Since sentences are dynamic in length, we can add padding to the end of the sequences to make them the same length.

## Models
<br/><br/>In this section, I will experiment with various neural network architectures.
I will begin by training four relatively simple architectures.
- Model 1 is a simple RNN
- Model 2 is a RNN with Embedding
- Model 3 is a Bidirectional RNN
- Model 4 is an optional Encoder-Decoder RNN
<br/>After experimenting with the four simple architectures, I will construct a deeper architecture that is designed to outperform all four models.

### Model 1: RNN
![RNN](images/rnn.png)
<br/>A basic RNN model is a good baseline for sequence data.

### Model 2: Embedding
![RNN](images/embedding.png)
<br/>You've turned the words into ids, but there's a better representation of a word.  This is called word embeddings.  An embedding is a vector representation of the word that is close to similar words in n-dimensional space, where the n represents the size of the embedding vectors.

### Model 3: Bidirectional RNNs
![RNN](images/bidirectional.png)
<br/>One restriction of a RNN is that it can't see the future input, only the past.  This is where bidirectional recurrent neural networks come in.  They are able to see the future data.

### Model 4: Encoder-Decoder
Time to look at encoder-decoder models.  This model is made up of an encoder and decoder. The encoder creates a matrix representation of the sentence.  The decoder takes this matrix as input and predicts the translation as output.
