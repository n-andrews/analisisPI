## Análisis de muestra PI

Objetivo: Obtener el error muestral, el valor máximo posible de los factores emocionales, y el valor máximo empírico de los subfactores necesarios para calcular el IE con el fin de representar estos valores de acuerdo a un porcentaje.

### Método

Para cumplir con el objetivo, se busca encontrar un valor referencial del máximo de las métricas para poder representar los valores con respecto a un porcentaje, además, se conoce que el valor mínimo es 0. Para esto se utilizó el siguiente método:
1. Debido a que el máximo teórico no está definido ya que según las limitaciones y alcances del software, es posible agregar nuevas palabras al diccionario y asignarles valores distintos, por lo tanto, se utilizó una aproximación empírica que nos permite obtener este valor bajo un margen de error. _(el error de esta aproximación se encuentra en sample_error.xlsx)_ 
2. Se utilizaron 2 métricas significativas del máximo (es decir, para utilizar de referencia como el 100%). La primera corresponde a tomar el bigote superior de un gráfico de caja (máximo IQR), y la segunda corresponde la máximo de la muestra (máximo empírico).
3. Sobre el procesamiento de los datos, para cada uno de las fuentes se corrió un algoritmo que removía el campo "content" (ya que no era necesario) y seleccionaba los valores máximos según el factor emocional destacado (ej. asertividad, comunicación asertiva, empatía, etc...), en efecto, sacaba el valor máximo de cada columna y lo guardaba en un dataframe para luego ser exportado a un archivo excel.
4. Finalmente se calcularon los valores relevantes (AE, CE, CS y RS) para luego determinar un IE de acuerdo a los máximos obtenidos. Donde los valores propuestos se encuentran en el archivo _maximo_e.xlsx_ separados por fuente.

### Notas relevantes

* Justificación de las 2 métricas: Ambas métricas nos dan información importante de los datos utilizados, sin embargo, los valores extremos podrían enturbiar el % máximo, dejando todos los valores represntados en el algoritmo nunca cercanos al 100% (ya que la diferencai entre el máximo IQR y el máximo empírico puede ser extremadamente grande), siendo que el método del rango iqr representa el 99.3% de los datos según la muestra. https://en.wikipedia.org/wiki/Interquartile_range (ver imagen) 

* Justificación del algoritmo: Se decidió primero tomar el valor máximo de los factores y luego calcular el valor de las métricas (AE, CE, CS, RS e IE) ya que estas formulas corresponden al promedio de los factores emocionales, por lo tanto, se pierde una gran cantidad de información al pasar de 17 factores emocionales a solo 4, lo cual podría hacer que el valor de los máximos sea bajo en comparación al resto de las fuentes. Esto casuaría que la información presentada sobre las fuentes tenga valores muy cercanos entre sí.

* Recomendación: Dependiendo de la cantidad de outliers estimada en la basedatos se recomienda utilizar la métrica correspondiente.

#### Archivos

- _maximos_e.xlsx_ \- Contiene el resúmen de los datos obtenidos.
- _carpeta "json"_ \- Input de datos en formato JSON(v1 y v2)
- _carpeta "csv"_ \- Input de datos en formato CSV (v1 y v2)
- _maximos.xlsx_ \- Contiene los valores obtenidos del programa en la hoja "maximos" 
- _sample_error.xlsx_ \- Contiene el error muestral obtenido según los csv extraídos 
- _analisisPI.ipynb_ \- Python notebook con el procesamiento de la información

#### Autores
- Equipo de trabajo GPI Análisis 2020-2
