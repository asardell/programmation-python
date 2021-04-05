# Rappels du langage Python🐍

## Les bases de la programmation

### Variables

On peut définir des variables locales


```python
a = 2
```


```python
b = "Hello"
```

On peut supprimer une variable de la mémoire


```python
del a
```


```python
a
```


    ---------------------------------------------------------------------------

    NameError                                 Traceback (most recent call last)

    <ipython-input-236-3f786850e387> in <module>
    ----> 1 a
    

    NameError: name 'a' is not defined


### Structure conditionnelle

⛔ Il faut bien respecter une indentation sinon on sort de la structure conditionnelle


```python
if (2 > 1):
    print("C'est vrai")
```

    C'est vrai



```python
if (2 > 3):
    print("C'est vrai")
else:
    print("c'est faux")
```

    c'est faux


La fonction *input()* permet à l'utilisateur de renseigner une valeur


```python
input()
```


```python
valeur = int(input())
if valeur < 5:
    print(str(valeur) + " est plus petit que 5")
elif valeur <= 10:
    print(str(valeur) + " est compris entre 5 et 10")
else :
    print(str(valeur) + " est plus grand que 10")
```

### Construire une fonction


```python
def calcul_IMC(poids = 60, taille = 1.70):
    imc = poids / taille**2
    return(imc)
```


```python
calcul_IMC(poids = float(input("Quel poids (en kg) ? ")) ,
           taille = float(input("Quelle taille (en metres) ? ")))
```

On est pas obligé de renseigner le nom des arguments s'ils sont renseignés dans le même ordre de l'implémentation de la fonction


```python
calcul_IMC(50,1.66)
```

L'ordre des arguments n'est pas important si on les renseigne


```python
calcul_IMC(taille = 1.66, poids = 50)
```

Avec des arguments par défaut


```python
def calcul_IMC(poids = 60, taille = 1.70):
    imc = poids / taille**2
    return(imc)
```


```python
calcul_IMC()
```


```python
calcul_IMC(poids = 80)
```

### Boucles

#### FOR

La variable *nb* correspond au nombre d'itération de la boucle

⛔ Il faut bien respecter une indentation sinon on sort de la structure


```python
nb = int(input())
for i in range(1,nb):
    un_poids = float(input("Quel poids (en kg) ? "))
    une_taille = float(input("Quelle taille (en metres) ? "))
    print(calcul_IMC(un_poids,une_taille))
```

⚠ La valeur de la borne droite d'une fonction *range()* est ouverte. Donc quand nb = 3, la boucle est lancée deux fois.

#### WHILE

⚠ Il est important d'exprimer une condition d'arrêt pour ne pas avoir de boucle infinie


```python
nb = int(input())
i = 1
while i <= nb:
    un_poids = float(input("Quel poids (en kg) ? "))
    une_taille = float(input("Quelle taille (en metres) ? "))
    print(calcul_IMC(un_poids,une_taille))
    i=i+1
```

### Liste

On utilis les crochets [ ] pour définir une liste


```python
liste = [1,2,3,4]
liste
```




    [1, 2, 3, 4]



La méthode *append( )* permet d'ajouter un élément à une liste


```python
liste.append(8)
liste
```




    [1, 2, 3, 4, 8]



La méthode *extend( )* permet d'ajouter une liste à la fin d'une liste


```python
liste.extend([1,2,3])
liste
```




    [1, 2, 3, 4, 8, 1, 2, 3]



La fonction *len( )* renvoie la longueur d'une liste


```python
len(liste)
```




    8



Pour acceder aux éléments d'une liste on utilise les crochets [ ] . <br>
⚠ L'indexation commence à 0


```python
liste[0]
```




    1




```python
liste[0:5]
```




    [1, 2, 3, 4, 8]



### Librairies

Lorsqu'on installe python, plusieurs librairies sont installées par défaut. Généralement, il est nécessaire d'en installer d'autres. Par exemple la librairie **numpy** permet de manipuler des matrices et des listes. Il est recommandé d'installer des libraries via le terminal avec la commande *pip install nom_librairie* ou par un navigateur. Une fois installé, il faut import la librairie pour  l'utiliser.


```python
import numpy
```

On recommande souvent de mettre un alias pour une librairie et éviter d'avoir à saisir le nom complet de la librairie à chaque usage de ses fonctions


```python
import numpy as np
```

#### Numpy

Voici quelques fonctions utiles de la librairie **numpy**

La fonction *linspace( )* génère une séquence de *n* nombre


```python
np.linspace(start= 0 , stop = 1, num = 9)
```




    array([0.   , 0.125, 0.25 , 0.375, 0.5  , 0.625, 0.75 , 0.875, 1.   ])



La fonction *arange( )* génère une séquence avec un step *n* <br>
⚠ La valeur *stop* n'est pas prise en compte


```python
np.arange(start= 0 , stop = 1, step = 0.1)
```




    array([0. , 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9])



# **L'essentiel de 🐼**

Dans ce notebook, nous allons voir l'essentiel de la manipulation de tableaux sous Python. Des notions importantes dans une démarche data science !

## Importer la librairie pandas

on peut donc charger la librairie, la plupart du temps on lui associe un alias


```python
import pandas as pd
```

⚠ Certaines fonctionnalités sont disponibles qu'à partir de certaines versions de pandas.


```python
#Afficher la version de pandas
pd.__version__
```




    '1.2.3'



## Importer un jeu de données

On importe le jeu de données avec la méthode read_*mon_format*() selon l'extension du fichier



```python
df = pd.read_csv("../Dataset/Titanic.csv")
```

On affiche un extrait du tableau avec la méthode *head()*


```python
df.head(2)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Unnamed: 0</th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>1st</td>
      <td>29.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>Allison, Miss Helen Loraine</td>
      <td>1st</td>
      <td>2.0</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



On supprime la première colonne inutile


```python
df.drop(['Unnamed: 0'], axis=1, inplace=True)
```

On utilise la méthode *shape* pour afficher le nombre de lignes et colonnes


```python
df.shape
```




    (1313, 6)



On utilise  la méthode *info()* ou *dtypes* pour afficher une description du data frame


```python
df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1313 entries, 0 to 1312
    Data columns (total 6 columns):
     #   Column    Non-Null Count  Dtype  
    ---  ------    --------------  -----  
     0   Name      1313 non-null   object 
     1   PClass    1313 non-null   object 
     2   Age       756 non-null    float64
     3   Sex       1313 non-null   object 
     4   Survived  1313 non-null   int64  
     5   SexCode   1313 non-null   int64  
    dtypes: float64(1), int64(2), object(3)
    memory usage: 61.7+ KB



```python
df.dtypes
```




    Name         object
    PClass       object
    Age         float64
    Sex          object
    Survived      int64
    SexCode       int64
    dtype: object



## Manipuler un jeu de données

### Interroger le data frame avec le nom des colonnes


```python
df.PClass
```




    0       1st
    1       1st
    2       1st
    3       1st
    4       1st
           ... 
    1308    3rd
    1309    3rd
    1310    3rd
    1311    3rd
    1312    3rd
    Name: PClass, Length: 1313, dtype: object




```python
df['PClass']
```




    0       1st
    1       1st
    2       1st
    3       1st
    4       1st
           ... 
    1308    3rd
    1309    3rd
    1310    3rd
    1311    3rd
    1312    3rd
    Name: PClass, Length: 1313, dtype: object



Tester le type de l'objet que renvoie la méthode *type()* sur une colonne du dataframe


```python
type(df['PClass'])
```




    pandas.core.series.Series



Nous n'avons pas l'information sur le type des données que rassemble cette colonne. En revanche, l'objet est une série pandas. Avec pandas, les différents vecteurs ou colonnes d''une dataframe sont appelées "Series". Un DataFrame pandas est donc une collection de pd.Series.

Sélectionner deux colonnes en mêmes temps


```python
df[['Name','PClass']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>1st</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Allison, Miss Helen Loraine</td>
      <td>1st</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Allison, Mr Hudson Joshua Creighton</td>
      <td>1st</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Allison, Mrs Hudson JC (Bessie Waldo Daniels)</td>
      <td>1st</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Allison, Master Hudson Trevor</td>
      <td>1st</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1308</th>
      <td>Zakarian, Mr Artun</td>
      <td>3rd</td>
    </tr>
    <tr>
      <th>1309</th>
      <td>Zakarian, Mr Maprieder</td>
      <td>3rd</td>
    </tr>
    <tr>
      <th>1310</th>
      <td>Zenni, Mr Philip</td>
      <td>3rd</td>
    </tr>
    <tr>
      <th>1311</th>
      <td>Lievens, Mr Rene</td>
      <td>3rd</td>
    </tr>
    <tr>
      <th>1312</th>
      <td>Zimmerman, Leo</td>
      <td>3rd</td>
    </tr>
  </tbody>
</table>
<p>1313 rows × 2 columns</p>
</div>



Il suffit de donner une liste avec des noms de colonnes. <br> 
⚠ L'ordre des colonnes renvoyé est le même que celles de la liste


```python
df[['PClass','Name']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PClass</th>
      <th>Name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1st</td>
      <td>Allen, Miss Elisabeth Walton</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1st</td>
      <td>Allison, Miss Helen Loraine</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1st</td>
      <td>Allison, Mr Hudson Joshua Creighton</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1st</td>
      <td>Allison, Mrs Hudson JC (Bessie Waldo Daniels)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1st</td>
      <td>Allison, Master Hudson Trevor</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1308</th>
      <td>3rd</td>
      <td>Zakarian, Mr Artun</td>
    </tr>
    <tr>
      <th>1309</th>
      <td>3rd</td>
      <td>Zakarian, Mr Maprieder</td>
    </tr>
    <tr>
      <th>1310</th>
      <td>3rd</td>
      <td>Zenni, Mr Philip</td>
    </tr>
    <tr>
      <th>1311</th>
      <td>3rd</td>
      <td>Lievens, Mr Rene</td>
    </tr>
    <tr>
      <th>1312</th>
      <td>3rd</td>
      <td>Zimmerman, Leo</td>
    </tr>
  </tbody>
</table>
<p>1313 rows × 2 columns</p>
</div>



Des lors que l'objet retouné a plus de 1 une colonne, c'est un objet pandas *DataFrame* et non pandas *Series*


```python
type(df[['PClass','Name']])
```




    pandas.core.frame.DataFrame



### Interroger le data frame avec les indices lignes/colonnes

La méthode *iloc[ ]* permet d'interroger un data frame Pandas avec les indices


```python
#Afficher la première ligne
df.iloc[0]
```




    Name        Allen, Miss Elisabeth Walton
    PClass                               1st
    Age                                 29.0
    Sex                               female
    Survived                               1
    SexCode                                1
    Name: 0, dtype: object




```python
#Afficher la première colonne
df.iloc[:,0]
```




    0                        Allen, Miss Elisabeth Walton
    1                         Allison, Miss Helen Loraine
    2                 Allison, Mr Hudson Joshua Creighton
    3       Allison, Mrs Hudson JC (Bessie Waldo Daniels)
    4                       Allison, Master Hudson Trevor
                                ...                      
    1308                               Zakarian, Mr Artun
    1309                           Zakarian, Mr Maprieder
    1310                                 Zenni, Mr Philip
    1311                                 Lievens, Mr Rene
    1312                                   Zimmerman, Leo
    Name: Name, Length: 1313, dtype: object




```python
#Afficher les 3 premières lignes de la première colonne
df.iloc[:3,0]
```




    0           Allen, Miss Elisabeth Walton
    1            Allison, Miss Helen Loraine
    2    Allison, Mr Hudson Joshua Creighton
    Name: Name, dtype: object




```python
#Afficher les 3 premières lignes
df.iloc[0:3,:]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>1st</td>
      <td>29.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Allison, Miss Helen Loraine</td>
      <td>1st</td>
      <td>2.0</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Allison, Mr Hudson Joshua Creighton</td>
      <td>1st</td>
      <td>30.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



⚠ En python, la borne extérieure d'une <font color=red> plage  </font> est toujours ouverte, c'est pourquoi la ligne d'indice 3 correspondant à la ligne 4 ne s'affiche pas contrairement à une liste


```python
#Afficher les 3 premières lignes
df.iloc[ [0,1,2,3] ,:]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>1st</td>
      <td>29.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Allison, Miss Helen Loraine</td>
      <td>1st</td>
      <td>2.0</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Allison, Mr Hudson Joshua Creighton</td>
      <td>1st</td>
      <td>30.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Allison, Mrs Hudson JC (Bessie Waldo Daniels)</td>
      <td>1st</td>
      <td>25.0</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Afficher la dernière lignes
df.iloc[-1,:]
```




    Name        Zimmerman, Leo
    PClass                 3rd
    Age                   29.0
    Sex                   male
    Survived                 0
    SexCode                  0
    Name: 1312, dtype: object



La méthode *loc[ ]* permet d'interroger un data frame Pandas avec le nom des lignes **et** des colonnes


```python
df.loc[:, ['PClass','Name']]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PClass</th>
      <th>Name</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1st</td>
      <td>Allen, Miss Elisabeth Walton</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1st</td>
      <td>Allison, Miss Helen Loraine</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1st</td>
      <td>Allison, Mr Hudson Joshua Creighton</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1st</td>
      <td>Allison, Mrs Hudson JC (Bessie Waldo Daniels)</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1st</td>
      <td>Allison, Master Hudson Trevor</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1308</th>
      <td>3rd</td>
      <td>Zakarian, Mr Artun</td>
    </tr>
    <tr>
      <th>1309</th>
      <td>3rd</td>
      <td>Zakarian, Mr Maprieder</td>
    </tr>
    <tr>
      <th>1310</th>
      <td>3rd</td>
      <td>Zenni, Mr Philip</td>
    </tr>
    <tr>
      <th>1311</th>
      <td>3rd</td>
      <td>Lievens, Mr Rene</td>
    </tr>
    <tr>
      <th>1312</th>
      <td>3rd</td>
      <td>Zimmerman, Leo</td>
    </tr>
  </tbody>
</table>
<p>1313 rows × 2 columns</p>
</div>



L'association des méthodes *columns* et *difference* permet d'afficher toutes les colonnes d'un data frame exceptées celles mentionnées


```python
df.columns.difference(['Age','SexCode'])
```




    Index(['Name', 'PClass', 'Sex', 'Survived'], dtype='object')



On réutilise cette liste sans les variables mentionnées directement dans l'indexation du data frame


```python
df[  df.columns.difference(['Age','SexCode'])  ].head(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Sex</th>
      <th>Survived</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>1st</td>
      <td>female</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Allison, Miss Helen Loraine</td>
      <td>1st</td>
      <td>female</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Allison, Mr Hudson Joshua Creighton</td>
      <td>1st</td>
      <td>male</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



📢 Attention : Lorqu'on utilise cette méthode, la liste des colonnes affichées est triée par ordre alphabetique ce qui conduit à une réorganisation du tableau de départ


```python
df.columns
```




    Index(['Name', 'PClass', 'Age', 'Sex', 'Survived', 'SexCode'], dtype='object')




```python
df.columns.difference([''])
```




    Index(['Age', 'Name', 'PClass', 'Sex', 'SexCode', 'Survived'], dtype='object')



### Interroger le data frame avec des filtres

Pour cela on utilise les opérateurs logiques qui permettent de renvoyer des booléens.


```python
#Tester une égalité
df.PClass == "1st"
```




    0        True
    1        True
    2        True
    3        True
    4        True
            ...  
    1308    False
    1309    False
    1310    False
    1311    False
    1312    False
    Name: PClass, Length: 1313, dtype: bool




```python
df[df.PClass == "1st"]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>1st</td>
      <td>29.00</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Allison, Miss Helen Loraine</td>
      <td>1st</td>
      <td>2.00</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Allison, Mr Hudson Joshua Creighton</td>
      <td>1st</td>
      <td>30.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Allison, Mrs Hudson JC (Bessie Waldo Daniels)</td>
      <td>1st</td>
      <td>25.00</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Allison, Master Hudson Trevor</td>
      <td>1st</td>
      <td>0.92</td>
      <td>male</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>317</th>
      <td>Robbins, Mr Victor</td>
      <td>1st</td>
      <td>NaN</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>318</th>
      <td>Segesser, Mlle Emma</td>
      <td>1st</td>
      <td>NaN</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>319</th>
      <td>Seredeca, Ms</td>
      <td>1st</td>
      <td>NaN</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>320</th>
      <td>Ward, Ms Anna</td>
      <td>1st</td>
      <td>NaN</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>321</th>
      <td>Wilson, Ms Helen</td>
      <td>1st</td>
      <td>NaN</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>322 rows × 6 columns</p>
</div>




```python
#Tester une différence
df.PClass != "3rd"
```




    0        True
    1        True
    2        True
    3        True
    4        True
            ...  
    1308    False
    1309    False
    1310    False
    1311    False
    1312    False
    Name: PClass, Length: 1313, dtype: bool




```python
df[df.PClass != "3rd"]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>1st</td>
      <td>29.00</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Allison, Miss Helen Loraine</td>
      <td>1st</td>
      <td>2.00</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Allison, Mr Hudson Joshua Creighton</td>
      <td>1st</td>
      <td>30.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Allison, Mrs Hudson JC (Bessie Waldo Daniels)</td>
      <td>1st</td>
      <td>25.00</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Allison, Master Hudson Trevor</td>
      <td>1st</td>
      <td>0.92</td>
      <td>male</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>597</th>
      <td>Yrois, Miss Henriette</td>
      <td>2nd</td>
      <td>NaN</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>598</th>
      <td>Aldworth, Mr Charles Augustus</td>
      <td>2nd</td>
      <td>30.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>599</th>
      <td>Brown, Miss Mildred</td>
      <td>2nd</td>
      <td>24.00</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>600</th>
      <td>Pernot, Mr Rene</td>
      <td>2nd</td>
      <td>NaN</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>601</th>
      <td>Swane, Mr George</td>
      <td>2nd</td>
      <td>18.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>602 rows × 6 columns</p>
</div>




```python
#Tester si supérieur
df.Age > 20
```




    0        True
    1       False
    2        True
    3        True
    4       False
            ...  
    1308     True
    1309     True
    1310     True
    1311     True
    1312     True
    Name: Age, Length: 1313, dtype: bool




```python
df[df.Age > 20]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>1st</td>
      <td>29.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Allison, Mr Hudson Joshua Creighton</td>
      <td>1st</td>
      <td>30.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Allison, Mrs Hudson JC (Bessie Waldo Daniels)</td>
      <td>1st</td>
      <td>25.0</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Anderson, Mr Harry</td>
      <td>1st</td>
      <td>47.0</td>
      <td>male</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Andrews, Miss Kornelia Theodosia</td>
      <td>1st</td>
      <td>63.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1308</th>
      <td>Zakarian, Mr Artun</td>
      <td>3rd</td>
      <td>27.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1309</th>
      <td>Zakarian, Mr Maprieder</td>
      <td>3rd</td>
      <td>26.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1310</th>
      <td>Zenni, Mr Philip</td>
      <td>3rd</td>
      <td>22.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1311</th>
      <td>Lievens, Mr Rene</td>
      <td>3rd</td>
      <td>24.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1312</th>
      <td>Zimmerman, Leo</td>
      <td>3rd</td>
      <td>29.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>584 rows × 6 columns</p>
</div>




```python
#Tester si comris dans des bornes
(df.Age > 15) & (df.Age < 30)
```




    0        True
    1       False
    2       False
    3        True
    4       False
            ...  
    1308     True
    1309     True
    1310     True
    1311     True
    1312     True
    Name: Age, Length: 1313, dtype: bool




```python
df[(df.Age > 15) & (df.Age < 30)]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>1st</td>
      <td>29.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Allison, Mrs Hudson JC (Bessie Waldo Daniels)</td>
      <td>1st</td>
      <td>25.0</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>11</th>
      <td>Astor, Mrs John Jacob (Madeleine Talmadge Force)</td>
      <td>1st</td>
      <td>19.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>16</th>
      <td>Baxter, Mr Quigg Edmond</td>
      <td>1st</td>
      <td>24.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>20</th>
      <td>Behr, Mr Karl Howell</td>
      <td>1st</td>
      <td>26.0</td>
      <td>male</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1308</th>
      <td>Zakarian, Mr Artun</td>
      <td>3rd</td>
      <td>27.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1309</th>
      <td>Zakarian, Mr Maprieder</td>
      <td>3rd</td>
      <td>26.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1310</th>
      <td>Zenni, Mr Philip</td>
      <td>3rd</td>
      <td>22.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1311</th>
      <td>Lievens, Mr Rene</td>
      <td>3rd</td>
      <td>24.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1312</th>
      <td>Zimmerman, Leo</td>
      <td>3rd</td>
      <td>29.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>328 rows × 6 columns</p>
</div>




```python
#Tester avec deux valeurs possibles 
(df.PClass == "1st") | (df.PClass == "2nd")
```




    0        True
    1        True
    2        True
    3        True
    4        True
            ...  
    1308    False
    1309    False
    1310    False
    1311    False
    1312    False
    Name: PClass, Length: 1313, dtype: bool




```python
df[(df.PClass == "1st") | (df.PClass == "2nd")]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>1st</td>
      <td>29.00</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Allison, Miss Helen Loraine</td>
      <td>1st</td>
      <td>2.00</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Allison, Mr Hudson Joshua Creighton</td>
      <td>1st</td>
      <td>30.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Allison, Mrs Hudson JC (Bessie Waldo Daniels)</td>
      <td>1st</td>
      <td>25.00</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Allison, Master Hudson Trevor</td>
      <td>1st</td>
      <td>0.92</td>
      <td>male</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>597</th>
      <td>Yrois, Miss Henriette</td>
      <td>2nd</td>
      <td>NaN</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>598</th>
      <td>Aldworth, Mr Charles Augustus</td>
      <td>2nd</td>
      <td>30.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>599</th>
      <td>Brown, Miss Mildred</td>
      <td>2nd</td>
      <td>24.00</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>600</th>
      <td>Pernot, Mr Rene</td>
      <td>2nd</td>
      <td>NaN</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>601</th>
      <td>Swane, Mr George</td>
      <td>2nd</td>
      <td>18.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>602 rows × 6 columns</p>
</div>




```python
#Tester si compris dans la liste
df.PClass.isin(['1st', '2nd'])
```




    0        True
    1        True
    2        True
    3        True
    4        True
            ...  
    1308    False
    1309    False
    1310    False
    1311    False
    1312    False
    Name: PClass, Length: 1313, dtype: bool




```python
df[df.PClass.isin(['1st', '2nd'])]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>1st</td>
      <td>29.00</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Allison, Miss Helen Loraine</td>
      <td>1st</td>
      <td>2.00</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Allison, Mr Hudson Joshua Creighton</td>
      <td>1st</td>
      <td>30.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Allison, Mrs Hudson JC (Bessie Waldo Daniels)</td>
      <td>1st</td>
      <td>25.00</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Allison, Master Hudson Trevor</td>
      <td>1st</td>
      <td>0.92</td>
      <td>male</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>597</th>
      <td>Yrois, Miss Henriette</td>
      <td>2nd</td>
      <td>NaN</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>598</th>
      <td>Aldworth, Mr Charles Augustus</td>
      <td>2nd</td>
      <td>30.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>599</th>
      <td>Brown, Miss Mildred</td>
      <td>2nd</td>
      <td>24.00</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>600</th>
      <td>Pernot, Mr Rene</td>
      <td>2nd</td>
      <td>NaN</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>601</th>
      <td>Swane, Mr George</td>
      <td>2nd</td>
      <td>18.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>602 rows × 6 columns</p>
</div>




```python
#Tester si n'est pas compris dans la liste
~ df.PClass.isin(['1st', '2nd'])
```




    0       False
    1       False
    2       False
    3       False
    4       False
            ...  
    1308     True
    1309     True
    1310     True
    1311     True
    1312     True
    Name: PClass, Length: 1313, dtype: bool




```python
~pd.Series([True,False,True,True])
```




    0    False
    1     True
    2    False
    3    False
    dtype: bool



En réalité, l'opérateur **~** permet de renvoyer l'inverse des tests logiques effectués


```python
df[~ df.PClass.isin(['1st', '2nd'])]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>602</th>
      <td>Abbing, Mr Anthony</td>
      <td>3rd</td>
      <td>42.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>603</th>
      <td>Abbott, Master Eugene Joseph</td>
      <td>3rd</td>
      <td>13.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>604</th>
      <td>Abbott, Mr Rossmore Edward</td>
      <td>3rd</td>
      <td>16.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>605</th>
      <td>Abbott, Mrs Stanton (Rosa)</td>
      <td>3rd</td>
      <td>35.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>606</th>
      <td>Abelseth, Miss Anna Karen</td>
      <td>3rd</td>
      <td>16.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1308</th>
      <td>Zakarian, Mr Artun</td>
      <td>3rd</td>
      <td>27.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1309</th>
      <td>Zakarian, Mr Maprieder</td>
      <td>3rd</td>
      <td>26.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1310</th>
      <td>Zenni, Mr Philip</td>
      <td>3rd</td>
      <td>22.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1311</th>
      <td>Lievens, Mr Rene</td>
      <td>3rd</td>
      <td>24.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1312</th>
      <td>Zimmerman, Leo</td>
      <td>3rd</td>
      <td>29.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>711 rows × 6 columns</p>
</div>



Les méthodes *isna()* et *notna()* permettent d'effectuer des filtres sur des valeurs manquantes


```python
df.Age.isna()
```




    0       False
    1       False
    2       False
    3       False
    4       False
            ...  
    1308    False
    1309    False
    1310    False
    1311    False
    1312    False
    Name: Age, Length: 1313, dtype: bool




```python
df[df.Age.isna()]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>12</th>
      <td>Aubert, Mrs Leontine Pauline</td>
      <td>1st</td>
      <td>NaN</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>13</th>
      <td>Barkworth, Mr Algernon H</td>
      <td>1st</td>
      <td>NaN</td>
      <td>male</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>Baumann, Mr John D</td>
      <td>1st</td>
      <td>NaN</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>29</th>
      <td>Borebank, Mr John James</td>
      <td>1st</td>
      <td>NaN</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>32</th>
      <td>Bradley, Mr George</td>
      <td>1st</td>
      <td>NaN</td>
      <td>male</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1300</th>
      <td>Wiseman, Mr Phillippe</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1302</th>
      <td>Yalsevac, Mr Ivan</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>male</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1305</th>
      <td>Youssef, Mr Gerios</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1306</th>
      <td>Zabour, Miss Hileni</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1307</th>
      <td>Zabour, Miss Tamini</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>557 rows × 6 columns</p>
</div>




```python
df.Age.notna()
```




    0       True
    1       True
    2       True
    3       True
    4       True
            ... 
    1308    True
    1309    True
    1310    True
    1311    True
    1312    True
    Name: Age, Length: 1313, dtype: bool




```python
df[df.Age.notna()]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>1st</td>
      <td>29.00</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Allison, Miss Helen Loraine</td>
      <td>1st</td>
      <td>2.00</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Allison, Mr Hudson Joshua Creighton</td>
      <td>1st</td>
      <td>30.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Allison, Mrs Hudson JC (Bessie Waldo Daniels)</td>
      <td>1st</td>
      <td>25.00</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Allison, Master Hudson Trevor</td>
      <td>1st</td>
      <td>0.92</td>
      <td>male</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1308</th>
      <td>Zakarian, Mr Artun</td>
      <td>3rd</td>
      <td>27.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1309</th>
      <td>Zakarian, Mr Maprieder</td>
      <td>3rd</td>
      <td>26.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1310</th>
      <td>Zenni, Mr Philip</td>
      <td>3rd</td>
      <td>22.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1311</th>
      <td>Lievens, Mr Rene</td>
      <td>3rd</td>
      <td>24.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1312</th>
      <td>Zimmerman, Leo</td>
      <td>3rd</td>
      <td>29.00</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>756 rows × 6 columns</p>
</div>



### Trier un jeu de données

On utilise la méthode *sort_values()* pour trier un data frame ou une série pandas


```python
#On trie la série Age
df.Age.sort_values()
```




    763     0.17
    751     0.33
    544     0.80
    616     0.83
    358     0.83
            ... 
    1300     NaN
    1302     NaN
    1305     NaN
    1306     NaN
    1307     NaN
    Name: Age, Length: 1313, dtype: float64




```python
#On trie la série Age par ordre décroissant
df.Age.sort_values(ascending=False)
```




    505     71.0
    119     71.0
    9       71.0
    72      70.0
    73      69.0
            ... 
    1300     NaN
    1302     NaN
    1305     NaN
    1306     NaN
    1307     NaN
    Name: Age, Length: 1313, dtype: float64




```python
# On trie le data frame
df.sort_values(by = 'Age', ascending=False)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>505</th>
      <td>Mitchell, Mr Henry Michael</td>
      <td>2nd</td>
      <td>71.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>119</th>
      <td>Goldschmidt, Mr George B</td>
      <td>1st</td>
      <td>71.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>Artagaveytia, Mr Ramon</td>
      <td>1st</td>
      <td>71.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>72</th>
      <td>Crosby, Captain Edward Gifford</td>
      <td>1st</td>
      <td>70.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>73</th>
      <td>Crosby, Mrs Edward Gifford (Catherine Elizabet...</td>
      <td>1st</td>
      <td>69.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1300</th>
      <td>Wiseman, Mr Phillippe</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1302</th>
      <td>Yalsevac, Mr Ivan</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>male</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1305</th>
      <td>Youssef, Mr Gerios</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1306</th>
      <td>Zabour, Miss Hileni</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1307</th>
      <td>Zabour, Miss Tamini</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>1313 rows × 6 columns</p>
</div>




```python
# On trie le data frame avec selon plusieurs colonnes
df.sort_values(by = ['PClass','Age'], ascending=[True,False])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>9</th>
      <td>Artagaveytia, Mr Ramon</td>
      <td>1st</td>
      <td>71.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>119</th>
      <td>Goldschmidt, Mr George B</td>
      <td>1st</td>
      <td>71.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>72</th>
      <td>Crosby, Captain Edward Gifford</td>
      <td>1st</td>
      <td>70.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>73</th>
      <td>Crosby, Mrs Edward Gifford (Catherine Elizabet...</td>
      <td>1st</td>
      <td>69.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>252</th>
      <td>Straus, Mr Isidor</td>
      <td>1st</td>
      <td>67.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1300</th>
      <td>Wiseman, Mr Phillippe</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1302</th>
      <td>Yalsevac, Mr Ivan</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>male</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1305</th>
      <td>Youssef, Mr Gerios</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1306</th>
      <td>Zabour, Miss Hileni</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1307</th>
      <td>Zabour, Miss Tamini</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
<p>1313 rows × 6 columns</p>
</div>



## Exploration statistique sur un jeu de données

On utilise souvent la librairie *numpy* avec pandas


```python
import numpy as np
```

### Indicateurs statistiques


```python
df.Age.mean()
```




    30.397989417989415




```python
df.Age.median()
```




    28.0




```python
df.Age.max()
```




    71.0




```python
df.Age.std()
```




    14.259048710359023




```python
df.Age.var()
```




    203.32047012439133




```python
df.Age.quantile([.1, .5])
```




    0.1    16.0
    0.5    28.0
    Name: Age, dtype: float64




```python
df.Age.quantile(np.linspace(start = 0, stop = 1, num= 11))
```




    0.0     0.17
    0.1    16.00
    0.2    20.00
    0.3    22.00
    0.4    25.00
    0.5    28.00
    0.6    32.00
    0.7    36.00
    0.8    43.00
    0.9    50.00
    1.0    71.00
    Name: Age, dtype: float64



La méthode *describe()* calcule des statistiques élémentaires sur les données


```python
df.describe()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>756.000000</td>
      <td>1313.000000</td>
      <td>1313.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>30.397989</td>
      <td>0.342727</td>
      <td>0.351866</td>
    </tr>
    <tr>
      <th>std</th>
      <td>14.259049</td>
      <td>0.474802</td>
      <td>0.477734</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.170000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>21.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>28.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>39.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>71.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>



L'argument *include* permet de prendre en compte toutes les colonnes quelques soit leur type


```python
df.describe(include = "all")
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1313</td>
      <td>1313</td>
      <td>756.000000</td>
      <td>1313</td>
      <td>1313.000000</td>
      <td>1313.000000</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>1310</td>
      <td>3</td>
      <td>NaN</td>
      <td>2</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>top</th>
      <td>Connolly, Miss Kate</td>
      <td>3rd</td>
      <td>NaN</td>
      <td>male</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>2</td>
      <td>711</td>
      <td>NaN</td>
      <td>851</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>30.397989</td>
      <td>NaN</td>
      <td>0.342727</td>
      <td>0.351866</td>
    </tr>
    <tr>
      <th>std</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>14.259049</td>
      <td>NaN</td>
      <td>0.474802</td>
      <td>0.477734</td>
    </tr>
    <tr>
      <th>min</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>0.170000</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>21.000000</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>28.000000</td>
      <td>NaN</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>39.000000</td>
      <td>NaN</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>NaN</td>
      <td>NaN</td>
      <td>71.000000</td>
      <td>NaN</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.describe(exclude=[np.number])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Sex</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>1313</td>
      <td>1313</td>
      <td>1313</td>
    </tr>
    <tr>
      <th>unique</th>
      <td>1310</td>
      <td>3</td>
      <td>2</td>
    </tr>
    <tr>
      <th>top</th>
      <td>Connolly, Miss Kate</td>
      <td>3rd</td>
      <td>male</td>
    </tr>
    <tr>
      <th>freq</th>
      <td>2</td>
      <td>711</td>
      <td>851</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.describe(include=[np.number])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>756.000000</td>
      <td>1313.000000</td>
      <td>1313.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>30.397989</td>
      <td>0.342727</td>
      <td>0.351866</td>
    </tr>
    <tr>
      <th>std</th>
      <td>14.259049</td>
      <td>0.474802</td>
      <td>0.477734</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.170000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>21.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>28.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>39.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>71.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>



L'argument *percentiles* permet d'avoir la main sur les quantiles affichés


```python
df.describe(percentiles=np.linspace(start = 0, stop = 1, num= 11))
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>756.000000</td>
      <td>1313.000000</td>
      <td>1313.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>30.397989</td>
      <td>0.342727</td>
      <td>0.351866</td>
    </tr>
    <tr>
      <th>std</th>
      <td>14.259049</td>
      <td>0.474802</td>
      <td>0.477734</td>
    </tr>
    <tr>
      <th>min</th>
      <td>0.170000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>0%</th>
      <td>0.170000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>10%</th>
      <td>16.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>20%</th>
      <td>20.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>30%</th>
      <td>22.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>40%</th>
      <td>25.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>28.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>60%</th>
      <td>32.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <th>70%</th>
      <td>36.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>80%</th>
      <td>43.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>90%</th>
      <td>50.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>100%</th>
      <td>71.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>71.000000</td>
      <td>1.000000</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>



La méthode *unique()* renvoie une liste des valeurs uniques d'une *Series* pandas


```python
df.PClass.unique()
```




    array(['1st', '2nd', '3rd'], dtype=object)



La méthode *nunique()* compte le nombre de valeurs uniques d'une *Series* pandas


```python
df.PClass.nunique()
```




    3



Cela fonctionne aussi sur un data frame


```python
df.nunique()
```




    Name        1310
    PClass         3
    Age           75
    Sex            2
    Survived       2
    SexCode        2
    dtype: int64



La méthode *value_counts()* renvoie un tri à plat d'une *Series* pandas


```python
df.PClass.value_counts()
```




    3rd    711
    1st    322
    2nd    280
    Name: PClass, dtype: int64




```python
#en pourcentage
df.PClass.value_counts(normalize=True)
```




    3rd    0.541508
    1st    0.245240
    2nd    0.213252
    Name: PClass, dtype: float64



### Grouper les données

#### Tableaux croisés

La méthode *crosstab()* permet de calculer un tableau croisé


```python
pd.crosstab(df.PClass, df.Sex, margins=True)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Sex</th>
      <th>female</th>
      <th>male</th>
      <th>All</th>
    </tr>
    <tr>
      <th>PClass</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1st</th>
      <td>143</td>
      <td>179</td>
      <td>322</td>
    </tr>
    <tr>
      <th>2nd</th>
      <td>107</td>
      <td>173</td>
      <td>280</td>
    </tr>
    <tr>
      <th>3rd</th>
      <td>212</td>
      <td>499</td>
      <td>711</td>
    </tr>
    <tr>
      <th>All</th>
      <td>462</td>
      <td>851</td>
      <td>1313</td>
    </tr>
  </tbody>
</table>
</div>




```python
#pourcentage total général
pd.crosstab(df.PClass, df.Sex, margins=True, normalize = True)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Sex</th>
      <th>female</th>
      <th>male</th>
      <th>All</th>
    </tr>
    <tr>
      <th>PClass</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1st</th>
      <td>0.108911</td>
      <td>0.136329</td>
      <td>0.245240</td>
    </tr>
    <tr>
      <th>2nd</th>
      <td>0.081493</td>
      <td>0.131759</td>
      <td>0.213252</td>
    </tr>
    <tr>
      <th>3rd</th>
      <td>0.161462</td>
      <td>0.380046</td>
      <td>0.541508</td>
    </tr>
    <tr>
      <th>All</th>
      <td>0.351866</td>
      <td>0.648134</td>
      <td>1.000000</td>
    </tr>
  </tbody>
</table>
</div>



Pour un tableau croisé en pourcentage on utilise la méthode *apply()* permet de mapper une fonction sur tout les éléments de l'objet


```python
#pourcentage colonne
pd.crosstab(df.PClass, df.Sex).apply(lambda x: x/x.sum(), axis=0)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Sex</th>
      <th>female</th>
      <th>male</th>
    </tr>
    <tr>
      <th>PClass</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1st</th>
      <td>0.309524</td>
      <td>0.210341</td>
    </tr>
    <tr>
      <th>2nd</th>
      <td>0.231602</td>
      <td>0.203290</td>
    </tr>
    <tr>
      <th>3rd</th>
      <td>0.458874</td>
      <td>0.586369</td>
    </tr>
  </tbody>
</table>
</div>




```python
#pourcentage ligne
pd.crosstab(df.PClass, df.Sex).apply(lambda x: x/x.sum(), axis=1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Sex</th>
      <th>female</th>
      <th>male</th>
    </tr>
    <tr>
      <th>PClass</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1st</th>
      <td>0.444099</td>
      <td>0.555901</td>
    </tr>
    <tr>
      <th>2nd</th>
      <td>0.382143</td>
      <td>0.617857</td>
    </tr>
    <tr>
      <th>3rd</th>
      <td>0.298172</td>
      <td>0.701828</td>
    </tr>
  </tbody>
</table>
</div>



#### Agrégation

On utilise la méthode *groupby()* pour grouper les données. Il faut ensuite utiliser *agg()* pour calculer des indicateurs pour chaque groupe


```python
df.groupby(['PClass']).Age.agg([min, max])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>min</th>
      <th>max</th>
    </tr>
    <tr>
      <th>PClass</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1st</th>
      <td>0.92</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>2nd</th>
      <td>0.80</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>3rd</th>
      <td>0.17</td>
      <td>65.0</td>
    </tr>
  </tbody>
</table>
</div>



On peut grouper les données selon plusieurs variables


```python
df.groupby(['PClass','Sex']).Age.agg([min, max])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>min</th>
      <th>max</th>
    </tr>
    <tr>
      <th>PClass</th>
      <th>Sex</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">1st</th>
      <th>female</th>
      <td>2.00</td>
      <td>69.0</td>
    </tr>
    <tr>
      <th>male</th>
      <td>0.92</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">2nd</th>
      <th>female</th>
      <td>1.00</td>
      <td>57.0</td>
    </tr>
    <tr>
      <th>male</th>
      <td>0.80</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">3rd</th>
      <th>female</th>
      <td>0.17</td>
      <td>63.0</td>
    </tr>
    <tr>
      <th>male</th>
      <td>0.33</td>
      <td>65.0</td>
    </tr>
  </tbody>
</table>
</div>



On peut aussi utiliser un dictionnaire


```python
df_agg = df.groupby(['PClass','Sex']).agg( { 'Age' : ['min','max'] , 'PClass' : 'count'  })
df_agg
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }

    .dataframe thead tr:last-of-type th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th></th>
      <th colspan="2" halign="left">Age</th>
      <th>PClass</th>
    </tr>
    <tr>
      <th></th>
      <th></th>
      <th>min</th>
      <th>max</th>
      <th>count</th>
    </tr>
    <tr>
      <th>PClass</th>
      <th>Sex</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">1st</th>
      <th>female</th>
      <td>2.00</td>
      <td>69.0</td>
      <td>143</td>
    </tr>
    <tr>
      <th>male</th>
      <td>0.92</td>
      <td>71.0</td>
      <td>179</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">2nd</th>
      <th>female</th>
      <td>1.00</td>
      <td>57.0</td>
      <td>107</td>
    </tr>
    <tr>
      <th>male</th>
      <td>0.80</td>
      <td>71.0</td>
      <td>173</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">3rd</th>
      <th>female</th>
      <td>0.17</td>
      <td>63.0</td>
      <td>212</td>
    </tr>
    <tr>
      <th>male</th>
      <td>0.33</td>
      <td>65.0</td>
      <td>499</td>
    </tr>
  </tbody>
</table>
</div>



Ce code permet d'éliminer les  deux niveaux d'index colonne en concatenant les noms


```python
df_agg.columns = ['_'.join(col) for col in df_agg.columns]
df_agg
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>Age_min</th>
      <th>Age_max</th>
      <th>PClass_count</th>
    </tr>
    <tr>
      <th>PClass</th>
      <th>Sex</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">1st</th>
      <th>female</th>
      <td>2.00</td>
      <td>69.0</td>
      <td>143</td>
    </tr>
    <tr>
      <th>male</th>
      <td>0.92</td>
      <td>71.0</td>
      <td>179</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">2nd</th>
      <th>female</th>
      <td>1.00</td>
      <td>57.0</td>
      <td>107</td>
    </tr>
    <tr>
      <th>male</th>
      <td>0.80</td>
      <td>71.0</td>
      <td>173</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">3rd</th>
      <th>female</th>
      <td>0.17</td>
      <td>63.0</td>
      <td>212</td>
    </tr>
    <tr>
      <th>male</th>
      <td>0.33</td>
      <td>65.0</td>
      <td>499</td>
    </tr>
  </tbody>
</table>
</div>



⚠ Le résultat utilise plusieurs index pour chaque ligne et colonne.

On utilise la méthode *reset_index()* pour mettre les index ligne en colonne


```python
df.groupby(['PClass','Sex']).Age.agg([min, max]).reset_index()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PClass</th>
      <th>Sex</th>
      <th>min</th>
      <th>max</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1st</td>
      <td>female</td>
      <td>2.00</td>
      <td>69.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1st</td>
      <td>male</td>
      <td>0.92</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2nd</td>
      <td>female</td>
      <td>1.00</td>
      <td>57.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>2nd</td>
      <td>male</td>
      <td>0.80</td>
      <td>71.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>3rd</td>
      <td>female</td>
      <td>0.17</td>
      <td>63.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>3rd</td>
      <td>male</td>
      <td>0.33</td>
      <td>65.0</td>
    </tr>
  </tbody>
</table>
</div>



## Modifier un jeu de données

### Changement de type des variables


```python
df.dtypes
```




    Name         object
    PClass       object
    Age         float64
    Sex          object
    Survived      int64
    SexCode       int64
    dtype: object



On transforme la variable *Survived* en caractère


```python
df.Survived = df.Survived.astype('str')
df.dtypes
```




    Name         object
    PClass       object
    Age         float64
    Sex          object
    Survived     object
    SexCode       int64
    dtype: object



On la repasse en numérique


```python
df.Survived = df.Survived.astype('int')
df.dtypes
```




    Name         object
    PClass       object
    Age         float64
    Sex          object
    Survived      int64
    SexCode       int64
    dtype: object



#### Renommer des colonnes


```python
df.columns
```




    Index(['Name', 'PClass', 'Age', 'Sex', 'Survived', 'SexCode'], dtype='object')



On utilise la méthode *rename()* pour renommer une colonne


```python
df.rename(columns={'PClass': 'Classe passager',
                  'Age': 'Age passager'}, inplace=True)
```


```python
df.columns
```




    Index(['Name', 'Classe passager', 'Age passager', 'Sex', 'Survived',
           'SexCode'],
          dtype='object')



💡 Quelques fois, il est pénible de manipuler des variables avec des espaces, voici une commande pour remplacer les espaces par un  '_'


```python
df.columns = df.columns.str.replace(' ', '_')
df.columns
```




    Index(['Name', 'Classe_passager', 'Age_passager', 'Sex', 'Survived',
           'SexCode'],
          dtype='object')



On remet le nom des colonnes d'origine


```python
df.rename(columns={'Classe_passager': 'PClass',
                  'Age_passager': 'Age'}, inplace=True)
```

### Gerer les valeurs manquantes

#### Remplacer avec *fillna()*

On observe les valeurs manquantes présentent dans la variable age


```python
df.rename(columns={'Age_passager': 'Age'}, inplace=True)
```


```python
df.Age.isna().value_counts()
```




    False    756
    True     557
    Name: Age, dtype: int64




```python
df.Age.describe()
```




    count    756.000000
    mean      30.397989
    std       14.259049
    min        0.170000
    25%       21.000000
    50%       28.000000
    75%       39.000000
    max       71.000000
    Name: Age, dtype: float64



On remplace les valeurs manquantes par des 0 avec la méthode *fillna()* dans une nouvelle colonne


```python
df['Age_fillna_0'] = df.Age.fillna(0)
```

On remarque qu'il n'y a plus de valeurs manquantes


```python
df.Age_fillna_0.isna().value_counts()
```




    False    1313
    Name: Age_fillna_0, dtype: int64



⚠ Cela modifie la structure des données (ex : moyenne)


```python
df.Age_fillna_0.describe()
```




    count    1313.000000
    mean       17.502574
    std        18.516945
    min         0.000000
    25%         0.000000
    50%        18.000000
    75%        30.000000
    max        71.000000
    Name: Age_fillna_0, dtype: float64



L'astuce pourrait-être de remplacer les valeurs manquantes par la moyenne ?


```python
#calcul de la moyenne
mean = df.Age.mean()
```

On remplace par la moyenne


```python
df['Age_fillna_mean'] = df.Age.fillna(mean)
```

⚠ Cela modifie la structure des données sauf la moyenne


```python
df.Age_fillna_mean.describe()
```




    count    1313.000000
    mean       30.397989
    std        10.816758
    min         0.170000
    25%        26.000000
    50%        30.397989
    75%        30.397989
    max        71.000000
    Name: Age_fillna_mean, dtype: float64



Récapitulatif des méthodes utilisées


```python
df[df.Age.isna()].iloc[:,[2,6,7]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Age</th>
      <th>Age_fillna_0</th>
      <th>Age_fillna_mean</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>12</th>
      <td>NaN</td>
      <td>0.0</td>
      <td>30.397989</td>
    </tr>
    <tr>
      <th>13</th>
      <td>NaN</td>
      <td>0.0</td>
      <td>30.397989</td>
    </tr>
    <tr>
      <th>14</th>
      <td>NaN</td>
      <td>0.0</td>
      <td>30.397989</td>
    </tr>
    <tr>
      <th>29</th>
      <td>NaN</td>
      <td>0.0</td>
      <td>30.397989</td>
    </tr>
    <tr>
      <th>32</th>
      <td>NaN</td>
      <td>0.0</td>
      <td>30.397989</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1300</th>
      <td>NaN</td>
      <td>0.0</td>
      <td>30.397989</td>
    </tr>
    <tr>
      <th>1302</th>
      <td>NaN</td>
      <td>0.0</td>
      <td>30.397989</td>
    </tr>
    <tr>
      <th>1305</th>
      <td>NaN</td>
      <td>0.0</td>
      <td>30.397989</td>
    </tr>
    <tr>
      <th>1306</th>
      <td>NaN</td>
      <td>0.0</td>
      <td>30.397989</td>
    </tr>
    <tr>
      <th>1307</th>
      <td>NaN</td>
      <td>0.0</td>
      <td>30.397989</td>
    </tr>
  </tbody>
</table>
<p>557 rows × 3 columns</p>
</div>



On supprime les colonnes crées


```python
df.drop(columns=['Age_fillna_0', 'Age_fillna_mean'], inplace=True)
```

#### Supprimer avec *dropna()*

Une autre méthode plus radicale consiste à supprimer les observations ou colonnes avec des valeurs manquantes. On utilise la méthode *dropna()* avec :

* axis = 0 pour les lignes et 1 pour les colonnes
* how = 'all' si des NaN sur l'ensemble des les lignes/ colonne ouf how = 'any' si au moins un NaN sur l'ensemble des les lignes/ colonne


```python
df.dropna(axis=0, how="all").shape
```




    (1313, 6)




```python
df.dropna(axis=0, how="any").shape
```




    (756, 6)



⚠ On peut utiliser l'argument *inplace = True* pour modifier directement le data frame


```python
#avant le dropna()
df.shape
```




    (1313, 6)




```python
df.dropna(axis=0, how="any", inplace=True)
```


```python
#après le dropna()
df.shape
```




    (756, 6)



#### Remplacer avec *KNNImputer()*

Cette méthode consiste à utiliser l'algorithme des K-plus proches voisins. <br> https://scikit-learn.org/stable/modules/generated/sklearn.impute.KNNImputer.html


```python
d = {'x': [5, 10, np.nan, 20], 'y': [np.nan,4,6,9]}
X = pd.DataFrame(d)
X
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>x</th>
      <th>y</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>NaN</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>20.0</td>
      <td>9.0</td>
    </tr>
  </tbody>
</table>
</div>



💡 L'argument *weights* permet de pondérer la moyenne des voisins les plus proches leur distance de proximité.


```python
from sklearn.impute import KNNImputer
imputer = KNNImputer(n_neighbors=2, weights="distance")
X = pd.DataFrame(imputer.fit_transform(X), columns = X.columns)
X
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>x</th>
      <th>y</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>5.0</td>
      <td>5.25</td>
    </tr>
    <tr>
      <th>1</th>
      <td>10.0</td>
      <td>4.00</td>
    </tr>
    <tr>
      <th>2</th>
      <td>14.0</td>
      <td>6.00</td>
    </tr>
    <tr>
      <th>3</th>
      <td>20.0</td>
      <td>9.00</td>
    </tr>
  </tbody>
</table>
</div>



⚠ Cette méthode ne fonctionne que sur des variables numériques !

### Gérer les doublons

On remarque que certaines personnes sont présentes deux fois


```python
df_counts_name = df.Name.value_counts()
df_counts_name
```




    Kelly, Mr James                     2
    Connolly, Miss Kate                 2
    Carlsson, Mr Frans Olof             2
    Thayer, Mr John Borland, jr         1
    Butt, Major Archibald Willingham    1
                                       ..
    Driscoll, Miss Bridget              1
    Boulos, Miss Laura                  1
    Nasser (Nasrallah), Mrs Nicholas    1
    Hampe, Mr Leon                      1
    Angheloff, Mr Minko                 1
    Name: Name, Length: 753, dtype: int64



On récupère le nom des personnes en doublon avec la méthode *index*


```python
doublons = df_counts_name[ df_counts_name > 1].index
print(doublons)
```

    Index(['Kelly, Mr James', 'Connolly, Miss Kate', 'Carlsson, Mr Frans Olof'], dtype='object')


On filtre le data frame sur les doublons pour observer s'il y a bien une erreur ou s'il s'agit d'homonyme


```python
df_doublons = df[df.Name.isin(doublons)]
df_doublons
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>44</th>
      <td>Carlsson, Mr Frans Olof</td>
      <td>1st</td>
      <td>33.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>707</th>
      <td>Carlsson, Mr Frans Olof</td>
      <td>3rd</td>
      <td>33.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>728</th>
      <td>Connolly, Miss Kate</td>
      <td>3rd</td>
      <td>30.0</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>729</th>
      <td>Connolly, Miss Kate</td>
      <td>3rd</td>
      <td>22.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>921</th>
      <td>Kelly, Mr James</td>
      <td>3rd</td>
      <td>44.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>922</th>
      <td>Kelly, Mr James</td>
      <td>3rd</td>
      <td>42.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



Pour illustrer les méthodes pour dédoubloner, on travaille sur le dataset *df_doublons*

La première méthode consiste à supprimer les doublons basés sur une seule colonne


```python
df_doublons.drop_duplicates(subset=['Name'])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>44</th>
      <td>Carlsson, Mr Frans Olof</td>
      <td>1st</td>
      <td>33.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>728</th>
      <td>Connolly, Miss Kate</td>
      <td>3rd</td>
      <td>30.0</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>921</th>
      <td>Kelly, Mr James</td>
      <td>3rd</td>
      <td>44.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



La deuxième méthode consiste à supprimer les doublons basés sur plusieurs colonnes à la fois


```python
df_doublons
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>44</th>
      <td>Carlsson, Mr Frans Olof</td>
      <td>1st</td>
      <td>33.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>707</th>
      <td>Carlsson, Mr Frans Olof</td>
      <td>3rd</td>
      <td>33.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>728</th>
      <td>Connolly, Miss Kate</td>
      <td>3rd</td>
      <td>30.0</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>729</th>
      <td>Connolly, Miss Kate</td>
      <td>3rd</td>
      <td>22.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>921</th>
      <td>Kelly, Mr James</td>
      <td>3rd</td>
      <td>44.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>922</th>
      <td>Kelly, Mr James</td>
      <td>3rd</td>
      <td>42.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_doublons.drop_duplicates(subset=['Name',"PClass"])
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>44</th>
      <td>Carlsson, Mr Frans Olof</td>
      <td>1st</td>
      <td>33.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>707</th>
      <td>Carlsson, Mr Frans Olof</td>
      <td>3rd</td>
      <td>33.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>728</th>
      <td>Connolly, Miss Kate</td>
      <td>3rd</td>
      <td>30.0</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>921</th>
      <td>Kelly, Mr James</td>
      <td>3rd</td>
      <td>44.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



Les deux dernières méthodes consistent à supprimer les doublons selon leur position dans le data frame en utilisant la méthode *groupby()* avec *tail()* ou *nth()*

On sélectionne la première ligne ou apparaît le doublon


```python
df_doublons.groupby('Name').nth(0)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
    <tr>
      <th>Name</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Carlsson, Mr Frans Olof</th>
      <td>1st</td>
      <td>33.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>Connolly, Miss Kate</th>
      <td>3rd</td>
      <td>30.0</td>
      <td>female</td>
      <td>0</td>
      <td>1</td>
    </tr>
    <tr>
      <th>Kelly, Mr James</th>
      <td>3rd</td>
      <td>44.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



On sélectionne les x dernières lignes ou apparaît le doublon


```python
df_doublons.groupby('Name').tail(1)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>PClass</th>
      <th>Age</th>
      <th>Sex</th>
      <th>Survived</th>
      <th>SexCode</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>707</th>
      <td>Carlsson, Mr Frans Olof</td>
      <td>3rd</td>
      <td>33.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>729</th>
      <td>Connolly, Miss Kate</td>
      <td>3rd</td>
      <td>22.0</td>
      <td>female</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>922</th>
      <td>Kelly, Mr James</td>
      <td>3rd</td>
      <td>42.0</td>
      <td>male</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



### Créer de nouvelle variables

#### Discrétisation

La méthode *cut()* permet de découper une variable numérique en tranche


```python
pd.cut(df.Age, bins = [0,18,40,150])
```




    0       (18, 40]
    1        (0, 18]
    2       (18, 40]
    3       (18, 40]
    4        (0, 18]
              ...   
    1308    (18, 40]
    1309    (18, 40]
    1310    (18, 40]
    1311    (18, 40]
    1312    (18, 40]
    Name: Age, Length: 756, dtype: category
    Categories (3, interval[int64]): [(0, 18] < (18, 40] < (40, 150]]



⚠ L'argument *include_lowest* est important pour prendre en compte la plus petite borne inférieure


```python
pd.cut(df.Age, bins = [0,18,40,150], include_lowest=True)
```




    0         (18.0, 40.0]
    1       (-0.001, 18.0]
    2         (18.0, 40.0]
    3         (18.0, 40.0]
    4       (-0.001, 18.0]
                 ...      
    1308      (18.0, 40.0]
    1309      (18.0, 40.0]
    1310      (18.0, 40.0]
    1311      (18.0, 40.0]
    1312      (18.0, 40.0]
    Name: Age, Length: 756, dtype: category
    Categories (3, interval[float64]): [(-0.001, 18.0] < (18.0, 40.0] < (40.0, 150.0]]



On crée une colonne avec ce découpage en ajoutant des labels


```python
df['Age_cut'] = pd.cut(df.Age, bins = [0,18,40,150],
                       labels=['moins de 18','entre 19 et 40','plus de 40'],
                       include_lowest=True)
```

On affiche un tri à plat en triant selon les index avec la méthode *sort_index()*


```python
df['Age_cut'].value_counts().sort_index()
```




    moins de 18       126
    entre 19 et 40    456
    plus de 40        174
    Name: Age_cut, dtype: int64



#### Recodage de variables

On peut utiliser la méthode *where()* de la librarie numpy


```python
df['PClass_category'] = np.where(df['PClass'] == '1st', '1st', '2nd and 3rd')
df['PClass_category'].value_counts()
```




    2nd and 3rd    530
    1st            226
    Name: PClass_category, dtype: int64



La méthode *get_dummies()* permet de construire un condage disjonctif complet (appelé aussi *one-hot encoding*). Cela est trés utilisé en data science pour traiter les variables qualitatives en machine learning


```python
pd.get_dummies(df, columns=['PClass','Sex']).head(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>Survived</th>
      <th>SexCode</th>
      <th>Age_cut</th>
      <th>PClass_category</th>
      <th>PClass_1st</th>
      <th>PClass_2nd</th>
      <th>PClass_3rd</th>
      <th>Sex_female</th>
      <th>Sex_male</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>29.0</td>
      <td>1</td>
      <td>1</td>
      <td>entre 19 et 40</td>
      <td>1st</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Allison, Miss Helen Loraine</td>
      <td>2.0</td>
      <td>0</td>
      <td>1</td>
      <td>moins de 18</td>
      <td>1st</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Allison, Mr Hudson Joshua Creighton</td>
      <td>30.0</td>
      <td>0</td>
      <td>0</td>
      <td>entre 19 et 40</td>
      <td>1st</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



⚠ Créer autant de colonne que de modalité est problématique car on ajoute des colonnes qui ne sont plus indépendante. C'est pourquoi en machine learning on crée plutot K-1 indicatrices, la dernière modalité étant déduite des autres. L'argument *drop_first* permet de gérer cela.


```python
df = pd.get_dummies(df, columns=['PClass','Sex'], drop_first=True)
df.head(3)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Name</th>
      <th>Age</th>
      <th>Survived</th>
      <th>SexCode</th>
      <th>Age_cut</th>
      <th>PClass_category</th>
      <th>PClass_2nd</th>
      <th>PClass_3rd</th>
      <th>Sex_male</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Allen, Miss Elisabeth Walton</td>
      <td>29.0</td>
      <td>1</td>
      <td>1</td>
      <td>entre 19 et 40</td>
      <td>1st</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Allison, Miss Helen Loraine</td>
      <td>2.0</td>
      <td>0</td>
      <td>1</td>
      <td>moins de 18</td>
      <td>1st</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Allison, Mr Hudson Joshua Creighton</td>
      <td>30.0</td>
      <td>0</td>
      <td>0</td>
      <td>entre 19 et 40</td>
      <td>1st</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



## Exporter le jeu de données

On exporte le data frame avec la méthode to_*mon_format*() selon l'extension du fichier



```python
#df.to_csv("mon_Titanic.csv", index = False)
```


```python
# df.to_excel(excel_writer = "Titanic.xlsx" , 
#             sheet_name = "Feuil1", index=False)
```

## Créer un objet pandas

Pour céer une *Series* pandas on utilise la méthode *Series()*


```python
#Creation des Séries   
ls_prenom = pd.Series(["Wilfried", "Alex", "Morgane", "Etienne", "Célia", "Baptiste", "Anthony", "Fred"])
ls_bi = pd.Series([15,9,12,15,6,14,11,19])
ls_dataviz = pd.Series([14,7,15,13,15,10,12,14])

print(ls_prenom)
```

    0    Wilfried
    1        Alex
    2     Morgane
    3     Etienne
    4       Célia
    5    Baptiste
    6     Anthony
    7        Fred
    dtype: object


Pour céer un *DataFrame* pandas on utilise la méthode *DataFrame()*


```python
d = {'Prenom': ls_prenom, 'BI': ls_bi, 'Dataviz' : ls_dataviz, 'Maths' : [5,20,11,13,5,14,12,16]}
df = pd.DataFrame(data=d)
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Prenom</th>
      <th>BI</th>
      <th>Dataviz</th>
      <th>Maths</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Wilfried</td>
      <td>15</td>
      <td>14</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Alex</td>
      <td>9</td>
      <td>7</td>
      <td>20</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Morgane</td>
      <td>12</td>
      <td>15</td>
      <td>11</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Etienne</td>
      <td>15</td>
      <td>13</td>
      <td>13</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Célia</td>
      <td>6</td>
      <td>15</td>
      <td>5</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Baptiste</td>
      <td>14</td>
      <td>10</td>
      <td>14</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Anthony</td>
      <td>11</td>
      <td>12</td>
      <td>12</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Fred</td>
      <td>19</td>
      <td>14</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>



## Les options pandas

Il est possible de modifier les options d'affichage avec la gestion des options de la librairie pandas


```python
#gerer le nombre de ligne à afficher
pd.set_option("display.min_rows", 2)
```


```python
#gérer le nombre de colonne à afficher
pd.set_option("display.max_columns", 4)
```


```python
#gérer la largeur des colonnes
pd.set_option('max_colwidth', 5)
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Prenom</th>
      <th>BI</th>
      <th>Dataviz</th>
      <th>Maths</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>W...</td>
      <td>15</td>
      <td>14</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Alex</td>
      <td>9</td>
      <td>7</td>
      <td>20</td>
    </tr>
    <tr>
      <th>2</th>
      <td>M...</td>
      <td>12</td>
      <td>15</td>
      <td>11</td>
    </tr>
    <tr>
      <th>3</th>
      <td>E...</td>
      <td>15</td>
      <td>13</td>
      <td>13</td>
    </tr>
    <tr>
      <th>4</th>
      <td>C...</td>
      <td>6</td>
      <td>15</td>
      <td>5</td>
    </tr>
    <tr>
      <th>5</th>
      <td>B...</td>
      <td>14</td>
      <td>10</td>
      <td>14</td>
    </tr>
    <tr>
      <th>6</th>
      <td>A...</td>
      <td>11</td>
      <td>12</td>
      <td>12</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Fred</td>
      <td>19</td>
      <td>14</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>



La méthode *reset_option()* permet de réinitialiser les paramètres


```python
pd.reset_option(("^display"))
```


```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Prenom</th>
      <th>BI</th>
      <th>Dataviz</th>
      <th>Maths</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Wilfried</td>
      <td>15</td>
      <td>14</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Alex</td>
      <td>9</td>
      <td>7</td>
      <td>20</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Morgane</td>
      <td>12</td>
      <td>15</td>
      <td>11</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Etienne</td>
      <td>15</td>
      <td>13</td>
      <td>13</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Célia</td>
      <td>6</td>
      <td>15</td>
      <td>5</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Baptiste</td>
      <td>14</td>
      <td>10</td>
      <td>14</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Anthony</td>
      <td>11</td>
      <td>12</td>
      <td>12</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Fred</td>
      <td>19</td>
      <td>14</td>
      <td>16</td>
    </tr>
  </tbody>
</table>
</div>



Plus d'information sur la librairie pandas avec le cours de Kaggle : https://www.kaggle.com/learn/pandas

#### Pandas Profiling

Lancer la ligne de commande dans un terminal, une mise à jour de conda est peut être nécessaire


```python
#conda install -c conda-forge pandas-profiling
```


```python
# import pandas_profiling
```


```python
# profile = pandas_profiling.ProfileReport(df, title='Pandas Profiling Report', explorative=True)
```


```python
# profile
```
