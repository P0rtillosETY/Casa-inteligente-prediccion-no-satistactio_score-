# Predicción de decisión de compra de vivienda

**Objetivo**: predecir si un cliente comprará una casa basándose en sus características financieras, de la propiedad y del entorno.


Usamos el [Global House Purchase Decision Dataset](https://www.kaggle.com/datasets/mohankrishnathalla/global-house-purchase-decision-dataset) con 200 000 registros y 25 variables.  

La meta es construir un clasificador binario (compra / no compra) que obtenga la mayor exactitud posible, respetando una división 70 % entrenamiento, 20 % prueba y 10 % validación (esta última solo se evalúa una vez al final).

- **EDA e ingeniería de variables**  
  Detecté que `satisfaction_score` era la característica más discriminante y que los ratios financieros (ej. `log(salario) – log(precio)`) capturaban la capacidad de compra.  
  Transformé variables con logaritmos, creé *ratios* y codifiqué las categóricas, pasando de 25 a 83 columnas.

- **Modelado y optimización**  
  Empecé con una regresión logística (94 % de acierto en prueba).  
  Entrené una red neuronal con regularización (Dropout, BatchNorm, L2) y afiné hiperparámetros usando **Optuna** (25 combinaciones) monitoreando el conjunto de prueba.

- **Ensamble y evaluación final**  
  Promediando las probabilidades de la red neuronal y un Random Forest obtuve **0.999200 de exactitud sobre 20 000 casos nunca vistos** (solo 16 errores).  
  La validación se respetó como conjunto ciego hasta el último paso, siguiendo la regla del concurso.

## Registro de experimentos

Todos los experimentos (métricas, hiperparámetros, curvas de aprendizaje) se guardaron en **Weights & Biases**:

- [Proyecto Optuna](https://wandb.ai/dsaltyp0rtillo-buap/house-purchase-optuna)  
- [Evaluación final](https://wandb.ai/dsaltyp0rtillo-buap/house-purchase-final)

