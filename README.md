# Project README

## Notebooks:

### A3.ipynb:
This is the main notebook addressing all tasks requested in sections A, B, and C.

### data_generation.ipynb:
Contains essays generated via a Markov statistical model Language Model (LM).

### create_augmentation_train_file.ipynb:
Contains summarizations of all files to create the combined_train.csv, which is our main file containing data for the project.

## Explanation of augmentation.csv:

### Columns:
| Column Name   | Explanation |
|---------------|-------------|
| essay_id      | Column containing each essay ID for reference purposes. |
| prompt_id     | The prompt ID used for each generation of text. |
| text          | The essays themselves. |
| generated     | Labels the 'text' column as LLM generated (1) and student (0). |
| label         | Same as 'generated' for plotting purposes. |
| token_text    | Tokenized text for the preprocessing procedure and Jaccard similarity calculation. |
| max_jaccard_sim | Calculated maximum Jaccard similarity for each LLM essay (generated==1) compared to all student essays (generated==0). |
| avg_jaccard_sim | Calculated average Jaccard similarity for each LLM essay (generated==1) compared to all student essays (generated==0). |

### Jaccard Similarity (similarity scores task):
Jaccard similarity scores are calculated based on a function called jaccard_similarity(list_of_words1, list_of_words_2). Specifically, the Jaccard similarity measures the proportion of common elements to the total number of unique elements in the sets. Here, the sets are the generated essays and the student essays.

### Probability Scores:
Probability scores regarding the generated essays are calculated via k-fold splits, which perform the leave-one-out method.

### Learning Curves (Train-Test):
Learning curves for different proportions of the training set (10%, 20%, ..., 100%) are calculated via the function train_evaluate(X_train, y_train, X_test, y_test).

### Elbow Method:
The `perform_elbow()` function generates plots regarding the clusters and the given text data.

### Silhouette Score:
The `silhouette_score_analysis()` function performs silhouette score analysis for a given set of clusters and text data.

### K-Means Clustering:
The `kmeans_clustering()` function performs k-means clustering for the optimal given k and the given text data.
