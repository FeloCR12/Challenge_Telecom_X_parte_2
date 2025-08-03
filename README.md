# Challenge_Telecom_X_parte_2
Creación de modelos predictivos para identificar qué clientes tienen mayor probabilidad de cancelar sus servicios.

Los pirncipales objetivos del proyecto son: 

- Preparar los datos para el modelado (tratamiento, codificación, normalización).
- Realizar análisis de correlación y selección de variables.
- Entrenar dos o más modelos de clasificación.
- Evaluar el rendimiento de los modelos con métricas.
- Interpretar los resultados, incluyendo la importancia de las variables.
- Crear una conclusión estratégica señalando los principales factores que influyen en la cancelación.

Desarrollo de Modelos Predictivos para Predecir la Cancelación de Clientes
Con base en un conjunto histórico de datos de clientes de la empresa TelecomX, que incluía 7,267 registros y 31 variables, se planteó el desarrollo de un modelo predictivo con el objetivo de identificar qué clientes tienen una mayor probabilidad de cancelar sus servicios en el futuro.
1. Preparación y limpieza de los datos
Como primer paso, se realizó una depuración del conjunto de datos. Se identificaron 224 registros sin información en la variable objetivo (“¿Dejó la empresa?”), por lo que dichos registros fueron eliminados para evitar distorsiones en el análisis.
Posteriormente, se llevó a cabo un análisis de correlación entre variables, con el fin de identificar redundancias y relaciones fuertes que permitieran simplificar la base sin pérdida significativa de información. Entre las variables evaluadas destacan:
•	¿Dejó la empresa? (cancelación)
•	Total de suscripciones
•	Cuentas diarias
•	Cargos mensuales
•	Cargos totales
•	Meses de contrato
•	¿Tiene pareja?
•	¿Tiene dependientes?
•	Género
A partir del análisis de correlaciones:


	Charges.Total	Total_suscripciones	Charges.Monthly	Cuentas_Diarias
Charges.Total	1.000000	0.745065	0.650864	0.650864
Total_suscripciones	0.745065	1.000000	0.822187	0.822187
Charges.Monthly	0.650864	0.822187	1.000000	1.000000
Cuentas_Diarias	0.650864	0.822187	1.000000	1.000000
 
<img width="333" height="221" alt="image" src="https://github.com/user-attachments/assets/f18c975f-5f2c-4ea8-b64c-391097d614e9" />

Se decidió eliminar las variables Cuentas Diarias y Cargos Mensuales por su alta correlación con Cargos Totales, lo cual evitó multicolinealidad. Asimismo, se descartaron columnas binarias que indicaban si el cliente tenía ciertos servicios, ya que esta información estaba duplicada en las variables numéricas de suscripciones. Como resultado, la base fue optimizada a un total de 19 variables.
2. Análisis del balance de clases
Se analizó la distribución de la variable objetivo, encontrando un desbalance significativo entre clientes que cancelaron y los que no. Para mitigar este problema y mejorar el rendimiento del modelo, se optó por igualar el número de observaciones de ambas clases, ajustando a la clase minoritaria y evitando generar registros sintéticos.

 <img width="333" height="206" alt="image" src="https://github.com/user-attachments/assets/1294289e-72f7-4578-a658-3c9d0a166f26" />


3. Modelo Random Forest
   
Una vez preprocesados los datos, se entrenó un modelo basado en Random Forest, obteniendo los siguientes resultados promedio tras validación cruzada:
•	Accuracy: 0.6904
•	Precision: 0.6773
•	Recall: 0.7254
•	F1 Score: 0.7005
Estos resultados indican un buen desempeño general del modelo, con especial fortaleza en la capacidad de detección de clientes que efectivamente cancelan (recall).
También se desarrolló la matriz de confusión 
 
<img width="317" height="257" alt="image" src="https://github.com/user-attachments/assets/9fe82cf4-e94e-45a8-a504-548ff577a017" />

4. Modelo K-Nearest Neighbors (KNN)
   
Posteriormente se implementó un segundo modelo, K-Nearest Neighbors (KNN), el cual requiere normalización de las variables. Tras aplicar la técnica de escalamiento y entrenar el modelo, se obtuvieron los siguientes resultados:
•	Accuracy: 0.6320
•	Precision: 0.6270
•	Recall: 0.6505
•	F1 Score: 0.6384

De igual forma se desarrolló la Matriz de confusión 

<img width="321" height="260" alt="image" src="https://github.com/user-attachments/assets/fe60615c-8e20-489d-a61a-6c6f2b42cd40" />

 
Aunque el desempeño del modelo KNN fue aceptable, sus métricas fueron inferiores a las obtenidas con Random Forest.

5. Comparación entre modelos
   
Métrica	Random Forest 	KNN
Accuracy	0.6904	0.6320
Precision	0.6773	0.6270
Recall	0.7254	0.6505
F1 Score	0.7005	0.6384

6. Conclusiones:
   
•	Random Forest superó a KNN en todas las métricas evaluadas, por lo que se recomienda como modelo principal para implementar en la empresa.
•	El Recall del modelo Random Forest (0.7254) indica una mayor capacidad para identificar correctamente a los clientes que efectivamente cancelan.
•	La métrica F1 Score también fue más alta y equilibrada en Random Forest, lo que sugiere un mejor balance entre falsos positivos y falsos negativos.
•	Aunque KNN puede ser útil como modelo base o de comparación, su rendimiento fue inferior al menos en un 5% en todas las métricas clave.

7. Recomendaciones
   
A partir de los hallazgos obtenidos en el análisis exploratorio y el desarrollo de modelos predictivos, se proponen las siguientes estrategias para mejorar la retención de clientes en la empresa TelecomX:
•	Implementar el modelo Random Forest como herramienta predictiva:
Dado su superior desempeño en todas las métricas clave (Accuracy, Precision, Recall y F1 Score), se recomienda utilizar el modelo de Random Forest como base para identificar a los clientes con mayor probabilidad de cancelar sus servicios. Esta herramienta permitirá a la empresa tomar decisiones más informadas, proactivas y focalizadas, mejorando la efectividad de las estrategias de fidelización.
•	Ofertas personalizadas para clientes sin dependientes:
El análisis demostró que los clientes sin dependientes presentan una mayor tendencia a cancelar. Por lo tanto, se sugiere desarrollar paquetes exclusivos y personalizados para este segmento, que ofrezcan beneficios diferenciados y mayor valor percibido, alineados con su perfil y necesidades.
•	Fomento de paquetes combinados de servicios:
Se identificó una relación positiva entre la cantidad de servicios contratados y la permanencia del cliente. En consecuencia, se recomienda incentivar la contratación de combos o paquetes de servicios con precios preferenciales y beneficios escalables a medida que se contraten más servicios.
•	Optimización e incentivo del uso de métodos de pago automáticos:
Mejorar la experiencia de pago también puede impactar la permanencia del cliente. Se propone promover el uso de métodos de pago automáticos (como tarjetas de crédito o débitos directos), ofreciendo a cambio beneficios tangibles, como acumulación de puntos, descuentos o facilidad en la gestión de pagos.
•	Promoción de contratos de mayor duración:
Para reducir la rotación, se recomienda fomentar la contratación de planes semestrales o anuales, apoyándose en incentivos como descuentos por fidelidad, promociones especiales o regalos vinculados a los servicios adquiridos.


