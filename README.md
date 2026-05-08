# Predicción de Intención de Compra - Casa Inteligente

* **Framework:** TensorFlow / Keras
* **Optimización:** Optuna (Búsqueda Bayesiana)
* **Monitoreo:** Weights & Biases (WandB)
* **Entorno:** Miniconda / Python 3.13
  

1.  **Exploración de Arquitecturas:** Se utilizó **Optuna** para iterar sobre decenas de combinaciones de capas, neuronas y tasas de aprendizaje (`learning_rate`), buscando minimizar la función de pérdida.
2.  **Seguimiento de Experimentos:** Cada "trial" fue registrado en **WandB**, lo que permitió visualizar la convergencia de las curvas de *Loss* y *Accuracy* en tiempo real, garantizando que el modelo no sufriera de sobreajuste (**Overfitting**).
3.  **Ajuste de Pesos:** Dado el desbalance de clases, se implementaron `class_weights` para darle mayor importancia a los compradores reales.


| Métrica | Modelo de Concurso (Base) | Modelo de Negocio (Optimizado) |
| :--- | :--- | :--- |
| **Accuracy** | **77.01%** | 65.37% |
| **Umbral (Threshold)** | 0.6192 | 0.25 |
| **Estrategia** | Maximizar el acierto global. | Maximizar la detección de compradores. |
| **Veredicto** | Excelente para filtrar "No Compradores". | **Ideal para ventas**, capturando al 99% de los clientes potenciales. |

> **Nota Técnica:** Presentar un Accuracy del 77% es matemáticamente superior, pero en un entorno de ventas, el modelo con un umbral de **0.25** es el que genera valor real al reducir drásticamente los Falsos Negativos (clientes perdidos).

El repositorio incluye los notebooks con las gráficas de entrenamiento donde se observa una convergencia limpia entre el set de entrenamiento y el de validación, validando la robustez del sistema.

* [P0rtillosETY](https://github.com/P0rtillosETY)  
*
