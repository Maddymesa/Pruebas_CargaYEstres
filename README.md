# Pruebas_CargaYEstres
Repositorio para pruebas de carga y estrés en jMeter

Conclusiones y Recomendaciones para el Servicio de Consulta de Guía
1. Análisis de Resultados

--- A partir de las gráficas obtenidas en la prueba de carga, se pueden analizar las siguientes conclusiones:

* Tiempo de Respuesta Promedio: 470 ms, lo que se encuentra dentro del umbral esperado (≤ 500 ms).
* Mediana del Tiempo de Respuesta: 346 ms, lo que indica que la mayoría de las solicitudes están por debajo de la media.
* Máximo Tiempo de Respuesta: 1010 ms, lo que sugiere que hay algunas solicitudes que tardan más de 1 segundo, lo que puede afectar la experiencia del usuario en casos específicos.
* Desviación Estándar: 270 ms, lo que indica una variabilidad en los tiempos de respuesta, aunque no es excesiva.
Percentiles:
90% de las solicitudes tardan hasta 973 ms.
95% de las solicitudes tardan hasta 978 ms.
99% de las solicitudes tardan hasta 1007 ms.
Estos datos indican que, aunque el tiempo promedio de respuesta cumple con el objetivo, hay casos extremos donde algunas solicitudes tardan más de lo ideal.

2) Recomendaciones generales para mejorar la estabilidad y confiabilidad del servicio de consulta de guía, se sugieren las siguientes acciones:
* Optimización del Backend, y revisar consultas a la base de datos u optimizar índices si es necesario.
* Tambièn implementar almacenamiento en caché para reducir la latencia en respuestas repetidas y mejorar la eficiencia del código backend para reducir los tiempos de procesamiento.
* Escalabilidad: Evaluar el rendimiento del servidor bajo carga y considerar el escalado horizontal (más instancias de servidores) o vertical (más recursos en el servidor).
* Implementar balanceo de carga para distribuir mejor las solicitudes y evitar picos de latencia.

--- A partir de las gráficas obtenidas en la prueba de estres, se pueden extraer tambièn las siguientes conclusiones:
De acuerdo a los datos o puntos clave de la prueba y usando las siguientes cantidades, se observa:

Usuarios concurrentes máximos en prueba: 400
Rendimiento alcanzado: 228.5 solicitudes/segundo
Tiempo de respuesta percentil 99: 4252 ms (4.2 s)
Tiempo máximo de respuesta: 5371 ms (5.3 s)
Errores: 0% (hasta 400 usuarios)
Duración de la prueba: 60 segundos

Se realiza una proyección del lìmite de usuarios, de acueerdo a los resultados y basàndonos en la tendencia de los tiempos de respuesta, podemos estimar el punto en el que el sistema podría volverse inestable:

1) Tiempo de respuesta p99 vs carga: Actualmente, con 400 usuarios, el p99 es de 4.2 s, sì el crecimiento es lineal, al llegar a 600-700 usuarios, el p99 podría superar los 6-7 s, lo que degradaría la experiencia del usuario.

2) Capacidad de solicitudes por segundo: Actualmente, el sistema procesa 228.5 req/seg con 400 usuarios. Si esto escala linealmente, con 600 usuarios, el sistema podría manejar 342 solicitudes/seg, pero con latencias aún mayores. Sì la infraestructura no soporta más carga, las solicitudes podrían empezar a acumularse o fallar.

3) Estimación del lìmite màximo de solicitudes: Un límite aproximado estaría en 700-900 usuarios concurrentes, momento en el cual los tiempos de respuesta probablemente superen los 10s, afectando gravemente la experiencia y pudiendo causar fallos en la aplicación o timeouts y por ende mala experiencia de ususario y afectaciòn de la imagen de la marca.
