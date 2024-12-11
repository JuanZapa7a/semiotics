# QAT

Mi idea es continuar por esta línea. Por ejemplo (y te lo pongo en pasos)


- Instalación de Larq y dependencias necesarias.
- Preparación de datos (MNIST).
- Creación de un modelo base (sin cuantización).
- Entrenamiento y evaluación del modelo base.
- Creación de un modelo cuantizado con QAT.
- Entrenamiento y evaluación del modelo cuantizado.
- Comparación de rendimiento y tamaño del modelo.



Cuando sepa hacer esto (creo que ya está hecho, ¿no?, pero permíteme que lo haga yo a mi manera que me aclaro mejor.)


Una vez hecho esto, vendría la parte desconocida, he pensado:


1. Añadir ruido gaussiano al la salida de alguna/todas capa durante el entrenamiento. La idea es que el ruido ayude a generalizar el modelo y que se adapte a las perturbaciones. ***`El ruido no ayuda a generalizar`***


2. Las variaciones de proceso CMOS (corrígeme si me equivoco) pueden cambiar los parámetros de los transistores, afectando el comportamiento de las operaciones aritméticas. Esto podría modelarse como una desviación en los pesos del modelo. Se simula una variación de proceso aplicando una pequeña desviación a los pesos de la capa lineal. Esto ayuda a entrenar el modelo para ser más robusto frente a variaciones de fabricación del hardware. Si te das ciuenta no me meto en la CNN. Poco a poco.


3. No linealidades. En hardware real, las operaciones aritméticas pueden saturarse o recortarse debido a limitaciones en el rango de los valores que se pueden representar. Por ejemplo, un multiplicador de 8 bits puede saturar cuando el resultado excede los límites de 0 a 255. Para simularlo supongo que hay que saturar los valores de la salida y se entrena el modelo con esta saturación a ver como responde.



Bueno, son ideas que no sé si podré hacer, pero vamos lo intento si te parece bien. Creo que la parte primera de larq (Comparación de rendimiento y tamaño del modelo normal vs. cuantizado.) debe ser asequible (creo), del resto ya te iré contando.



Ya me cuentas lo que te parece. Intentaré trabajar al menos una mañana a la semana sobre esto.


Saludos


Archivos creados:

1. Cifar.ipynb (**11 november**) --> `INTRODUCTION TO BNNs WITH LARQ`: A simple CNN binarized vs CNN to classify MNIST.
2. Larq1.ipynb (**11 november**) --> `Pasos para Implementar y Comparar VGG8 Normal vs. Hardware-Aware en Larq`: 1er intento. Dejado sin entrenar.
3. mnist_with_larq.ipynb (**12 noviembre**) -->  `Quantization Aware Training (QAT) using Larq for 4-bit quantization with the MNIST dataset`: A simple CNN binarized to classify MNIST (no 4 bits).
4. mnist.ipynb (**12 noviembre**): --> `Quantization Aware Training (QAT) using Larq for binarized quantization with the MNIST dataset`: A simple CNN binarized vs CNN to classify MNIST - *Comparison of Model Size, Performance, and Speed*.
5. QAT_MNIST.ipynb (**12 noviembre**) --> `Quantization Aware Training (QAT) using Larq for binarized quantization with the MNIST`
6. QAT_CIFAR10.ipynb (**20 noviembre**) --> `Quantization Aware Training (QAT) using Larq for binarized quantization with the CIFAR10 dataset`: A simple CNN binarized vs CNN to classify CIFAR10 - *Comparison of Model Size, Performance, and Speed*.
7. QAT_MNIST_NOISY.ipynb (**25 noviembre**) --> `Quantization Aware Training (QAT) using Larq for a noisy binarized quantization with the CIFAR10 dataset`: `NoisyLayer` wraps `QuantConv2D` and `QuantDense`. Noise is considered Gaussian (most comun noise soruces in hardware like thermal and electronic noise assumed Gaussian noises)
8. QAT_MNIST_NOISY.ipynb (**10 diciembre**) 

Este último archivo es el comienzo de ampliaciones buscando simular ademas del ruido las perturbaciones CMOS. 