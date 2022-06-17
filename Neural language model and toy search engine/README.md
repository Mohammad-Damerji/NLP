Instructions

    Build an LSTM-based language model for a given corpus.

        Software: tokenization etc. with spaCy, neural modeling with Keras.

    Build a simple "search engine" for sentences of the corpus using the LSTM hidden states as representations.

        Recommended software: the Annoy indexer/nearest neighborhood library (https://github.com/spotify/annoy)

Dataset: Brown corpus (available via NLTK).

Details:
Data set

    Use the Brown corpus

    Prepare the data set:

        Assign unique ids to each word in the data set (starting from 1, keep 0 free for empty places)

        Define a number for the maximum input size of the model

    Create a function for converting sentences to id vectors which can be used by the model: string_to_model_input(sentence)

        Input: A string sentence ("This is a sentence.")

        Create word id vectors from the sentence ([3, 5, 8, 6, 1])

        Output: A tuple of 2 vectors: X and Y with length of maximum input size. X will be the ids except the last token ([3, 5, 8, 6, 0, 0, 0]). Y will be the ids except the first token ([5, 8, 6, 1, 0, 0, 0]). Use 0 to fill empty places if there is any.

    Run the function string_to_model_input on all sentences in the corpus to create the X and Y input for training the model.

Language model

    Build a Keras neural network with these layers:

        An Input layer

        An Embeddings layer for dimensionality reduction.

        An LSTM layer (or 2 if you want)

        A Dense layer with a softmax activation for the output.

    Fit the model with the training data.

    Create a function for getting the LSTM cell state: get_cell_state(word_id_vector)

        Input: An input vector which can be used to call the model.

        Output: The cell state vector of the LSTM layer.

Next word prediction

    Create a function: predict_next_word(word_sequence)

        Input: a list of words

        Use the language model for predicting the next word with the highest probability.

        Output: the most likely next word

    Create an input field for reading the word sequence. Put it in a loop, the exit will be the empty string.

    Tokenize the input string and call the predict function.

    Print the input and the predicted output.

Cosine similarity of sentences

    Create a function: cosine_similarity(a,b)

        Input: 2 vectors

        Output: the cosine similarity of the vectors

    Create an input field for reading 2 sentences. Put it in a loop, the exit will be the empty string

    Create input vectors from the sentences and run the language model to get the LSTM cell state (call get_cell_state function). Use the output vectors for the cosine similarity.

    Print the sentences and the result.

Mini search engine

    Use AnnoyIndex for indexing the vectors

    Create cell state vectors from all sentences in the Brown corpus.

    Create an input field for reading the search word sequence. Put it in a loop, the exit will be the empty string.

    Create a cell state vector from the search word sequence.

    Get the 5 nearest neighbors from the index and print them.
