![{021DD5A9-46E7-476F-AFEE-B8841F155419}](https://github.com/user-attachments/assets/504245b1-7adf-40e3-9301-63787b4c39b4)


### Updated Summary of the Project:
1. **Preprocessing**:
   - Cleaned the data by removing special characters, stopwords, and references to ensure consistency and relevance.
   - Used **NomicBERT Embedded Text v1.5** to generate text embeddings, resulting in a **768-dimensional feature space** that captures the semantic meanings of the documents.

2. **Dimensionality Reduction**:
   - Applied **UMAP** and **PCA** to reduce the high-dimensional embeddings, with **UMAP** providing better results in terms of preserving the structure of the data for clustering.
   - The UMAP-reduced embeddings allowed for a more effective and interpretable clustering outcome compared to PCA.

3. **Feature Learning**:
   - Built an **autoencoder** model to learn a compressed representation of the reduced embeddings, ensuring that the model captured important features even after dimensionality reduction.
   - This step helped retain non-linear relationships in the data and improved the subsequent clustering process.

4. **Clustering**:
   - Used **KMeans clustering** on the encoded embeddings, initialized with **KMeans++** to optimize centroid initialization and convergence speed.
   - Through experimentation, determined that **150 clusters** provided an optimal balance between capturing meaningful groupings and maintaining a manageable number of clusters.

5. **Keyword Extraction**:
   - Utilized **KeyBERT** instead of traditional TF-IDF to extract the most relevant keywords for each cluster, taking advantage of **BERT-based embeddings** for more context-aware keyword extraction.
   - This allowed for a better representation of the key themes in each cluster, as it considered the semantic relationships between words.

6. **Representative Term Generation**:
   - Leveraged a **GPT-based model** to generate a single representative term or label for each cluster's top keywords. This provided concise labels that summarized the central theme of each cluster.
   - This approach improved the interpretability of the clusters by generating short, meaningful descriptors based on the extracted keywords.

7. **Visualization**:
   - Visualized the clusters using **UMAP** for dimensionality reduction to 2D space, followed by a **scatter plot** colored by cluster labels.
   - The visualization provided a clear representation of the clustering structure, showing how well-separated the clusters were and highlighting relationships between different text entries.

### Major Challenges Faced:
1. **Balancing Dimensionality Reduction and Feature Retention**:
   - Finding the right balance between reducing dimensionality and retaining critical features was challenging, requiring experimentation with **UMAP** and **autoencoders** to achieve a suitable representation.
   
2. **Optimizing Cluster Numbers**:
   - Determining the appropriate number of clusters for **KMeans** was non-trivial, as too few clusters resulted in overlapping themes, while too many clusters led to fragmentation. This required careful analysis using methods like the **elbow method** and **silhouette scores**.

3. **Maintaining Feature Quality in Encoded Space**:
   - Ensuring that the **autoencoder** retained key features during the encoding and decoding process required fine-tuning the architecture and parameters to prevent loss of important information.

4. **Generating Accurate and Concise Summaries**:
   - Using **GPT** to generate representative terms for each cluster involved refining prompts and adjusting parameters like **temperature** and **max tokens** to ensure that the outputs were focused and consistent across clusters.

5. **Keyword Extraction Complexity**:
   - Transitioning from **TF-IDF** to **KeyBERT** introduced additional complexities in managing large sets of documents and ensuring that the extracted keywords truly represented each cluster's essence.

6. **Resource Management**:
   - The combination of models (UMAP, autoencoders, GPT-based models) required careful **resource management** to handle the computational load, particularly during dimensionality reduction and clustering phases.

### Additional Insights:
- **Iterative Process**: The project involved an iterative cycle of **model evaluation, adjustment, and re-evaluation** to improve both clustering quality and keyword extraction.
- **Focus on Interpretability**: The use of **GPT-generated terms** and **KeyBERT-based keywords** significantly enhanced the interpretability of each cluster, allowing for a clearer understanding of the themes present in the data.
- **Practical Applications**: The refined clustering approach and keyword extraction can be applied to **chatbots**, **recommendation systems**, and **topic modeling**, where understanding the core themes of large text datasets is crucial.

