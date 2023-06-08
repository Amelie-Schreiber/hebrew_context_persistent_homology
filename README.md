# hebrew_context_persistent_homology
Persistent homology of context vectors computed by individual attention heads in Hebrew language models

In the notebooks we compute the persistent homology of context vectors for individual attention heads to analyze the attention head's linguistic properties. We find that come attention heads represent certain collocations and multiword expressions in topologcially interesting ways. We also find that when focusing on the persistent homology of a subset of the tokens corresponding to a collocation or multiword expression, the topology is not necessarily preserved from one context to another. We hypothesize that maintaining the topological structure of a collocation or multiword expression may be important to model performance on tasks like collocation and multiword expression extraction. If the topological structure is in fact important and if this is included in the training objective of the model, this could improve performace on tasks related to collocations and multiword expressions. The potential applications are improved performance on document summarization, subject or content matching, search, and grammatical parsing, and OCR using TrOCR like models (which don't yet exists for Hebrew). It is important to note that the tokenizer, as well as the model used are important inthis analysis. We use both HeBERT `avichr/heBERT_sentiment_analysis`, AlephBETR, `onlplab/alephbert-base`, and `bert-base-multilingual-cased` in our expirements with Hebrew. It would also be interesting to include `alephbertgimmel`. 
