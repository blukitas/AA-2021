# Sesgo y varianza

Error debido a sesgo / Bias => Debido a diferencia entre prediccion del modelo y valor correcto.
Error debido a varianza => Variabilidad de la prediccion de un modelo para unos datos dados. Cuánto varian los resultados para distintos datos.

Uno esperaria lograr un modelo con baja varianza y bajo sesgo (Low variance, low bias)

Para disminuir el error requerimos de un método que tenga bajo sesgo y baja varianza

**Algoritmos de aprendizaje inestables**: aquellos que sufren cambios importantes ante pequeñas variaciones en datos de entrenamiento (ej: árboles de decisión, redes neuronales). 
* Ej. de algoritmos estables: regresión lineal, vecino más cercano.
* Predictores rígidos: poca flexibilidad (menos complejos). Mayor error de sesgo. (estimación de un error muy complejo con un modelo simple, por ej. lineal)
* redictores flexibles: más complejos. Mayor error de varianza y menor error de sesgo

## Flexibilidad de los modelos

Dilema => Bias - Varianza. A bajo sesgo alta varianza y a alto sesgo baja varianza.
* Bajo bias y alta varianza -> Curva que pasa por cada ejemplo de entrenamiento
* Baja varianza y alto bias -> Línea recta que atraviesa los datos

Soluciones:
* Usando predictores con bajo sesgo, disminuir la varianza (Muchos predictores y promediarlos. Por ejemplo con bagging y random forest)
* Reducir sesgo de predictores (Construir predictores en serie, de forma tal de disminuir el sesgo. Por ejemplo boosting)

## Ensambles

* Uso de un conjunto de modelos para construir un metamodelo.
	* Distintos datos o distintos algoritmos o parámetros
	* Combinando decisiones, por ejemplo por votación o promedio
* Sabiduría de la multitud. Usar conocimiento de distintas fuentes para tomar decisiones

### Ensambles Planos

Es como un comité de expertos en un mismo tema. Que a veces tienen distinta opinion. Ejemplos:
* Bagging
* Booting
* Random forest

### Ensambles Divisivos 

Comité de experos en distintas áreas. El problema es dividido en sub-problemas con poca superposición. Se necesitan decisiones acercad e como combinar los resultados:
* Stacking
* Mezcla de expertos


## Boostraping

Es una herramienta estadística de 1979. Resampleo a partir de un conjunto de datos con reemplazo.

## Bagging (Bootstrap aggregating)

Método para reducir varianza de un modelo. Promediar un conjunto de observaciones reduce la varianza. Podríamos tomar muchos conjuntos de entrenamiento y hacer un promedio de predicciones, o hacer boostrap (Tomamos muchas muestras repetidas de un único conjunto de entrenamiento).

* Se hace un promedio en caso de predicción numérica
* Se hace votación en caso de predcción de variable categórica

Se generan B datasets de entrenamiento con bootstrapping.
* Se entrena el método con el b-ésimo conjunto de entrenamiento y obtenemos ˆf ∗b (x), la predicción en el punto x.
* Se promedian todas las predicciones.

## Random forest

Mejora a bagging cuando se usa con árboles de decisiones. Si hay atributos que son predictores fuertes (Por ejemplo con alto information gain) los árboles serán muy similares).

Se intenta eliminar la correlación de los árboles. Para reducir varianza es mejor promediar cantidades no correlacionadas.

En random forest, en cada split de un nodo se considera sólo un subconjunto m de los p atributos (m elegidos al azar). m tienda a la raíz de p atributos.

## Boosting

Difiere de bagging en que **cada modelo se arma usando información de modelos anteriores**. Se computan pesos para mejorar los casos en que el algoritmo dio mal.

Procedimiento:
* H_o -> Modelo simple entrenado sobre todos los datos
* En cada iteracion, se entrena dando mayor importancia a los datos mal clasificados por la iteracion anterior.
* Se termina luego de un cierto numero de iteraciones
* Clasificar nuevas instancias usando una votación de todos los modelos construidos

Esto es weight-based boosting. Ej: AdaBoost

## Stacking

Hacer varias predicciones a un held-out dataset. Usar esas predicciones para armar un nuevo dataset, con el cuál se entrena un nuevo modelo. 

Procedimiento:

1. Dividir el dataset en entrenamiento y validación
2. Entrenar distintos modelos con el dataset de entrenamiento
3. Hacer predicciones con los modelos entrenados sobre el conjunto held-out
4. Usar los resultados para entrenar otro modelo

# Resumen
* Ensambles, Bagging, Boosting, Random Forest, Stacking
	* Arquitecturas: paralelas (ej: bagging) vs. secuenciales (ej: boosting)
	* Mismo clasificador (la mayor parte) vs. distinto clasificador (ej: stacking)
	* Distintas formas de combinar resultados.
* Menor interpretabilidad
* Para clasificadores inestables (ej. árboles de decisión) usar bagging o random forest.
* Para clasificadores estables y simples (ej.: Naive Bayes): usar boosting.
* Solución al dilema bias-varianza
	* Disminuir varianza usando predictores con bajo sesgo (i.e. construir muchos predictores y promediarlos. ej. bagging y random forest)
	* Reducir sesgo de predictores (i.e. construir predictores en serie, de forma tal de disminuir el sesgo. ej. boosting)

# Bibliografía

Capítulos de libros:
* ISLR 2 (2.2.2), 5 (5.2), 8 (8.2, 8.3.3, 8.3.4)
* Seni, Elder, “Ensemble Methods in Data Mining: Improving Accuracy Through Combining Predictions”, Morgan & Claypool, 2010.

Otros:
http://scott.fortmann-roe.com/docs/BiasVariance.html

