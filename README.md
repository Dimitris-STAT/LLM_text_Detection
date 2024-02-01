
Notebooks: 
A3.ipynib:
	 is the main notebook answering to all A,B,C task requested.

data_generation.ipynib:
	 contains the generated (via markov statistic model LM) essays

create_augmentation_train_file.ipynib  :
	contains the summarizations of all the files to create the combined_train.csv which is 
	our main file that contains the data that will be used for the project.



=============== ================================= Explanation of augmentation.csv  =========================================================================================
Columns                  |            |                       Explanation   	
___________________________________________________________________________________________________________________________________
essay_id                   | ===> |        A column conatining each essay Id for reference purposes
prompt_id              | ===> |        The prompt id used for each generation of text
text                             | ===> |         The essays themselfs
generated               | ===> |         Labels the 'text' column as LLM generated(1) and student(0) 
label                            | ===> |          Same as 'generated' for plotting purposes
token_text              | ===> |          Tokenized text for the preprocessing procedure and jaccard similarity
max_jaccard_sim | ===> |          Calculated maximum jaccard similarity only for each LLM essay(generated==1) compared to all the student essays(generated==0)
avg_jaccard_sim  | ===> |          Calculated average jaccard similarity only for each LLm essay (generated==1)  compared to all the student essays(generated==0)

======================================================================================================================================
					JACCARD SIMILARITY(similarity scores task)
_______________________________________________________________________________________________________________________________________
Jaccard similarity scores are calculated based on a function called jaccard_similarity(list_of_words1, list_of_words_2) . More specifically, The Jaccard similarity,
measures the proportion of common elements to the total number of unique elements in the sets. 
The sets, for us here are the generated essays and the student essays!

Also, the probability scores regarding the generated essays are calculated via the k-fold splits which performs the leave-one-method 
======================================================================================================================================


					Learning Curves(Train-Test)
________________________________________________________________________________________________________________________________________
The learning curves for different proportions of the trainning set (10%,20%, ..., 100%)  are calculated via the function train_evaluate(X_train, y_train, X_test, y_test)


=======================================================================================================================================

					         Elbow Method
_________________________________________________________________________________________________________________________________________

The perform_elbow(text_data: str,name: str, cluster_range:int ) function generates plots regarding the clusters and the text given as data.

_________________________________________________________________________________________________________________________________________
					Silhouette Score 

_________________________________________________________________________________________________________________________________________

The function: silhouette_score_analysis(text_data:str,cluster_num:int,name:str, left_div:int=4, right_div:int = 6). Performs the shilloutte score analysis for a given 
set of clusters and text data.



===========================================================================================================================================
					K-Means Clustering

Here the function kmeans_clustering(data: pd.DataFrame, num_clusters:int = 2) peforms the k-means clustering for the optimal given k and the text.data given. 