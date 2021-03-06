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

#### Consecuencias

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

Big data ethics: sistematizar, defender, recomendar actitudes éticas en relación a los datos, en particular a los datos personales. 

**Problemas éticos**:
* Privacidad -> ¿Quién debería controlar acceso a los datos?
* Ownership -> ¿Quién es el dueño de los datos, cuáles son las obligaciones de quienes generan y usan datos?
* Reputación -> ¿Cómo podemos determinar que los datos son confiables?
* Identidad -> La identidad de a quién se refieren los datos debería permanecer privada

Algunas **instituciones** relacionadas:
* The Institute for Ethical AI & Machine Learning
* The Institute for Ethics and Emerging Technologies

_Los sistemas son creados por humanos, que pueden tener sesgos._

Posibles problemas:
- **Datos**: mala calidad (no disponibilidad, cantidad inadecuada, mal balanceo, no actuales, formato, sesgos, no correctitud, no consistencia), errores en su estructuración, mala interpretación (ej, correlación no implica causalidad)
- **Algoritmos**: parametrización, mala elección
- **Capacidad de procesamiento**: Inadecuada
- **Cuestiones éticas**

**Correlación no implica causalidad**

## Data science

Habilidades requiere un data scientist:

* Recolectar datos,
* Saber interpretar los datos,
* Organizar, resumir y analizar datos,
* Sacar conclusiones válidas


# Lecturas complementarias

Papers de temas relacionados con sesgos en datos

* [Data statements] Bender, Emily M., and Batya Friedman. "Data statements for natural language processing: Toward mitigating system bias and enabling better science." Transactions of the Association for Computational Linguistics 6 (2018): 587-604. https://direct.mit.edu/tacl/article/doi/10.1162/tacl_a_00041/43452/Data-Statements-for-Natural-Language-Processing

* [AI to reduce medical disparities] Chen, Irene Y., Peter Szolovits, and Marzyeh Ghassemi. "Can AI help reduce disparities in general medical and mental health care?." AMA journal of ethics 21, no. 2 (2019): 167-179. https://journalofethics.ama-assn.org/article/can-ai-help-reduce-disparities-general-medical-and-mental-health-care/2019-02

## Artículos:

No hubo bibliografía de los libros de siempre, sino artículos

* Nature. AI can be sexist and racist — it’s time to make it fair.
	* https://www.nature.com/articles/d41586-018-05707-8
* Datos generados por minuto:
	* https://techstartups.com/2018/05/21/how-much-data-do-we-create-every-day-infographic/
* De los estantes muy altos a la mayor probabilidad de morir en un choque (...).
	* https://www.infobae.com/america/mundo/2019/03/02/de-los-estantes-muy-altos-a-la-mayorprobabilidad-de-morir-en-un-choque-el-mundo-medido-para-los-hombres-pone-en-peligro-a-lasmujeres/ht
* Gender in the world of science https://www.nytimes.com/paidpost/lorealfondation/gender-in-the-world-of-science.html


# Conversaciones clase previa

Definir problema, métrica y error- Pequeña reflexión sobre definicion de problema, como medirlo, y algunas cositas así. 

Intro a lo que viene, sesgo. Discusión sobre que es un sesgo. Por ejemplo, raza en los jucios (Las personas negras son más acusadas, las personas transmiten su sesgo, si alimentamos el algoritmo con esos datos, el algoritmo se sesga). Otro en NLP se podría neutralizar el genero en algunas palabras. 

Sesgo por los datos (Alimento el algoritmo con datos sesgados)
Sesgo 'natural' (Hay casos donde la condicion de una persona puede ser una feature)
Sesgo 'artificial' (Muestra desbalanceadas)

Conocimiento experto ayuda a identificar y minimizar sesgos.

--------------------------

Interpretabilidad del algoritmo puede ser importante. En algunos casos necesitas poder explicarlo.



-- Refuerzo
Mitchell cap 13
apaydin 19
reinforcement learning. an introduction. Sutton. Barto
Algorithms for reinforcement learning. SZepesvary 
curso ucl reinforcement learning david silver
cs229 stanford andrew ng










