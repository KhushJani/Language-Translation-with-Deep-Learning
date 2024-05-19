# Language-Translation-with-Deep-Learning

### Project Overview
This project focuses on creating a Recurrent Neural Network (RNN) sequence-to-sequence model using Keras to translate text from one language to another.

### Languages and Dataset
In this project, we translate English to French, leveraging the flexibility of our model to support any language pair (e.g., English to French). We utilize the [ANKI dataset](https://www.manythings.org/anki/).

### What is Sequence-to-Sequence Learning?
Sequence-to-sequence (Seq2Seq) learning involves training models to transform sequences from one domain into sequences in another domain. The process is as follows:

  1.  Input and Target Sequences: Begin with sequences in the source language (e.g., English) and their corresponding sequences in the target language (e.g., French).
  2.  Encoding: An encoder LSTM processes the input sequences into two state vectors (retaining only the final LSTM state).
  3.  Decoding: A decoder LSTM is trained to generate target sequences offset by one timestep, a method known as "teacher forcing." The decoder uses the encoder's state vectors as its initial state, learning to         predict future tokens based on past tokens and the encoded input sequence.

### Inference Process
For decoding new input sequences:

1.  Encode: Convert the input sequence into state vectors.
2.  Initialize: Start with a single start-of-sequence token.
3.  Predict: Use the decoder to predict the next character, based on the state vectors and the initial token.
4.  Sample: Select the next character (using argmax).
5.  Repeat: Add the predicted character to the sequence and repeat until the end-of-sequence token is generated or a predefined length limit is reached.

### LSTM vs. GRU
By default, the model employs Long Short-Term Memory (LSTM) cells. However, users can opt for Gated Recurrent Unit (GRU) cells, which have a simpler structure with a single gate, potentially speeding up the training process.

Results
While this system doesn't yet match the accuracy of Google Translate, it performs well on short sentences after 20 epochs:

* Input: "I love you."
    * Output: "Je t'aime !" (Accurate)
* Input: "We studied."
    * Output: "Nous étudions." (Accurate)
* Input: "I slept well."
    * Output: "J'ai dormi toute la journée." (Similar meaning, but not entirely accurate; correct translation: "j'ai bien dormi")
* Input: "He worked a lot."
    * Output: "Il a travaillé pour un homme riche." (Incorrect translation)

### Conclusion
Our model has grasped basic English/French translation concepts, but improvements are needed:

### Extended Training: More training time is required.
*  Enhanced Architecture: Incorporating additional LSTM layers could improve performance.
