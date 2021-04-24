# Clase 5: Arboles de decision + Aprendizajes de conceptos

# Aprendizaje de conceptos

*Concepto* -> Subconjunto de objetos o eventos definidos sobre un conjunto mayor.

*Aprender concepto* -> Indicur automaticamente una funcion booleana a partir de conjuntos de ejemplos o datos. Dado un nuevo caso, devuelve su clase.
 
## Aprendizaje de ocnceptos

Se lo puede definir como un problema de búsqueda de la hipotesis que más se adecua a los ejemplos mostrados sobre un espacio predefinido de posibles hipótesis.
 
 
## Aprendizaje inducido

## Inferencia lógica:

*Inferir*: Establecer relación entre premisas y conclusiones

* Razonamiento deductivo: p => q; p; q. De lo general a lo particular.
* Razonamiento inductivo: p => q; r => q; s => q. De lo particular a lo general.

## Aprendizaje supervisado:

Dado una funcion objetivo desconocida, queremos aproximarla mediante una hipotesis o modelo.

*Los algoritmos de aprendizaje automatico son procedimientos para entrenar modelos a partir de un conjunto de datos*


## Sesgo inductivo:

Hacemos una suposicion para facilitar el algoritmo de ML, reducir el espacio de búsqueda. Para hacerlo asumimos que las hipótesis tienen una forma en particular.

La reduccion de espacio de conceptos grandes a uno chico: sesgo inductivo (inductive bias). Todos los algoritmos de aprendizaje tiene sesgo inductivo.


# Árboles de decisiones

Es un método que intenta, con la menor cantidad de reglas, clasificar. Es un método de caja blanca, tiene buena explicabilidad.

## Cuando si?

* Instancias representables como diccionario (CLave valor)
* Valores de salida discretos
* Hipotesis disyuntivas
* Posibles atributos faltantes
* Explicabilidad alta

## Algoritmo

