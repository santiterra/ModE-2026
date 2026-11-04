# Obligatorio 2 — Modelos Estadísticos

Enunciado completo: [`Segunda entrega.pdf`](Segunda%20entrega.pdf)

**Objetivo:** entrenar y comparar modelos de regresión sobre datos sintéticos y analizar cómo se comportan las predicciones cuando los datos de test provienen de una distribución ligeramente distinta (desplazamiento de la media). El PCA se usa como herramienta para detectar y visualizar ese desplazamiento.

---

## Datos

El archivo [`problema1/mat_cov.csv`](problema1/mat_cov.csv) contiene la matriz de covarianzas **50×50** provista en el EVA (encabezados `V1`…`V50`, diagonal ≠ 1). Es simétrica y definida positiva (autovalor mínimo ≈ `1.2e-07`), por lo que puede usarse directamente en `np.random.multivariate_normal`.

## Pasos

| # | Qué hacer |
|---|-----------|
| 1 | Generar `X` con 150 observaciones y 50 variables a partir de una normal multivariada con la matriz de covarianzas provista. Fijar semilla. |
| 2 | Definir `Y` como combinación lineal de las 50 variables, con **solo 5 coeficientes no nulos**, más ruido gaussiano `N(0, σ²)` pequeño (la letra sugiere varianza 0.25). Guardar `beta_true`. |
| 3 | Separar en **train = 100** y **test = 50** observaciones. |
| 4 | Entrenar 4 modelos sobre train: **OLS** (50 vars), **Ridge** (50 vars), **Bayesiana** (50 vars) y **PCR** (elegir *k* componentes y regresar sobre ellas). Graficar los 50 coeficientes de cada modelo y compararlos con las 5 variables informativas. **Elegir un modelo y justificar.** Para PCR, mapear los pesos de las componentes al espacio original: `beta_std = V[:, :k] @ coef_pc`, luego deshacer el escalado. |
| 5 | Aplicar **PCA sobre train** y graficar **PC1 vs PC2** (indicar % de varianza explicada). Este ajuste de PCA es el mismo que usa el PCR del paso 4. |
| 6 | Partir test en **A = 25** y **B = 25**. Generar `delta ~ U(-5, 5)` de tamaño 50 y sumarlo a todas las filas de A. B queda con la distribución original. |
| 7 | Predecir A y B con el modelo elegido. Calcular **error por observación** y **MSE por conjunto**; comentar. |
| 8 | Proyectar A y B con el PCA de train (misma media y componentes) y graficar **PC1 vs PC2 coloreando por error de predicción**. Comentar. |
| 9 | Si no se conocieran las constantes sumadas a A, **¿qué estrategia elegiría para mejorar las predicciones?** (detectar el shift, estimarlo como diferencia de medias, corregirlo, modelo robusto, etc.). |

## Notas

- La numeración de la letra tiene un desfase: los pasos 7 y 8 dicen "modelo de la parte 2" y "componentes de la parte 3", pero se refieren a los pasos **4** y **5**.
- **Estandarizar** antes de Ridge y PCA (la penalización y el PCA no son invariantes a escala). Ser consistente al reportar coeficientes.
- El escalado, el PCA, `α` de Ridge y `k` del PCR se ajustan **solo con train** (evitar fuga de datos).
- Al proyectar A y B en el PCA usar la **media de train**; si se centra cada conjunto por su propia media, el desplazamiento desaparece del gráfico.
- Fijar semilla y partición una sola vez: cambiarlas obliga a rehacer todo el pipeline.

## Estructura de código

```
Obligatorio2/
├── RESUME.md
├── Segunda entrega.pdf
└── problema1/
    ├── mat_cov.csv
    └── problema1.ipynb
```

## Dependencias

```bash
pip install numpy pandas matplotlib scikit-learn jupyter
```
