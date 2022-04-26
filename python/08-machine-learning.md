<h1 align="center">Machine Learning</h1>
<p align="center"><a href="#expl">Data Exploration</a> | <a href="#vis">Data Visualization</a> | <a href="#preproc">Data Preprocessing</a></p>
<br />

<h2 align="center" id="expl">Data Exploration</h2>
<p align="center"><a href="#load">Carregar Arquivos</a> | <a href="#summary">Summary</a> | <a href="#sort">Ordenar</a> | <a href="#cov">Covariância e Correlação</a></p>

<h3 id="load">Carregar arquivos de dados</h3>
<p><b>read_csv</b> e <b>read_table</b> para ler dados delimitados de um arquivo, sendo respectivamente a vírgula e tab ('\t') o delimitador</p>
<p><b>read_excel</b> para ler dados de arquivos excel</p>
<p><b>read_fwf</b> para ler dados em formatos de tamanho fixo de coluna</p>
<p>Pode-se adicionar o parâmetro <b>na_values='?'</b> para indicar que valores ausentes estao representados com ? (serão alterados para NaN)</p>

```
import pandas as pd
df = pd.read_csv(filepath.csv)
df = pd.read_excel(filepath.xlsx, 'Sheet')
df = pd.read_csv(filepath.txt, sep='\t')
```
<h3>Linhas e Colunas</h3>

```
df.shape
```
<h3>Head</h3>
<p>Mostra as primeiras n linhas do dataframe (padrão: n = 5)</p>

```
df.head(n)
```
<h3>Nomear colunas</h3>

```
df.columns = ['col1', 'col2', ..., 'colN']
```
<h3 id="summary">Informações básicas</h3>
<p>Atributos numéricos: média, desvio padrão, valores mínimo e máximo, amplitude, variância</p>

```
from pandas.api.types import is_numeric_dtype

for col in df.columns:
    if is_numeric_dtype(df[col]):
        media = df[col].mean()
        desvioPadrao = df[col].std()
        variancia = df[col].var()
        minimo = df[col].min()
        maximo = df[col].max()
        amplitude = maximo - minimo
```
<p>Atributos qualitativos: contar a frequência de cada valor</p>

```
df[nomeColQualitativa].value_counts()
```
<p>Ambos: moda</p>

```
moda = df[col].mode()
```
<h3>Describe</h3>
<p>Função que retorna as informações básicas de todos os atributos de um dataframe</p>
<p>Se o atributo é quantitativo, mostra a média, desvio padrão, mínimo, máximo e mediana; se é qualitativo, mostra o número de valores distintos e os mais frequentes</p>

```
df.describe(include='all')
```
<h3 id="sort">Ordenar valores</h3>

```
df.sort_values(by=['atributo'])
```
<h3 id="cov">Covariância</h3>

```
# valores numéricos
df.cov()

# gráfico
import seaborn as sns

sns.heatmap(df.cov(), annot=True, cmap='YlGnBu')
```
<h3>Correlação</h3>

```
# valores numéricos
df.corr()

# gráfico
import seaborn as sns

sns.heatmap(df.corr(), annot=True, cmap='YlGnBu')
```
<br />
<h2 align="center" id="vis">Data Visualization</h2>
<p align="center"><a href="#grafs">Exibir Gráficos</a> | <a href="#hist">Histogramas</a> | <a href="#bp">Boxplots</a> | <a href="#sp">Scatter Plots</a> | <a href="#sm">Scatter Plot Matrixs</a></p>

<h3 id="grafs">Exibir Gráficos</h3>
<p>O método show exibe todas as imagens</p>

```
import matplotlib.pyplot as plt

# gráfico

plt.show()
```
<h3 id="hist">Histogramas</h3>

```
df['nomeAtributo'].hist(bins=10)

# com seaborn
import seaborn as sns

sns.histplot(df['nomeAtributo'], bins=4, color="red", stat="density",kde=True,element="step")
```
<h3 id="bp">Boxplots</h3>

```
df.boxplot()

# com seaborn
import seaborn as sns

sns.boxplot(data=df, showmeans=True)
```
<h3 id="sp">Scatter Plots</h3>

```
import matplotlib.pyplot as plt

fig, axes = plt.subplots(3, 2, figsize=(12,12))
index = 0
for i in range(3):
    for j in range(i+1,4):
        ax1 = int(index/2)
        ax2 = index % 2
        axes[ax1][ax2].scatter(df[df.columns[i]], df[df.columns[j]], color='red')
        axes[ax1][ax2].set_xlabel(df.columns[i])
        axes[ax1][ax2].set_ylabel(df.columns[j])
        index = index + 1
```

```
import seaborn as sns

sns.scatterplot(data=df, x="atributo1", y="atributo2", hue="atributo3")
```
<h3 id="sm">Scatter Plot Matrix</h3>

```
import plotly.express as px

fig = px.scatter_matrix(df,
    dimensions=["atributo1", "atributo2", "atributo3", "atributo4"],
    color="classe")
#fig.update_traces(diagonal_visible=False)
fig.show()
```
<h3 id="cp">Coordenadas Paralelas</h3>

```
from pandas.plotting import parallel_coordinates

parallel_coordinates(df, 'atributo')

parallel_coordinates(df, 'atributo', cols=['at1','at2', 'at3', 'at4'])
```
<br />
<h2 align="center" id="preproc">Data Preprocessing</h2>
<p align="center"><a href="#remove">Remover Atributos</a> | <a href="#missing">Valores Ausentes</a> | <a href="#outliers">Outliers</a> | <a href="#dupl">Dados Duplicados</a> | <a href="#agg">Agregação</a> | <a href="#amostragem">Amostragem</a> | <a href="#disc">Discretização</a> | <a href="#encoding">Encoding</a> | <a href="#pca">PCA</a></p>

<h3 id="remove">Remover Atributos</h3>

```
df = df.drop(['atributo'],axis=1)
```
<p>axis: 0 para linha, 1 para coluna</p>

<h3 id="missing">Valores Ausentes</h3>
<p>Útil substituir o caracter que indica a ausência de valor por NaN</p>

```
import numpy as np

df = df.replace('?',np.NaN)

print('Valores ausentes por atributo:')
for col in df.columns:
    print('\t%s: %d' % (col, df[col].isna().sum()))
    
# substituindo valores ausentes pela mediana
for col in df.columns:
    data = df[col]
    data = data.fillna(data.median())
    df[col] = data
    
# removendo valores ausentes    
df = df.dropna()
```

```
import numpy as np
from sklearn.impute import SimpleImputer

imp = SimpleImputer(missing_values=np.nan, strategy='mean')
dados_t = imp.fit_transform(dados)
```
<h3 id="outliers">Outliers</h3>
<p>Podem ser removidos ao calcular o z-score dos dados e remover ocorrências em que esse valor é "anormal" (ex: Z > 3 ou Z <= -3)</p>

```
Z = (df - df.mean()) / df.std()

print(f'Número de objetos antes de descartar outliers: {Z.shape[0]}')

Z2 = Z.loc[((Z > -3).sum(axis=1) == 9) & ((Z <= 3).sum(axis=1) == 9), :]

print(f'Número de objetos depois de descartar outliers: {Z2.shape[0]}')
```
<p>Método IQF</p>

```
def remove_outlier_IQR(data):
    Q1 = data.quantile(0.25)
    Q3 = data.quantile(0.75)
    IQR = Q3-Q1
    LB = Q1-1.5*IQR
    UB = Q3+1.5*IQR
    return data[(data < LB) | (data > UB)]
    
df_outlier_removed = remove_outlier_IQR(df['atributo'])
update_data = df.drop(df_outlier_removed.index)
```
<p>Método LOF: vai mostrar qual deve ser removido, não permite colunas categóricas</p>

```
from sklearn.neighbors import LocalOutlierFactor
from numpy import where

lof = LocalOutlierFactor(n_neighbors=3, p=2)

# y_pred => um para cada ocorrência, os -1 são os outliers
y_pred = lof.fit_predict(data_encoded)
indexes = np.where(y_pred==-1)[0]

print(f"Número de outliers: {indexes.shape[0]}")
print(f"{indexes}")

data_encoded.drop(index=indexes, inplace=True)
```
<h3 id="dupl">Dados Duplicados</h3>

```
dups = df.duplicated()
print('Linhas duplicadas = %d' % (dups.sum()))

# descartando linhas duplicadas
df = df.drop_duplicates()
```
<h3 id="agg">Agregação</h3>
<p>Exemplo: quando há dados datetime</p>

```
monthly = df.groupby(pd.Grouper(freq='M')).sum()
```
<h3 id="amostragem">Amostragem</h3>

``` 
# amostra de tamanho 3, sem reposição
sample = data.sample(n=3)

# amostra de 1%, sem reposição
sample = data.sample(frac=0.01, random_state=1)

# com reposição
sample = data.sample(frac=0.01, replace=True, random_state=1)
```

```
from sklearn.utils.random import sample_without_replacement

index = sample_without_replacement(150, 75, random_state=0)
```
<h3 id="disc">Discretização</h3>
<p>Transformar valor contínuo num valor categórico</p>
<p>Método equal width: n é o número de bins e o value_counts() mostra quantos elementos há em cada um</p>

```
bins = pd.cut(df['atributo'],n)
bins.value_counts(sort=False)
```

```
from sklearn.preprocessing import KBinsDiscretizer

disc = KBinsDiscretizer(n_bins=3, encode='ordinal', strategy='uniform')
intervalos = disc.fit_transform(data_np)
```
<p>Método equal frequency: n é o número de bins, mas o corte será feito de modo que cada um tenha aproximadamente o mesmo número de elementos</p>

```
bins = pd.qcut(df['atributo'],n)
``` 

```
disc = KBinsDiscretizer(n_bins=3, encode='ordinal', strategy='quantile')
intervalos = disc.fit_transform(data_np)
```
<p>Método k-means</p>

```
disc = KBinsDiscretizer(n_bins=3, encode='ordinal', strategy='kmeans')
intervalos = disc.fit_transform(data_np)
```
<h3 id="encoding">Encoding</h3>
<p>Transformar atributos categóricos em numéricos</p>
<p>One Hot Encoding</p>

```
import category_encoders as ce

categoricalColumns = ['A1', 'A9', 'A10', 'A12']
encoder = ce.OneHotEncoder(cols=categoricalColumns, handle_unknown='return_nan',return_df=True,use_cat_names=True)
data_encoded = encoder.fit_transform(df)
```
<h3 id="pca">PCA</h3>
<p>Diminuir o número de atributos</p>

```
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler

scaler = StandardScaler()
df_padronizado = scaler.fit_transform(df)

pca = PCA(n_components=0.9) #quanto de variância se quer explicar
projected = pca.fit_transform(df_padronizado)

print("Componentes Principais")
print(pca.components_)

print("Variâncias")
print(pca.explained_variance_ratio_)

component_names = ['component {}'.format(i) for i in range(len(pca.components_))]

components_df = pd.DataFrame(data=pca.components_,index=component_names,columns=df.columns)
components_df.head()

print(df.loc[[0]])
print(df_padronizado[[0]])
print(projected[[0]])

instancias_classes = data["classe"]
sns.scatterplot(x=projected[:, 0], y=projected[:, 1], hue=instancias_classes) # dim1-pca, dim2-pca, classes
```
