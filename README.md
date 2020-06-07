# Ironhack project 6 Steam machine learning

![GitHub Logo](https://cdn.mmos.com/wp-content/uploads/2017/03/steam-user-reviews-change-news-banner.jpg)

### Project description

In this project the goal was to compare different machine learning models and their efficiency to predict a value/parameters. For this project I choosed to work on a steam database found on kaggle, and tried to build models to see if a game would have overall bad or good reviews, from its other features (price, genre, categories, required age, etc...)

Steps of the project :
- Data cleaning ; checking nan, types of the features, calculating new features, creating dummies for categorical variables, dropping unimportant/redundant ones
- Simple data exploration ; checking distribution of numerical variables, searching for trends or link with prices and genres, or price and categories mainly
- Checking outliers and multicollinearity between features
- Building models ; Logistic Regression, NuSVC (Nu Support Vector Machine/Classifier), Random Forest, KNN (KNeighbors Classifier)
  - 3 versions of the 4 models, after different step of dataset modification :
    - simple data cleaning
    - RFE (Recursive Feature Elimination) applied
    - Scaling

- For each versions of the 4 models, their efficiency is checked with 4 metrics ; a confusion matrix, accuracy, precision, roc auc score

### Libraries

- pandas
- numpy
- matplotlib
- seaborn
- datetime
- boxcox (from scipy.stats)
- sklearn
  - MultiLabelBinarizer
  - train_test_split
  - RFE
  - LinearRegression
  - StandardScaler
  
  Models
  - LogisticRegression
  - NuSVC
  - RandomForestClassifier
  - KNeighborsClassifier
  
  Metrics
  - confusion_matrix
  - accuracy_score
  - precision_score
  - roc_auc_score

### Code details

OPEN A JUPYTER INSTANCE TO BE ABLE TO READ THE .ipynb FILE HERE ON GITHUB

- list_unique(), which retrieves unique values from categorical features where values are lists
- mean_owners(), which returns the mean of the 2 bounds of owners from the original column
- outliers_lim(), which returns for a given column its outliers limits
- calculate_age(), which calculates the age (in years) of the games (comparison between the date and the release date of the games)
- stat_col(), which return for a given dummies column the percent of positive reviews for the latest (ex : for the action genre it gets the percentage of the games in this category that had positive reviews)

- for creating the dummies for the categories and genres features, I used the MultiLabelBinarizer function, which allows creation of dummies with multiple true cases
- also for categories and genres, the unique values were regrouped to have less in both, using dictionnaries mapped to them
- the review column was created simply by comparing the number of positive and negative reviews (more positive = 1 and more negative = 0)

- the boxcox method was tried to make the numerical variables follow a normal distribution, but since it didn't worked that well, the original variables were kept for the models
- multicollinearity was checked and dealt with by displaying the correlation matrix for the variables and removing them one by one

Models steps :
- train_test_split method was used to separate the dataset between training and testing, and the same sets were used for each models, using a random state and a stratify method so that it would remain exactly the same samples, and with an adaptation for the imbalanced dataset (much more games with positive reviews than with negative reviews)
- all models were fit, then prediction values were created
- the different metrics choosed were then checked for each models, using especially the precision because the goal was essentially to know which model gave the least false positive (games with bad reviews that were classified as game with good reviews)
- for the RFE, the model used was a linear regression model, and the default value was used, which returned half of the most important features
- to scale the data, the StandardScaler() function was used ; it should most likely have been used before doing the models

### Links

Source page : 

Presentation : 

