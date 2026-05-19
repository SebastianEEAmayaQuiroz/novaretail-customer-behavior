<div align="center">

<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" />
<img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" />
<img src="https://img.shields.io/badge/NumPy-013243?style=for-the-badge&logo=numpy&logoColor=white" />
<img src="https://img.shields.io/badge/Seaborn-3776AB?style=for-the-badge&logo=python&logoColor=white" />
<img src="https://img.shields.io/badge/Matplotlib-11557c?style=for-the-badge&logo=python&logoColor=white" />
<img src="https://img.shields.io/badge/SciPy-8CAAE6?style=for-the-badge&logo=scipy&logoColor=white" />

# 🛒 NovaRetail+ — Análisis de Comportamiento de Clientes 2024

**¿Qué factores del comportamiento del cliente están más fuertemente asociados con el ingreso anual generado?**

</div>

---

## 📌 Contexto del negocio

NovaRetail+ es una plataforma de e-commerce en Latinoamérica con millones de usuarios activos. Para el cierre de 2024, el equipo de **Crecimiento y Retención** necesitaba entender qué variables de comportamiento explican mejor el ingreso anual generado por cliente — con el objetivo de priorizar estrategias de retención y conversión de alto impacto.

Este proyecto es un **análisis correlacional exploratorio** sobre 15,000 registros de clientes. La hipótesis central: no todos los comportamientos del cliente tienen el mismo peso en los ingresos.

> ⚠️ **Nota metodológica:** Correlación ≠ causalidad. Los hallazgos identifican asociaciones, no relaciones causales.

---

## 🎯 Objetivos del análisis

- Identificar las variables de comportamiento más fuertemente asociadas con `ingreso_anual`
- Evaluar el rol de variables binarias (membresía premium, abandono) y categóricas (región, dispositivo)
- Generar recomendaciones de negocio accionables basadas en evidencia estadística

---

## 📂 Dataset

| Campo | Descripción |
|---|---|
| `id_cliente` | Identificador único del cliente |
| `edad` | Edad del cliente |
| `nivel_ingreso` | Ingreso anual estimado del cliente |
| `visitas_mes` | Visitas a la plataforma por mes |
| `compras_mes` | Número de compras realizadas en el mes |
| `gasto_publicidad_dirigida` | Gasto en anuncios asignado al cliente |
| `satisfaccion` | Calificación de satisfacción (escala 1–5) |
| `miembro_premium` | Suscripción premium: 1 = sí, 0 = no |
| `abandono` | Abandono de plataforma: 1 = sí, 0 = no |
| `tipo_dispositivo` | Móvil / Tablet / Escritorio |
| `region` | Norte / Sur / Este / Oeste |
| `ingreso_anual` | **Variable objetivo** — ingreso generado para NovaRetail+ |

**Registros:** 15,000 clientes · **Nulos:** ninguno · **Período:** 2024

---

## 🧪 Metodología

Se aplicaron cuatro coeficientes de correlación según el tipo de variable:

| Tipo de relación | Método utilizado | Razón |
|---|---|---|
| Numérica ↔ Numérica | **Spearman** | `ingreso_anual` presenta distribución asimétrica positiva |
| Numérica ↔ Binaria | **Punto-biserial** | Variables 0/1 vs. variable continua |
| Categórica ↔ Categórica | **V de Cramér** | Variables nominales sin orden |

---

## 📊 Hallazgos principales

### 🔑 Hallazgo 1 — `compras_mes` domina el ingreso anual (r = 0.97)

La cantidad de compras mensuales tiene una correlación **casi perfecta** con el ingreso anual. Los clientes con mayor frecuencia de compra generan sistemáticamente más ingresos para la plataforma.

**Implicación:** Estrategias de fidelización orientadas a la segunda y tercera compra (cupones post-compra, programas de puntos) tendrían el mayor ROI potencial.

---

### 🔑 Hallazgo 2 — Las visitas tienen efecto moderado e indirecto (r = 0.32)

Las visitas a la plataforma muestran una correlación moderada con el ingreso, pero esta relación parece estar **mediada por las compras**. No toda visita se convierte en compra.

**Implicación:** Más tráfico no es suficiente. La optimización de la tasa de conversión (checkout rápido, carritos abandonados, recomendaciones) es más rentable que invertir solo en visitas.

---

### 🔑 Hallazgo 3 — Membresía premium: asociación débil (r = 0.09)

Los clientes premium generan ligeramente más ingresos, pero la diferencia es mínima. La membresía por sí sola **no explica** el ingreso anual.

**Implicación:** El valor del cliente premium está condicionado a su comportamiento de compra, no a la membresía en sí.

---

### 🔑 Hallazgo 4 — Región y dispositivo: sin impacto relevante (V ≈ 0.01)

Ninguna variable categórica (región, tipo de dispositivo) muestra asociación con el ingreso generado. Los clientes de todas las regiones y dispositivos se comportan de forma similar.

**Implicación:** Las estrategias de crecimiento pueden ser uniformes a nivel geográfico y de plataforma.

---

### 🔑 Hallazgo 5 — Edad, satisfacción e ingreso del cliente: sin relación (r < 0.07)

Variables demográficas y perceptuales no predicen el valor del cliente para NovaRetail+. Un cliente satisfecho o de alto ingreso personal no necesariamente genera más ingresos para la plataforma.

**Implicación:** El foco de segmentación debe estar en **comportamiento** (compras, visitas), no en demografía.

---

## 📈 Resumen de correlaciones con `ingreso_anual`

| Variable | Método | Coeficiente | Magnitud |
|---|---|---|---|
| `compras_mes` | Spearman | **0.9675** | 🔴 Muy fuerte |
| `visitas_mes` | Spearman | 0.3210 | 🟡 Moderada |
| `gasto_publicidad_dirigida` | Spearman | 0.1900 | 🟡 Débil |
| `miembro_premium` | Punto-biserial | 0.0931 | ⚪ Muy débil |
| `satisfaccion` | Spearman | 0.0608 | ⚪ Nula |
| `nivel_ingreso` | Spearman | 0.0250 | ⚪ Nula |
| `abandono` | Punto-biserial | -0.0028 | ⚪ Nula |
| `tipo_dispositivo` | V de Cramér | 0.0145 | ⚪ Nula |
| `region` | V de Cramér | 0.0172 | ⚪ Nula |

---

## 🗂️ Estructura del proyecto

```
novaretail-customer-behavior/
├── novaretail_comportamiento_clientes_2024.csv   # Dataset (15,000 registros)
├── S8_Student_Version-Project-NovaRetail.ipynb   # Notebook principal
└── README.md
```

---

## 🔮 Próximos pasos sugeridos

1. **Segmentación por frecuencia de compra** — Crear clusters (baja / media / alta) y analizar comportamientos diferenciales
2. **Análisis de clientes con ingreso = 0** — ¿Por qué existen y qué los activa?
3. **Modelado predictivo** — Random Forest o XGBoost para predecir `ingreso_anual`
4. **Análisis longitudinal** — Incorporar datos históricos para evaluar tendencias
5. **Experimentación A/B** — Medir el impacto causal de incentivos de segunda compra

---

## 👤 Autor

**Sebastián Amaya** — Analista de Datos | Contador Público en formación

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/sebastianamayada)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/SebastianEEAmayaQuiroz)

---

*Proyecto desarrollado como parte del Bootcamp de Análisis de Datos — TripleTen (2025–2026)*
