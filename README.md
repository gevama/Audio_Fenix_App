# Audio_Fenix_App

## Indice

1. [Introducción](#introduccion)
2. [Departamento de Algoritmos de Audio](#algoritmo)
3. [Software & librerias utilizadas](#software)
4. [Datasets](#datasets)
    1. [ESC50](#ESC50)
    2. [Kaggle Dataset](#kaggledataset)
5. [Proceso](#proceso)
    1. [Ventanas](#window)
    2. [Espectrogramas](#spectrograms)
6. [Resultados](#resultados)
7. [Paper](#paper)


## Introducción <a name="introduccion"></a>

Debido a la situación provocada por el coronavirus en prácticamente todo el planeta. Nos encontramos en un punto en el cual la velocidad de propagación del virus se está produciendo de manera exponencial. 

Para ello Fenix propone una App que pueda ayudar a prevenir la enfermedad y dotar de información en tiempo real tanto a usuarios como a organismos sanitarios para poder tomar decisiones efectivas. Sus características son las siguientes: 

Predicción del estado de Salud: Mostrando sintomático, asintomático y sano.
Trackeo en tiempo real de los usuarios mediante la geolocalización. 
Histórico de trazabilidad del usuario.
Detección de tipos de sonidos.
Análisis de datos en tiempo real.
Nuestro rol dentro del proyecto que gira en torno al Hackathon 4 y el desarrollo de la aplicación FENIX estaba encuadrado dentro del departamento de Imagen donde nos hemos encargado del desarrollo de los algoritmos de imagen que van a formar parte de la aplicación final. 



## Departamento de Algoritmos de Audio <a name="algoritmo"></a>

Para llevar a cabo el desarrollo de un algoritmo de audio se ha contando para el departamento de audio con la empresa de Audio Consulting. Gracias a su experiencia en este tipo de proyectos se va a desarrollar un modelo que permita clasificar los sonidos de modo que se pueda reconocer la tost mediante la recogida de audios. 
El objetivo es poder transformar estos datos para ponerlos a disposición de su tratamiento para evaluar frecuencia y situaciones puntuales. El tratamiento del algortimo permite extraer un dataset que informe sobre la fecha, la hora y si se ha producido tos. 

Para más información se puede consultar la [Presentación del proyecto](https://github.com/gevama/Audio_Fenix_App/blob/master/4.%20Data%20example/Presentacio%CC%81n_DP4.pdf).

![image](https://github.com/gevama/Audio_Fenix_App/blob/master/4.%20Data%20example/Portada_presentacio%CC%81n.png)

## Software & librerias utilizadas <a name="software"></a>

* **Tensor Flow** : Biblioteca de Machine Learning
* **Keras** : Biblioteca de Redes Neuronales
* [Pydub](https://github.com/jiaaro/pydub): Biblioteca desarrollada para la modificación de archivos de audio
* [Librosa](https://github.com/librosa/librosa): Biblioteca desarrollada el análisis de música y audio en general
* [Modelo](https://storage.cloud.google.com/hackathon_4_audio/MixV1_New_Densenet201_stft_weights.best.hdf5): Pincha en el enlace para descargar el modelo. 

## Datasets <a name="datasets"></a>

Durante el desarrollo del proyecto hemos utilizado dos datasets públicos, creados para cubrir las necesidades de aquellos problemas relacionados con sonido ambiente:

### ESC50 <a name="ESC50"></a>

El ESC50 corresponde al conjunto de datos Clasificación de sonido ambiental (ESC), que fue lanzado por Piczak en 2015. Dicho conjunto contiene 2.000 clips de audio de 5 segundos de duración, divididos por igual en 50 categorías. Para este caso de uso se trabaja con 13 de ellas, las cuales están estrechamente relacionadas con los sonidos a los que un dispositivo móvil puede estar expuesto en el día a día.

### Kaggle Dataset <a name="kaggledataset"></a>

Por otra parte también se utiliza el Freedsound Dataset Kaggle 2018 (o FSDKaggle2018 para abreviar). Este conjunto de datos de audio contiene 11,073 archivos anotados con 41 etiquetas. Este conjunto de datos se usó originalmente para un desafío en la detección y clasificación de escenas y eventos acústicos (DCASE) en 2018. En este conjunto de datos también se seleccionan aquellas categorías o etiquetas de sonido que coinciden con nuestro caso de uso. De esta forma nos quedamos sólo con 17 categorías.

Accede al siguiente link para obtener un ejemplo de audio: [Audio_Ejemplo](https://drive.google.com/file/d/1saZQI0pY8eFjmyBZcsIdXGD9xkRL89Cx/view)

## Proceso<a name="proceso"></a>

A continuación se muestra un diagrama del proceso de clasificación de sonidos:

![image](https://github.com/gevama/Audio_Fenix_App/blob/master/4.%20Data%20example/Work_flow_DP4.jpeg)

### Ventanas<a name="window"></a>

Con el fin de poder realizar un análisis completo del sonido, se divide el audio en ventanas que permitan estudiar todo el contenido del mismo sin perder información. Para ello se define la duración de las ventanas y el salto que deben tomar las ventanas hasta recorrer todo el audio por completo.

### Espectrogramas<a name="spectrograms"></a>

El preprocesamiento implica la transformación de nuestros archivos de audio en datos que nuestro modelo pueda utilizar para hacer predicciones. Para hacerlo, necesitamos transformar el audio en imágenes, y para ello utilizamos los espectrogramas. Dichos espectrogramas se generan utilizando el paquete Librosa aplicando un banco de filtros de mel al espectro de magnitud de cada segmento y luego tomando su logaritmo.
En nuestra configuración, aplicamos tareas simultáneas, así que a medida que generamos nuestros espectrogramas, también aplicamos nuestra división de datos para capacitación y validación, lo que nos da como resultado que nuestros espectrogramas se guardan en directorios de entrenamiento y prueba y están listos para ser procesados ​​por nuestro modelo.

![gif](https://github.com/gevama/Audio_Fenix_App/blob/master/4.%20Data%20example/espectrograma.gif)

## Resultados <a name="resultados"></a>

### Accuracy 

| Medida  |    Accuracy    |
| ------------- | ------------- |
| Validation accuracy     |    84,04%    |
| Top 5 Prediction       |    96,17 %    |
| Cough Prediction    |    79,00 %    |

A continuación se puede comprobar el resultado que se obtiene en Google BigQuery.

![image](https://github.com/gevama/Audio_Fenix_App/blob/master/4.%20Data%20example/big_query.jpeg)


## Paper <a name="paper"></a>

Para unificar y completar la información sobre este proyecto se adjuntan un Paper en el cual se muestran más detalles de la arquitectura, conclusiones.

* [Paper_DP4](https://github.com/gevama/Audio_Fenix_App/blob/master/4.%20Data%20example/Paper_DP4.pdf)


![image](https://github.com/gevama/Audio_Fenix_App/blob/master/4.%20Data%20example/Image_abstract.png)

