# Listen_Attend_Spell
This project is based on the following work: https://arxiv.org/pdf/1508.01211.pdf
Listen, Attend and Spell (LAS), is a neural network that learns to transcribe speech utterances to characters. Unlike traditional DNN-HMM models, this model learns all the components of a speech recognizer jointly. Our system has two components: a listener and a speller. The listener is a pyramidal recurrent network encoder that accepts filter bank spectra as inputs. The speller is an attentionbased recurrent network decoder that emits characters as outputs. The network produces character sequences without making any independence assumptions between the characters. This is the key improvement of LAS over previous end-toend CTC models. 

# RESULTING ATTENTION PLOT
Near convergence of training, the attention curve looks as below:


![---](attention_plot.jpg)


The Seq2Seq model has an encoder part which comprises of 1 BiLSTM layer, 3 PbLSTM layers. The key and values each have a hidden dimension of 256 neurons. The decoder part has dynamic teacher forcing with 2 LSTM layers. Furthermore, the context and the query of the network are each passed through a linear, ReLU and BachNorm layer before passing into the final classification layer. Various regularization techniques like weight dropout and locked dropout have been used. Crossentropy loss is used for this model. Attention based context has been used in this model.
The training is done for a total of 41 epochs with Adam optimizer with a learning rate of 1e-3. A batch size of 64  has been used for training with a validation metric called Levenshtein distance.

The final Levenshtein distance was found to be 16.98
