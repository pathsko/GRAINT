# 🧬 Genetic Grammar-Guided Algorithm for Interest Group Discovery

Este proyecto implementa un algoritmo genético guiado por gramática para encontrar **grupos de interés** en un conjunto de datos basado en diferencias significativas de correlaciones entre variables.

📓 Proyecto desarrollado en un cuaderno de Google Colab:  
[Accede al Notebook](https://colab.research.google.com/drive/124fEF-KhpDtGB6XHJKp7AXAKHFV6uN3y?usp=sharing)

## 📌 Descripción del Problema

El objetivo es identificar subconjuntos de datos donde ciertas variables (por ejemplo, tiempo en redes sociales vs. tipo de contenido consumido) presentan **correlaciones significativamente diferentes** respecto al resto de la población.

Estos grupos pueden ayudar a una empresa a detectar patrones de comportamiento inusuales o valiosos.

## 🔧 Algoritmo Implementado

Se desarrolló un **algoritmo genético** con las siguientes características:

- 🧠 **Gramática de contexto libre (GCL)** para generar consultas condicionales.
- 🌳 Las soluciones se representan como **árboles sintácticos** que combinan condiciones sobre las variables.
- 🏆 **Función de evaluación** basada en la diferencia de correlaciones (valor absoluto si el p-valor es significativo).
- 🔄 **Operadores evolutivos personalizados**:
  - **Cruce** por intercambio de ramas en árboles.
  - **Mutación** en condiciones (sustitución o modificación de rangos/valores).
- 🎯 Se mantiene una élite con las mejores soluciones durante toda la ejecución.

## ⚙️ Parámetros Principales

### Usuario final:

- `dataInput`: DataFrame de entrada.
- `vInput`: Lista de variables continuas para evaluar.
- `nElite`: Número de soluciones óptimas a retornar.
- `exTh`: Umbral de significancia para evaluar correlaciones.
- `sOutput`: Formato de salida (`True` para SQL, `False` para árbol).
- `plotOutput`: Mostrar gráficos de las soluciones.

### Usuario experto (opcional):

- `depthTree`, `nSolutions`, `nGenerations`, `nTourn`, `pCross`, `pMut`.

## 📈 Resultados

- El algoritmo obtiene soluciones con buen rendimiento incluso con 4 variables.
- Tiempo de ejecución < 1 minuto.
- Fitness promedio decrece con más variables, como es esperable.

| Variables | Fitness promedio | Tiempo promedio (s) |
|----------|------------------|----------------------|
| 2        | 0.98 ± 0.22      | 37.72 ± 12.52        |
| 3        | 0.80 ± 0.17      | 39.25 ± 7.92         |
| 4        | 0.80 ± 0.17      | 52.02 ± 10.42        |

## ▶️ Uso

1. Abre el notebook en Google Colab.
2. Carga tu conjunto de datos como un DataFrame de `pandas`.
3. Ejecuta la sección `Algoritmo guiado por gramática`.
4. Configura tus parámetros en la sección `Material para el Usuario`.
5. Ejecuta el algoritmo y observa los resultados.

## 📚 Ejemplo de Uso

```python
encontrar_subgrupos(
    dataInput=df,
    vInput=['tiempo_rs', 'tipo_contenido', 'edad'],
    nElite=3,
    exTh=0.05,
    sOutput=True,
    plotOutput=True
)
```
