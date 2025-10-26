# Análisis de Clustering - Línea 141 SEDRONAR

**Materia:** Análisis de la Información y la Decisión  
**Carrera:** Ingeniería en Inteligencia Artificial – Universidad de Palermo  
**Período de Datos:** Primer Semestre 2025  

---

## Descripción del Proyecto

Este proyecto implementa un **análisis de clustering no supervisado** sobre las consultas telefónicas recibidas por la **Línea 141** (línea nacional de asistencia en adicciones de SEDRONAR) durante el primer semestre de 2025.

Se aplicó el algoritmo **K-Means** sobre **14.091 llamadas efectivas**, identificando **3 perfiles diferenciados** de demanda con características demográficas, contextuales y necesidades específicas.

### Objetivos

- Identificar **perfiles diferenciados** de consultantes mediante clustering  
- Analizar **patrones demográficos, geográficos y temporales** de las consultas  
- Caracterizar tipos de crisis y necesidades específicas por segmento  
- Generar **recomendaciones basadas en evidencia** para optimizar el servicio  

### Resultados Clave

✅ **3 clusters identificados** con perfiles distintos  
✅ **Silhouette Score: 0.252** (tras optimización dimensional 109→67 features)  
✅ **14.091 llamadas efectivas** analizadas (71.2% del total)  
✅ **11 visualizaciones profesionales** generadas  
✅ **Pipeline reproducible** con random_state=42  

---

## Clusters Identificados

### 🔹 Cluster 0 - Consultas Informativas (41.0%)  
**5.782 llamadas** - Pedidos de información general sin caso específico de consumo  

**Características:**
- 100% tipo "Informe" - no refieren a una persona con consumo  
- Sin datos demográficos del consumidor (edad, género, motivo)  
- Consultantes variados: Consumidor (26%), Madre (19%), Otros (12%)  
- Horario: Principalmente tarde (40%), seguido de mañana (28%)  

**Recomendaciones:**
- ✅ Implementar chatbot para consultas frecuentes  
- ✅ Crear FAQs y material educativo descargable  
- ✅ Derivación automática a recursos según región  
- ✅ Campañas de difusión sobre servicios disponibles  

---

### 🔹 Cluster 1 - Consumidores Adultos Crónicos (22.5%)
**3.177 llamadas** - Adultos de mediana edad con consumo prolongado  

**Características:**
- **Edad promedio:** 42.5 años (mediana: 40 años)  
- **Ellos mismos llaman** - principal consultante: Consumidor (38%)  
- **Tiempo de consumo:** >10 años en la mayoría de casos  
- **Antecedentes:** 32% ya estuvo en tratamiento, 37% nunca estuvo  
- **Motivos principales:** Trastornos crónicos (24%), Crisis (17%), Recaídas, Inquietudes por tipo de vida  

**Recomendaciones:**
- ✅ Programas de seguimiento prolongado  
- ✅ Grupos de apoyo para prevención de recaídas  
- ✅ Articulación con servicios de salud mental  
- ✅ Estrategias de adherencia a tratamientos de largo plazo  

---

### 🔹 Cluster 2 - Jóvenes con Familias Preocupadas (36.4%)
**5.132 llamadas** - Jóvenes adultos con detección familiar temprana  

**Características:**
- **Edad promedio:** 26.0 años (mediana: 26 años)  
- **MADRES** son las principales consultantes (33% del cluster)  
- **Consultas mayormente indirectas** (80%)  
- **Tratamiento:** 52% nunca estuvo - **primeros contactos críticos**  
- **Motivos principales:** Inquietudes por tipo de vida (19%), Trastornos (16%), Crisis (13%)  

**Recomendaciones:**
- ✅ Protocolo de derivación urgente - ventana de oportunidad  
- ✅ Talleres de orientación para padres y familiares  
- ✅ Trabajo en detección temprana y prevención secundaria  
- ✅ Fortalecimiento del rol familiar en el proceso terapéutico  

---

## Dataset

- **Fuente:** [SEDRONAR - Base Línea 141](https://datos.gob.ar/dataset/sedronar-base-linea-141/archivo/sedronar_12.5)  
- **Período:** Enero - Junio 2025  
- **Total de registros:** 19.795 llamadas  
  - **Efectivas:** 14.091 (71.2%) - usadas para clustering  
  - **No efectivas:** 5.704 (28.8%) - análisis de eficiencia del servicio  

### Variables Principales

- **Demográficas:** Edad, género, localidad y provincia del consumidor y consultante  
- **Contextuales:** Tipo de consulta (Directa/Indirecta/Informe), motivo de consulta, relación con consumidor  
- **Temporales:** Fecha, día de la semana, hora, franja horaria  
- **Clínicas:** Tiempo de consumo, antecedentes de tratamiento, tipo de crisis  

### Distribución Geográfica (según estadísticas oficiales)

- **Buenos Aires:** ~58% de las llamadas  
- **CABA:** ~11-13%  
- **Córdoba:** ~5%  
- **Santa Fe:** ~6%  
- **Mendoza:** ~3%  
- **Resto del país:** ~11-14%  

### Calidad de los Datos

✅ Variables bien definidas y estandarizadas  
✅ Consistencia con estadísticas oficiales publicadas por SEDRONAR  
✅ Distribución geográfica alineada con reportes mensuales  
⚠️ Valores faltantes esperables según tipo de llamada (no implican error de calidad)  
✅ Registros completos para variables críticas (fecha, tipo de consulta, modalidad)  

---

## Stack Tecnológico

### Lenguaje y Librerías
```
Python 3.12
├── pandas==2.3.3          # Manipulación de datos
├── numpy==2.3.4           # Operaciones numéricas
├── scikit-learn==1.7.2    # Clustering y preprocesamiento
├── matplotlib==3.10.7     # Visualización
└── seaborn==0.13.2        # Visualización estadística
```

### Entorno
- **Jupyter Notebook** - Análisis interactivo
- **VSCode** - Editor principal
- **Git/GitHub** - Control de versiones

---

## Instalación y Configuración

### 1. Clonar el repositorio
```bash
git clone https://github.com/ginasoft/tp-mineria-141.git
cd tp-mineria-141
```

### 2. Crear entorno virtual
```bash
pip install virtualenv
virtualenv .venv -p python
```

### 3. Activar entorno virtual

**Windows (PowerShell):**
```powershell
. .\.venv\Scripts\Activate.ps1
```

> Si aparece error de políticas de ejecución:
> ```powershell
> Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
> ```

**Linux/Mac:**
```bash
source .venv/bin/activate
```

### 4. Instalar dependencias
```bash
pip install -r requirements.txt
```

---

## Estructura del Proyecto

```
tp-mineria-141/
├── data/
│   └── 1ersemestre2025.csv           # Dataset original (19.795 registros)
├── notebooks/
│   └── 01_clustering_linea141.ipynb  # Notebook principal con análisis completo
├── outputs/
│   ├── grafico_segmentacion_dataset.png
│   ├── comparacion_v1_v2_clustering.png
│   ├── grafico_resumen_clusters.png
│   ├── grafico_tipo_consulta_cluster.png
│   ├── grafico_edad_cluster.png
│   ├── grafico_consultante_cluster.png
│   ├── grafico_motivos_cluster.png
│   ├── grafico_tratamiento_cluster.png
│   ├── grafico_franja_horaria_cluster.png
│   ├── llamadas_no_efectivas.png
│   ├── metodo_codo_silhouette.png
│   └── tablas/
│       ├── df_clusters.csv                # Dataset con clusters asignados
│       ├── resumen_clusters.csv           # Resumen ejecutivo
│       ├── perfil_detallado_clusters.csv  # Top 3 categorías por variable
│       └── perfil_clusters_ppt.csv        # Tabla para presentación
├── docs/
│   ├── presentacion_clustering_linea141.pdf   # Presentación en PDF
│   └── presentacion_clustering_linea141.pptx  # Presentación PowerPoint
├── requirements.txt
├── .gitignore
└── README.md
```

---

## Metodología

### 1. Exploración y Limpieza de Datos (EDA)
- Análisis de calidad de datos y valores faltantes (19.795 → 14.091 efectivas)
- Limpieza de caracteres UTF-8 y estandarización de categorías
- Conversión de edad a tipo nullable (Int64) para manejar NaN correctamente
- Identificación de 0 duplicados

### 2. Ingeniería de Features
- **Features temporales:** Mes, día de semana, franja horaria (Madrugada/Mañana/Tarde/Noche), es_fin_de_semana
- **Segmentación:** Llamadas efectivas (71.2%) vs. no efectivas (28.8%)
- **Reducción dimensional:** 15 variables → 10 variables seleccionadas
- **Optimización:** 109 features → 67 features tras One-Hot Encoding (reducción de 42 features)

### 3. Preprocesamiento (Pipeline)
- **Imputación:** Mediana para variables numéricas, "Desconocido" para categóricas
- **Encoding:** One-Hot Encoding para variables categóricas (drop=None)
- **Escalado:** StandardScaler para variables numéricas
- **Pipeline:** ColumnTransformer para transformación reproducible

### 4. Selección del k Óptimo
- **Método del codo:** Análisis de inercia para k=2..8
- **Silhouette Score:** Evaluación de calidad de clustering
- **Comparación V1 vs V2:**
  - V1 (109 features): Silhouette = 0.169
  - V2 (67 features): Silhouette = 0.252 → **Mejora del 47%**
- **Resultado:** k=3 elegido (codo + silhouette + interpretabilidad)

### 5. Clustering Final
- **Algoritmo:** K-Means con k=3
- **Random state:** 42 (reproducibilidad garantizada)
- **N_init:** 10 (múltiples inicializaciones)
- **Evaluación:** Silhouette Score: 0.2520, Inercia: 68,611.28

---

## Resultados y Visualizaciones

### Métricas del Modelo

| Métrica | Valor |
|---------|-------|
| Algoritmo | K-Means |
| Número de clusters | 3 |
| Variables seleccionadas | 10 (2 numéricas + 8 categóricas) |
| Features tras One-Hot Encoding | 67 |
| Silhouette Score | 0.2520 |
| Inercia final | 68,611.28 |
| Registros analizados | 14,091 (efectivas) |

### Distribución de Clusters

| Cluster | Nombre | Tamaño | Porcentaje | Edad Promedio |
|---------|--------|--------|------------|---------------|
| 0 | Consultas Informativas | 5,782 | 41.0% | N/A |
| 1 | Adultos Crónicos | 3,177 | 22.5% | 42.5 años |
| 2 | Jóvenes + Familias | 5,132 | 36.4% | 26.0 años |

### Gráficos Generados (11 visualizaciones)

1. **Segmentación del dataset** - Efectivas (71.2%) vs No efectivas (28.8%)
2. **Comparación V1 vs V2** - Optimización del modelo (mejora 47%)
3. **Resumen de clusters** - Distribución y edades promedio
4. **Tipo de consulta por cluster** - Directa/Indirecta/Informe
5. **Distribución de edad** - Boxplot comparativo (42 vs 26 años)
6. **Tipos de consultante** - Top 5 por cluster (Madres 33% en Cluster 2)
7. **Top 5 motivos de consulta** - Trastornos, crisis, inquietudes
8. **Antecedentes de tratamiento** - Nunca estuvo vs Está/Estuvo
9. **Patrones de franja horaria** - Tarde (40-43%), Mañana, Noche
10. **Llamadas no efectivas** - Cortes (35%), Equivocados (29%)
11. **Método del codo y Silhouette** - Selección de k óptimo

---

## Hallazgos Principales

### 1. Diferenciación Demográfica Clara
- **Cluster 1:** Edad promedio 42 años (adultos/mediana edad)
- **Cluster 2:** Edad promedio 26 años (jóvenes adultos)
- **Diferencia de 16 años** entre segmentos - evidencia consumos en etapas vitales distintas

### 2. Rol Crítico de la Familia en Detección Temprana
- **Cluster 2:** Madres representan el 33% de consultantes
- Consultas mayormente indirectas (80%) - familias detectan señales
- 52% nunca estuvo en tratamiento - **ventana crítica de intervención**

### 3. Consumo Crónico vs Primeros Contactos
- **Cluster 1:** 32% ya estuvo en tratamiento, >10 años de consumo - recaídas y cronicidad
- **Cluster 2:** Primeros contactos - oportunidad de cambiar trayectorias de vida

### 4. Llamadas No Efectivas (28.8% - Oportunidad de Mejora)
- **Cortes:** 35.4% - problemas técnicos/operativos
- **Equivocados:** 28.9% - necesidad de mejor difusión del número correcto
- **Insultos/Bromas:** 19.8% - uso indebido del servicio
- **Silencio:** 15.9% - posibles abandonos por duda/miedo
- **Impacto:** Reducir estas ineficiencias podría aumentar capacidad efectiva del servicio sin aumentar recursos

### 5. Patrones Temporales Homogéneos
- **Tarde:** 40-43% de llamadas (pico de demanda consistente)
- **Mañana:** 27-28% (volumen moderado)
- **Distribución similar** entre los 3 clusters
- **Recomendación:** Mantener cobertura robusta en horario diurno/vespertino

### 6. Necesidad de Automatización
- **41% de llamadas** son consultas informativas sin caso específico
- Representa carga operativa que podría optimizarse con tecnología

---

## Recomendaciones Estratégicas

### Por Cluster

| Cluster | Acción Prioritaria | Justificación |
|---------|-------------------|---------------|
| **0 - Informativas (41%)** | Automatización: chatbot, FAQs, material educativo descargable | Libera recursos humanos para casos complejos |
| **1 - Adultos Crónicos (22.5%)** | Seguimiento prolongado, grupos de apoyo, prevención de recaídas | Necesitan acompañamiento sostenido por cronicidad |
| **2 - Jóvenes + Familias (36.4%)** | Derivación urgente, talleres para padres, detección temprana | Ventana crítica - primeros contactos con tratamiento |

### Transversales
- **Reducir llamadas no efectivas (28.8%):** Inversión en infraestructura técnica y campañas de difusión
- **Optimizar recursos:** Asignación diferenciada según franja horaria y perfil de demanda
- **Fortalecer vínculo familiar:** Orientación específica para familias del Cluster 2
- **Monitoreo continuo:** Análisis trimestrales para detectar cambios en perfiles

---

## Reproducibilidad

### Garantías
✅ `random_state=42` fijado en K-Means
✅ Versiones de librerías documentadas en `requirements.txt`
✅ Pipeline completo documentado en notebook ejecutado
✅ Dataset público de datos.gob.ar (enlace permanente)
✅ Código completo con comentarios explicativos

### Verificación del Entorno
```bash
python --version
pip list
python -c "import pandas, numpy, sklearn, matplotlib, seaborn; print('Entorno OK')"
```

### Reproducir el Análisis Completo
```bash
# 1. Activar entorno
. .\.venv\Scripts\Activate.ps1  # Windows
# source .venv/bin/activate      # Linux/Mac

# 2. Abrir notebook
jupyter notebook notebooks/01_clustering_linea141.ipynb

# 3. Ejecutar Run All
```

---

## Ejecución del Análisis

### Opción 1: Jupyter Notebook (Recomendada)
```bash
jupyter notebook notebooks/01_clustering_linea141.ipynb
```

### Opción 2: VSCode
1. Abrir `notebooks/01_clustering_linea141.ipynb`
2. Seleccionar kernel Python (.venv)
3. Ejecutar `Run All` (⏩)

### Contenido del Notebook (20 puntos completos)

1. Carga y exploración inicial del dataset (19.795 registros)
2. Análisis de calidad de datos y valores faltantes
3. Creación de features temporales (mes, día, hora, franja)
4. Segmentación efectivas (14.091) vs no efectivas (5.704)
5. Selección de 10 variables para clustering
6. Limpieza semántica de categorías ("Sin definir" estandarizado)
7. Partición final para modelado (df_model con 15 columnas)
8. Preprocesamiento con Pipeline (imputación + encoding + escalado)
9. Búsqueda del k óptimo (V1: 109 features vs V2: 67 features)
10. Entrenamiento final K-Means con k=3 (Silhouette: 0.252)
11. Perfilado detallado de clusters (variables clave por grupo)
12. Visualizaciones para presentación (11 gráficos profesionales)
13. Tablas exportables (4 CSVs generados)
14. Narrativa y conclusiones por cluster
15. Análisis de llamadas no efectivas (tipos y patrones)
16. Exportables finales (dataset con clusters + resúmenes)
17. Documentación de reproducibilidad (versiones de librerías)
18. Métricas finales del modelo (inercia, silhouette, distribución)
19. Resumen ejecutivo del proyecto completo
20. Checklist de entregables generados

---

## Presentación

### Materiales Disponibles

**Descargas:**
- [📄 Presentación en PDF](docs/presentacion_clustering_linea141.pdf)
- [📊 Presentación en PowerPoint](docs/presentacion_clustering_linea141.pptx)

---

## Conclusiones

### Hallazgos Técnicos
- El clustering K-Means con k=3 logró **segmentar efectivamente** las llamadas en 3 perfiles diferenciados
- La **optimización dimensional** (109→67 features) mejoró el Silhouette Score en **47%**, reduciendo ruido
- Los 3 clusters tienen perfiles **demográficos y contextuales claramente diferenciados** (edad, consultante, motivos)
- El modelo alcanzó un **Silhouette Score de 0.252**, indicando segmentación coherente

### Valor para el Negocio (SEDRONAR)
- Permite **priorizar intervenciones** según perfil de riesgo (jóvenes vs crónicos)
- Facilita **optimización de recursos** por franja horaria y tipo de demanda
- Identifica **ventanas críticas de oportunidad** (Cluster 2 - 52% sin tratamiento previo)
- Evidencia necesidad de **automatización** para consultas informativas (41% del total)
- Ofrece base para **asignación diferenciada** de personal especializado

### Impacto Social
- Los datos revelan **historias humanas diferenciadas** que requieren respuestas adaptadas:
  - **Cluster 1:** Personas de mediana edad luchando contra consumos crónicos (>10 años), enfrentando recaídas - requieren acompañamiento sostenido
  - **Cluster 2:** Jóvenes en situaciones de crisis detectadas por sus madres - representa una oportunidad de cambiar trayectorias de vida mediante intervención temprana
- El **rol familiar es crítico** en la detección de señales de alarma (80% consultas indirectas en Cluster 2)
- Base para **políticas públicas más humanas y efectivas** centradas en personas, no solo en números

### Proyección Futura
- **Análisis longitudinales** trimestrales/anuales para detectar evolución de perfiles
- **Modelos predictivos** (predicción de recaídas, probabilidad de abandono de tratamiento)
- **Integración con datos** de efectividad de derivaciones para medir impacto real
- **Análisis de series temporales** para detectar estacionalidad y picos de demanda
- **Clustering jerárquico** como método complementario para validar segmentación

### Limitaciones Reconocidas
- Silhouette Score de 0.252 indica segmentación aceptable pero con margen de mejora
- No se dispone de datos de sustancia consumida (variable potencialmente relevante)
- Análisis limitado a 6 meses - series más largas permitirían detectar tendencias anuales
- Variables geográficas de alta cardinalidad (LOCALIDAD) fueron excluidas para reducir ruido

---

## Referencias y Fuentes

- [SEDRONAR - Estadísticas Línea 141](https://www.argentina.gob.ar/sedronar)
- [Dataset oficial - Base Línea 141 (Datos Abiertos)](https://datos.gob.ar/dataset/sedronar-base-linea-141/archivo/sedronar_12.5)
- Boletines mensuales de actividad Línea 141 - Primer semestre 2025
- Scikit-learn Documentation - K-Means Clustering
- Documentación oficial de SEDRONAR sobre protocolos de atención

---

## Autor

**[Tu Nombre Completo]**
Natalia G. Cuellas

---

## Licencia

Este proyecto es de carácter **académico** y utiliza datos públicos de SEDRONAR disponibles en el portal de Datos Abiertos de Argentina. Los hallazgos y recomendaciones son producto de un ejercicio educativo y no representan posiciones oficiales de SEDRONAR.

---

**Última actualización:** Octubre 2025
