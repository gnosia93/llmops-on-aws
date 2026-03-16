

## ReRanking (Cross-Encoder/Bert) ##

Different from embedding model, reranker uses question and document as input and directly output similarity instead of embedding. You can get a relevance score by inputting query and passage to the reranker. And the score can be mapped to a float value in [0,1] by sigmoid function.


* https://huggingface.co/BAAI/bge-reranker-v2-m3
* https://hypro2.github.io/bge-reranker-gemma/
