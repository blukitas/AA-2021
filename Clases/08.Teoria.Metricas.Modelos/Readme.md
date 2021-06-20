# Evaluación de modelos y métricas

# Evaluación de modelos

Las preguntas que disparan son:
* ¿Cómo sabemos cuán bueno es nuestro modelo?
* ¿Sobre qué conjunto de datos lo medimos? 

## Conjunto Held-Out (o Control o Test)

Al comenzar hay que separar un conjunto de datos (Held-Out, Control o Test) y NO TOCARLOS hasta el final
Todas las pruebas y ajustes se realizan sobre el conjunto de Desarrollo
Al terminar todas las pruebas, se evalúa el modelo obtenido con el conjunto Held-out

### Estimación de performance

Se prueban distintas configuraciones. Los datos de desarrollo se separan en:
* (100-q) % para entrenamiento
* q % para validación del modelo

Una vez definido cuál es el mejor modelo se entrena con cjto. de desarrollo (también llamado de entrenamiento). Los datos se pueden separar al azar o con otro criterio, para evitar cualquier orden o estructura subyacente en los datos. 

El azar puede no ser el mejor criterio. Los datos de entrenamiento y validación deben ser independientes entre sí; los datos pueden estar desbalanceados, tener orden temporal, etc.

Resumen de esto:
* Train
* Validacion
* Test

## Validación cruzada (o cross-validation)

Podría pasar que por la separación de los datos (Train-validacion-test) tuvieramos 'mala' suerte y nos perjudicara la métrica. Para disminuir este riesgo: **k-Fold Cross Validation**

1. Desordenar los datos.
2. Separar en k folds disjuntos del mismo tamaño.
3. Para i = 1 .. k: entrenar sobre todos menos i; evaluar sobre i.

Validación cruzada sobre train, test para las métricas definitivas. Pero hacemos k splits y probamos las distintas opciones. Minimizamos la chance de que sea azar nuestro resultado. Obtenemos k métricas, una media y la dispersión de la media. Nos ayuda a elegir con más criterio.

# Selección de modelos

¿Por qué tendríamos distintos modelos para comparar?

* Distintos atributos (selección y transformación de atributos)
* Distintos algoritmos (árboles, LDA, NB, KNN, SVM, …)
* Distintos hiperparámetros de cada algoritmo.
	* Ejemplo: hiperparámetros de los árboles de decisión
	* Criterio de elección de atributos en cada nodo (Information Gain, Gini Gain...)
	* Criterio de parada (ej: máxima profundidad)
	* Estrategia de poda
	
## ¿Cómo buscar la mejor combinación de atributos + algoritmos + hiperparámetros?

Exploramos un espacio de búsqueda (Siguiendo una lista/matriz de valores para los hiperparámetros), usando k-fold CV para medir el desempeño de cada combinación. Tenemos dos opciones (Por lo menos las que vimos):

* Grid search: Buscar todas las posibles combinaciones.
* Random search: Buscamos aleatoriamente combinaciones.

Al terminar, nos quedamos con la combinación con mejor desempeño, y entrenamos un único modelo usando todos los datos. El objetivo es plantear un espacio de búsqueda, buscar teniendo métricas intermedias y luego continuar con un único modelo que sea el mejor.

La diferencia entre grid y random tiene que ver con completitud y uso de recursos. Grid es más completo, pero tambien puede demorar muchisimo más, tiende a infinito si se quiere. Random, es 'peor' pero uno podría dejar un número alto de intentos, o correr varias vueltas con distintos seed y tener un resultado decente.

## Medidas de performance

### Matriz de confusión

| 			| 			| valores reales 	  									|
| 		   	| 			| positivo 					| negativo 					|
|-----------|-----------|---------------------------|---------------------------|
|prediccion | Positivo 	|  Verdadero Positivo (TP) 	| Falso Positivo (FP) 		|
|			| Negativo 	|  Falso Negativo (FN) 		| Verdadero negativo (TN) 	|

**Accuracy** = (TP + TN) / (TP + TN + FN + TN)

No dice nada sobre los tipos de aciertos y de errores que tiene el modelo.

**Precision** = TP / ( TP + FP )
_De las instancias clasificadas como positivas, cuantas lo son_ (Cuán útiles son los resultados)

**Recall** = TP / ( TP + FN )
_De las instancias positivas, cuantas fueron clasificadas como positivas_ (Cuán completos son los resultados)

Accuracy es más simple. Precision y recall son más interesantes, nos dan más información sobre como fue el resultado. 

Hay una variante más, que trabaja sobre precision y recall (Media armónica)

**F-measure/F_1-score** = 2 * (Precision * Recall) / (Precisión + Recall)

La generalización es <img src="https://render.githubusercontent.com/render/math?math=F_{\beta} = (1+\beta^2) \frac{Precision*Recall}({\beta^2*Precision) + Recall}"> 

* F_2 da más peso al recall
* F_0.5 da más peso a precision

Página 14 del ppt	













