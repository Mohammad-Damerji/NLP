Instructions

Implement 3 NN models in Keras. Their structures are similar, they differ in how their embedding layer is initialized. The structure of the models is this: 

    Embedding layer

    Pooling layer (GlobalMaxPool1D or GlobalAveragePooling1D)

    Dense (for classification)

Train all 3 models and evaluate. Compare their performances.
Dataset

Stanford Large Movie Review Dataset: https://ai.stanford.edu/~amaas/data/sentiment/

Use​ spaCy​ for tokenization.
1. Build a model without pretrained embeddings

The input is a fixed size, right aligned word id vector. The size is your choice, depending on the corpus.

The output is one of “positive” or “negative”, one-hot encoded.

Example training data:

>>> x_train[:5]

array([[ 0, 0, 0, ..., 3, 391, 4348], [ 0, 0, 0, ..., 71, 11, 28], [ 0, 0, 0, ..., 27, 32, 8058], [ 0, 0, 0, ..., 7, 7, 1456], [ 0, 0, 0, ..., 78, 10, 121]], dtype=int32)

>>> y_train[:5]

array([[0., 1.], [1., 0.], [0., 1.], [1., 0.], [1., 0.]], dtype=float32)
2. Build a model with pretrained fastText​ embeddings

Initialize the Embedding layer with fastText word vectors. You can download it from here: https://fasttext.cc/docs/en/english-vectors.html. For performance reasons keep only the vectors belonging to words that appear in the corpus. 

The input and output are the same as in the previous model.
3. Build a model with subword tokenization and embeddings

Use the same model but with subword tokenization and embeddings. Use BPEmbed (https://github.com/bheinzerling/bpemb​)
