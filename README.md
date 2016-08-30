### Goku Mohandas

#### Representation Learning:

	word2vec Explained.pdf: excellent mathematical explanation of CBOW and skipgram models for word2vec.

	Doctor AI: Edward Choi's implementation of using an RNN to determine patient diagnostic codes and time until next visit. He uses a patient's previous visit's diagnostic codes and features about visit and time from last visit to predict next time's events. He uses embeddings to capture the latent features.

	Multi-layer Representation Learning for Medical Concepts: Using a skipgram model, where the input if medical diagnostic codes and then later on paired with visit features to predict the diagnostic codes and visit features of previous and future visits (similar to using a target word to predict context words.) He uses embeddings for diagnostic and visist features and after training, we are able to use the embeddings to extract some interesting latent features and can even cluster the codes based on disease and can also cluster the visits.

