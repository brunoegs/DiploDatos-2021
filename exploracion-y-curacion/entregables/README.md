# Entregas Grupo 18

Entregas del Grupo18 para la materia Análisis Exploratorio y Curación de Datos.

Miembros:
- J. Francisco Correa
- Paula Bergamasco
- Nicolas Chiapello
- Bruno García

# Documentación

## Criterios de exclusión de ejemplos
  1. Se eliminan registros donde las variables `Price`, `Car`, `Bathroom`, `Rooms`  superen en 2.5 veces el tercer cuartil, ya que estos valores son considerados valores extremos, y dichos ejemplos no son considerados relevantes para la población que se quiere evaluar.

## Características seleccionadas
  
* ### Características categóricas:
  1. Suburb: zona residencial en las afueras de una ciudad de Melbourne.
  2. Type: Tipo de propiedad, puede tomar los siguientes valores: 
    * h - house,cottage,villa, semi,terrace.
    * u - unit, duplex.
    * t - townhouse; dev site - development site; o res - other residential.
  3. date: Fecha en la que fué vendida.

Todas las características categóricas fueron codificadas con un método OneHotEncoding.

* ### Características numéricas:
  1. Price: Precio de la vivienda en dolares.
  2. Rooms: Cantidad de habitaciones.
  3. Distance: Distancia al centro de la ciudad.
  4. Postcode: Codigo postal del dataset original (se utilizó para unir el dataset externo).
  5. Bathroom: Numero de baños.
  6. Car: Numero de cocheras.
  7. Lattitude: Latitud.
  8. Longtitude: Longitud.
  9. zipcode: Codigo postal del dataset externo (se utilizó para unir al dataset original)
  10. airbnb_price_mean: Se agrega el precio promedio diario de publicaciones de la plataforma AirBnB en el mismo código postal.
  11. airbnb_record_count: Cantidad de regitros que existen sobre la variable 'price' para cada codigo postal en dataset Airbnb.
  12. airbnb_weekly_price_mean: Se agrega el precio promedio semanal de publicaciones de la plataforma AirBnB en el mismo código postal.
  13. airbnb_monthly_price_mean:  Se agrega el precio promedio mensual de publicaciones de la plataforma AirBnB en el mismo código postal.

## Transformaciones
  1. Las variables `airbnb_price_mean`, `airbnb_record_count`, `airbnb_weekly_price_mean`, `airbnb_monthly_price_mean` fueron imputadas utilizando el Simple Imputer utilizando como estrategia imputación por la media 
  2. Las columnas `YearBuilt` y `BuildingArea` fueron agregadas posteriormente a la matriz de datos obtenida, luego de realizar el encoding e imputadas utilizando el IterativeImputer con un estimador KNeighborsRegressor utilizando todo el conjunto de variables seleccionadas, siendo previamente escaladas con el metodo MinMaxScaler.

## Datos aumentados
  1. Se agregan las primeras 5 columnas correspondientes a las 5 primeras componentes principales, obtenidas a través del método de PCA, aplicado sobre el conjunto de datos totalmente procesado.
