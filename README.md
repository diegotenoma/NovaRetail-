🛍️ Análisis de Factores de Comportamiento — NovaRetail+

Análisis estadístico del comportamiento de clientes de NovaRetail+, una plataforma de e-commerce en Latinoamérica, con el objetivo de identificar qué variables están más fuertemente asociadas con el ingreso anual generado por cada cliente.

🎯 Pregunta de Negocio

¿Qué factores del comportamiento del cliente están más fuertemente asociados con el ingreso anual generado?

Este análisis fue desarrollado para el equipo de Crecimiento y Retención como cierre del ejercicio 2024.

📂 Dataset
Archivo	Descripción
novaretail_comportamiento_clientes_2024.csv	Dataset con 15,000 registros y 12 columnas de comportamiento de clientes
Variables del dataset
Variable	Tipo	Descripción
id_cliente	Categórica	Identificador único del cliente
edad	Numérica	Edad del cliente
nivel_ingreso	Numérica	Ingreso anual estimado del cliente
visitas_mes	Numérica	Visitas a la app o sitio web durante el mes
compras_mes	Numérica	Número de compras realizadas en el mes
gasto_publicidad_dirigida	Numérica	Gasto en anuncios asignado al usuario
satisfaccion	Numérica	Calificación de satisfacción (escala 1–5)
miembro_premium	Binaria	Suscripción premium activa (1 = sí, 0 = no)
abandono	Binaria	Abandono de la plataforma (1 = sí, 0 = no)
tipo_dispositivo	Categórica	Móvil, escritorio o tablet
region	Categórica	Norte, sur, oeste o este
ingreso_anual ⭐	Numérica	Variable objetivo — ingreso anual generado por el cliente
🧩 Etapas del Análisis
1. Carga y exploración inicial
Revisión de estructura: .info(), .head(), .describe()
Identificación de tipos de variables: numéricas, binarias y categóricas
2. Limpieza y supuestos
Conversión de edad de float64 a int64 (los decimales no aplican para edades)
Verificación de variables binarias (solo valores 0 y 1)
Sin valores nulos ni duplicados — dataset limpio desde el inicio
Documentación de supuestos metodológicos por tipo de coeficiente
3. Visualización de relaciones
Heatmap de correlación general entre todas las variables numéricas
Scatterplot de compras_mes vs ingreso_anual para el par de mayor correlación
4. Coeficientes de correlación

Se usó el método estadístico adecuado según el tipo de variable:

Par de variables	Método	Resultado
compras_mes vs ingreso_anual	Pearson	0.97 — correlación fuerte y positiva
miembro_premium vs ingreso_anual	Punto-biserial	0.093 — débil pero significativa
abandono vs ingreso_anual	Punto-biserial	-0.003 — no significativa
tipo_dispositivo vs miembro_premium	V de Cramér	0.020 — asociación muy débil
region vs miembro_premium	V de Cramér	0.013 — asociación prácticamente nula
5. Interpretación y hallazgos de negocio
Traducción de los resultados estadísticos en implicaciones accionables para el equipo de crecimiento
🔍 Hallazgos Principales
Hallazgo 1 — Las compras mensuales son el principal motor del ingreso anual

La variable compras_mes presenta una correlación de Pearson de 0.97 con ingreso_anual — la más alta de todo el análisis. El scatterplot confirma visualmente una tendencia ascendente clara y consistente.

Implicación: La frecuencia de compra es la palanca más directa sobre el ingreso. Estrategias de recompra, recordatorios personalizados y programas de fidelización deben ser la prioridad número uno.

Hallazgo 2 — La membresía premium tiene una asociación real pero pequeña con el ingreso

El coeficiente punto-biserial de miembro_premium vs ingreso_anual es 0.093 — estadísticamente significativo (p = 3.09e-30) pero de baja magnitud práctica. Solo el 13.9% de los clientes son premium.

Implicación: El programa premium no es un motor de ingreso por sí solo, sino una herramienta de retención. Su valor está en mantener activos a clientes que de otra forma podrían abandonar.

Hallazgo 3 — Abandono, región y dispositivo no son relevantes para el ingreso

Ninguna de estas variables mostró asociación significativa con ingreso_anual. El abandono tiene un coeficiente de -0.003 (p = 0.729), y las variables categóricas presentan V de Cramér menores a 0.02.

Implicación: La segmentación por región o dispositivo no es una palanca de ingreso. Los recursos deben orientarse al comportamiento de compra, no al canal o ubicación geográfica.

⚠️ Limitaciones
Correlación ≠ causalidad — los hallazgos son asociaciones observadas, no relaciones causa-efecto
Snapshot de un solo periodo — no es posible evaluar tendencias en el tiempo
Variables no capturadas — historial de compras, categorías de producto, descuentos y canal de adquisición podrían mejorar el análisis
Los clientes con abandono = 1 permanecen en el dataset y pueden afectar el análisis de ingreso
🔭 Próximos Pasos
Segmentar clientes por frecuencia de compra (bajo / medio / alto) y comparar ingreso anual promedio por segmento
Evaluar si los clientes premium tienen menor tasa de abandono que los no premium
Construir un modelo de regresión lineal con compras_mes para predecir ingreso_anual
Explorar un modelo de clasificación para identificar clientes con alto riesgo de abandono
🛠️ Tecnologías Utilizadas
Python 3
pandas
numpy
matplotlib
seaborn
scipy (correlación punto-biserial, chi-cuadrado, V de Cramér)
Google Colab / Jupyter Notebook
▶️ Cómo Ejecutar el Proyecto
bash
# Clona el repositorio
git clone https://github.com/diegotenoma/<nombre-repo>.git
cd <nombre-repo>

# Instala dependencias
pip install pandas numpy matplotlib seaborn scipy

# Abre el notebook
jupyter notebook S8_Student_Version-Project-NovaRetail.ipynb

Nota: El archivo novaretail_comportamiento_clientes_2024.csv debe estar disponible en la ruta /datasets/ o ajusta la ruta de carga en el notebook según tu entorno.

👤 Autor

Diego Tenorio Martínez — Data Analyst
linkedin.com/in/tenoriodiego | github.com/diegotenoma
