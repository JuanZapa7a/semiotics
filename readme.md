Mi idea es continuar por esta línea. Por ejemplo (y te lo pongo en pasos)


Instalación de Larq y dependencias necesarias.
Preparación de datos (MNIST).
Creación de un modelo base (sin cuantización).
Entrenamiento y evaluación del modelo base.
Creación de un modelo cuantizado con QAT.
Entrenamiento y evaluación del modelo cuantizado.
Comparación de rendimiento y tamaño del modelo.



Cuando sepa hacer esto (creo que ya está hecho, ¿no?, pero permíteme que lo haga yo a mi manera que me aclaro mejor.)


Una vez hecho esto, vendría la parte desconocida, he pensado:


1. añadir ruido gaussiano al la salida de alguna capa durante el entrenamiento. La idea es que el ruido ayude a generalizar el modelo y que se adapte a las perturbaciones.


2. Las variaciones de proceso CMOS (corrígeme si me equivoco) pueden cambiar los parámetros de los transistores, afectando el comportamiento de las operaciones aritméticas. Esto podría modelarse como una desviación en los pesos del modelo. Se simula una variación de proceso aplicando una pequeña desviación a los pesos de la capa lineal. Esto ayuda a entrenar el modelo para ser más robusto frente a variaciones de fabricación del hardware. Si te das ciuenta no me meto en la CNN. Poco a poco.


3. No linealidades. En hardware real, las operaciones aritméticas pueden saturarse o recortarse debido a limitaciones en el rango de los valores que se pueden representar. Por ejemplo, un multiplicador de 8 bits puede saturar cuando el resultado excede los límites de 0 a 255. Para simularlo supongo que hay que saturar los valores de la salida y se entrena el modelo con esta saturación a ver como responde.



Bueno, son ideas que no sé si podré hacer, pero vamos lo intento si te parece bien. Creo que la parte primera de larq (Comparación de rendimiento y tamaño del modelo normal vs. cuantizado.) debe ser asequible (creo), del resto ya te iré contando.



Ya me cuentas lo que te parece. Intentaré trabajar al menos una mañana a la semana sobre esto.


Saludos


