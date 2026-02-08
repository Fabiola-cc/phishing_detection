# Laboratorio 1 — Deteccion de Phishing con Machine Learning

**CC3094 — Security Data Science | Semestre I, 2026**  
Universidad del Valle de Guatemala  
Seccion 11 — Docente: Jorge Yass

---

## Autores

| Nombre | Carnet |
|---|---|
| Fabiola Contreras | 22787 |
| Maria Jose Villafuerte | 22129 |

---

## Descripcion

Este laboratorio implementa un sistema de deteccion de URLs de phishing utilizando tecnicas de Machine Learning. El proyecto se divide en dos fases: ingenieria de caracteristicas (feature engineering) y entrenamiento/evaluacion de modelos de clasificacion.

Se extraen 23 caracteristicas de las URLs y se seleccionan las 7 mas relevantes para entrenar dos modelos: **Random Forest** y **Logistic Regression**. Ambos modelos se evaluan con metricas estandar de clasificacion y se comparan para determinar cual ofrece mejor rendimiento en la deteccion de phishing.

---

## Estructura del Proyecto

```
Lab01-Phishing/
|
|-- feature_engineering/
|    |-- dataset_phishing_preprocessed.csv       # Dataset normalizado (StandardScaler)
|    |-- dataset_phishing_preprocessed_raw.csv   # Dataset sin normalizar
|
|-- models/ 
|    |-- models_implementation.ipynb                  # Notebook principal con los modelos|
|    |-- train_dataset.csv                            # Split de entrenamiento (55%)
|    |-- validation_dataset.csv                       # Split de validacion (15%)
|    |-- test_dataset.csv                             # Split de prueba (30%)
|
|-- Reporte_Laboratorio1_Phishing.pdf
```

---

## Caracteristicas Seleccionadas

Las siguientes 7 features fueron seleccionadas durante la fase de ingenieria de caracteristicas:

| Caracteristica   | Descripcion                                      |
|-------------------|--------------------------------------------------|
| shannon_entropy   | Entropia de Shannon de la URL                    |
| digit_ratio       | Proporcion de digitos en la URL                  |
| sensitive_words   | Presencia de palabras sensibles (login, verify)  |
| url_length        | Longitud total de la URL                         |
| domain_length     | Longitud del dominio                             |
| num_params        | Cantidad de parametros en el query string        |
| special_chars     | Conteo de caracteres especiales                  |

---

## Modelos Implementados

| Modelo              | Optimizacion              | Metrica de seleccion |
|---------------------|---------------------------|----------------------|
| Random Forest       | GridSearchCV (3-fold CV)  | F1-Score             |
| Logistic Regression | GridSearchCV (3-fold CV)  | F1-Score             |

---

## Resultados — Conjunto de Prueba

| Metrica   | Random Forest | Logistic Regression |
|-----------|---------------|---------------------|
| Accuracy  | 0.7929        | 0.7302              |
| Precision | 0.8239        | 0.8051              |
| Recall    | 0.7450        | 0.6074              |
| F1-Score  | 0.7825        | 0.6924              |
| AUC       | 0.8751        | 0.7728              |

**Mejor modelo:** Random Forest, con ventajas en todas las metricas evaluadas.

---

## Requisitos

- Python 3.8+
- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn

Instalacion rapida:

```bash
pip install pandas numpy scikit-learn matplotlib seaborn
```

