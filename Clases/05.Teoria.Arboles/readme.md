# Clase 5: Arboles de decision + Aprendizajes de conceptos

# Aprendizaje de conceptos

*Concepto* -> Subconjunto de objetos o eventos definidos sobre un conjunto mayor.

*Aprender concepto* -> Indicur automaticamente una funcion booleana a partir de conjuntos de ejemplos o datos. Dado un nuevo caso, devuelve su clase.
 
## Aprendizaje de ocnceptos

Se lo puede definir como un problema de búsqueda de la hipotesis que más se adecua a los ejemplos mostrados sobre un espacio predefinido de posibles hipótesis.
 
 
## Aprendizaje inducido

### Inferencia lógica:

*Inferir*: Establecer relación entre premisas y conclusiones

* Razonamiento deductivo: p => q; p; q. De lo general a lo particular.
* Razonamiento inductivo: p => q; r => q; s => q. De lo particular a lo general.

## Aprendizaje inductivo

Consiste en construir un modelo general a partir de información específica.

Principio de Aprendizaje Inductivo: Cualquier hipótesis (modelo) que aproxime bien a una función objetivo sobre un conjunto suficientemente grande de datos también aproximará bien a la función objetivo sobre datos no observados.


### Aprendizaje supervisado:

Dado una funcion objetivo desconocida, queremos aproximarla mediante una hipotesis o modelo.

*Los algoritmos de aprendizaje automatico son procedimientos para entrenar modelos a partir de un conjunto de datos*

## Sesgo inductivo - Bias

Hacemos una suposicion para facilitar el algoritmo de ML, reducir el espacio de búsqueda. Para hacerlo asumimos que las hipótesis tienen una forma en particular. Un conjunto finito de datos no suele alcanzar para inferir un modelo.

* El sesgo inductivo de un algoritmo de aprendizaje es el conjunto de afirmaciones que el algoritmo utiliza para construir un modelo.
* El sesgo inductivo incluye:
	* Forma de las hipótesis (número y tipo de parámetros);
	* Características de funcionamiento del algoritmo (cómo recorre el espacio de hipótesis hasta elegir un único modelo).

La reduccion de espacio de conceptos grandes a uno chico: sesgo inductivo (inductive bias). 

_Todos los algoritmos de aprendizaje tiene sesgo inductivo._


## Bibliografía

* Mitchell, Cap. 2 - Leer todo. Incluyendo:
	* Adquisición de conceptos como búsqueda
	* Algoritmos
		* FIND-S
		* List-then-eliminate
		* Eliminación de candidatos

# Árboles de decisiones

Es un método que intenta, con la menor cantidad de reglas, clasificar. Es un método de caja blanca, tiene buena explicabilidad.

* Nodo: Pregunta. Test sobre un atributo de la instancia. 
* Ejes/ramas: Posibles respuestas, valor para ese atributo
* Hojas: Nosotros que representan objetos
* Caminos desde la raiz

**Árbol** representa la disyunción de conjunciones sobre valores de los atributos. 

## Cuando si?

* Instancias representables como diccionario (CLave valor)
* Valores de salida discretos
* Hipotesis disyuntivas
* Posibles atributos faltantes
* **Explicabilidad alta** 
	* En lo médico y en riesgos crediticio suelen usarse por la explicabilidad, y la 'transparencia' para el negocio.

## Algoritmo

(ID-3, C4.5)

1. A <- El 'mejor' atributo para el nodo_actual
2. Asignar A como el atributo de decisión
3. Para cada valor de A, crear un nuevo hijo del nodo_actual
4. Clasificar las instancias en los nuevos nodos, según el valor de A
5. Si las instancias están bien clasficadas, es decir clasificamos todas  => **Terminar**
	1. Sino => Iterar sobre los nuevos nodos
	

### ¿Cuál es el mejor atributo? (Punto 1)

Medidas de impureza:
* Entropía, Information Gain 
	* Medida de incertidumbre
	* Si discrimina más objetos entonces reduce la entropía
	* ID3 algorithm uses entropy to calculate the homogeneity of a sample
		* 0.5 significa que las clases están balanceadas
		* Más cerca de 1 o 0 significa que alguna clase prevalece
	* https://www.saedsayad.com/decision_tree.htm
* Gini, Gini Gain
	* Gini impurity is a measure of how often a randomly chosen element from the set would be incorrectly labeled if it was randomly labeled according to the distribution of labels in the subset. 
	* Gini impurity measures how heterogeneous or mixed some value is over a set. 
	* The highest Gini score is 0.50
	* 0 o 1 son buenos valores. Va a ser una impureza baja
	* Ref: https://medium.com/@jason9389/gini-impurity-and-entropy-16116e754b27

Medidas de efectividad:
* Information gain: Reducción esperada de entropía por partir ejemplos basados en ese atributo
* Gain ratio: Reducción del índice de gini por partir ejemplos basados en ese atributo

### Information gain

Entropía de una muestra S:

<img src="https://render.githubusercontent.com/render/math?math=Entropy(S) = \sum_{c \in Clases} - p_{c} * log_{2} p_{c}">

<img src="https://render.githubusercontent.com/render/math?math=p_{c}"> es la proporción de instancias de S pertenecientes a la clases c. La entropia(S) mide la impureza de S.

Nosotros queremos **reducir la entropía**. 

Reducción de entropía de la muestra S causada por particionar ejemplos de acuerdo a un atributo A.

<img src="https://render.githubusercontent.com/render/math?math=Gain(S, A) = Entropy - \sum_{v \in Valores(A) } \frac{ \mid s_{v} \mid}{ \mid S \mid} * Entropy(S_{v})">

Valores(A): Posibles valores del atributo
<img src="https://render.githubusercontent.com/render/math?math=S_{v} = \left\{ s \in S \mid A(S) = v \right\}">

Nosotros queremos quedarnos con los atributos que mayor ganancia de información ofrecen. (Otra opción es usar Gain Ratio que corrige la preferencia de información en atributos con muchos valores).


**TODO**: Hacer ejecicios de cálculo de entropía (En clase fue con el ejemplo del clima).
**TODO**: Como es el intervalo de cada medida de efectividad. Cuando es una entropia optima? Cuando es un gini optimo? 


### Sesgo inductivo
(Capítulo 3 del mitchell)
 
Hay muchos posibles árboles para un conjunto de datos, _¿Cómo elejimos una hipótesis por sobre las otras?_

* El algoritmo que vimos tiene preferencia por: 
	* Árboles más bajos
	* Atributos con information gain alto, cerca de la raíz
* Sesgo: Un algoritmo puede privilegiar uno de los dos sesgos
	* Preferencia la búsqueda incompleta en espacio de hipótesis completo. El sesgo es la preferencia por una hipótesis sobre otras. (Ej: ID3)
	* Restriccion: Búsqueda completa en un espacio de hipótesis incompleto. Sesgo: Consecuencia de poder expresivo de la representación de hipótesis (Ej: CEA)
* Navaja de Occam/Ockham: Se prefiere la hipótesis más corta que satisface a los datos
	* “Pluralitas non est ponenda sine necessitate.” La pluralidad no debe postularse sin necesidad
	* Las soluciones simples tienen más probabilidades de ser correctas

## Overfitting

Hay sobreajuste cuando el árbol es "demasiado" profundo. ¿Qué pasa si hay descripciones exactas de instancias únicas y aisladas?

**Accuracy** (Exactitud): ( TP + TN ) / ( TP + TN + FP + FN )

Cuando sobre entreno, soy muy exacto en datos de entrenamiento y muy poco exacto en test. Más profundo el árbol, más chance de overfitting.

**Soluciones**: 
* Detener el crecimiento del árbol 
* Hacer crecer el árbol y podarlo (Post-prune - Relacionado con el ccp_alpha en Skitlearn)

### Reduced Error Pruning

Uno un conjunto de validación, y considero cada noto como candidato de pruning.

1. Particiono datos en conjunto de train y test
2. Repetir hasta que la poda sea perjudicial
	a. Evaluar impacto de cada posible nodo (y los de abajo..)
	b. Remover aquel que mejora el accuracy de validación set (Es de tipo greedy o ansioso)
	
### Rule post pruning

1. Inferir el árbol
2. Convertir el árbol en conjunto de reglas
3. Podar cada regla independientemente de las demas, removiendo precondiciones que mejoran la accuray
4. Ordenar las reglas de 4 de acuerdo con su accurat estimada.


## Adecuaciones 

### Atributos continuos 

* Si tenemos un atributo numérico, lo discretizamos. 
	* Existen extensiones para particionar atributos contínuos en múltiples intervalos
* Buscamos un umbarl t (threshold en inglés) y discriminamos en función de si A < t.
	* La idea es encontrar el umbral, que nos ayude a mejorar la toma de decisiones
	* Por ejemplo encontrar un valor t, tal que podamos usarlo para decidir y tomar decisiones
		* Umbral que maximice el information gain
	* Puede ser útiles encontrar entre los casos el punto en el que cambia la categoría

### Atributos faltantes

Posibles estrategias:
* Asignar el valor más común en entrenamiento
* Asignar el valor más común entre los datos de entrenamiento que tienen la misma clasificación
* Asignar una probabilidad basa en frecuencias observadas en valores de A en nodo N
* Modelo que prediga (Knn que estima multivariado)

### Atributos con costo

Costo puede representar $, pero tambien tiempo, comodidad, complejidad.

* Preferimos árboles que usen atributos de bajo costo usando los de alto costo solo cuando es necesario.
* Modificación ID3: Se usa el término de costo en medida selección de atributo. Se prefieren atributos de menor costo.
	* Gain(S, A) / Costo(A) 


## Resumen de algoritmos

* Criterio de selección de atributos (Splitting criteria)
	* ID-3: Information gain
	* C4.5: Gaion Ratio
	* CART: Gini
	* CHAID: Chi cuadrado
* Tipo de valores
	* ID-3: Categóricos
	* C4.5 y CART: Categóricos y númericos
* Valores faltantes
	* ID-3 no los trata
	* C4.5, CART los tratan
* Estrategias de poda
	* ID-3 sin poda
	* C4.5: Error-based prunning
	
## Resumen árboles

* Aprendizaje supervisado.
* Para clasificación y regresión
* Fáciles de usar y de entender
* Buen método exploratorio para ver qué atributos son importantes
* (Otras cositas que se hablaron: Tipo de generalización, sesgo, overfitting)

### Ventajas:
* Fácil de visualizar e interpretar
* Permite usar atributos categóricos, continuos, binarios

### Desventajas:
* Overfitting (Todos overfite
* Suelen necesitarse ensambles para tener mejor performance

# Bibliografia

Capítulos de libros:

* Mitchell, Cap. 3
* Alpaydin, Cap. 9
* Marsland, Cap. 12

Artículos:
* Induction of Decision Trees. Quinlan. 
	* http://hunch.net/~coms-4771/quinlan.pdf
* Simplifying Decision Trees. Quinlan. 
	* https://www.sciencedirect.com/science/article/pii/S0020737387800536

# Referencia
* Helper para formulas en latex
<img src="https://render.githubusercontent.com/render/math?math=A">