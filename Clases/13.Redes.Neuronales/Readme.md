# Redes neuronales artificiales (RNA -RN, ANN, NN-)

* Aprendizaje supervisado
	* Perceptrón simple
	* Redes feedforward multicapa
* Aprendizaje no supervisado
	* Aprendizaje Hebbiano
	* Aprendizaje Competitivo
	* Mapas Auto-Organizados

Están inspiradas en el modelo biológico de neurona. 
* Neurona como la unidad básica de procesamiento de información de una red neuronal
* El modelo matemático está dado por:
	* Conjunto de conexiones con pesos asociados
	* Una señal conectada a una neurona multiplicada por un peso
	* Sumador de señales de entrada pesadas por la sinápsis, arroja una combinación lineal de las entradas
	* Una función de activación que limita la amplitud de salida de una neurona
	* Un umbral para variar la actividad de la neurona
	* (Ref: Ppt página 5)

Unidades de procsamiento sencillas que operan en paralelo (Hace que sean más robusto)
* Canal de entrada
* Procesador
* Canal de salida

El **perceptrón** simple resuelve problemas linealmente separables. Funciona por ejemplo para un and/or/not y no para un xor.
* Funciones de activación:
	* Sigmoid -> 1 / (1 + e ^ -z)
	* Tanh => (e^x - e^-x) / (e^x + e^-x)
	* Lineal => s(x) = x
	* Relu => a = max(O, z)
	* Leaky ReLU => a = max(0.01 z, z)
	* Ref: ppt 8, funciones de activación y gráficas
	* Cada función tiene su utilidad y problemas donde funciona mejor.

**Arquitecturas** 
Si la red neuronal es muy chiquita podría parecerse a una regresión lineal, o funciones de Machine learning que ya existian.

Estándares
* Feed forward
* Perceptrón mutilcapa
* Conexión total

Profundas:
* Convolutional Neural Networks (CNN) -> Imágenes
	* Invarianza a la traslación (Por parameter sharing)
	* Campo receptivo (Toma zonas)
	* ref: https://towardsdatascience.com/a-simple-cnn-multi-image-classifier-31c463324fa
	* Opciones?
		* Pooling (Juntan la matriz esa que va convolucionando)
		* Convolución
	* Tienden a armarse capas de redes convolucionales, capas de pooling
* Recurrent Neural Networks (RNN) -> Texto, habla
	* https://towardsdatascience.com/recurrent-neural-networks-rnns-3f06d7653a85
	* http://karpathy.github.io/2015/05/21/rnn-effectiveness/
* Long Short-term Memory

* Híbridas

Vienen pegando cada vez más, porque cada vez más datos, cada vez mpas poder de cómputo, y algunos cambios en algoritmos (Por ejemplo ReLU). En los últimos años ha habido varios avances.

## Regresion logística como red neuronal

**tbd** que onda esto?

## Parámetros de una red neuronal

* Función de activación (Relacionada con los valores que esperamos de salida)
	- Cual es mejor? Es heurístico, pero si hay algunas propiedades.
	- Para regresiones queremos devolver una probabilidad, pero generalmente son probabilidades excluyentes (Si los datos no pueden tener más de una etiqueta)
		- Softmax - Regresión logistica multinominal
* Inicialización de pesos
* Cantidad de capas ocultas
	- Muchas en serie o pocas capas
	- En teoria con dos capas puede aproximar cualquier cosa
	- Una red muy profunda anda mejor que una sola capa, con menos parametros
		- Porque la capacidad de expresión es mucho mucho mayor
		- Las capas van ayudando a extraer atributos (En lugar de gente experta armando atributos, la red neuronal va abstrayendo conceptos)
* Conexión entre capas
* Tasa de aprendizaje (learning rate)

# Bibliografía
Capítulos de libros:
* Mitchell, cap. 4

Libros enteros:
* Neural Networks. A comprehensive foundation. Haykin
	* https://cdn.preterhuman.net/texts/science_and_technology/artificial_intelligence/Neural%20Networks%20-%20A%20Comprehensive%20Foundation%20-%20Simon%20Haykin.pdf
* Introduction To The Theory Of Neural Computation. Hertz, Krogh, Palmer
	* https://www.researchgate.net/publication/200033871_Introduction_To_The_Theory_Of_Neural_Computation
* Deep Learning. Goodfellow, Bengio, Courville
	* http://www.deeplearningbook.org/

Curso online:
* Neural Networks and Deep Learning. Coursera.
	* https://www.coursera.org/learn/neural-networks-deep-learning/
* Machine Learning. Coursera. Semanas 4 y 5.
	* https://www.coursera.org/learn/machine-learning/home/welcome
* Tensor Flow Playground. 
	* http://playground.tensorflow.org/#activation=tanh&batchSize=10&dataset=circle&regDataset=reg-plane&learningRate=0.03&regularizationRate=0&noise=0&networkShape=4,2&seed=0.20540&showTestData=false&discretize=false&percTrainData=50&x=true&y=true&xTimesY=false&xSquared=false&ySquared=false&cosX=false&sinX=false&cosY=false&sinY=false&collectStats=false&problem=classification&initZero=false&hideText=false
	
	





































































































