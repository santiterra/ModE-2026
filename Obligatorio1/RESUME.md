# Obligatorio 1 — Modelos Estadísticos

Enunciado completo: [`Obligatorio1.pdf`](Obligatorio1.pdf)

Cada problema ocupa una carilla del informe final (máx. 4 carillas en total, incluyendo portada con nombres, cédulas y link al repositorio).

---

## Problema 1 — Estimador de máxima verosimilitud

Dada la v.a. con densidad `fX(x) = (1/2)(1 + θx)` para `|x| ≤ 1`, `θ ∈ [-1, 1]`.

| Ítem | Qué hacer |
|------|-----------|
| 1.1 | Función para simular una muestra de tamaño `n` con `θ = -1/3` |
| 1.2 | Para `n = 10`: graficar la función de máxima verosimilitud (o log-verosimilitud) y aproximar su máximo con Golden search |
| 1.3 | Generar ~50 muestras de `n = 10`, estimar `θ` en cada una y calcular MSE, sesgo y varianza (con `θ = -1/3` conocido) |
| 1.4 | Repetir 1.3 con `n = 100` y `n = 1000`; analizar cómo varían MSE, sesgo y varianza |

**Entregable:** código + gráfica de la verosimilitud + tabla de MSE/sesgo/varianza por tamaño de muestra + conclusiones.

---

## Problema 2 — Regresión en Boston Housing

Dataset clásico: 506 observaciones, 13 atributos. Objetivo: predecir **MEDV**.

| Ítem | Qué hacer |
|------|-----------|
| 2.1 | Carga y análisis exploratorio inicial |
| 2.2 | División en conjuntos de entrenamiento y validación |
| 2.3 | Regresión lineal con todas las características; evaluar con MSE en train y validación |
| 2.4 | Características polinomiales hasta grado 3; entrenar y evaluar |
| 2.5 | Ridge sobre las características polinomiales; λ óptimo por validación cruzada |

**Gráficas sugeridas:**
- MSE vs. grado del polinomio
- MSE vs. λ para Ridge
- Mejor modelo polinomial (con y sin regularización) vs. datos reales

**Conclusiones:** ¿qué modelo es el mejor? ¿Cómo impactan las features polinomiales y la regularización?

---

## Problema 3 — Alturas

A partir del juego de datos *alturas* recabado en clase:

- Construir un modelo lineal para predecir la altura de los hijos.
- Se deciden libremente variables y observaciones a incluir (no es obligatorio usar todo).
- Escribir el modelo final y explicar el significado de cada coeficiente.

**Nota:** este problema depende de la calidad de los datos (reales y sin curar); es esperable que las decisiones de curación sean propias del grupo.

---

## Estructura de código

```
Obligatorio1/
├── problema1/
│   └── problema1_mle.ipynb
├── problema2/
│   └── problema2_boston.ipynb
└── problema3/
    └── problema3_alturas.ipynb
```

> Los archivos de código se agregan en esta etapa; la estructura puede ajustarse según se organice el grupo.

## Dependencias

```bash
pip install numpy pandas matplotlib scikit-learn jupyter
```
