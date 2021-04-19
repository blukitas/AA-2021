# Clase 3 - Datos y Cesgos

## Temario:

* Disponibilidad
* Calidad


## Parte 1:

### Donde se usa AA? 

Muchos lados, las principales empresas están basadas en eso (Facebook, Netflix - recomendacion por todos lados, waze, google, uber, deteccion de fraude)

### Porque se da el auge?

* Mundo más interconectado
* Más computarizacion
* Más datos se guardan
* Aumenta la necesidad de procesarlos
* CPU más potentes, luego GPU más potentes, ahora TPU (Tensorflow processor units)

Un loop positivo:
* Una sinergia de más interconexión, el mundo se computariza, más procesamiento, menor costo de procesamiento y almacenamiento

Si bien mucho conocimiento teórico es anterior, de los 60/70/80. En el último tiempo con todo esto, boom en uso y aplicacion, nuevas investigaciones.


## Disponibilidad:

Cada vez más.

* En grandes proyectos de investigacion, 
* Muchas empresas (No libres pero si internos). 
* Más dispositivos midiendo y conectados a internet (O registrados).
* Más satelites, drones, imagenes satelitales
* Datos médicos, banca, 

Una movida nueva de open data.

Partes que nombramos:
1) Dominios (Distintas áreas de conocimiento, todo lo que a uno se lo ocurra y más)
2) Dispositivos (PC, pero tambien drones, satelites, imagenes satelitales, sensores...)
3) Formatos (Imagenes, señales, texto - tabulado, estructurado, libre, con modismos -, estructurados, IOT)



### Big data

Procesar, almacenar, visualizar,

1) Volumen - Cantidad
2) Velocidad - Rapidez de generacion y consulta
3) Variedad - Distintos tipos de datos
4) Veracidad
5) Valor


### Footprint

* Activa: Intencionalmente. Ej: posteo de foto
* Pasiva: No intencional. Ej: Habitos de web browsing, historial de busqueda, viajes en la sube


## Calidad

### Datos:

1) Estructurados

* Numericos
* Ordinales (Status socioeconomico)
* Categoricos (Ubicacion (Urbano, suburbano, rural)

2) Semi estructurados

3) No estructurados


### Calidad de datos

Redman 1996
* Un dato es de mayore calidad si satisface las ecesidades del usuario mejor que otro conjunto de datos.

English 1999
* Satisfacer de manera consistente las expectativas de los usuarios

(Muy subjetivas)


* -> Entra basura -> Sale basura -> *

Consecuencias: 
* Descreimiento
* Insatisfaccion de clientes
* Costos innecesarios
* Impacto en la toma de decisiones

### Posibles causas de problemas

* Procesos masivos que reparan (Pero no todo)
* Misma informacion distribuida
* Valores predeterminados

### Dependence de:

* Calidad del sw (Mala usabilidad, obligatoriedad de datos que no es realmente necesario)
* Definicio de procesos asociados a los datos
* Diseño de DB
* Capacitacion

### Que hace a la calidad de datos

* Datos completos
* Oportunos y vigentes
* Consistentes y correctos
* En cantidad adecuata
* Disponibles/Accesibles
* Seguros y privados

### Atributos de calidad

* Completitud: Que esten presentes todos los valores para representar la realidad
* Relevancia: Relevantes para representar la realidad
* Vigencia: Actualizados con la frecuencia adecuada
* Disponibilidad: Accesibles
* Confiabilidad: Que podamos considerar que los datos representan información verídica
* Consistencia: No hay contradiccion entre distintos datos almacenados
* Corrección: Representa la situación real
* Seguridad y relevancia: Que complen con los requerimientos de privacidad adecuados

Esto son características, pero para medirlo hay que definir métricas. Por ejemplo completitud debería tener una segunda vía para ver si tengo todo cargado.


No hay datos perfectos, debo priorizar algunas de las características (?

## Cesgos

Correctitud / Bias

En ML muchas veces se entrenan con grandes conjuntos de datos anotados (Expertos, estudiantes, crowdsourcing). A veces tomados a partir de scrapping (Es necesario saber de donde salen, como se generaron, que calidad tienen).

Crowdsourcing: etiquetados por laburo en equipo.

En los grandes conjuntos de datos puede haber sesgos (Genero, etnia,...). En los datos hay sesgos que las personas tenemos. 

En muchos aspectos la medida estandar es un hombre, blanco/cacucasico, 70Kg, 1,7m, 25/30 años. Por ejemplo temperatura de una habitacion, ataque al corazon, sistemas de reconocimiento de voz / reconocimiento facial (Coded bias. Entrenar con imagenes de imagenet), prejuicio racial en los juicios, deteccion de cancer de piel (Problemas con piel morena), el caso general de pruebas de medicamentos sigue ese hombre promedio.

Si el data set está desbalanceado va a optimizarse para un cierto grupo de personas (Lo que pasaba con personas negras en coded bias el documental. El reconocimiento de mujeres negras era el que peor score tenía).

Hay como un par de tipos de sesgos diferentes:

* Sesgo de representatividad, un dataset que por estar desbalanceado, optimiza los resultados para cierto grupo de personas. (Deteccion de cancer de piel con muestra mayoritariamente blanca)
* Sesgo donde se atribuye un resultado por una característica inherente de la persona. (Detectar como peligroso una persona con ascendencia árabe, asumir como más riesgoso en el sistema judicial a una persona negra/latina)

(Ejemplo que repitió mil veces es el de gorila con personas negras).


## Open data

Iniciativa global para disponibilizar datos.


## Ética


















