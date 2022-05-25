## Manipulacion de datos

`data.describe()` muestra descripción gral de datos

`data.dtypes` muestra tipo de datos existentes

## 5. Operaciones de manejo de datos

### Distribución

Distribución normal: randn

### Agrupación

`grouped_gender = data.groupby("Gender")` se le pone la columna la cual se quiere agrupar (gender).

Se crea un objeto con nombre y grupo.

* Resumen de grupos > `grouped_gender.groups`

* Escoger un grupo > `grouped_gender.get_group("Female")`

* Varios grupos > `data.groupby(["Gender", "Economic Status"])`

### Agregar datos

Aplicar una función a los **grupos a la vez**  y obtener resultados para ese grupo.

* `double_group.mean()`

* `double_group.size()`

* `double_group.describe()`

Para seleccionar una columna.

`variable = double_group["Income"]`

Hacer respectivas operaciones en *variable*

Para agregar datos se usa **agregate**:

```python
double_group.agregate(
    {
        "Income":np.sum,
        "Age": np.mean
    }
)
```

#### Lambda

**Lambda** define un tipo de cálculo específico.

Para definir cálculos a una variable:

```python
    double_group.agregate(
        {
            "Income":np.sum,
            "Age": np.mean,
            "Height": lambda h: np.mean(h)/np.std(h)
        }
    )
```

Para definir cálculos en todas las variables agregar dentro de corhetes los cálculos:

`double_group.agregate([np.sum, np.mean, np.std])`

O

`double_group.agregate ([lambda h: np.mean(h)/np.std(h)])`

### Filtrado

`double_group["age"].filter(lambda x: x.sum>2400)` filtra aquellos cuya suma supera los 2400.

### Transformar variables

Transformar elementos de una tabla o columna

`zscore = lambda x: (x-x.mean())/std(x)`

`double_group.gtransform(zscore)`

#### Rellenar N/A

Reemplaza los NA en un valor (promedio)

```python
fill_na_mean = lambda x: x.fillna(x.mean())
double_group.transform (fill_na_mean)
```

### Operaciones diversas

`.head . tail  ` muestra elementos al principio o final

 `.nth` el n seavo elemento

`double_group.head(1)` muestra primer objeto de los grupos con sus elementos.

`.sort`     ordea

`data_sorted = data.sort_values(["Age", "Income"]) `

### Entenamiento y testig

Puede ser 75% y 25%  o  80% y 20%. 

```python
#condición de check a verificar
training = data[check]
testing = data[~check]
```

Es mejor un método aleatorio para esto.

Evitar overfitting. 

#### Sklearn

**cómo dividir conjunto de entrenamiento y test:** 

`from _sklearn.model_selection_ import _train_test_split_`

```python
train, test = train_test_split(data, test_size = 0.2) #20% para testing
```

#### Shuffle

Permite aleatorizar los elementos.

```python
import numpy as np
import sklearn
data = sklearn.utils.shuffle(data)#se reordenan aleatoriamente los datos
#se toman los datos para testeos
cut_id = int(0.75*len(data))
train_data=data[:cut_id]#desde el principio hasta el corte de datos
train_data=data[cut_id+1:]#desde el corte hasta terminar


```

representar un vector de variables booleanas añadir un casting con `.astype(int)` al final de la lista:

`plt.hist(check.astype(int))`

### Concatener dos datasets por fila

#### Concatenar y apendizar

axis=0 *Eje horizontal*

axis=1 *Eje vertical*

```python
import pandas as pd
red_wine = #dataset
white_wine = #dataset
#ambos tienen mismas columnas.
wine_data = pd.concat([red_wine,white_wine],axis = 0)
```

De esta forma se apilan los datos.

#### Datos distribuidos

* Importar el primer fichero

* Bucle para recorrer ficheros (tener en cuenta nombre de ficheros)

```python
filepath = #direccion de archivos
data = #primer archivo.csv
longitud=333
for i in range(2,longitud):
    if i < 10:
        filename = "00"+str(i)
    if 10<=i<100:
        filename = "0"+str(i)
    if i>=100:
        filename = str(i)
    file = filepath + filename+".csv"
    temp_data = pd.read_csv(file)

    data = pd.concat([data,temp_data],axis = 0)
```

### Join - Merge

**Unir dos tablas.**

```python
pd.merge(left = data_main, right = data_country, #dataset izquierdo y derecho
            left_on = "Athlete", right_on = "Athlete") #columna dataset izquierdo y derecho
```

Para evitar duplicados de información se puede hacer:

`data_set.drop_duplicates(subset="Columna")`

Para eliminar elementos que están dentro de una tabla condicional:

```python
new_table = data[(~data["columna"].isin(tabla_condicional))    &
                   alguna_otra_condicion]
```

el simbolo ~ es para la negación de alguna condición.

#### Inner join

Aparece en A & B *(intersección)* 

```python
pd.merge(left = data_main, right = data_missing_values, 
         how = "inner", left_on = "Athlete", right_on = "Athlete")
```

#### Left join

Todos los que aparecen en A 

```python
pd.merge(left = data_main, right = data_missing_values, 
         how = "left", left_on = "Athlete", right_on = "Athlete")
```

Se crearán NA para atletas que no tenian info en tabla de izquierda.

#### Right join

Todos los que aparecen en B

#### Outer join

Aparece en A | B *(unión)*.

Utilizado si uno tiene más elementos que otro.

## 6. Conceptos básicos de estadística para modelización predictiva.

ver capitulo 71.

**Distribución normal**:

**Contraste de hipótesis**: hipótesis que debe tomar un estimador (número o mayor que o menor que).

    Hipótesis nula: es cierta o no mediante reglas con distribución normal. Defiende que es cierto hasta lo contrario.

    Hipótesis contraria/alternativa.

**Varianza** es como se aleja cada valor de la media.

**Desviación típica o estandar** es la raíz cuadrada de la varianza.

**Coeficiente de variación:** nos mide en porcentaje la variabilidad/dispersión relativa de un conjunto de datos. Variabilidad relativa entre la media y la std, si hay mucha variabilidad será grande el coeficiente. `std/mean*100`.

**Población:**

$\mu$ media

$\sigma$ desviación típica

$\rho$ proporción poblacional

**Muetstra:**

$\bar{x}$ media

$\tilde{s}$ desviación típica

$\hat{p}$ proporción

**Test de Chi cuadrado** ($\chi$) compara datos observados con los esperados para: 

* Elemento bondad de ajustes, datos tienen desvios?

* Test homogeneidad. 

* Test independencia. Relación o no entre dos variables, uno de entrada y uno de salida.

Correlaciones.

* Lineal

* Exponencial

Coefiiente de correlación de pearson: categoriza el grado de correlación.

Correlación positiva

Coeficiente de correlación de Pearson

$r= \frac{\sum^n_{i=1} (x_i-\bar{x})(y_i-\bar{y})} {\sqrt{\sum^n_{i=1} (x_i-\bar{x})^2 \sum^n_{i=1}(y_i-\bar{y})^2} }$ 

El siguiente código muestra las correlaciones de gastos diarios en determinado periodo en radio, tv y periodico y cómo repercutió en las ventas.

```python
def correlacion_coeficiente(df,var1,var2)
    df["corrn"] = (df[var1] - np.mean(df[var1])) * (df[var2] - np.mean(df[var2]))
    df["corr1"] = (df[var1] - np.mean(df[var1]))**2
    df["corr2"] = (df[var2] - np.mean(df[var2]))**2
    corr_p = sum(df["corrn"])/np.sqrt(sum(df[corr1]) * sum(df[corr2]))
    return corr_p
```

`data_ads.corr()` Formula de pandas.

`plt.matshow(data_ads.corr())` Matriz de correlación

## 7. Regresión lineal

Encontrar valores significativos 

### Modelo de regresión lineal

**SSD** Diferencia de Suma de cuadrados (scuare sum diference). *Diferencia entre el punto observado y la línea de predicción*

**SST** Suma de los cuadrados totales. *Diferencia entre el punto observado y la línea del promedio*.

**SSR** Suma de los cuadrados de la regresión. *Diferencia entre punto de línea de predicción y línea del promedio del punto observado*

**SRE** Error Estandar de los Residuos = $\sqrt{\frac{SSD}{n-k-1}}$

Columna con Mayor p-valor menor significante para el modelo

+valores - errores

## 8. Regresión logistica

## 15. Redes neuronales

**Perceptrón** dada x 

### Tensor flow

Se necesita una parte de sesión operativa para evaluación

```python
import tensorflow as tf
x1 = tf.constant([1,2,3,4,5])
x2 = tf.constant([6,7,8,9,10])
res = tf.multiply(x1,x2)

#1
sess=tf.Session()
print(sess.run(res))
sess.close()
#2
with tf.Session() as sess:
    output = sess.run(res)
    print(res)

```

### Modelado

operaciones dentro de la red neuronal.

Place holders para entradas y etiquetas, estos son valores no asignados inicializados dentro de la sesión cuando se ejecute. Son como variables en memoria.

```python
x =  tf.placeholder(dtype = tf.float32, shape = [None, 30,30])
y = tf.placeholder(dtype = tf.int32, shape = [None])
#red. Flaten con datos totales de c/u imágenes
#Distribuye datos desde matrices a lista
```
