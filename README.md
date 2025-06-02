### Summary on bank marketing campaigns classification study

    - Data is imbalanced. Thus AUC score is used to comapre the models instead of test score.
    - VotingClassifier receied best AUC score 0.9432 among all the models studied 
        - VotingClassifier uses all all the best estimates using GridSearchCV from LogisticRegression, KNN, DecisionTreeClassifier, SVC

### Data observation:
    #### Information Coefficient (IC) between features and target column:
        
        - Here are the top 10 features and their IC to the 'y' column
            | Feature           | Information Coefficient (Mutual Information)   |
            |-------------------|------------------------------------------------|
            | duration          | 0.077351                                       |
            | euribor3m         | 0.073186                                       |
            | cons.price.idx    | 0.068945                                       |
            | cons.conf.idx     | 0.067400                                       |
            | nr.employed       | 0.063110                                       |
            | emp.var.rate      | 0.056823                                       |
            | nr.employed       | 0.041711                                       |
            | poutcome          | 0.035422                                       |
            | month             | 0.028797                                       |
            | previous          | 0.018647                                       |
        
        - IC of loan feature  and target feature is 0. This may be ideal candidate feature to be dropped.
        - The following features have least IC to target column
            | Feature           | Information Coefficient (Mutual Information)   |
            |-------------------|------------------------------------------------|
            | default           | 0.009196                                       |
            | housing           | 0.008090                                       |
            | marital           | 0.004378                                       |
            | day_of_week       | 0.004060                                       |
            | campaign          | 0.004018                                       |
            | education         | 0.002754                                       |
            



### Data preprocessing
    - The OrdinalEncoder for education, month, day_of_week, job is used.
        - This improves AUC score slightly, but no much.
        - Note: month, day_of_week, job are not usualy candidates for OrdinalEncoder
        
    - OneHotEncoder is used for other non-numerically features.
        

### Detailed reporting
    - Baseline model has test score 0.887346

    - The following models are studied with default parameters with best test score 0.912596 from LogisticRegression
        - Best AUC score is from LogisticRegression 0.936491 among the following models studied
            - LogisticRegression
            - LogisticRegression with selector        
            - KNeighborsClassifier
            - DecisionTreeClassifier
            - SVC

    - RandomForestClassifier with default parameters
        - Best AUC score is 0.939945 among 2 runs.
        
    - class_weight='balanced' is also studied for each of the model above. But no improvement in test score is observed.
        - Best AUC score is  0.939689 for LogisticRegression with selector

    - GridSearchCV is used to search hyper-parameters
        - Best AUC score is 0.9365 for GridSearch for logistic regression
        - Models searched by GridSearchCV:
            - LogisticRegression
            - KNeighborsClassifier
            - DecisionTreeClassifier
            - SVC

    - VotingClassifier from the best estimator from GridSearchCV of LogisticRegression, LogisticRegression with selector, KNeighborsClassifier, DecisionTreeClassifier, SVC is also studied
        - The AUC score is 0.9432 for VotingClassifier.
        - This is the best AUC score among all the models studied.

    - Mode train speed analysis:
        - SVC and GridSearchCV of SVC turns out to be extremely slow and the AUC score is not as good as LogisticRegression or GridSearchCV of GridSearchCV
        - DecisionTreeClassifier and GridSearchCV of GridSearchCV are the fastest besides the baseline model.
        - RandomForestClassifier is also very fast with very good AUC score.
    
    - Study on removing less import features from IC point of view
        - The following features were removed for dataset, but no change to the outcome of the test AUC score:
            - education
            - day_of_week
            - campaign
    
### Interpretation of coefficients in models:
    - Coefficients for LogisticRegression represent the contribution of each feature to the log-odds of the predicted outcome
        - Top 10 important coefficients found by logistic regression model:
            - Log-odds of outcome increases when the feature value i increases:
                - mar in month
                - duration
                - cons.price.idx
                - euribor3m
            - Log-odds of outcome decreases when the feature value i increases:
                - emp.var.rate
                - jun/may/nov in month
                - poutcome_failure


### Implementation reference:
        - [prompt_III.ipynb](https://github.com/mingl2000/UCBAI/blob/main/prompt_III.ipynb)
    
