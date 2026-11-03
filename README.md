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
```

---

## 📋 Fases del Análisis y Metodología
1. Definición del Dataset: Selección estratégica de variables clave (flujos diarios, acumulados y capacidad hospitalaria actual) a partir
a partir del dataset bruto.
2. Diagnóstico de Calidad e Imputación: Auditoría de valores nulos (con énfasis en la escasez de registros UCI e infraestructura) y aplicación de técnicas de interpolación y asignación de ceros en flujos no reportados.
3. Análisis Univariado: Estudio de distribución y asimetría positiva en variables de flujo diario, demostrando el comportamiento de la pandemia por olas extremas.
4. Tendencias Temporales y Desfase (Lag): Identificación empírica del desfase estructural entre el pico de contagios (positiveIncrease) y el pico de saturación/mortalidad (deathIncrease).
5. Análisis Bivariado y Regional: Comparación de volúmenes absolutos frente a métricas estandarizadas por habitante, revelando el impacto relativo en distintas zonas.
6. Matriz de Correlación: Identificación de variables críticas (como la ocupación UCI) frente a los decesos.
7. Conclusiones Directivas: Recomendaciones operativas basadas en la ventana de anticipación para la gestión de recursos sanitarios.   

---

## ⚙️ Tecnologías y Librerías UtilizadasEl proyecto está desarrollado íntegramente en Python, utilizando el siguiente stack tecnológico:

- Pandas & NumPy: Ingesta, limpieza, transformación y estructuración de series temporales.
- Matplotlib & Seaborn: Visualización avanzada de distribuciones, matrices de correlación y gráficos exploratorios.

---

## App interactiva
App que muestra casi la misma información y gráficas del notebook.

streamlit run src/Appsteamlit.py

---

## 📌 Principales Conclusiones Operativas
- Ventana Predictiva: El desfase identificado permite a las directivas activar planes de contingencia con antelación.
- KPI Central: La monitorización debe priorizar la ocupación de camas críticas por encima de los contagios absolutos para medir la verdadera severidad sanitaria.
- Estrategia Demográfica: La asignación de recursos debe basarse en la vulnerabilidad per cápita y no solo en el volumen poblacional absoluto.
