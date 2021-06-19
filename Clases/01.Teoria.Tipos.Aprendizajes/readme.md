# Clase 1 - Intro

## Definiciones de Aprendizaje automático

Hay IA por todos lados (Robots de limpieza, reconocimiento de caras, filtros de spam). 

* Algoritmo: secuencia finita de instrucciones para resolver un problema
* Programa: implementación de un algoritmo en un lenguaje de programación (Camino más corto entre dos puntos, Ordenar una lista de valores)

* Aprendizaje automático: Rama de la Inteligencia Artificial, que estudia algoritmos para que las computadoras aprendan a resolver problemas a partir del uso de datos sin ser programadas específicamente.
	* Extracción de información
	* Data mining
	* Soluciones complejas que no pueden programarse específicamente (Sistema de conducción autónomo)
	* Sistemas de recomendación
	* Reconocimiento del habla
	* Prediccion del tiempo de viaje, camino más corto
	* Detección de fraude
	* Publicidad online
	
* Otras definiciones de aprendizaje automático:
	* Campo de estudio que le da a las computadoras la habilidad de aprender sin ser programadas de manera explícita (Samuel)
	* Un programa de computadora se dice que aprende de una experiencia E con respecto a una clase de tareas T y una medida de performance P, si su performance en las tareas T, medidas por P, mejoran con la experiencia E (Mitchell)

Un programa de computadora aprende una tarea si su performance en la tarea mejora con la experiencia. Hay que definir:
* Tarea (**T**)
* Medida de performance (**P**)
* Experiencia (**E**)

**Ejemplo**: Reconocimiento de escritura a mano
* T: reconocer la escritura
* P: porcentaje de palabras bien reconocido
* E: consultar el repositorio de imágenes de palabras manuscritas y sus transcripciones

## Tipos de clasificación

* Aprendizaje **Supervisado** -> Se le dan al algoritmo un conjunto de datos y su respuesta correcta para que pueda aprender. El objetivo es predecir luego, nuevos valores.
	* Obtener datos
		* Problemas de disponibilidad, podemos publicar despues? Que tan sensible es la información.
		* Problema de los tipos de datos. Datos estructurados y no estructurados.
	* Requerimos datos anotados
		* Anotar los datos es costoso (Tiempo, recursos, dinero)
		* Hay que tener un esquema y lineamientos de anotación. No puede anotarse el mismo resultado con dos nombres diferentes. 
		* Puede haber problemas de calidad
	* Pasos:
		* Definir el problema (Tarea a aprender y su medida de performance)
		* Recolectar los datos 
			* Limpiarlos (Limpiar, anonimizar, conjuntos de entrenamiento, validacion y test)
			* Estudiar las features
		* Experimentación
			* Seleccionar el algoritmo
			* Seleccionar las features
			* Busqueda de hiperparametros
		* Evaluación del modelo sobre nuevos datos
		
* Aprendizaje **No supervisado** -> Se dan los datos, pero no están anotados.  El propio algoritmo encuentra conocimiento. 
	* Por ejemplo, segmentación del mercado. Clustering o Reducción de dimensionalidad.
	
* Aprendizaje por **refuerzos** -> Aprendizaje de un agente autónomo (con sensores) para elegir acciones óptimas que le permitan lograr sus objetivos.
	* Hay premios y castigos en función de la satisfacción del objetivo.
	* El agente aprende la mejor secuencia de acciones que maximizan el premio.
		
# Tarea

Leer:

	* Mitchell, Cap. 1
	* Alpaydin, Cap. 1
	* Marslan, Cap. 1