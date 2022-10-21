Task Description.
(yash)

Data Crawling:


Methodologies Implemented:

We implemented 2 baseline approaches:

1)  After getting the data, we have pre-processed the data and extracted the essential parameters like title, description, keywords and text of every news article. Then using the sentence transformer(sentence-transformers/all-MiniLM-L6-v2), by which we can capture the sematic information of the text in the news article and also combined with extracted features like description, title and keywords.From this we get the sentence embeddings for the text to be compared. Then we used the cosine similarity function on sentence embeddings to find the text similarity score.
    On comparing our data with the Overall similarity score from the annotated data, the mean difference is not close to zero.    


2) We implemented a Siamese Architecture inspired by [1] to predict the news similarity scores.
    dataPrepare.py takes the crawled data and puts it in one json (list of dict)
    MLNS_Siamese_roberta.ipynb implements the model to get predictions.
        We used xlm-roberta-base for tokenization and modeling.

Reference:
[1] Sagar Joshi, Dhaval Taunk, and Vasudeva Varma. 2022. IIIT-MLNS at SemEval-2022 Task 8: Siamese Architecture for Modeling Multilingual News Similarity. In Proceedings of the 16th International Workshop on Semantic Evaluation (SemEval-2022), pages 1145–1150, Seattle, United States. Association for Computational Linguistics.
