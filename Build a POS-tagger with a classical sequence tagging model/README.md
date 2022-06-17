Instructions

    Use ​ spaCy​ for tokenization
    Define an appropriate feature template – use ​spaCy​ for feature extraction
    Build and train a POS-tagger with one of the classical methods discussed in the lecture (​HMM​, ​Maximum Entropy​, CRF​)
        Recommended method: ​CRF​ with the sklearn-crfsuite package.
    Dataset: Brown corpus with the universal tagset (available via NLTK).

Details:

    Download the brown corpus from NLTK.
        Use the tagged sentences with the universal tagset. 
    Write a function (token2features) for the feature extraction.
        The input of this function is some spacy tokens.
        The output is a feature dictionary which contains the features of the current, the previous and the next words. (Or 'BOS' or 'EOS' in case of the first or the last words of the sentences.)
        You can start with the word2features function in the sklearn-crfsuite tutorial but you need to change it as it has string inputs. 
    Build and train a POS tagger with one of the classical methods discussed in the lecture (HMM, Maximum Entropy, CRF). Recommended method: CRF with the sklearn-crfsuite package.
        Use the brown corpus for training your model.
        Use the token2features function to create the features.
        Use the POS tags provided by the brown corpus for the labels.
        Use separate training and testing sets when you build the model.
        Evaluate your POS tagger model. 
    Write a funcion (pos_tagger) which can be called to use your model.
        The input can be one of two types: either "untokenized string sentences" or ['tokenized', 'list', 'of', 'words']. Both need to be handled.
        If the input is a string sentence, use spacy for tokenization but don't use spacy's POS tagger. Use your own model as a POS tagger.
        Call token2features for creating the features.
        The output is a list of POS tags ['DET', 'NOUN', 'VERB', 'NOUN'] or a list of tuples of tagged words: [('The', 'DET'), ('Fulton', 'NOUN'), ('County', 'NOUN'), ('Grand', 'ADJ'), ('Jury', 'NOUN'), ('said', 'VERB'), ...]. 
    Create an input field where a custom text can be typed and when enter is hit, it calls the pos_tagger() function. Display the POS tags.
    Comments are important!
        This assignment will have 5-6 points on comments and explanations out of the 20.
        Write down not just WHAT your code does but WHY you use that solution.
        Use the text cells for comments, don't write comments in the code.
    When you send me your final assignment on Teams, please send me the ipynb file, not the colab link. Colab notebooks are mutable and they are owned by you, not me. I need the immutable file for later reference. You can easily export the ipynb file from Colab.
