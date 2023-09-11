# Simulación Monte Carlo y Series Temporales para Modelización Financiera
***********************
<p align="center">
  <img width="600" height="350" src="https://github.com/EricPassosScience/Hypothesis_Test_Business/assets/97414922/c4f6a57e-e042-4862-8e1c-afe4acba8003">
</p>

***************************
# Consideraciones sobre la simulación Monte Carlo
Las simulaciones de Monte Carlo se utilizan para modelar la probabilidad de diferentes resultados en un proceso que no se puede predecir fácilmente debido a la intervención de variables aleatorias. Es una técnica utilizada para comprender el impacto del riesgo y la incertidumbre en los modelos de pronóstico.

Se puede utilizar para resolver una variedad de problemas en prácticamente todos los campos, como finanzas, ingeniería, cadena de suministro y ciencia. También se le conoce como Simulación de Probabilidad Múltiple.

En general, en escenarios donde tenemos una incertidumbre significativa para hacer predicciones y estimaciones, en lugar de simplemente reemplazar la variable incierta con un único número promedio, la simulación Monten Carlo puede ser una mejor solución.

Dado que los negocios y las finanzas se ven afectados por variables aleatorias, las simulaciones de Monte Carlo tienen una amplia aplicación potencial en estos campos.

Las simulaciones se utilizan para estimar la probabilidad de que se produzcan sobrecostos en grandes proyectos y la probabilidad de que el precio de un activo se mueva de cierta manera.

Las empresas de telecomunicaciones los utilizan para evaluar el rendimiento de la red en diferentes escenarios, lo que les ayuda a optimizar la red. Los analistas utilizan la simulación Monte Carlo para evaluar el riesgo asociado con retrasar y analizar los derivados y otros productos financieros de una entidad.

Las simulaciones de Monte Carlo llevan el nombre del "hot spot" de apuestas en Mónaco, ya que el azar y los resultados aleatorios son fundamentales para la técnica de modelado, así como en juegos como la ruleta, los dados y las tragamonedas.

La técnica fue desarrollada por primera vez por Stanislaw Ulam, un matemático que trabajó en el Proyecto Manhattan. Después de la guerra, mientras se recuperaba de una cirugía cerebral, Ulam disfrutaba jugando numerosos juegos de "paciencia", por lo que se interesó en trazar el resultado de cada uno de estos juegos para observar su distribución y determinar la probabilidad de victoria.

Después de esta fase, compartió su idea con John Von Neumann, los dos colaboraron para desarrollar la simulación de Monte Carlo.
***************************************************
# Modelado de Precios de Activos
<p align="center">
  <img width="1000" height="350" src="https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/1a3fe2b8-89ba-4a84-ad6c-577cc717cc9b">
</p>
Fuente de imagen:https://www.suno.com.br/artigos/opcoes-de-acoes/

Una forma de emplear una simulación de Monte Carlo es modelar posibles movimientos de precios de activos. Hay dos componentes en los movimientos del precio de un activo:
- drift: movimiento direccional constante;
- entrada aleatoria: representa la volatilidad del mercado.

Al analizar los datos históricos de precios, es posible determinar la "drift", la desviación estándar, la variación y el movimiento promedio del precio de un valor. Éstos son los componentes básicos de una simulación de Montecarlo.

************************************
## Meta

El objetivo será utilizar la simulación de Montecarlo para predecir el recuento de acciones al cierre de la empresa "Cedar Realty Trust, Inc (CDR)", que cotiza en la bolsa de valores estadounidense:

![imagem_2023-09-09_234535893](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/75d15e59-bc15-4746-8f23-35a808afb87b)

Página Web de la compañía -> http://cedarrealtytrust.com/

Para proyectar una posible trayectoria de precios, utilizaremos los datos históricos de precios del activo para generar una serie de rendimientos diarios periódicos.

Con base en estos componentes, podemos crear una fórmula simplificada para la simulación Monte Carlo del precio de un valor en el siguiente período de tiempo (Δt). Llamemos al precio en el momento t Pt.

Pt+Δt = Pt + Deriva * Δt + Z * Desviación_estándar * √(Δt)

Dónde:
- Pt+Δt es el precio estimado en el próximo período de tiempo.
- Pt es el precio actual en el momento t.
- La deriva es la deriva promedio.
- Δt es el tamaño del intervalo de tiempo.
- Z es una variable aleatoria con distribución normal estándar (media 0 y desviación estándar 1), que representa la variación aleatoria.
- Standard_Deviation es la desviación estándar.

Esta fórmula representa una simulación de Monte Carlo de un solo paso para predecir el precio futuro de un valor basándose en la deriva, la volatilidad y la variación aleatoria. La simulación generalmente implica repetir estos pasos muchas veces para generar múltiples trayectorias de precios posibles a lo largo del tiempo.
****************************************
## Fuente de datos
Recopilé datos del período comprendido entre 1994 y 2020. Se puede acceder a estos datos en el portal financiero de Yahoo -> https://finance.yahoo.com/quote/CDR/history/
*******************************************
# Simulación Usando Lenguaje Python en Databricks
*********************************************
***Versión del lenguaje Python:***
![imagem_2023-09-11_153033537](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/7ebe7a09-f321-4129-956a-16bbcae2ac6f)

***CARGANDO PAQUETES:***
![imagem_2023-09-11_153436268](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/edec2e52-92b6-4c9e-aee2-182265237531)

***Importaciones para formato de gráficos:***
![imagem_2023-09-11_153543723](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/d1033f7a-8b6a-4e4b-8ad4-93ad7a38ba19)
********************
***Versiones de paquetes utilizados en este cuaderno jupyter:***
![imagem_2023-09-11_153918344](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/adb6f9c7-8694-4b20-9dfe-46c33df5de70)
**************************
## Cargando los Datos
- El valor de las acciones se ha ajustado para facilitar la creación de gráficos de forma didáctica
- Ver registros
- Cada columna representa el valor de la acción en cada día de la serie.
- valor de apertura, cierre, máximo, mínimo y volumen.
- La columna Mudanca(%) representa la variación diaria.

![imagem_2023-09-11_154347105](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/14476edf-413a-4f95-9758-1a948783fe18)

![imagem_2023-09-11_154738009](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/242a8dd8-7a28-49a2-a4d7-7e9cccf25af0)
***************************
***Tipos de datos y Forma:***
![imagem_2023-09-11_155136721](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/2b85d4e3-5278-43cc-a92a-10eed0474bf6)
****************************
***Resumen estadístico:***

![imagem_2023-09-11_155533279](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/d4f72f03-a955-428a-9ab9-7493fb091a20)
******************************
# Ver el precio de cierre diario de las acciones a tiempo
![imagem_2023-09-11_161240667](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/9149a2c7-b232-4124-8a22-a270b5615b2e)

## Calculemos el retorno diario de la serie:
- Calcular el porcentaje de cambio en el precio de cierre diario de la acción,
- Es decir, cuánto varía el valor de cierre de un día para otro, el rendimiento diario de la acción.

![imagem_2023-09-11_162727190](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/989f0271-e8db-401e-a2ca-526f46c0ed78)

***Calculemos el rendimiento acumulado de la serie***

![imagem_2023-09-11_162930045](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/cfec57ca-b3c2-4efb-b672-991d4313ca63)

# Análisis y Estadística Descriptiva
- Usemos estadísticas para calcular el rendimiento promedio y la varianza (desviación estándar)

![imagem_2023-09-11_163928957](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/980d68e2-6836-4355-8e3f-29de85c9655c)

## Nota: Consideremos el año con 252 días de actividad en la bolsa americana
***Promedio y desviación estándar del año***

![imagem_2023-09-11_164812179](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/7a57476c-8e26-4343-aeac-fd351d69a19a)

## Nota: Aunque el comportamiento de las acciones ha sido bueno en los últimos años, en promedio la ganancia ha sido baja, aunque positiva. A largo plazo, el inversor no perdió dinero. Creemos una trama con el retorno diario:

![imagem_2023-09-11_170844491](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/3babd123-bd01-486f-bc86-fe0e53b836fb)

## Nota: Con sólo dos variaciones importantes, el rendimiento diario ha sido constante en el tiempo. Creemos un histograma con la distribución del retorno diario:

![imagem_2023-09-11_171549944](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/ca586809-a8f1-4274-916b-29e9a1a20f78)

## Los valores están muy cerca de la media. Pero confirmemos esto calculando la curtosis y la asimetría:

![imagem_2023-09-11_171752304](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/a1bd5727-7327-4509-9d28-b80e1bad73d6)

#### Nota: Kurtosis indica que los registros están muy cerca de la media. Pero la asimetría indica que los datos están muy distorsionados y lejos de una distribución normal. Apliquemos la prueba de normalidad a la serie.

## Prueba de normalidad de Shapiro-Wilk:

![imagem_2023-09-11_172256635](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/0f247bb3-72cd-4ecb-a2e1-43562dd260d6)

#### Nota: Como imaginábamos, la distribución no es normal. Apliquemos una transformación logarítmica a la serie y luego apliquemos la técnica de diferenciación para eliminar patrones de tendencia de la serie y dejar solo los datos reales que nos interesan. Con esto calculamos el retorno diario.

