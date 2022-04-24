<h1 align="center">Machine Learning</h1>
<p align="center"><a href="#expl">Data Exploration</a> | <a href="#vis">Data Visualization</a></p>
<br />

<h2 align="center" id="expl">Data Exploration</h2>
<p align="center"><a href="#load">Carregar Arquivos</a> | <a href="#summary">Summary</a> | <a href="#cov">Covariância e Correlação</a></p>

<h3 id="load">Carregar arquivos de dados</h3>
<p><b>read_csv</b> e <b>read_table</b> para ler dados delimitados de um arquivo, sendo respectivamente a vírgula e tab ('\t') o delimitador</p>
<p><b>read_excel</b> para ler dados de arquivos excel</p>
<p><b>read_fwf</b> para ler dados em formatos de tamanho fixo de coluna</p>
<p></p>

```
import pandas as pd
df = pd.read_csv(filepath.csv)
df = pd.read_excel(filepath.xlsx, 'Sheet')
df = pd.read_csv(filepath.txt, sep='\t')
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
<p>Atributos numéricos: média, desvio padrão, valores mínimo e máximo</p>

```
from pandas.api.types import is_numeric_dtype

for col in data.columns:
    if is_numeric_dtype(data[col]):
        media = data[col].mean()
        desvioPadrao = data[col].std()
        minimo = data[col].min()
        maximo = data[col].max()
```
<p>Atributos qualitativos: contar a frequência de cada valor</p>

```
data[nomeColQualitativa].value_counts()
```
<h3>Describe</h3>
<p>Função que retorna as informações básicas de todos os atributos de um dataframe</p>
<p>Se o atributo é quantitativo, mostra a média, desvio padrão, mínimo, máximo e mediana; se é qualitativo, mostra o número de valores distintos e os mais frequentes</p>

```
df.describe(include='all')
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
```
<h3 id="bp">Boxplots</h3>

```
df.boxplot()
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



