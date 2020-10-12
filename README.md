# NLP_YouTube_Comments

Project goals:

1. Identify Cat And Dog Owners 
Find the users who are cat and/or dog owners.

2. Build And Evaluate Classifiers 
Build classifiers for the cat and dog owners and measure the performance of the classifiers.

3. Classify All The Users 
Apply the cat/dog classifiers to all the users in the dataset. Estimate the fraction of all users who are cat/dog owners.

4. Extract Insights About Cat And Dog Owners 
Find topics important to cat and dog owners.

5. Identify Creators With Cat And Dog Owners In The Audience Find creators with the most cat and/or dog owners. 
Find creators with the highest statistically significant percentages of cat and/or dog owners.

Procedures:

● Identified dog/cat owners and topics important to them for targeted marketing based on 5 million+ user comments

● Self-labeled potential dog/cat owners using RegexTokenizer and Word2Vector

● Trained a Gradient Boosted Tree model and tuned hyper parameters via grid search with AUC = 0.96

● Extracted features with TF-IDF approach and trained a Latent Dirichlet Analysis (LDA) model
