# 📊 Informe Ejecutivo: Análisis Exploratorio de Datos (EDA) sobre COVID-19 en EE.UU.

**Fuente de Datos:** `all-states-history.csv` (10 variables clave seleccionadas)  
**Fecha de Análisis:** Noviembre 2026  
**Objetivo:** Evaluar el impacto epidemiológico, la calidad de los datos y las dinámicas temporales del COVID-19 para la toma de decisiones informadas.

---

## 🟢 Tarjetas de Métricas Clave (KPIs)

| 📈 Total Casos Incrementales Registrados | 💀 Total Fallecimientos Registrados | 🏥 Pico Máximo de Hospitalizaciones Activas | 🧪 Ratio Promedio Test Positivos / Total Tests |
| :---: | :---: | :---: | :---: |
| **+28.7M** | **+515K** | **132,474** | **~8.5%** |

---

## 1. Calidad e Integridad de los Datos

### ❓ Pregunta Clave de Negocio
> **¿Es el dataset lo suficientemente fiable y completo para fundamentar decisiones estratégicas y de gestión de recursos de salud pública?**

### 📋 Análisis de Valores Nulos
El análisis de completitud revela que las variables de seguimiento directo de casos y muertes cuentan con una excelente cobertura, mientras que las métricas de capacidad hospitalaria crítica presentan una omisión significativa debido a diferencias en los reportes estatales.

| Variable | Porcentaje de Nulos (%) | Nivel de Riesgo | Acción Recomendada |
| :--- | :---: | :---: | :--- |
| `date_dt` | **0.00%** | 🟢 Nulo | Usar como eje temporal primario. |
| `state` | **0.00%** | 🟢 Nulo | Segmentación geográfica completa. |
| `positiveIncrease` | **0.90%** | 🟢 Muy Bajo | Imputación directa / Filtrado simple. |
| `deathIncrease` | **4.09%** | 🟢 Bajo | Apto para agregaciones diarias. |
| `totalTestResultsIncrease` | **8.42%** | 🟡 Moderado | Validar saltos en reportes estatales. |
| `hospitalizedCurrently` | **16.56%** | 🟡 Moderado | Utilizar sesgado a estados con reporte continuo. |
| `inIcuCurrently` | **44.00%** | 🔴 Alto | No usar para comparativas agregadas nacionales. |

> 📊 **UBICACIÓN DE GRÁFICO [EDA Fig. 1]:**  
> **Tipo de Gráfico:** Barplot de Calidad de Datos  
> **Variables:** `Variables` vs `% Valores Nulos`  
> **Objetivo Visual:** Identificar rápidamente qué métricas requieren precaución analítica antes de su integración en tableros de control.

---

## 2. Distribución y Asimetría de las Variables Críticas

### ❓ Pregunta Clave de Negocio
> **¿Cómo se comporta la distribución diaria de la carga viral y la mortalidad, y cuáles son los niveles operativos típicos frente a los picos extremos?**

### 📈 Comportamiento Estadístico
Las métricas diarias de contagios, fallecimientos y capacidad hospitalaria muestran una **asimetría positiva severa (derecha)**. Esto indica que la mayor parte del tiempo los valores se mantienen en rangos moderados, intercalados por olas severas de picos extremos.

* **Nuevos Casos (`positiveIncrease`):** Mediana sustancialmente inferior a la media, impulsada por los brotes de invierno.
* **Mortalidad Diaria (`deathIncrease`):** Presencia de sesgos por retrasos de reporte en fines de semana (efecto "fin de semana").
* **Hospitalizaciones (`hospitalizedCurrently`):** Distribución bimodal que refleja las distintas olas epidemiológicas a nivel nacional.

> 📊 **UBICACIÓN DE GRÁFICO [EDA Fig. 2]:**  
> **Tipo de Gráfico:** Cuadrícula de Histogramas y KDE (2x2)  
> **Variables:** `positiveIncrease`, `deathIncrease`, `hospitalizedCurrently`, `totalTestResultsIncrease`  
> **Objetivo Visual:** Visualizar la asimetría de las distribuciones e identificar la presencia de valores atípicos (outliers).

---

## 3. Dinámica Temporal y Olas Epidemiológicas

### ❓ Pregunta Clave de Negocio
> **¿Existe un desfase temporal claro entre el incremento de contagios y el aumento en la mortalidad y presión hospitalaria?**

### ⏳ Análisis de Tendencia Temporal
El estudio de la serie temporal demuestra una clara correlación desfasada entre los contagios confirmados y la mortalidad:

1. **Primera Ola (Primavera 2020):** Alta mortalidad relativa debido a la menor capacidad de testeo inicial.
2. **Segunda Ola (Verano 2020):** Incremento de contagios con menor letalidad proporcional.
3. **Tercera Ola (Invierno 2020-2021):** Pico máximo conjunto en contagios (`positiveIncrease`), hospitalizaciones activas (`hospitalizedCurrently`) y fallecimientos (`deathIncrease`).

```
[ Incremento de Positivos ] ──(Desfase 10-14 días)──> [ Ocupación UCI / Hospitalaria ] ──(Desfase 7 días)──> [ Incremento de Defunciones ]
```

> 📊 **UBICACIÓN DE GRÁFICO [EDA Fig. 3]:**  
> **Tipo de Gráfico:** Serie Temporal de Doble Eje Y  
> **Variables:** `date_dt` (Eje X) vs `positiveIncrease` (Eje Y Izq.) & `deathIncrease` (Eje Y Der.)  
> **Objetivo Visual:** Evaluar el retardo entre el pico de contagios y el pico de fallecimientos para la planificación de respuesta médica.

---

## 4. Conclusiones Estratégicas y Recomendaciones

1. **Estandarización de Reportes:** Se debe priorizar la recolección de datos de UCI (`inIcuCurrently`), ya que el 44% de vacíos limita la capacidad de predicción en unidades de cuidados intensivos a nivel federal.
2. **Sistema de Alerta Temprana:** Implementar modelos predictivos basados en `positiveIncrease` con una ventana de anticipación de 14 días para prever el colapso hospitalario.
3. **Ajuste de Calendario:** Corregir las métricas de `deathIncrease` mediante medias móviles de 7 días para eliminar el ruido provocado por el subregistro de fin de semana.