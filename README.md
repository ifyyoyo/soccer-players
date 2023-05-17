# soccer-players

Data source : https://www.kaggle.com/hugomathien/soccer

Goal of Project : A sport magazine is writing an article on soccer players

They have a special interest in left-footed players

A question is whether they playing style can predict if a player is left-footed

The questions they want to answer: Can you from a features set on players predict if it is left-footed player

If so, what features matters the most

I imported the relevant python libraries needed for the project, i then read the data which is a parquet file using pandas into a DataFrame 


i checked for the Data types using info() to see if some numeric column are not represented in numeric, checked for missing data using isnull() and applied dropna() to drop all the missing data.

This project is just for demonstration, so i limited the data to the first 10000 row iloc[:10000]

The classifier i want to predict is preferred_foot (independent feature/classification)
I assigned the dependent features to X and the independent feature to y

i used the train_test_split to divide into train and test data.

I created a MinMaxScaler(), Fitted it on the X_train dataset and transform X_train and X_test

Created a StandardScaler(), fitted it on the X_train dataset and transform X_train and X_test

I compared the sets, for the Original, Normalized, and Standardized datasets, i created a SVM model and fit it and predict values to calculate an accuracy score.

To find the most important feature, permutation importance was used, also i used the standardized dataset because it performed better in the model.

perm_importance = permutation_importance(svc, X_test_stand, y_test)

The results was found in perm_importance.importances_mean.

The result was visualized by sorting the most important features, perm_importance.importances_mean.argsort()

pd.DataFrame(perm_importance.importances_mean[sorted_idx], X_test.columns[sorted_idx], columns=['Value']), then i made a barh plot.

conclusion: This project was conducted using the first 10000 rows which may not tell so much about the entire dataset because it could predominantly include only players who are left footed, so i cannot for a fact say those features are features that defines a left footed player.
