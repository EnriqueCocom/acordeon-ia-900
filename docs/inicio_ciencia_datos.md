# Introducción a la ciencia de datos.

> [!NOTE]
> Esto es solo una sencilla introducción ajustada al temario de la certificación. Para más información consulta [-> AQUÍ <-](https://machinelearningmastery.com/start-here/)

La Ciencia de Datos es un campo multidisciplinario que combina estadística, matemáticas, programación y dominio del negocio para extraer información valiosa de datos estructurados y no estructurados. El proceso sigue una metodología similar al método científico y consta de etapas que incluyen el análisis, modelado, evaluación y despliegue de modelos predictivos o descriptivos.

## 1. Método Científico en Ciencia de Datos

Aquí tienes una introducción **muy detallada** a **Ciencia de Datos**, siguiendo los pasos esenciales que cubren desde el **método científico**, **análisis exploratorio de datos (EDA)**, hasta la **evaluación y empaquetado del modelo**. A lo largo del documento, se incluirá **código en Python** y referencias a fuentes externas que te ayudarán a aprender más.


## **1. Método Científico en Ciencia de Datos**

El método científico en la Ciencia de Datos sigue estos pasos:

1. **Definir el Problema**: 
   - Comprender el problema de negocio.
   - Formular una hipótesis.

2. **Recolección de Datos**: 
   - Identificar las fuentes de datos: bases de datos, APIs, archivos CSV, etc.
   - Obtener los datos necesarios para el análisis.

3. **Procesamiento y Limpieza de Datos**:
   - Manejar datos faltantes, eliminar duplicados y transformar variables.

4. **Análisis Exploratorio de Datos (EDA)**:
   - Visualización y análisis estadístico de los datos.

5. **Construcción del Modelo**:
   - Seleccionar un modelo de Machine Learning.

6. **Evaluación del Modelo**:
   - Probar el modelo con métricas de desempeño.

7. **Empaquetado y Despliegue del Modelo**:
   - Implementar el modelo en un entorno productivo.

---

## **Dataset Utilizado**

Utilizaremos el dataset **Titanic - Machine Learning from Disaster** de Kaggle, uno de los más famosos para practicar Machine Learning.

- Enlace al dataset: [https://www.kaggle.com/competitions/titanic/data](https://www.kaggle.com/competitions/titanic/data)

---

## **Paso 1: Aplicación del Método Científico**

El método científico es la base de la Ciencia de Datos. Consiste en los siguientes pasos:

1. **Planteamiento del problema**: ¿Qué queremos predecir?
   - **Objetivo**: Predecir si un pasajero del Titanic sobrevivió o no, utilizando características como edad, sexo, clase de boleto, etc.
2. **Hipótesis**: Factores como la clase del boleto (1ª clase), el sexo (mujeres) y la edad influyen en la probabilidad de sobrevivir.
3. **Experimentación**: Crear un modelo de Machine Learning para validar la hipótesis.
4. **Análisis de resultados**: Evaluar si el modelo cumple con las expectativas y mejora con ajustes.

---

## **Paso 2: Instalación de Librerías y Configuración del Entorno**

Primero, asegúrate de tener las siguientes librerías instaladas:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
```

**Código en Python: Configuración inicial**

```python
# Importar las librerías necesarias
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

# Configuración para ver gráficos en línea
%matplotlib inline
sns.set(style="whitegrid")
```

---

## **Paso 3: Obtención y Carga de Datos**

Descarga el dataset de Kaggle y carga los archivos CSV en tu entorno de trabajo.

```python
# Cargar los datos
train_df = pd.read_csv("train.csv")
test_df = pd.read_csv("test.csv")

# Visualizar las primeras filas del dataset
print(train_df.head())
```

**Salida:**

| PassengerId | Survived | Pclass | Name           | Sex    | Age  | SibSp | Parch | Ticket  | Fare  | Cabin | Embarked |
|-------------|----------|--------|----------------|--------|------|-------|-------|---------|-------|-------|----------|
| 1           | 0        | 3      | Braund, Mr. O. | male   | 22.0 | 1     | 0     | A/5 211 | 7.25  | NaN   | S        |
| 2           | 1        | 1      | Cumings, Mrs.  | female | 38.0 | 1     | 0     | PC 1759 | 71.28 | C85   | C        |

---

## **Paso 4: Limpieza y Preparación de Datos**

En esta etapa, identificamos los valores faltantes, realizamos transformaciones necesarias y creamos características útiles.

**1. Identificación de valores faltantes**

```python
# Información general del dataset
print(train_df.info())

# Visualizar valores faltantes
print(train_df.isnull().sum())
```

**2. Tratamiento de valores faltantes**

```python
# Llenar valores faltantes en 'Age' con la mediana
train_df['Age'].fillna(train_df['Age'].median(), inplace=True)

# Llenar valores faltantes en 'Embarked' con la moda
train_df['Embarked'].fillna(train_df['Embarked'].mode()[0], inplace=True)

# Llenar valores faltantes en 'Fare' con la mediana (para test)
test_df['Fare'].fillna(test_df['Fare'].median(), inplace=True)
```

**3. Codificación de variables categóricas**

```python
# Convertir 'Sex' y 'Embarked' a variables numéricas
train_df['Sex'] = train_df['Sex'].map({'male': 0, 'female': 1})
train_df['Embarked'] = train_df['Embarked'].map({'S': 0, 'C': 1, 'Q': 2})

# Verificar los cambios
print(train_df.head())
```

---

## **Paso 5: Análisis Exploratorio de Datos (EDA)**

El **EDA** nos permite entender la distribución de los datos y sus relaciones.

**1. Distribución de la variable objetivo**

```python
# Visualizar la distribución de 'Survived'
sns.countplot(x='Survived', data=train_df)
plt.title("Distribución de Sobrevivientes")
plt.show()
```

**2. Relación entre variables**

```python
# Relación entre 'Pclass' y 'Survived'
sns.barplot(x='Pclass', y='Survived', data=train_df)
plt.title("Tasa de Supervivencia por Clase")
plt.show()

# Relación entre 'Sex' y 'Survived'
sns.barplot(x='Sex', y='Survived', data=train_df)
plt.title("Tasa de Supervivencia por Sexo")
plt.show()
```

---

## **Paso 6: Construcción del Modelo de Machine Learning**

Utilizaremos un modelo simple de **Regresión Logística**.

```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import accuracy_score, confusion_matrix

# Selección de características y objetivo
features = ['Pclass', 'Sex', 'Age', 'SibSp', 'Parch', 'Fare', 'Embarked']
X = train_df[features]
y = train_df['Survived']

# División en entrenamiento y validación
X_train, X_val, y_train, y_val = train_test_split(X, y, test_size=0.2, random_state=42)

# Creación del modelo
model = LogisticRegression(max_iter=1000)
model.fit(X_train, y_train)

# Predicción y evaluación
y_pred = model.predict(X_val)
print("Accuracy:", accuracy_score(y_val, y_pred))

# Matriz de confusión
print("Confusion Matrix:")
print(confusion_matrix(y_val, y_pred))
```

---

## **Paso 7: Evaluación y Empaquetado del Modelo**

1. **Evaluación del modelo**: Utiliza métricas como Accuracy, Precision y Recall.
2. **Empaquetado**: Puedes guardar el modelo usando **Pickle**.

```python
import pickle

# Guardar el modelo
with open('titanic_model.pkl', 'wb') as file:
    pickle.dump(model, file)

# Cargar el modelo
with open('titanic_model.pkl', 'rb') as file:
    loaded_model = pickle.load(file)

# Validar el modelo cargado
print("Accuracy del modelo cargado:", loaded_model.score(X_val, y_val))
```


---

## **Recursos Externos para Aprender Más**

1. **Documentación de Pandas**: Biblioteca fundamental para manipulación de datos.
   [Documentación oficial](https://pandas.pydata.org/docs/)

2. **Scikit-Learn**: Guía completa para Machine Learning en Python.
   [Scikit-learn Documentation](https://scikit-learn.org/stable/)

3. **Kaggle**: Práctica con datasets y notebooks de ciencia de datos.
   [Kaggle](https://www.kaggle.com)

4. **Matplotlib y Seaborn**: Visualización de datos en Python. 
   [Matplotlib](https://matplotlib.org/stable/) | [Seaborn](https://seaborn.pydata.org/)

5. **Machine Learning con Python de Microsoft Learn**:  
   [Ruta de aprendizaje de Microsoft](https://learn.microsoft.com/es-es/training/paths/get-started-machine-learning/?utm_source=chatgpt.com)

6. **IBM: Introducción a la Ciencia de Datos**:  
   [IBM Recursos de Ciencia de Datos](https://www.ibm.com/analytics/data-science)
