# Aprendizaje basado en instancias

Ppt muy tranqui, repasar con el video y el libro.

## Motivación
  
Para resolver un problema, uno podría ser con:
- Por reglas: Los árboles van por reglas, y priorizo reglas que aporten más información.   
- Por probabilidades: Por ejemplo bayes, probabilidades condicionales.
- Por distancias: Buscando pares de casos parecidos, con poca distancia. 
	- Por el registro más cercano
	- Por k vecinos + votación
		- Votación simple 
		- Votación compleja
	- Por k vecinos pero pesados por la distancia


Hay un problema de dimensionalidad. Mayor dimensionalidad más complejo. 
Otro problema es elegir la forma de medir la distancia entre filas de muchos valores
Otro problema es como medir la distancia datos no numericos ordinales.


## KNN

* Es el más simple de los métodos basados en instancias
* Supervisado
* Asume que todas las instancias están en un espacio n-dimensional
* Difiere el proceso de clasificar hasta que una nueva instancia deba ser clasificada
* Puede aprender funciones complejas
* No pierde información
* Puede ser “engañado” por atributos irrelevantes


### Distancia

Tenemos que elegir una forma de medir la distancia. La más simple podría ser euclídea, distancia de manhattan, una más compleja mahalanobis.

### Método

Por cada par entrenamiento lo agrego a la lista de ejemplos (valor, clase).
Para testear dada una instancia, busco dentro de la lista de ejemplo las k instancias más cercanas.

En la **versión discreta** devuelve el valor más probable. Se queda con la clase que más ocurrencia tienen entre los k vecinos más cercanos.

Podemos usar el _diagrama de voronoi_ para graficar la ingerencia de cada instancia y las áreas de 'actuación' 

En la **versión continua** se usa el promedio (Suma de valores de la función / k instancias)

La tercera opción es distancia pesada, se pesa el voto de cada vecino por el inverso de la distancia (**Distance-weighted**). Tiene la misma lógica de discretos y continuos.

## Locally weighted regression

Es una extensión de Knn. Armamos una función explicita para la región alrededor del punto, ajustando una función a sus k vecinos más cercanos, pesada por su distancia. 

La función puede ser lineal, cuadrática. 

## Core based reasoning

Tiene una mejor representación y medidas de distancias más elaboradas. Da un ejemplito más cortito sobre texto. Por ejemplo para los texto es buscar textos similares incluyendo la similitud semántica.

## Bibliografia

Libro:
* Machine Learning cap. 8 - T. Mitchell

Artículos
* https://web.archive.org/web/20080312053714/
* http://www.iiia.csic.es/People/enric/AICom.html
* https://towardsdatascience.com/how-to-rank-text-content-bysemantic-similarity-4d2419a84c32
