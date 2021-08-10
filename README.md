# Analise_De_Dados

Análise De Dados Da Covid Em Angola¶
Este notebook tem como objetivo análisar a propagação da covid-19 no territorio Angolano

Contextualização do Problema
A covid-19 é um problema que está abalando não só Angola mais o mundo todo, o meu objetivo é analisarmos a propagação do covid-19 em Angola.

O meu objetivo hoje é análisar simplesmente a coluna "Total_casos"
In [72]:
#importando as bibliotecas
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import numpy as np

%matplotlib inline
Vamos Importar os dados que pegamos de um site Angolano
In [73]:
dados=pd.read_csv("summary.csv",parse_dates=["Data"])
In [74]:
#Mudando o nome dados colunas



colunas={
    
    'Novos Casos':'Novos_Casos', 
    'Total de Casos':'Total_casos', 
    'Novos Óbitos':'Novos_obitos', 
    'Total de Óbitos':'Total_Obitos',
    'Novos Recuperados':'Novos_Recuperados', 
    'Total de Recuperados':'Total_recuperados'
    
    
}

dados.rename(colunas,axis=1,inplace=True)
In [75]:
dados.head()
Out[75]:
Data	Novos_Casos	Total_casos	Novos_obitos	Total_Obitos	Novos_Recuperados	Total_recuperados
0	2020-03-21	2	2	0	0	0	0
1	2020-03-22	0	2	0	0	0	0
2	2020-03-23	1	3	0	0	0	0
3	2020-03-24	0	3	0	0	0	0
4	2020-03-25	0	3	0	0	0	0
In [76]:
#Vamos ver algumas informações
dados.info()
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 424 entries, 0 to 423
Data columns (total 7 columns):
 #   Column             Non-Null Count  Dtype         
---  ------             --------------  -----         
 0   Data               424 non-null    datetime64[ns]
 1   Novos_Casos        424 non-null    int64         
 2   Total_casos        424 non-null    int64         
 3   Novos_obitos       424 non-null    int64         
 4   Total_Obitos       424 non-null    int64         
 5   Novos_Recuperados  424 non-null    int64         
 6   Total_recuperados  424 non-null    int64         
dtypes: datetime64[ns](1), int64(6)
memory usage: 23.3 KB
In [77]:
# Veja que não temos nenhum valor NAN

dados.count()
Out[77]:
Data                 424
Novos_Casos          424
Total_casos          424
Novos_obitos         424
Total_Obitos         424
Novos_Recuperados    424
Total_recuperados    424
dtype: int64
In [78]:
#Transformando nossa coluna Data em index
dados.set_index("Data",inplace=True)
Análisando o progresso da covid-19 em 2020
In [79]:
dados.loc["2020"].count()
Out[79]:
Novos_Casos          286
Total_casos          286
Novos_obitos         286
Total_Obitos         286
Novos_Recuperados    286
Total_recuperados    286
dtype: int64
Análisando o progresso da covid-19 em 2021
In [80]:
dados.loc["2021"].count()
Out[80]:
Novos_Casos          138
Total_casos          138
Novos_obitos         138
Total_Obitos         138
Novos_Recuperados    138
Total_recuperados    138
dtype: int64
In [84]:
#Pegando os 5 ultimos dados
dados.tail()
Out[84]:
Novos_Casos	Total_casos	Novos_obitos	Total_Obitos	Novos_Recuperados	Total_recuperados
Data						
2021-05-14	335	30043	2	653	21	25411
2021-05-15	324	30367	4	657	53	25464
2021-05-16	283	30650	4	661	12	25476
2021-05-17	154	30804	18	679	280	25756
2021-05-18	258	31062	8	687	18	25774
Análisando o Total de casos em 2020
In [86]:
total_casos_2020=dados.loc["2020","Total_casos"]
In [87]:
total_casos_2020
Out[87]:
Data
2020-03-21        2
2020-03-22        2
2020-03-23        3
2020-03-24        3
2020-03-25        3
              ...  
2020-12-27    17240
2020-12-28    17296
2020-12-29    17371
2020-12-30    17433
2020-12-31    17553
Name: Total_casos, Length: 286, dtype: int64
In [89]:
# A media dos casos de 2020
total_casos_2020.mean()
Out[89]:
4698.27972027972
In [129]:
#Plotando o gráfico vemos que apartir de abrir de 2020 os casos em Angola começaram a subir
total_casos_2020.plot()
Out[129]:
<matplotlib.axes._subplots.AxesSubplot at 0x218aefdd280>

Análisando o Total de casos em 2021
In [137]:
total_casos_2021=dados.loc["2021","Total_casos"]
In [138]:
total_casos_2021.head()
Out[138]:
Data
2021-01-01    17568
2021-01-02    17608
2021-01-03    17642
2021-01-04    17684
2021-01-05    17756
Name: Total_casos, dtype: int64
In [139]:
# A media dos casos de 2021
total_casos_2021.mean()
Out[139]:
22185.41304347826
In [140]:
#Plotando o gráfico vemos que apartir de abrir de 2021 os casos em Angola continuam  a aumentar
total_casos_2021.plot()
Out[140]:
<matplotlib.axes._subplots.AxesSubplot at 0x218af08ab20>

In [ ]:
