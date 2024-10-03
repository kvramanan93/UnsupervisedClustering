# UnsupervisedClustering
BERTopic visualization :
![{4B18F474-3253-440E-9C3A-648C51A6F63B}](https://github.com/user-attachments/assets/cc633974-73b4-4caf-8cff-8c9c06d3ccd8)
![{613EDF5A-4A9A-47A0-A835-405BE6F6E7CE}](https://github.com/user-attachments/assets/b9508546-d843-4036-b684-598b880bfe0e)
Topic model heirarchial clustering : ![{ECB7E0C7-A336-4FC1-924E-5F2CDD413A24}](https://github.com/user-attachments/assets/2f0122ee-9827-49c6-8540-a38d7f6f9b49)

Topic Modelling
Topic Modeling Process:
- Loading the Dataset: The dataset consists of approximately 40k text examples.
-  Cleaning the Text: The text is cleaned by removing stop words and unnecessary symbols.
-  Finding Important Words: Word factorization is used to identify important words in each document.
-  Topic Modeling with LDA: Latent Dirichlet Allocation (LDA) is applied to group similar words into topics based on word distributions.
-  Text Embeddings using BERT: BERT embeddings are used to capture the semantic meaning of each document. This is followed by:
        UMAP: For dimensionality reduction.
        HDBSCAN: For clustering the documents into meaningful groups.
- Topic Labeling: The most relevant words from each topic are used to assign labels to the topics.
- Visualization: The topics are visualized to display their distribution and relationships.
    
Approach:
  Algorithms Used:
* **LDA**: A classical topic modeling technique that identifies distinct topics by modeling the distribution of words across documents. It is effective for simpler, non-contextual tasks but has limitations in capturing deeper semantic meanings.
* **BERTopic**: A more advanced method that uses BERT embeddings to capture semantic relationships within the text. Paired with UMAP for dimensionality reduction and HDBSCAN for clustering, BERTopic is well-suited for complex, context-dependent text datasets like the one in this project.
  Challenges and Solutions:
* **Contextualized Topic Models**: I experimented with contextualized_topic_models, but they didn't yield valid or relevant results for the dataset.
* **NomicBERT**: A high-level model, NomicBERT, was tested but was computationally expensive. It ran for over 6 hours on Kaggle without completing due to the size of the dataset (~40k examples). As a result, I pivoted to LDA and BERTopic, which were more efficient and provided better results for the dataset size.
Final Models:
-    BERTopic produced the most coherent and contextually relevant topics, making it the preferred model over LDA.
-   LDA still served as a useful benchmark but performed sub-optimally for this context-rich dataset.
   

For future implementations we can try to tokenize using GP4 tokenizer. then embedd using BERTNomic which is specifically made for topic modelling tasks of longer lenghts. 
We can even use ChatGPT or other models from OpenAI to generate labels, summaries, phrases.
