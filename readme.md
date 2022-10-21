##1.Task Description.
(yash)

##2.Data Crawling:
Since the task is from semeval 2021, we got the got data which contains links for the news articles and overall similarity score in a csv file. Then by using the [downloader provided][https://github.com/euagendas/semeval_8_2022_ia_downloader] we have crawlled the web pages and then from the files crawled we have managed to extract the required data in json format. From which we can further extract the required features.  

##3.Methodologies Implemented:

We implemented 2 baseline approaches:

###a.  After getting the data, we have pre-processed the data and extracted the essential parameters like title, description, keywords and text of every news article. Then using the sentence transformer(sentence-transformers/all-MiniLM-L6-v2), by which we can capture the sematic information of the text in the news article and also combined with extracted features like description, title and keywords.From this we get the sentence embeddings for the text to be compared. Then we used the cosine similarity function on sentence embeddings to find the text similarity score.
    On comparing our data with the Overall similarity score from the annotated data, the mean difference is not close to zero.    


###b. We implemented a Siamese Architecture inspired by [1] to predict the news similarity scores.
    dataPrepare.py takes the crawled data and puts it in one json (list of dict)
    MLNS_Siamese_roberta.ipynb implements the model to get predictions.
        We used xlm-roberta-base for tokenization and modeling.
##4.Findings       


##5.Comparision with Original scope document:
(yash)

##References:
[1] Sagar Joshi, Dhaval Taunk, and Vasudeva Varma. 2022. IIIT-MLNS at SemEval-2022 Task 8: Siamese Architecture for Modeling Multilingual News Similarity. In Proceedings of the 16th International Workshop on Semantic Evaluation (SemEval-2022), pages 1145–1150, Seattle, United States. Association for Computational Linguistics.
