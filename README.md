# hebrew_context_persistent_homology
Persistent homology of context vectors computed by individual attention heads in Hebrew language models

In the notebooks we compute the persistent homology of context vectors for individual attention heads to analyze the attention head's linguistic properties. We find that some attention heads represent certain collocations and multiword expressions in topologcially interesting ways. We also find that when focusing on the persistent homology of a subset of the tokens corresponding to a collocation or multiword expression, the topology is not necessarily preserved from one context to another. We hypothesize that maintaining the topological structure of a collocation or multiword expression may be important to model performance on tasks like collocation and multiword expression extraction. If the topological structure is in fact important and if this is included in the training objective of the model, this could improve performace on tasks related to collocations and multiword expressions such as machine translation. We note that the one multilingual model `bert-base-multilingual-cased` that we study is the worst at this compared to the other monolingual models. We also note that `onlplab/alephbert-base`, the newest models of the three with the largest vocabulary performs the best of the three, suggesting vocabulary size is a factor in performance on preserving the topology of the context vectors. 

It is important to note that the tokenizer, as well as the model used are important in this analysis. We use HeBERT `avichr/heBERT_sentiment_analysis`, AlephBERT, `onlplab/alephbert-base`, and `bert-base-multilingual-cased` in our expirements with Hebrew. It would also be interesting to include `alephbertgimmel` which is a more recent Hebrew model with a larger vocabulary than the other three, likely implying it will perform better at preserving the topology of the context vectors and at capturing collocations and multiword expressions. Note, including persistent homology, that is, the task of preserving the topology of the context vectors, in the objective of the model, may be a good way to improve models on languages considered "morphologically rich" and "low-resource". In our analysis we find that tokenization into fewer subwords seems to mean that topological stucture is preserved more. This makes sense, due to the fact that the topology becomes more complicated as we add context vectors, and thus will be more difficult to preserve. We also note that trying to cluster the tokens using DBSCAN with the $\epsilon$ distance threshold parameter set to near the lowest value of an $H_1$-persistence bar seems to provide more meaningful clusters than values lower or higher than the first $H_1$-persistence bar in the barcode diagram. 

Also note, that since there can be a hierarchical structure to the morphemes in a language, and persistent topology is a generalized form of hierarchical clustering (see [simplex trees](https://gudhi.inria.fr/python/latest/simplex_tree_ref.html)), we may find this provides an alternative perspective on morphological segmentation, and one that is self-supervised at that. See [Morphological Segmentation Inside-Out](https://arxiv.org/pdf/1911.04916v2.pdf) for an explanation of the hierarchical structure of morphological segmentation. See also [Word-level Morpheme segmentation using Transformer neural network](https://aclanthology.org/2022.sigmorphon-1.15.pdf) for an application of a character level transformer to this task. We also note that with the information contained in [Persistent Topology of Syntax](https://arxiv.org/abs/1507.05134v1), it would be interesting to have a model that understands the hiercharical structure from the character level to the word level and up to the sentence level, that is, with morpheme tree understanding, and with sentence level parse trees as well. 
