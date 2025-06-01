### Summary on bank marketing campaigns classification study
    - The following models are studied with default parameters with best test score 0.912596 from LogisticRegression comparing with baseline score 0.887346
        - LogisticRegression
        - LogisticRegression with selector
        - RandomForestClassifier
        - KNeighborsClassifier
5       - DecisionTreeClassifier
        - SVC
        
    - class_weight='balanced' is also studied for each of the model above. But no improvement in test score is observed.
    - GridSearchCV is used to search hyper-parameters for each of the model listed above.
        - GridSearchCV on LogisticRegression
        - GridSearchCV on LogisticRegression with selector
        - GridSearchCV on KNeighborsClassifier
        - GridSearchCV on DecisionTreeClassifier
        - GridSearchCV on SVC
    - VotingClassifier from the best estimator from GridSearchCV of LogisticRegression, LogisticRegression with selector, KNeighborsClassifier, DecisionTreeClassifier, SVC is also studied


    ### Implementation reference:
        - [prompt_III.ipynb](https://github.com/mingl2000/UCBAI/blob/main/prompt_III.ipynb)
    

