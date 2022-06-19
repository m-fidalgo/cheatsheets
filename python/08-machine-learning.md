<h1 align="center">Machine Learning</h1>
<p align="center"><a href="#expl">Data Exploration</a> | <a href="#vis">Data Visualization</a> | <a href="#preproc">Data Preprocessing</a> | <a href="#class">Classification</a></p>
<br />

<h2 align="center" id="class">Classification</h2>
<p align="center"><a href="#decision-tree">Decision Tree</a> | <a href="#knn">kNN</a> | <a href="#naive-bayes">Naive Bayes</a> | <a href="#svm">Support Vector Machine (SVM)</a> | <a href="#ann">Artificial Neural Networks</a> | <a href="#ensemble">Ensemble</a> | <a href="#results">Comparar Resultados</a></p>

<h3>Observação</h3>
<p>X é a matriz dos dados e y o vetor da variável target</p>
<p>Deve-se inicializar <b>results = {}</b></p>

<h3 id="decision-tree">Decision Tree</h3>
<p>Uso do <b>sklearn</b> - não dá suporte a variáveis categóricas por enquanto</p>
<p>Bibliotecas</p>

```
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
from sklearn.tree import DecisionTreeClassifier, plot_tree
from sklearn.metrics import classification_report, f1_score
from sklearn.model_selection import cross_val_score, cross_validate, GridSearchCV, train_test_split
```
<p>Scores</p>

```
clf_tree = DecisionTreeClassifier(random_state=0)
scores = cross_val_score(clf_tree, X, y, cv=3, scoring='f1_weighted')
print(scores)

results["tree"] = np.mean(scores)

scores = cross_validate(clf_tree, X, y, cv=3, scoring=('f1_weighted', 'precision_weighted', 'recall_weighted'), return_train_score=True)
```

```
# 1
print('test_f1_weighted')
print(np.mean(scores['test_f1_weighted']),scores['test_f1_weighted'])
print()

print('test_precision_weighted')
print(np.mean(scores['test_precision_weighted']),scores['test_precision_weighted'])
print()

print('test_recall_weighted')
print(np.mean(scores['test_recall_weighted']),scores['test_recall_weighted'])

#2
print('train_f1_weighted')
print(np.mean(scores['train_f1_weighted']),scores['train_f1_weighted'])

print('train_precision_weighted')
print(np.mean(scores['train_precision_weighted']),scores['train_precision_weighted'])

print('train_recall_weighted')
print(np.mean(scores['train_recall_weighted']),scores['train_recall_weighted'])
```

```
model_trees = clf_tree.fit(X, y)

# classe específica ou probabilidade da classe como output
model_trees.predict([[2., 2., 3., 3.]])
#model_trees.predict_proba([[2., 2., 3., 3.]])

plt.figure()
plt.rcParams["figure.figsize"] = (20,20)
plot_tree(model_trees, filled=True)
plt.title("Decision tree trained on all the iris features")
plt.show()

param_grid = {'criterion':['entropy'], 'max_depth':[3, 7, 9]}
best_tree = GridSearchCV(clf_tree, param_grid, scoring=('f1_weighted'), cv=3, refit=True)
best_tree.fit(X, y)

#sorted(best_tree.cv_results_.keys())

df = pd.DataFrame(best_tree.cv_results_)
print(df)

best_model = best_tree.best_estimator_
best_model.fit(X, y)

df = pd.DataFrame(best_tree.cv_results_)
print(df)

print(best_tree.cv_results_['mean_test_score'])
print(best_tree.best_estimator_)
print(best_tree.best_params_)
print(best_tree.best_score_)
```
<p>Exemplo: seleção e avaliação no teste</p>

```
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=0)

param_grid = {'criterion':['entropy'], 'max_depth':[3, 7, 9]}
best_tree = GridSearchCV(clf_tree, param_grid, scoring=('f1_weighted'), cv=3)
best_tree.fit(X_train, y_train)

df = pd.DataFrame(best_tree.cv_results_)
print(df)

print(best_tree.cv_results_['mean_test_score'])
print(best_tree.best_estimator_)
print(best_tree.best_params_)
print(best_tree.best_score_)

y_true, y_pred = y_test, best_tree.predict(X_test)
print(classification_report(y_true, y_pred))

f1_score(y_true, y_pred, average='weighted')
```
<h3 id="knn">kNN</h3>

```
import numpy as np
from sklearn.neighbors import KNeighborsClassifier
from sklearn.model_selection import cross_val_score

clf_knn = KNeighborsClassifier(n_neighbors=3)
clf_knn.fit(X, y)

scores = cross_val_score(clf_knn, X, y, cv=3, scoring='f1_weighted')
print(scores)

results["knn"] = np.mean(scores)

clf_knn.predict([[2., 2., 3., 3.]])
```
<h3 id="naive-bayes">Naive Bayes</h3>

```
import numpy as np
from sklearn.naive_bayes import GaussianNB
from sklearn.model_selection import cross_val_score

clf_nb = GaussianNB()
clf_nb.fit(X, y)

scores = cross_val_score(clf_nb, X, y, cv=3, scoring='f1_weighted')
print(scores)

results["nb"] = np.mean(scores)
clf_nb.predict([[2., 2., 3., 3.]])
```
<h3 id="svm">Support Vector Machine (SVM)</h3>

```
import numpy as np
from sklearn.svm import SVC
from sklearn.model_selection import cross_val_score

clf_svm = SVC()
clf_svm.fit(X, y)

scores = cross_val_score(clf_svm, X, y, cv=3, scoring='f1_weighted')
print(scores)

results["svm"] = np.mean(scores)
clf_svm.predict([[2., 2., 3., 3.]])

# get support vectors
print(clf_svm.support_vectors_)

# get indices of support vectors
print(clf_svm.support_)

# get number of support vectors for each class
print(clf_svm.n_support_)
```
<h3 id="ann">Artificial Neural Networks</h3>

```
import numpy as np
from sklearn.neural_network import MLPClassifier
from sklearn.model_selection import cross_val_score

#3 camadas intermediárias, uma com 50, a outra com 30 e a outra com 20
clf_mlp = MLPClassifier(hidden_layer_sizes=(50, 30, 20), max_iter=500, random_state=0)
clf_mlp.fit(X, y)

scores = cross_val_score(clf_mlp, X, y, cv=3, scoring='f1_weighted')
print(scores)

results["ann"] = np.mean(scores)
clf_mlp.predict([[2., 2., 3., 3.]])
```
<h3 id="ensemble">Ensemble</h3>

```
import numpy as np
from sklearn.ensemble import AdaBoostClassifier
from sklearn.model_selection import cross_val_score

clf_AdaB = AdaBoostClassifier()
clf_AdaB.fit(X, y)

scores = cross_val_score(clf_AdaB, X, y, cv=3, scoring='f1_weighted')
print(scores)

results["AdaB"] = np.mean(scores)
clf_AdaB.predict([[2., 2., 3., 3.]])
```
<h3 id="results">Comparar Resultados</h3>

```
for key, value in results.items():
    print(key, value)
```
