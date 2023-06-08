# hebrew_context_persistent_homology
Persistent homology of context vectors computed by individual attention heads in Hebrew language models

In the notebooks we compute the persistent homology of context vectors for individual attention heads to analyze the attention head's linguistic properties. We find that some attention heads represent certain collocations and multiword expressions in topologcially interesting ways. We also find that when focusing on the persistent homology of a subset of the tokens corresponding to a collocation or multiword expression, the topology is not necessarily preserved from one context to another. We hypothesize that maintaining the topological structure of a collocation or multiword expression may be important to model performance on tasks like collocation and multiword expression extraction. If the topological structure is in fact important and if this is included in the training objective of the model, this could improve performace on tasks related to collocations and multiword expressions such as machine translation. We note that the one multilingual model `bert-base-multilingual-cased` that we study is the worst at this compared to the other monolingual models. 

It is important to note that the tokenizer, as well as the model used are important in this analysis. We use HeBERT `avichr/heBERT_sentiment_analysis`, AlephBERT, `onlplab/alephbert-base`, and `bert-base-multilingual-cased` in our expirements with Hebrew. It would also be interesting to include `alephbertgimmel` which is a more recent Hebrew model with a larger vocabulary. In our analysis we find that tokenization into fewer subwords seems to mean that topological stucture is preserved more. We also note that when trying to cluster the tokens using DBSCAN with the $\epsilon$ distance threshold parameter set to near the lowest value of an $H_1$-persistence bar seems to provide more meaningful clusters than values lower or higher than the first $H_1$-persistence bar in the barcode diagram. 
