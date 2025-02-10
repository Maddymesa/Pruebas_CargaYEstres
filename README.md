# Pruebas_CargaYEstres
Repositorio para pruebas de carga y estrés en jMeter

Conclusiones y Recomendaciones para el Servicio de Consulta de Guía
1. Análisis de Resultados

A partir de las gráficas obtenidas en la prueba de carga, se pueden extraer las siguientes conclusiones:

Tiempo de Respuesta Promedio: 470 ms, lo que se encuentra dentro del umbral esperado (≤ 500 ms).
Mediana del Tiempo de Respuesta: 346 ms, lo que indica que la mayoría de las solicitudes están por debajo de la media.
Máximo Tiempo de Respuesta: 1010 ms, lo que sugiere que hay algunas solicitudes que tardan más de 1 segundo, lo que puede afectar la experiencia del usuario en casos específicos.
Desviación Estándar: 270 ms, lo que indica una variabilidad en los tiempos de respuesta, aunque no es excesiva.
Percentiles:
90% de las solicitudes tardan hasta 973 ms.
95% de las solicitudes tardan hasta 978 ms.
99% de las solicitudes tardan hasta 1007 ms.
Estos datos indican que, aunque el tiempo promedio de respuesta cumple con el objetivo, hay casos extremos donde algunas solicitudes tardan más de lo ideal.

2. Recomendaciones

Para mejorar la estabilidad y confiabilidad del servicio de consulta de guía, se sugieren las siguientes acciones:

Optimización del Backend:
Revisar consultas a la base de datos y optimizar índices si es necesario.
Implementar almacenamiento en caché para reducir la latencia en respuestas repetidas.
Mejorar la eficiencia del código backend para reducir los tiempos de procesamiento.
Escalabilidad:
Evaluar el rendimiento del servidor bajo carga y considerar el escalado horizontal (más instancias de servidores) o vertical (más recursos en el servidor).
Implementar balanceo de carga para distribuir mejor las solicitudes y evitar picos de latencia.
