# Prediccion-Fondo-E-AFP-Habitat

## Importación de datos
Los datos se agregan utilizando la librería pandas de python, posteriormente se debe seleccionar la columna fecha como índice, se deben rellenar los valores nulos y se debe establecer la frecuencia

## Limpieza de datos y transformación
Los datos fueron limpiados y transformados al fortmato de datos financieros en el siguiente repositorio: [Repositorio](https://github.com/CristianNac/Formatear-cuotas-fondo-E)

##Análisis exploratorio de los datos 
Para saber cómo se comportan los datos, se importará la librería stasmodels.tsa.seasonal para utilizar el función seasonal_decompose que permite graficar los datos y obtener
el tipo de tendencia que tienen los datos, además de mostrar si existe algún tipo de estacionalidad en estos y ver cómo se comportan los residuos, los gráficos obtenidos son los siguientes:

## Estacionariedad de la serie de datos

Para poder predecir el comportamiento de los datos de una serie de tiempo, deben compararse diferentes modelos utilizando métodos como: autoregresivos (AR), medias móviles (MA), modelos ARMA y modelos ARIMA, ya que varios de estos modelos para ser utilizados requieren que la serie de tiempo se comporte como una serie estacionaria, se realiza un test de hipótesis mediante el siguiente código: ```sts.adfuller(df_train.Close)``` para saber si la serie es estacionaria, se considera que si el valor p es menor a un nivel de significancia del 5% o 0.05, se rechaza la hipótesis nula que considera que la serie no es estacionaria.

## Selección del mejor modelo

Se probarán cada uno de los modelos empezando por los más básicos y se irá incrementando la complejidad, para seleccionar si uno modelo es mejor que otro se utilizarán como métricas de comparación el logarítmo de máxima verosimilitud y los criterios de información AIC y BIC, para que un modelo sea mejor que otro debe poseer un Log de máxima verosimilitud mayor a otro modelo, además debe poseer un criterio de información AIC menor que el otro modelo hasta encontrar un modelo que cumpla con las características de tener todos sus componenten significativos, ser el de menor complejidad posible y que sus residuos se comporten lo más similar posible a ruido blanco.


