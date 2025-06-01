### Summary on bank marketing campaigns classification study

    - Data is imbalanced. Thus AUC score is used to comapre the models instead of test score.
    - VotingClassifier receied best AUC score 0.9432 among all the models studied 
        - VotingClassifier uses all all the best estimates using GridSearchCV from LogisticRegression, KNN, DecisionTreeClassifier, SVC

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


### Implementation reference:
        - [prompt_III.ipynb](https://github.com/mingl2000/UCBAI/blob/main/prompt_III.ipynb)
    
