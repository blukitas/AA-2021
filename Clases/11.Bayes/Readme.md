# Aprendizaje Bayesiano

## Motivacion

Usar la probabilidad para predecir (A diferencia de reglas o distancias).

## Modelos generativos

* Los modelos **generativos** son una amplia clase de algoritmos de aprendizaje automático que hacen predicciones **modelando la distribución conjunta** P (y, x). 
* Los modelos **discriminativos** son una clase de modelos de aprendizaje automático _supervisados_ que hacen predicciones **estimando la probabilidad condicional** P (y | x). 

Para utilizar un modelo generativo, _se deben resolver más incógnitas_: hay que estimar la probabilidad de cada clase y la probabilidad de observación de la clase dada. Estas probabilidades se utilizan para calcular la probabilidad conjunta y, finalmente, la probabilidad conjunta se puede utilizar como sustituto de la probabilidad condicional para hacer predicciones. 

Modelo generativo => Teorema de Bayes
 
**Teorema de Bayes** => Divide el cálculo de la probabilidad conjunta P (y, x) en el cálculo de otros dos tipos de probabilidades: probabilidad de clase, P (y), y probabilidad de observación de clase dada, P (x | y). 

El tema con esto es la cantidad de probabilidades condicionales que debería calcular. El costo computacional se dispara.

Algunas suposiciones hacen que la estimación de P (x | y) sea manejable. El clasificador **Naive Bayes** puede servir como un ejemplo perfecto de un modelo generativo con tal suposición, lo que facilita el cálculo de P (x | y). Es decir, _tiene un supuesto de independencia entre las características_ xi,…, xn. 

Naive bayes asume que hay independencia entre las observaciones. Eso es una asunción fuerte, pero sirve en la práctica, y lo hace manejable. La productoria se simplifica mucho => P(X | Y) = Productoria( P (X_i | Y )

(**TBD** completar estas cosas con el libro)

## Naive Bayes

El algoritmo bayes ingenuo asume que todas las funciones son independientes entre sí. Sino tendría que calcular todas las posibles configuraciones. 

P (X | y_i) = P (y_i | x1, x2, ..., xn) = ( P(x1, x2, ..., xn | y_i) * p(y_i) ) / p(x1, x2, ... , xn)

La _P(x1, x2, ..., xn | y_i) * p(y_i)_ significa la probabilidad de una combinación específica de características dada una etiqueta de clase. Asumiendo independencia se transforma en el producto de la probabilidad de cada característica contra la partición.

y = P(y) * productoria( P(x_i | y) )

La función de probabilidad depende del tipo de datos:
* Si binario => Bernoulli
* Si discreto => Multinomial
* Si continua => Gaussiana


### Maximum Likelihood Estimation VS Maximum A Posterior 

(**Ref:** https://towardsdatascience.com/mle-vs-map-a989f423ae5c )

MAP => Máximo a posteriori. Asigno la clase del que tiene mayor probabilidad.
MLE => ?

(**TBD** completar estas cosas con el libro)


## Probabilistic graphical Model

Los modelos gráficos probabilísticos (PGM) proporcionan una representación gráfica para comprender la relación compleja entre un conjunto de variables aleatorias (RV). 

**Ref** => https://towardsdatascience.com/introduction-to-probabilistic-graphical-models-7d2c0b4bef19

PGM proporciona la estructura donde podemos aprovechar las propiedades de independencia para representar los datos de alta dimensión de una manera más compacta. Una herramienta poderosa para hacer inferencias sobre algunas variables no observadas, dada la evidencia sobre las variables observadas. 

* **Red Bayesiana**: Representa la estructura mediante grafo acíclico dirigido. El flujo de influencia probabilística entre las variables en tales redes tiene una dirección clara. La presencia de flechas implica la relación de causa y efecto entre las dos variables que está representada por la distribución de probabilidad condicional (CPD). 
* **Red de Markov**: el gráfico subyacente en una red de Markov no está dirigido. Como los arcos de esta red no tienen ninguna dirección, falta la relación causa-efecto. Por lo tanto, solo podemos representar qué combinación es más probable que ocurra en términos de afinidad. 

## Redes bayesianas

Las redes bayesianas son un tipo de modelo gráfico probabilístico que utiliza la inferencia bayesiana para los cálculos de probabilidad. 

Las redes bayesianas tienen como objetivo modelar la dependencia condicional y, por lo tanto, la causalidad, al representar la dependencia condicional por aristas en un gráfico dirigido. A través de estas relaciones, uno puede realizar inferencias de manera eficiente sobre las variables aleatorias en el gráfico.

**Ref**:
* https://www.coursera.org/specializations/probabilistic-graphical-models
* http://ai.stanford.edu/~paskin/gm-short-course/lec2.pdf

Las redes bayesianas satisfacen la propiedad local de Markov, que establece que un nodo es condicionalmente independiente de sus no descendientes dados sus padres. 

Formalmente, si existe una arista (A, B) en el gráfico que conecta las variables aleatorias A y B, significa que P (B | A) es un factor en la distribución de probabilidad conjunta, por lo que debemos conocer P (B | A) para todos los valores de B y A para realizar inferencias. 
 
### Patrones de razonamiento
* Causal
* Evidencial
* Intercausal


### Flujo de influencia probabilística


### Aprendizaje de hiperparámetros

Maxima verosimilitud => Busco obtener un hiperparametro que maximite la probailidad.  

MLE => Estimador de maxima verosimilitud (Maximum likelyhood estimator)

### Ventajas

* Flexibilidad
	* Decision-making
	* Clasificación
	* P(A|B)
	* P(B|A)






































































































