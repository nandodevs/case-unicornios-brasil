# Case: Maiores Unicórnios pelo Mundo

###### "Unicórnio" é um termo usado na indústria de capital de risco para descrever uma startup de capital fechado com valor superior a US$ 1 bilhão. O termo foi popularizado pela primeira vez pela capitalista de risco Aileen Lee, fundadora da Cowboy Ventures, um fundo de capital de risco com sede em Palo Alto, Califórnia.

##### Dataset:
[Baixar](https://www.kaggle.com/ramjasmaurya/unicorn-startups "Baixar")

###### Carregando bibliotecas:
```python
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import requests

import warnings
warnings.filterwarnings('ignore')
```

###### Cabeçalho do dataset
```python
base_dados.head()
```
[![](https://i.imgur.com/5VsKy7i.png)](https://i.imgur.com/5VsKy7i.png)

###### Renomeando as colunas
```python
base_dados.rename( columns = {
    'Unnamed: 0' : 'Id',
    'Company' : 'Empresa',
    'Valuation ($B)' : 'Valor ($)',
    'Date Joined' : 'Data de Adesão',
    'Country' : 'Pais',
    'City' : 'Cidade',
    'Industry': 'Setor',
    'Select Investors': 'Investidores',
}, inplace=True) 
```
------------

###### Contagem dos setores dos Unicórnios

```python
base_dados['Setor'].value_counts()
```

[![](https://i.imgur.com/sYqKRB3.png)](https://i.imgur.com/sYqKRB3.png)

###### Análise gráfica dos setores
```python
plt.figure(figsize=(15,6))
plt.title('Análise dos Principais Setores')
plt.bar(base_dados['Setor'].value_counts().index, base_dados['Setor'].value_counts());
plt.xticks(rotation=45, ha='right');
```
![](https://i.imgur.com/2JpRURT.png)

###### Resultado da Análise de Dados dos Unicórnios
```python
plt.figure(figsize=(20,8))

# Valuation
plt.subplot(2,2,1)
plt.title('Países com mais unicórnios')
x1 = Analise_Valor['Pais']
y1 =  Analise_Valor['Valor ($)']
plt.xticks(rotation=45, ha='right');
plt.plot(x1, y1)

# Setores
plt.subplot(2,2,2)
x2 = base_dados['Setor'].value_counts().index 
y2 = base_dados['Setor'].value_counts()
plt.title('Setores com maiores faturamentos')
plt.bar(x2, y2)
plt.xticks(rotation=45, ha='right');
plt.tight_layout(4)

# Ano e Valor
plt.subplot(2,2,3)
x3 = base_dados['Ano']
y3 = base_dados['Setor']
plt.title('Evolução durantes os anos')
plt.bar(x3, y3)
plt.xticks(rotation=45, ha='right');

# Ano e Valor
plt.subplot(2,2,4)
x4 = base_dados['Empresa'].head(20)
y4 = base_dados['Valor ($)'].head(20)
plt.title('Top 20 de empresas unicórnios')
plt.plot(x4, y4)
plt.xticks(rotation=45, ha='right');

plt.show()
```
##### Conclusão da Análise: Percebe-se que os Estudos Unidos são o maior produto de unicórnios no mundo, seguido da China e Reino Unido. O Brasil apesar de está bem abaixo de outros países, ele ainda consegue obter um grande valor de mercado por causa de vários unicórnios que nasceram nos últimos anos.











