# Análisis de la Relación entre los Hábitos Diarios y el Rendimiento Cognitivo

Este proyecto explora la relación entre diversos hábitos diarios y el rendimiento cognitivo, utilizando datos de 80,000 participantes que se sometieron a pruebas cognitivas y proporcionaron información sobre su estilo de vida.

[Enlace a las visualizaciones de EDA](https://public.tableau.com/app/profile/jazmin.sanchez8559/viz/EDA-Graficos_17450477382830/DashboardPortada)

[Enlace al análisis completo](https://public.tableau.com/app/profile/jazmin.sanchez8559/viz/Analisis_Cognitivo_Habitos_17453145840610/Presentacin?publish=yes)

## 1. Nuestra base de datos

El conjunto de datos utilizado en este análisis proviene de 80,000 voluntarios que participaron en pruebas cognitivas. La selección y el análisis de las variables se basó en la experiencia de Jazmín en el sector alimentario y de la salud, y el conocimiento de Noelia en la aplicación de tests psicológicos. Las pruebas cognitivas se dividieron en dos categorías principales:

* **Pruebas de memoria:** Evalúan exclusivamente la capacidad de retención de información (palabras, imágenes, secuencias, etc.).
* **Pruebas de rendimiento cognitivo global:** Evalúan un amplio rango de funciones mentales, incluyendo memoria, atención, razonamiento, velocidad de procesamiento y lenguaje.

Además de las puntuaciones de las pruebas, se registraron las siguientes variables:

* Tiempo de reacción
* Predicción de rendimiento cognitivo por IA (para validar la coherencia de las respuestas)
* Hábitos de alimentación (tipo de dieta)
* Frecuencia de ejercicio
* Nivel de estrés
* Horas de sueño
* Nivel de consumo de cafeína
* Horas frente a pantallas digitales al día
* Edad
* Género

## 2. Análisis Exploratorio de los Datos (EDA)

El Análisis Exploratorio de Datos (EDA) nos permitió obtener una comprensión inicial del conjunto de datos y guiar el análisis posterior. A continuación, se resumen los insights iniciales y las preguntas clave que surgieron durante esta fase:

* **`user_id`**: Cada ID parece ser único, lo que indica una observación por usuario. Se verificó que esta era la expectativa.
* **`age`**: El rango de edad es de 18 a 59 años, con la edad de 40 años como la más frecuente. Se analizó la distribución general de edades mediante un histograma, revelando una distribución aproximadamente normal con un ligero sesgo a la derecha.
* **`gender`**: El conjunto de datos está relativamente balanceado entre 'Female' y 'Male', con una menor representación de la categoría 'Other'. Se confirmó la importancia de incluir la categoría 'Other' en el análisis, aunque su tamaño muestral limitado requiere una interpretación cautelosa de los resultados.
* **`sleep_duration`**: La duración del sueño varía, incluyendo valores decimales. El promedio se sitúa en torno a 7 horas, con valores atípicos ocasionales. Se analizó la distribución general mediante un histograma y se identificaron los valores atípicos.
* **`stress_level`**: Los niveles de estrés se registraron en una escala de 0 a 10. Los niveles 3 y 8 son los más frecuentes. El nivel de estrés promedio en la población del dataset es de 4.5.
* **`diet_type`**: La mayoría de los participantes son 'Non-Vegetarian', seguido de 'Vegetarian' y 'Vegan'.
* **`daily_screen_time`**: El tiempo de pantalla diario muestra una amplia distribución, con un promedio de 6 horas. Se identificaron algunos valores extremos superiores a 12 horas.
* **`exercise_frequency`**: La frecuencia de ejercicio es 'Medium' o 'Low' para la mayoría de los participantes, con una menor proporción en la categoría 'High'.
* **`caffeine_intake`**: La ingesta de cafeína se midió en mg, con un promedio de 200 mg.
* **`reaction_time`**: El tiempo de reacción se midió en milisegundos (ms), con un rango de 200 a 600 ms. El tiempo de reacción promedio es de 400 ms.
* **`memory_test_score`**: Las puntuaciones de la prueba de memoria varían de 40 a 99, con un promedio de 70.
* **`cognitive_score`**: Las puntuaciones cognitivas varían de 0 a 100, con un promedio de 65.
* **`ai_predicted_score`**: Las puntuaciones predichas por la IA muestran una fuerte correlación con las puntuaciones cognitivas reales (correlación de 0.85), lo que indica su utilidad como predictor.

**Creación de nuevas variables clasificatorias:**

Para facilitar el análisis y la visualización, se crearon las siguientes variables categóricas a partir de las variables numéricas:

* **`generation`** (a partir de `age`): Generación Z (13-28 años), Millennials (29-44 años), Generación X (45-60 años).
* **`stress_category`** (a partir de `stress_level`): Bajo (1-3), Medio (4-7), Alto (8-10).
* **`caffeine_category`** (a partir de `caffeine_intake`): Sin Cafeína/Muy Bajo (0-10 mg), Bajo (11-80 mg), Moderado (81-200 mg), Medio-Alto (201-300 mg), Alto (301-400 mg), Muy Alto (401-499 mg).
* **`reaction_time_category`** (a partir de `reaction_time`): Muy rápido (200-299 ms), Rápido (300-399 ms), Normal (400-499 ms), Lento (500-599.99 ms).
* **`memory_test_score_category`** (a partir de `memory_test_score`): Bajo (40-59), Medio (60-79), Alto (80-99).
* **`cognitive_score_category`** (a partir de `cognitive_score`): Bajo (0-39), Medio-Bajo (40-59), Medio-Alto (60-79), Alto (80-100).
* **`ai_predicted_score_category`** (a partir de `ai_predicted_score`): Bajo (0-39), Medio-Bajo (40-59), Medio-Alto (60-79), Alto (80-100).

## 3. Comunicación de resultados: Visualizaciones y Dashboards

Los resultados del análisis se comunicarán a través de visualizaciones y dashboards interactivos. Se utilizarán histogramas, gráficos de barras, boxplots, gráficos de dispersión y un mapa de calor de correlación para explorar las distribuciones de las variables y las relaciones entre ellas. El objetivo es proporcionar una comprensión clara e intuitiva de los hallazgos clave del estudio.

**Hipótesis y Resultados Principales:**

A continuación, se presentan las hipótesis clave que se investigaron y un resumen de los resultados obtenidos:

* **Relación entre rendimiento de memoria y cognitivo global:** Se confirmó una correlación positiva significativa (r = 0.75) entre el rendimiento en las pruebas de memoria y el rendimiento cognitivo global, lo que sugiere que aquellos con mejor memoria tienden a tener un mejor rendimiento cognitivo general.
* **Hipótesis 1 (Cafeína):** Se exploró la relación entre el consumo de cafeína y el rendimiento cognitivo. Los resultados indican que el consumo moderado de cafeína (100-200 mg) se asocia con un mejor rendimiento cognitivo, mientras que el consumo excesivo (>400 mg) se relaciona con un mayor estrés y un menor rendimiento cognitivo.
* **Hipótesis 2 (Estrés):** Se examinó la relación entre el nivel de estrés y el rendimiento cognitivo, así como las posibles diferencias por género y dieta. Se encontró una fuerte correlación negativa (r = -0.60) entre el estrés y el rendimiento cognitivo, lo que indica que un mayor estrés se asocia con un peor rendimiento cognitivo. No se observaron diferencias significativas en los niveles de estrés entre los géneros. Se observó que el estrés medio es más volátil en vegetarianos y veganos.
* **Hipótesis 3 (Sueño):** Se investigó la relación entre la duración del sueño y el rendimiento cognitivo, considerando las diferencias generacionales. Se encontró una leve correlación positiva (r = 0.25) entre la duración del sueño y el rendimiento cognitivo, lo que sugiere que dormir más se asocia con un mejor rendimiento cognitivo.
* **Hipótesis 4 (Tiempo en Pantalla):** Se exploró la relación entre el tiempo dedicado a pantallas digitales, el estrés, la duración del sueño y el rendimiento cognitivo. Se encontró una correlación positiva débil entre el tiempo de pantalla y el estrés (r=0.2) y una correlación negativa débil entre el tiempo de pantalla y el rendimiento cognitivo (r=-0.15).
* **Hipótesis 5 (Ejercicio):** Se examinó la relación entre la frecuencia del ejercicio, el estrés y el rendimiento cognitivo. Se encontró que una mayor frecuencia de ejercicio se asocia con un menor estrés y un mejor rendimiento cognitivo, incluso en personas con niveles de estrés altos.

## Conclusiones

En resumen, este estudio destaca la importancia de diversos hábitos diarios para el rendimiento cognitivo. Los principales hallazgos son:

* Existe una alta correlación entre el rendimiento cognitivo global, el rendimiento de la memoria y el tiempo de reacción.
* El perfil de los participantes con mejor rendimiento cognitivo se caracteriza por una duración del sueño media (7-7.5 horas), niveles de estrés bajos, ejercicio frecuente, una dieta equilibrada con un consumo moderado de cafeína (100-200 mg) y un bajo tiempo de exposición a pantallas.
* El consumo excesivo de cafeína (>400 mg) se asocia con un mayor estrés y un menor rendimiento cognitivo.
* El estrés tiene un impacto negativo significativo en el rendimiento cognitivo.
* Dormir lo suficiente (7-7.5 horas) se asocia con un mejor rendimiento cognitivo.
* El ejercicio regular contribuye a reducir el estrés y mejorar el rendimiento cognitivo.

Estos hallazgos sugieren que intervenciones que promuevan hábitos de vida saludables podrían tener un impacto positivo en el rendimiento cognitivo.

### Próximos pasos
* Realizar análisis multivariados para explorar las interacciones complejas entre variables.
* Estudiar en profundidad el grupo de género "Other", ya que sus datos muestran mayor variabilidad.
* Analizar los valores extremos de horas de sueño para comprender mejor su impacto en el rendimiento.
