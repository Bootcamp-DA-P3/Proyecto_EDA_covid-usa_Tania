# 📊 Análisis Exploratorio de Datos (EDA) - Impacto Sanitario de COVID-19 en EE. UU.

> **Orientado a la Toma de Decisiones, Análisis de Ratios e Impacto Regional**

---

## 🚀 Descripción del Proyecto
Este proyecto consiste en un **Análisis Exploratorio de Datos (EDA)** completo sobre el registro histórico del COVID-19 en los Estados Unidos (`all-states-history.csv`)[cite: 7]. El objetivo principal es extraer inteligencia sanitaria procesable para la gestión directiva, identificando patrones de propagación, la relación desfasada (*lag*) entre contagios y mortalidad, y la presión real sobre la infraestructura hospitalaria[cite: 7].

---

## 🛠️ Estructura del Repositorio
```text
📦 EDA-COVID19-US/
│
├── 📂 graficas/                  # Directorio de visualizaciones generadas para el informe
│   ├── 📁 figura_1_nulos.png     # Auditoría de integridad y valores faltantes
│   └── 📁 figura_2_distribuciones.png # Análisis univariado de asimetría
│
├── 📓 EDA_Covid19_US.ipynb       # Jupyter Notebook con el código fuente y análisis paso a paso
├── 📄 Informe Ejecutivo Completo # Documentación directiva del proyecto
└── 📄 README.md                  # Documentación principal del repositorio

##📋 Fases del Análisis y MetodologíaDefinición del Dataset: Selección estratégica de variables clave (flujos diarios, acumulados y capacidad hospitalaria actual) a partir del dataset bruto.   Diagnóstico de Calidad e Imputación: Auditoría de valores nulos (con énfasis en la escasez de registros UCI e infraestructura) y aplicación de técnicas de interpolación y asignación de ceros en flujos no reportados.   Análisis Univariado: Estudio de distribución y asimetría positiva en variables de flujo diario, demostrando el comportamiento de la pandemia por olas extremas.   Tendencias Temporales y Desfase (Lag): Identificación empírica del desfase estructural entre el pico de contagios (positiveIncrease) y el pico de saturación/mortalidad (deathIncrease).   Análisis Bivariado y Regional: Comparación de volúmenes absolutos frente a métricas estandarizadas por habitante, revelando el impacto relativo en distintas zonas.   Matriz de Correlación: Identificación de variables críticas (como la ocupación UCI) frente a los decesos.   Conclusiones Directivas: Recomendaciones operativas basadas en la ventana de anticipación para la gestión de recursos sanitarios.
