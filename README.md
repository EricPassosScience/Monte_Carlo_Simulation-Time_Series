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
************************************
## Meta

El objetivo será utilizar la simulación de Montecarlo para predecir el recuento de acciones al cierre de la empresa "Cedar Realty Trust, Inc (CDR)", que cotiza en la bolsa de valores estadounidense:

![imagem_2023-09-09_225923506](https://github.com/EricPassosScience/PySpark_Streaming_Kafka_Recommendation_System/assets/97414922/8cd9d085-e710-4267-9200-25bf4fc15d5f)
Página Web de la compañía -> http://cedarrealtytrust.com/

Para proyectar una posible trayectoria de precios, utilizaremos los datos históricos de precios del activo para generar una serie de rendimientos diarios periódicos.

Supongamos que S(t) representa el precio de las acciones en el momento t, r es la tasa de rendimiento esperada, σ es la volatilidad y Δt es el intervalo de tiempo entre simulaciones. La fórmula para calcular el precio de la acción en el próximo periodo (S(t+Δt)) en un escenario concreto sería:

S(t+Δt) = S(t) * exp((r - (σ^2) / 2) * Δt + σ * sqrt(Δt) * Z)

Onde Z é um número aleatório de uma distribuição normal padrão.

## Fuente de datos
Recopilé datos del período comprendido entre 1994 y 2020. Se puede acceder a estos datos en el portal financiero de Yahoo -> https://finance.yahoo.com/quote/CDR/history/




