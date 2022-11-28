# 1.Task Description.
Given a pair of news articles, predict if they are covering the same news story.
\
Develop a system that identifies news articles in multiple languages that provide similar information.
\
It is a document-level similarity task in the applied domain of news articles, rating them pairwise on a 4-point scale from most to least similar.

# 2.Data Crawling:
Since the task is from semeval 2021, we got the got data which contains links for the news articles and overall similarity score in a csv file. Then by using the [downloader provided](https://github.com/euagendas/semeval_8_2022_ia_downloader) we have crawlled the web pages and then from the files crawled we have managed to extract the required data in json format. From which we can further extract the required features.  

# 3.System Description:

## Base model using Siamese Architecture (DB):
We implemented a Siamese Architecture inspired by [1] to predict the news similarity scores. \
The dataPrepare.py takes the crawled data and puts it in one json (list of dict). \

MLNS_Siamese_dislitBert.ipynb implements the baseline model to get predictions. It uses dislitBert as encoder and for tokenization.\
We used xlm-roberta-base for tokenization and modeling.

## Other models:
We did 5 other experiments keeping the same Siamese Architecture  as follows:

### XRB
Used XLM-RoBERTa as encoder and for tokenization. Code is in MLNS_Siamese_roberta.ipynb

### DB_M
Used Metadata along with news text as input. Used dislitBert as encoder and for tokenization. Code is in MLNS_Siamese_dislitBert_Meta.ipynb

### DB_A
Used data augmentation to increase training data. Data augmentation was done by randomly jumbling up sentences  in the news articles. 4 times the original data was create in this way. Code for the data creation is in data_augmentation.ipynb . Used dislitBert as encoder and for tokenization. Training code is in data-augmentation.xpynb

### DB_ML
Used dislitBert as encoder and for tokenization. Some extra labels were provided along with the training data, like similarity of geography and time. We used them for multilabel Learning, in the training phase, but for testing we pridicted only the similarity score. Code is in MLNS_Siamese_dislitBert_multilable.ipynb

### DB_S
Since we had twice the test data as the training data. We performed a experiment where we combined all the d and split it into train, validation and test in 70:15:15 split. Used the base model on this split.


# 4.Results:       
| EXPERIMENT  | DEV. PCC | TEST PCC |
| ------------- | ------------- | ------------- |
| DB  | 0.4257 | 0.2817 |
| XRB  | 0.4278 | 0.2958 |
| DB_M  | 0.4705 | 0.2973 |
| DB_A  | 0.9608 | 0.2458 |
| DB_ML  | 0.4310 | 0.2389 |
| DB_S  | 0.449 | 0.405 |

\
We got the best result using DistilBERT along with meta data to train our model which achieved a test PCC of 0.2973.



# References:
[1] Sagar Joshi, Dhaval Taunk, and Vasudeva Varma. 2022. IIIT-MLNS at SemEval-2022 Task 8: Siamese Architecture for Modeling Multilingual News Similarity. In Proceedings of the 16th International Workshop on Semantic Evaluation (SemEval-2022), pages 1145–1150, Seattle, United States. Association for Computational Linguistics.
\
[2] SemEval-2022 Task 8: Multilingual news article similarity  https://aclanthology.org/2022.semeval-1.155.pdf
\
[3] Xu, Z., Yang, Z., Cui, Y., & Chen, Z. (2022, July). HFL at SemEval-2022 task 8: A linguistics-inspired regression model with data augmentation for multilingual news similarity. In Proceedings of the 16th international workshop on semantic evaluation (semeval-2022) (pp. 1114–1120). Seattle, United States: Association for Computational Linguistics.
