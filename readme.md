## 1.Task Description.
Given a pair of news articles, predict if they are covering the same news story.
Develop a system that identifies multilingual news articles that provide similar information.
It is a document-level similarity task in the applied domain of news articles, rating them pairwise on a 4-point scale from most to least similar.

## 2.Data Crawling:
Since the task is from semeval 2021, we got the got data which contains links for the news articles and overall similarity score in a csv file. Then by using the [downloader provided](https://github.com/euagendas/semeval_8_2022_ia_downloader) we have crawlled the web pages and then from the files crawled we have managed to extract the required data in json format. From which we can further extract the required features.  

## 3.Methodologies Implemented:
### [GITHUB LINK](https://github.com/sharma18yash/ire_project) 
We implemented 2 baseline approaches:

### a. Using Sentence transformer model:
After getting the data, we have pre-processed the data and extracted the essential parameters like title, description, keywords and text of every news article. Then using the sentence transformer(sentence-transformers/all-MiniLM-L6-v2), by which we can capture the sematic information of the text in the news article and also combined with extracted features like description, title and keywords.From this we get the sentence embeddings for the text to be compared. Then we used the cosine similarity function on sentence embeddings to find the text similarity score.
    

### b.Siamese Architecture:
We implemented a Siamese Architecture inspired by [1] to predict the news similarity scores. \
The dataPrepare.py takes the crawled data and puts it in one json (list of dict). MLNS_Siamese_roberta.ipynb implements the model to get predictions. \
We used xlm-roberta-base for tokenization and modeling.


## 4.Findings:       
In our first baseline model, On comparing our data with the Overall similarity score from the annotated data, the intial mean difference with cosine similarities was much greater than zero. 
Then by experimenting using the different parameters of the meta data like  title, description and keywords, by assigning different weights to parameters resulted in the better similarity scores when compared to the intial result.
We believe that on further optimization we can achieve the similarity scores which are closer to the given overall score.
\
\
We started exploring using the bert and other models, since the scores were not upto the mark, we will be fine tuning the other models on the train data. 



## 5.Comparision with Original scope document:
(yash)

## References:
[1] Sagar Joshi, Dhaval Taunk, and Vasudeva Varma. 2022. IIIT-MLNS at SemEval-2022 Task 8: Siamese Architecture for Modeling Multilingual News Similarity. In Proceedings of the 16th International Workshop on Semantic Evaluation (SemEval-2022), pages 1145–1150, Seattle, United States. Association for Computational Linguistics.
