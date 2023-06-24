# Asking-Clarifying-Questions
## NLP Term Paper 2023 Spring


### Team NMP

```
Narsupalli Yaswanth - 19AE3AI02
Muppirala Ramachandra Sreevatsa - 19AE30013
Aayush Pandey - 19AE10001
Ashish Gokarnkar - 18IM30027
```


### Folder Structure

```
\Notebooks
  -\Classification Task
  -\Retrieval Task
\Dataset
\Imgs

```

### Clarification Need Prediction LeaderBoard  (Our Best Rank = 2)

| **ًRank**  | **Creator**  | **Model Name**       | **Dev**  |           |          | **Test** |          |          |
|-----------|-------------|---------------------|---------|----------|----------|----------|----------|----------|
|           |             |                     | P       | R        | F1       | P        | R        | F1       |
| 1         | TAL ML      | Roberta+++          | 0.6039  | 0.56     | 0.5551   | 0.5981   | 0.6557   | 0.607    |
| 2     | **NMP**        | **GPT**                 |            |          | **0.4060**     |            |            | **0.5761**   |
| 3     | **NMP**        | **OPT**                 |            |          | **0.4564**     |            |            | **0.5478**    |
| 4     | CactusJam  | Roberta+ Stats      | 0.62       | 0.58     | 0.5717     | 0.5963     | 0.5902     | 0.5416    |
| 5     | TAL ML     | Roberta++           | 0.5807     | 0.54     | 0.5375     | 0.529      | 0.5574     | 0.5253    |
| 6     | Algis      | Roberta+ CatBoost   | 0.1402     | 0.28     | 0.1854     | 0.5171     | 0.5246     | 0.5138    |
| 7     | **NMP**        | **Electra**             |            |          | **0.4899**     |            |            | **0.5048**    |
| 8     | **NMP**        | **GPT-2**               |            |          | **0.42431**    |            |            | **0.50263**   |
| 9     | NTES_ALONG | cneed_add_ prior_v2 | 0.62       | 0.6      | 0.5984     | 0.5007     | 0.5082     | 0.5018    |
| 10    | NTES_ALONG | cneed_merge         | 0.583      | 0.52     | 0.5192     | 0.4847     | 0.5082     | 0.496     |



### Dataset Sample

![alt text](https://github.com/yaswanth-iitkgp/Asking-Clarifying-Questions/blob/main/Imgs/Task%20-1%20Dataset.png)
![alt text](https://github.com/yaswanth-iitkgp/Asking-Clarifying-Questions/blob/main/Imgs/Task%20-2%20Dataset.png)




### What is Ensemble.ipynb ?

Combining a classifier model and retriever model for asking clarifying questions in open-domain NLP can be achieved through a pipeline architecture. The pipeline architecture consists of two main components: a retriever model and a classifier model. Once the classifier model has classified each document, the pipeline architecture can select the most relevant document and extract the answer to the question from that document. If the classifier model determines that none of the candidate documents are relevant to the question, the pipeline architecture can prompt the user to provide more information or rephrase the question. A pipeline architecture can improve the accuracy by leveraging the strengths of each model. The retriever model is effective at finding relevant information, while the classifier model can accurately classify whether the information is relevant to the question.
Pipeline architecture that is implemented:
1. Train the classifier model using the datasets given
2. Question is inputted to the classifier model (e.g. BERT)
3. If the classification is:
          > 1 or 2: Questions don't require clarity. Output this directly.
          > 3 or 4: Question requires clarity. Proceed further.
4. Send the question to the retriever model (e.g. Electra)
5. Electra ranks the top 3 clarifying questions as per the contextual semantics
6. Choose a clarifying question out of the 3 as per a probability function

Model selected for Classification is BERT which is pre-trained on the csv files given. Model used for Retrieval is the BERT-ReRanker which is trained on ClariQ dataset..

