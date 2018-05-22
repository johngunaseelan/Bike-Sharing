pipe = Pipeline([('selectKBest', SelectKBest()), ('clf', SGDRegressor(random_state=42))])

param_grid = {
    'clf__loss':['squared_loss','huber','epsilon_insensitive', 'squared_epsilon_insensitive'],
    'clf__penalty' : ['l2', 'l1', 'elasticnet'],
    'clf__fit_intercept' : [True, False],
    'clf__learning_rate' : ['constant', 'optimal', 'invscaling'],
    'clf__max_iter' : [100],
    'clf__tol' : [None],
    'selectKBest__k' : range(1,50,1),
    'selectKBest__score_func' : [f_regression]
}

grid =GridSearchCV(pipe, param_grid, cv=5 )
grid.fit(df_train.iloc[:,:-1].astype(float),df_train.iloc[:,-1].astype(float) , scoring=r2_score)