Task Description.


Data Crawling:

We implemented 2 baseline approaches:
1)


2) We implemented a Siamese Architecture inspired by [1] to predict the news similarity scores.
    dataPrepare.py takes the crawled data and puts it in one json (list of dict)
    MLNS_Siamese_roberta.ipynb implements the model to get predictions.
        We used xlm-roberta-base for tokenization and modeling.

Reference:
[1] Sagar Joshi, Dhaval Taunk, and Vasudeva Varma. 2022. IIIT-MLNS at SemEval-2022 Task 8: Siamese Architecture for Modeling Multilingual News Similarity. In Proceedings of the 16th International Workshop on Semantic Evaluation (SemEval-2022), pages 1145–1150, Seattle, United States. Association for Computational Linguistics.
