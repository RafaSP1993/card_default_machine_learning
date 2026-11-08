# Predicción de impago de tarjetas de crédito (Taiwán, 2005)

*[English version](README.md)*

Predice si un cliente de tarjeta de crédito impagará el mes siguiente, a partir de seis meses de historial de pagos. Proyecto educativo de portfolio.

## Resultados

Conjunto de test de 6.000 clientes que el modelo no había visto:

| Modelo | ROC-AUC | PR-AUC |
|---|---|---|
| Regresión logística | 0,764 | 0,526 |
| **Random Forest** (modelo final) | **0,779** | **0,564** |

Con un umbral de 0,30 (F1 máximo), el Random Forest detecta el **55 % de los impagos** (731 de 1.327) y marca por error al **13 % de los clientes buenos** (629 de 4.673).

## Conclusiones principales

- **Las variables demográficas pesan poco.** El impago varía según la educación, la edad, el sexo y el estado civil, pero las diferencias son pequeñas.
- **El comportamiento de pago reciente es lo que mejor predice el impago**, sobre todo el retraso en el último mes.
- **El Random Forest supera a la regresión logística solo por poco**, sobre todo entre los clientes de más riesgo.

## Estructura

```
cardDefaultML/
├── UCI_Credit_Card.csv        no incluido, ver «Cómo ejecutarlo»
├── requirements.txt
├── cardDefault_SP/           notebooks en español
│   ├── 01_EDA_CC.ipynb         limpieza, EDA e ingeniería de variables
│   ├── 02_Modelado_CC.ipynb    entrenamiento y elección del modelo
│   └── 03_Evaluacion_CC.ipynb  umbral, calibración, test y conclusiones
└── cardDefault_ENG/          los mismos notebooks en inglés
```

Ejecuta los notebooks en orden: 01 → 02 → 03.

## Cómo ejecutarlo

1. Descarga `UCI_Credit_Card.csv` de [Kaggle](https://www.kaggle.com/datasets/uciml/default-of-credit-card-clients-dataset) y colócalo en la carpeta raíz, junto a `requirements.txt`. El dataset no está incluido en este repositorio.
2. Instala las dependencias (probado con Python 3.13) y abre Jupyter:

```bash
pip install -r requirements.txt
jupyter notebook
```

## Limitaciones

- Datos de 2005 y de un único mercado (Taiwán).
- Sin datos de ingresos ni de empleo.
- El modelo usa sexo, edad y estado civil, que muchas normativas prohíben en decisiones de crédito. No está listo para un uso real.

## Datos

Yeh, I. (2009). *Default of Credit Card Clients*. [UCI Machine Learning Repository](https://doi.org/10.24432/C55S3H). Licencia: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
