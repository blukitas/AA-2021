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

Una vez definido cuál es el mejor modelo se entrena con conjunto de desarrollo (también llamado de entrenamiento). Los datos se pueden separar al azar o con otro criterio, para evitar cualquier orden o estructura subyacente en los datos. 

El azar puede no ser el mejor criterio. Los datos de entrenamiento y validación deben ser independientes entre sí; los datos pueden estar desbalanceados, tener orden temporal, etc.
* Desbsalanceado -> podemos queres preservaar el desbalanceo, o bien podemos querer balancear
	* Balancear se puede hacer de varias formas (under o over sampling)
	* El desbalanceo te ensucia el accuracy (Alto porque una etiqueta monopoliza la muestra)
	* SMOTE como un método de balanceo, la opcion por defecto de balanceo de sklearn
	* Probablemente uno no vaya por un 50-50, porque se quiere respetar la desigualdad, pero si equilibrar ligeramente

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
* (Gradientes?

Al terminar, nos quedamos con la combinación con mejor desempeño, y entrenamos un único modelo usando todos los datos. El objetivo es plantear un espacio de búsqueda, buscar teniendo métricas intermedias y luego continuar con un único modelo que sea el mejor.

La diferencia entre grid y random tiene que ver con completitud y uso de recursos. Grid es más completo, pero tambien puede demorar muchisimo más, tiende a infinito si se quiere. Random, es 'peor' pero uno podría dejar un número alto de intentos, o correr varias vueltas con distintos seed y tener un resultado decente.

## Medidas de performance

### Matriz de confusión

| 			| 			| valores reales 	  									|
| 		   	| 			| positivo 					| negativo 					|
|-----------|-----------|---------------------------|---------------------------|
|prediccion | Positivo 	|  Verdadero Positivo (TP) 	| Falso Positivo (FP) 		|
|			| Negativo 	|  Falso Negativo (FN) 		| Verdadero negativo (TN) 	|

**Error tipo I** -> Falso positivo 
**Error tipo II** -> Falso negativo


**Accuracy** = (TP + TN) / (TP + TN + FN + TN)

No dice nada sobre los tipos de aciertos y de errores que tiene el modelo. Tiene bastantes problemas con datasets desbalanceados, el accuracy es alto pero se debe al desbalanceo.

**Precision** = TP / ( TP + FP )
_De las instancias clasificadas como positivas, cuantas lo son_ (Cuán útiles son los resultados)

**Recall** = TP / ( TP + FN ) = **Sensitivity** = **TPR** (True positive rate) 
_De las instancias positivas, cuantas fueron clasificadas como positivas_ (Cuán completos son los resultados). Que porcentaje de cobertura, si recall es uno, es porque detecto todos. 

Accuracy es más simple. Precision y recall son más interesantes, nos dan más información sobre como fue el resultado. 

Hay una variante más, que trabaja sobre precision y recall (Media armónica)

**F-measure/F_1-score** = 2 * (Precision * Recall) / (Precisión + Recall)

La generalización es <img src="https://render.githubusercontent.com/render/math?math=F_{\beta} = (1 + \beta^2) \frac{Precision*Recall}{ ( \beta^2*Precision) + Recall}"> 

* F_2 da más peso al recall
* F_0.5 da más peso a precision

**Specifity** = TN / (TN + FP) (True negative rate)
**FPR** = FP / (FP + TN)

**Curva ROC** 
Gráfico TPR ( Recall ) Vs FPR
Construcción: Variar el umbral de detección entre 0 y 100%. Para cada valor, calcular el TRP y FRP. 

Ref interesante -> http://arogozhnikov.github.io/2015/10/05/roc-curve.html

Una curva roc mala es una función identidad (Línea 45°). En el peor caso el **área abajo de la curva** (AUC) es 0.5, en el ideal es = 1.

**Matriz de confusión n-aria** para comparar n contra n clases de salida. Las medidas precisión, recall, etc. sólo pueden formularse en forma binaria: cada clase contra el resto.

### Factores a considerar en la elección de modelos

* Tasa de error
* Velocidad de entrenamiento y velocidad de test
* Interpretabilidad (¿el conocimiento extraído del modelo puede ser validado por expertos?)
* Facilidad de desarrollo

## Experimentos de aprendizaje automático

1. Establecer objetivo de estudio (error de un algoritmo, comparación dedos algoritmos, etc.)
2. Seleccionar la métrica para evaluar performance
3. Seleccionar factores importantes (dependen del punto 1): (hiperparámetros de un algoritmo, comparación de algoritmos: algoritmos a comparar)
4. Elegir diseño experimental (división de conjunto en entrenamiento y test, cross validation, hiperparámetros: modificaciones aleatorias vs. grid search)
5. Realización de experimento (uso de código testeado, **reproducibilidad** de resultados)
6. Realizar análisis estadísticos de los datos
7. Conclusiones: son sobre los datos utilizados. Realizar análisis de errores


# Bibliografía

Capítulos de libros:
* ISLR, Cap. 2 (2.2)
* Alpaydin, Cap. 19 (hasta 19.7 inclusive)