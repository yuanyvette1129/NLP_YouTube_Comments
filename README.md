# NLP_YouTube_Comments

Summary

In this project, I used Spark to analyze the user comments of youtube videos via Azure Databricks. The goal is to identify cat/dog owners based on these comments, find out the topics important to them, and identify youtubers who are most attractive to dog or cat owners.

Step 1. Extract, Explore, and Clean the Data
I downloaded the dataset (about 240MB compressed) from google drive link and load on Spark. There are 5.8 million comments in the dataset after dropping null comments. Each row has a youtuber name, user's comments and userid, and the an userid.

The data itself is unlabeled. To have a baseline label of dog/cat owners vs non dog/cat onwers, I extract comments that contains phrases like "my dog", "I have a dog", "my puppy", "I have a cate", etc., and label it as 1, meaning a dog/cat owner. In total, one percent of the users are identified as pet/cat owners (61240/5757744), which is very unbalanced.

Step 2. Feature PreProcessing and Train/Test Split
I converted each user's coments into a list of words, and used word2vector algorithm to transform text features into vectors. Given the label of the data is high unbalanced, I randomly downsized the data that has label = 0. Downsizing also can speed up model training process later as well. After train/test split, my training dataset count is 100601, and test dataset count is 42446.

Step 3. Trained a Gradient Boosted Tree Model to Classify Dog/Cat Owners
I train logistic regression model, random forest model, and gradient boosted tree model to classify audiences. After parameter tuning and cross validation, I ended up with the GBT model, which attained the highest AUR score (0.965)

I applied the GBT classifiers to all the users in the dataset, and estimated that the faction of users who are dog/cat owners is about 17.5%

Step 4. Implemented LDA to Identify Topics for Dog/Cate Owners
I preprocessed the comments of dog/cat owners by removing stopwords, limiting word length >=3, and generating a TF-IDF matrix. I applied LDA model to infer the topics hidden in the users. Dog/cat owners are interested in how to care/teach/train their dogs/cat. They are concerned with their pet's health, as words such as "cancer","old","life" ,"pain","clean" are frequently mentioned. They talk about their "lost" dogs/cats.

Step 5. Identify Creators With Cat And Dog Owners In The Audience
I used SparkSQL to itentify the youtubers who have the highest dog/cat owners as the audience. So marketing ads can be placed to these creators' videos to target specific audience.

Future Work
The top words identifed using LDA with one-gram is not quite satisfactory. I can try stemming the words to avoid duplicates words, or try bigram to extract more insights.
