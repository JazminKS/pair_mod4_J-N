
# Análisis de la Relación entre los Hábitos Diarios y el Rendimiento Cognitivo

1. Nuestra base de datos
2. Análisis Exploratorio de los Datos (EDA)
3. Comunicación de resultados: Visualizaciones y Dashboards



##  1. Nuestra base de datos

Queríamos manejar información que nos fuese útil comunicar, Jazmin ha trabajado y tiene conocimientos en el sector alimentario y salud y    Noelia tiene conocimientos y esperiencia con el uso y la aplicación de tests psicológicos.

Pudimos encontrar datos de 80000 usuarios que habían sido voluntarios para realizarse pruebas cognitivas, en concreto dos tipos:

- Pruebas de memoria: Evalúa exclusivamente la memoria. Generalmente, se obtiene de una prueba concreta en la que se mide cuántos elementos recuerda una persona (palabras, imágenes, secuencias, etc.).

- Pruebas de rendimiento cognitivo global: Evalúa el rendimiento cognitivo global. Esto puede incluir memoria, pero también atención, razonamiento, velocidad de procesamiento, lenguaje, y otras funciones mentales.

También se observará el tiempo de reacción o de respuesta y una predicción hecha por inteligencia artificial para observar la coherencia de respuestas y por tanto, su validez.

Por otra parte, queríamos encontrar relaciones entre los hábitos de alimentación (dieta), el nivel de ejercicio, de estrés, las horas de sueño, el nivel de consumo de cafeína y las horas frente a pantallas digitales al día.
Además, tenemos información sobre la edad y el género de los participantes.

##  2. Análisis Exploratorio de los Datos (EDA)

Podemos empezar a extraer algunos insights iniciales sobre nuestro dataset. Aquí encontramos algunos puntos y preguntas para guiar nuestro análisis:

**Insights Iniciales y Preguntas por Columna**

* **`user_id`**:
    * Parece que cada `user_id` aparece solo una vez (el conteo máximo es 1). Esto sugiere que cada fila en tu dataset representa una observación única para un usuario específico.
    * **Pregunta:** ¿Es esta la expectativa? ¿Deberíamos tener múltiples entries por usuario en algún caso?

* **`age`**:
    * Hay muchos valores únicos de edad. El conteo muestra las frecuencias de cada edad.
    * **Insight:** Podemos ver en la exploración que la edad más común en el dataset es '40' (1979 registros) con una frecuencia mayor que las demás listadas. El rango de edades se comprende entre 18 y 59 años.
    * **Pregunta:** ¿Cuál es la distribución general de edades? ¿Hay algún grupo de edad predominante? Sería útil visualizar esto con un histograma o un gráfico de densidad.

* **`gender`**:
    * Hay tres categorías: 'Female', 'Male', y 'Other'. Las frecuencias entre 'Female' y 'Male' son bastante similares, mientras que 'Other' tiene una representación mucho menor.
    * **Insight:** El dataset está relativamente balanceado en términos de género binario, con una minoría identificándose como 'Other'.
    * **Pregunta:** ¿Es importante la categoría 'Other' para tu análisis? ¿Necesitas más detalles sobre esta categoría si es relevante?

* **`sleep_duration`**:
    * Hay una variedad de duraciones de sueño, incluyendo valores decimales, lo que sugiere mediciones más precisas o un promedio.
    * **Insight:** Podemos ver las duraciones de sueño más comunes. '9.9', '4.4', '6.8', '7.9', '5.4' parecen tener frecuencias altas.
    * **Pregunta:** ¿Cuál es la distribución general de la duración del sueño? ¿Cuál es la duración promedio? ¿Hay valores atípicos nivel de estrés?

* **`stress_level`**:
    * Los niveles de estrés parecen estar en una escala numérica (posiblemente de 0 a 10, aunque solo vemos del 0 al 8 en los valores más frecuentes).
    * **Insight:** Los niveles '3' y '8' parecen ser los más frecuentes en los datos mostrados.
    * **Pregunta:** ¿Cuál es la escala completa del nivel de estrés? ¿Cuál es el nivel de estrés promedio en la población del dataset? ¿Cómo se relaciona el nivel de estrés con otras variables?

* **`diet_type`**:
    * Tres categorías: 'Non-Vegetarian', 'Vegetarian', y 'Vegan'. 'Non-Vegetarian' es la categoría dominante.
    * **Insight:** La mayoría de los individuos en el dataset no son vegetarianos ni veganos.
    * **Pregunta:** ¿Cómo influye el tipo de dieta en otras variables como el sueño, el estrés o las puntuaciones cognitivas?

* **`daily_screen_time`**:
    * Hay una amplia gama de tiempos de pantalla diarios, incluyendo valores decimales.
    * **Insight:** Podemos ver los tiempos de pantalla más frecuentes. '7.7', '5.2', '10.6', '1.4', '4.2' tienen frecuencias altas.
    * **Pregunta:** ¿Cuál es la distribución del tiempo de pantalla? ¿Cuál es el tiempo promedio? ¿Hay valores extremos? ¿Cómo se relaciona el tiempo de pantalla con el sueño o el rendimiento cognitivo?

* **`exercise_frequency`**:
    * Tres categorías: 'Medium', 'Low', y 'High'. 'Medium' y 'Low' tienen frecuencias similares y son mayores que 'High'.
    * **Insight:** La mayoría de los individuos reportan una frecuencia de ejercicio media o baja.
    * **Pregunta:** ¿Cómo se relaciona la frecuencia de ejercicio con la salud mental (estrés) o el rendimiento cognitivo?

* **`caffeine_intake`**:
    * Hay muchos valores únicos para la ingesta de cafeína, lo que sugiere una medición en unidades específicas (mg, tazas, etc.).
    * **Insight:** Podemos ver los valores de ingesta más frecuentes. '217', '198', '230', '196', '246' parecen ser comunes.
    * **Pregunta:** ¿Cuál es la unidad de medida para la ingesta de cafeína? ¿Cuál es la ingesta promedio? ¿Cómo se relaciona la ingesta de cafeína con el sueño o la reacción?

* **`reaction_time`**:
    * Hay muchísimos valores únicos para el tiempo de reacción, con una alta precisión (hasta dos decimales).
    La variable Reaction_Time está medida en milisegundos (ms), no en segundos. Es decir:
        200.00 ms = 0.2 segundos
        599.99 ms = 0.6 segundos
    Tiempo de reacción (segundos, mínimo 0.3 aprox., máximo 1.5 aprox.):
        Muy rápido: 200 - 299 ms (0.200 – 0.299 segundos)
        Rápido: 300 - 399 ms (0.300 – 0.399 segundos)
        Promedio: 400 - 499 ms (0.400 – 0.499 segundos)
        Lento: 500 - 599,99 ms (0.500 – 0.599 segundos)

    * **Insight:** Esto sugiere una medición continua y precisa del tiempo de reacción.
    * **Pregunta:** ¿Cuál es la distribución del tiempo de reacción? ¿Cuál es el tiempo de reacción promedio? ¿Hay valores atípicos (tiempos de reacción muy lentos o muy rápidos)? ¿Cómo se relaciona el tiempo de reacción con otras variables como la edad o el sueño?

* **`memory_test_score`**:
    * Los puntajes de la prueba de memoria parecen ser valores enteros dentro de un rango (viendo los valores más frecuentes).
     Memory_Test_Score (40 a 99 aprox.)
        Puntuación del test:
        Baja: 40 – 59
        Media: 60 – 79
        Alta: 80 – 99

Esta prueba empieza en 40, por eso ajustamos los rangos. También puedes dividir en cuartiles si prefieres.
    * **Insight:** Podemos ver los puntajes más comunes. '57', '42', '60', '71', '50' tienen frecuencias altas.
    * **Pregunta:** ¿Cuál es el rango posible de la puntuación en la prueba de memoria? ¿Cuál es la puntuación promedio? ¿Cómo se relaciona con otras variables como la edad o el sueño?

* **`cognitive_score`**:
    * Las puntuaciones cognitivas son valores continuos con decimales, lo que sugiere una métrica más compleja.
    Clasificación de Cognitive_Score (0 a 100)
            0 – 39 → Bajo: Rendimiento cognitivo bajo
            40 – 59 → Medio-bajo: Por debajo del promedio
            60 – 79 → Medio-alto: Por encima del promedio
            80 – 100 → Alto: Excelente rendimiento cognitivo
    * **Insight:** Podemos ver las puntuaciones más frecuentes, con '100.00' siendo la más alta en la lista.
    * **Pregunta:** ¿Cuál es el rango posible de la puntuación cognitiva? ¿Cuál es la puntuación promedio? ¿Cómo se relaciona con otras variables como el estrés o el tiempo de pantalla?

* **`ai_predicted_score`**:
    * Similar a la puntuación cognitiva, esta es una puntuación predicha por IA con valores continuos.
    🤖 AI_Predicted_Score (0 a 100), de la misma manera:
            Bajo: 0 – 39
            Medio-bajo: 40 – 59
            Medio-alto: 60 – 79
            Alto: 80 – 100
    * **Insight:** '100.00' también es la puntuación predicha más frecuente en la lista.
    * **Pregunta:** ¿Cómo se compara la puntuación predicha por la IA con la puntuación cognitiva real? ¿Es un buen predictor? Podríamos analizar la correlación entre estas dos variables.

**Creación de nuevas variables clasificatorias**
Para comprender mejor la observación de las gráficas estadísticas hemos clasificado las siguientes variables numéricas en categóricas:

- `age` (*edad*) -> `generation` (*generación*): Dividimos la variable 'age' en rangos que representen diferentes generaciones. Esta es una propuesta de rangos generacionales comunes:

    · Generación Z (Gen Z): 13 - 28 años (aproximadamente nacidos entre 1997 y 2007)
    · Millennials (Generación Y): 29 - 44 años (aproximadamente nacidos entre 1981 y 1996)
    · Generación X: 45 - 60 años (aproximadamente nacidos entre 1965 y 1980)

- `stress_level` (*nivel de estrés*) -> `stress_category` (*categoría de estrés*): Dividimos la variable 'stress_level' en rangos que representen diferentes niveles para mejorar la visualización de los datos:
    · `Low` (Bajo): 1 - 3
    · `Medium` (Medio): 4 - 7
    · `High` (Alto): 8 - 10

- `caffeine_intake` (*toma de cafeína*) -> `caffeine_category` (*categoría dosis cafeína*): Nos basamos en la información de varias búsquedas en línea en webs de alta fiabilidad para proponer una clasificación por rangos de ingesta diaria de cafeína (en mg):

    · `Almost nothing` (Sin Cafeína / Muy Bajo): 0 - 10 mg (Típicamente encontrado en descafeinado o cantidades traza en algunos alimentos).
    · `Low` (Bajo): 11 - 80 mg (Aproximadamente el contenido de una taza de té o una porción pequeña de chocolate).
    · `Moderate` (Moderado): 81 - 200 mg (Aproximadamente el contenido de 1-2 tazas de café estándar).
    · `Medium-High` (Medio-Alto): 201 - 300 mg (Aproximadamente el contenido de 2-3 tazas de café fuerte o algunas bebidas energéticas).
    · `High` (Alto): 301 - 400 mg (La mayoría de las fuentes consideran que hasta 400 mg al día es seguro para adultos sanos).
    · `Too much` (Muy Alto): 401 - 499 mg (Supera las recomendaciones diarias para muchas personas y podría aumentar el riesgo de efectos secundarios).

- `reaction_time` (*tiempo de reacción*) -> `caffeine_category` (*categoría dosis cafeína*):  La variable está medida en milisegundos (ms), no en segundos. Es decir:

    · 200.00 ms = 0.2 segundos
    · 599.99 ms = 0.6 segundos

    Tiempo de reacción (segundos, mínimo 0.3 aprox., máximo 1.5 aprox.):

    · `Top fast` (Muy rápido): 200 - 299 ms (0.200 – 0.299 segundos)
    · `Fast` (Rápido): 300 - 399 ms (0.300 – 0.399 segundos)
    · `Normal` (Promedio): 400 - 499 ms (0.400 – 0.499 segundos)
    · `Slow` (Lento): 500 - 599,99 ms (0.500 – 0.599 segundos)


- `memory_test_score` (*rendimiento prueba memoria*) -> `caffeine_category` (*categoría dosis cafeína*): La puntuación de la prueba de memoria parecen ser valores enteros dentro de un rango (viendo los valores más frecuentes).
    Memory_Test_Score (40 a 99 aprox.)

    Puntuación del test:
        · `Low` (Baja): 40 – 59
        · `Medium` (Media): 60 – 79
        · `High` (Alta): 80 – 99

- `cognitive_score` (*rendimiento cognitivo*) -> `caffeine_category` (*categoría dosis cafeína*): Las puntuaciones cognitivas son valores continuos con decimales, lo que sugiere una métrica más compleja.
    Clasificación de Cognitive_Score (0 a 100)
    
    · 0 – 39 → `Low` (Bajo): Rendimiento cognitivo bajo
    · 40 – 59 → `Medium-Low` (Medio-bajo): Por debajo del promedio
    · 60 – 79 → `Medium-High`(Medio-alto): Por encima del promedio
    · 80 – 100 → `High` (Alto): Excelente rendimiento cognitivo

- `ai_predicted_score` (*rendimiento cognitivo predicho por IA*) -> `caffeine_category` (*categoría dosis cafeína*): Similar a la puntuación cognitiva, esta es una puntuación predicha por IA con valores continuos.
    🤖 AI_Predicted_Score (0 a 100), de la misma manera:

    · 0 – 39 → `Low` (Bajo): Rendimiento cognitivo bajo
    · 40 – 59 → `Medium-Low` (Medio-bajo): Por debajo del promedio
    · 60 – 79 → `Medium-High`(Medio-alto): Por encima del promedio
    · 80 – 100 → `High` (Alto): Excelente rendimiento cognitivo

**Próximos Pasos para el Análisis:**

1.  **Visualizaciones:** La clave ahora es crear visualizaciones para entender mejor las distribuciones de cada variable y las relaciones entre ellas. Algunas visualizaciones útiles podrían ser:
    * **Histogramas y gráficos de densidad:** Para variables numéricas (age, sleep\_duration, stress\_level, daily\_screen\_time, caffeine\_intake, reaction\_time, memory\_test\_score, cognitive\_score, ai\_predicted\_score) para ver sus distribuciones.
    * **Gráficos de barras:** Para variables categóricas (gender, diet\_type, exercise\_frequency) para ver las proporciones de cada categoría.
    * **Boxplots:** Para comparar la distribución de una variable numérica entre diferentes categorías de una variable categórica (ej., sleep\_duration por gender).
    * **Scatter plots:** Para visualizar la relación entre dos variables numéricas (ej., sleep\_duration vs. cognitive\_score).
    * **Heatmap de correlación:** Para ver las correlaciones entre todas las variables numéricas.

2.  **Estadísticas Descriptivas:** Calcular medidas como la media, mediana, desviación estándar, cuartiles para las variables numéricas para cuantificar sus características centrales y dispersión.

3.  **Análisis Bivariado y Multivariado:** Investigar las relaciones entre pares y grupos de variables. Por ejemplo, ¿cómo se relaciona la edad con la duración del sueño y el rendimiento de la memoria? ¿Hay diferencias en el rendimiento cognitivo entre diferentes tipos de dieta y niveles de ejercicio?

**¿En qué área te gustaría enfocarte primero para el análisis? Por ejemplo, ¿te interesa explorar la relación entre el sueño y el rendimiento cognitivo, o la distribución de las edades en el dataset?** Una vez que me digas tu área de interés, puedo ayudarte a generar el código y a interpretar los resultados.


Podemos formular algunas hipótesis y pensar en las relaciones esenciales a analizar para llegar a conclusiones interesantes. Aquí te presento algunas hipótesis y las mejores gráficas para explorarlas:

  **Posibles Hipótesis y Relaciones Esenciales a Analizar:**

## Hipótesis 1 sobre la cafeína:
Los estudios realizados han mostrado que el consumo moderado de café está asociado con un menor riesgo de deterioro cognitivo, osteoporosis, diabetes y enfermedades neurodegenerativas como el Alzheimer y el Parkinson. La cafeína, como principal compuesto activo del café, parece tener un efecto protector sobre la memoria y la atención.
    El consumo de café podría estar relacionado con la salud, por ejemplo, la pérdida de demencia es menor en personas que han tenido una ingesta moderada y regular. También se ha desprendido del estudio que un exceso en la ingesta de esta bebida tiene consecuencias negativas para la salud. El café en una medida razonable tiene efectos antioxidantes e inflamatorios para ayudar a proteger nuestro cerebro.
    Fuente 2: https://www.sabervivirtv.com/nutricion/cuanta-cafeina-tiene-un-cafe-depende-de-como-lo-prepares_11344
    "Las ingestas de cafeína de hasta 400 mg al día […] no tienen efectos perjudiciales para la salud de los adultos en la población general, excepto en el caso de las embarazadas". Para estas últimas, el tope está en 200 mg diarios. Una taza de cafetera italiana contiene entorno a 70 miligramos de cafeína.

## Hipótesis 2 sobre el sueño:
Hipótesis: La duración del sueño varía significativamente entre diferentes generaciones y se relaciona con el rendimiento cognitivo y la memoria.
     Relaciones a analizar:
       ·sleep_duration vs. generation
       ·sleep_duration vs. cognitive_score (por generación)
       ·sleep_duration vs. memory_test_score (por generación)
    Gráficas representativas:
      - Boxplots o Violin Plots: Para comparar la distribución de sleep_duration entre las diferentes generaciones.
      - Scatter Plots: Para visualizar la relación entre sleep_duration y cognitive_score (o memory_test_score), coloreando los puntos por generación para ver si la relación varía.
      - Line Plots (con intervalos de confianza): Si agrupas por generación y calculas la media de cognitive_score (o memory_test_score) para diferentes rangos de sleep_duration, un line plot puede mostrar tendencias.

## Hipótesis 3 sobre el Estrés:

Hipótesis: Los niveles de estrés varían entre las categorías de género y se relacionan negativamente con el rendimiento cognitivo.
    Relaciones a analizar:
       ·stress_category vs. gender (ver si hay una distribución diferente de niveles de estrés entre géneros).
       ·stress_level vs. cognitive_score (separado por género si es relevante).
        Gráficas representativas:
          - Count Plots (con hue): Para visualizar la distribución de stress_category para cada gender.
          - Stacked Bar Charts: Para mostrar la proporción de cada stress_category dentro de cada gender.
          - Boxplots o Violin Plots: Para comparar la distribución de cognitive_score entre las diferentes categorías de stress_category.

## Hipótesis 4 sobre la Dieta:

Hipótesis: El tipo de dieta se asocia con diferentes niveles de ingesta de cafeína y puede influir en el rendimiento cognitivo.
    Relaciones a analizar:
           ·caffeine_category vs. diet_type (ver si hay patrones de consumo de cafeína diferentes según la dieta).
           ·diet_type vs. cognitive_score.
        Gráficas representativas:
          - Count Plots (con hue): Para visualizar la distribución de caffeine_category para cada diet_type.
          - Stacked Bar Charts: Para mostrar la proporción de cada caffeine_category dentro de cada diet_type.
          - Boxplots o Violin Plots: Para comparar la distribución de cognitive_score entre los diferentes tipos de diet_type.

## Hipótesis 5 sobre el Tiempo de Pantalla y el Ejercicio:

 Hipótesis: Un mayor tiempo de pantalla diario se asocia con niveles de estrés más altos y menor duración del sueño, mientras que una mayor frecuencia de ejercicio se asocia con menor estrés y mejor rendimiento cognitivo.
    Relaciones a analizar:
       ·daily_screen_time vs. stress_category
       ·daily_screen_time vs. sleep_duration
       ·exercise_frequency vs. stress_category
       ·exercise_frequency vs. cognitive_score
    Gráficas representativas:
          - Boxplots o Violin Plots: Para comparar la distribución de stress_level o sleep_duration entre diferentes rangos de daily_screen_time (podrías categorizar daily_screen_time si es necesario).
          - Boxplots o Violin Plots: Para comparar la distribución de stress_level o cognitive_score entre las diferentes categorías de exercise_frequency.
##  Hipótesis 6 sobre la Predicción de la IA:

Hipótesis: La puntuación predicha por la IA (ai_predicted_score) está fuertemente correlacionada con la puntuación cognitiva real (cognitive_score) y podría mostrar patrones similares en relación con otras variables.
    Relaciones a analizar:
       ·ai_predicted_score vs. cognitive_score (ya lo viste en la correlación).
       ·ai_predicted_score vs. otras variables (para ver si sigue tendencias similares a cognitive_score).  
    Gráficas representativas:
          - Scatter Plot: Para visualizar la relación entre ai_predicted_score y cognitive_score.
          - Comparación de Boxplots/Violin Plots: Superponer (si es posible y claro) las distribuciones de cognitive_score y ai_predicted_score para diferentes categorías de otras variables (ej., generation, stress_category).

*Multivariedad: Las relaciones entre variables pueden ser complejas y estar influenciadas por otras variables. Consideramos la posibilidad de realizar análisis multivariados más adelante si encuentras relaciones interesantes a nivel bivariado.*