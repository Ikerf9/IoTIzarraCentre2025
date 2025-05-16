# Grupo 6

## Integrantes
- [Sergio Lopez]
- [Erik Montero]
- [Mikel Perez]
- [Ignacio Arrizabalaga]
- [Iker Fariñas]

## Descripción del Proyecto
[Breve descripción del proyecto que desarrollarán]

## Visualización
En este proyecto hemos utilizado la placa ESP32-WROOM-32D para captar datos y enviarlos mediante peticiones HTTP hacia un servidor local donde empleamos Node-RED como intermediario. Node-RED recibe las solicitudes a través de una ruta específica (/grupo6) y redirige los datos a una base de datos InfluxDB, donde se almacenan con marcas de tiempo para su posterior análisis. En la captura de pantalla de Node-RED se puede observar un flujo en el que el nodo [GET] /grupo6 recibe las peticiones del ESP32, las envía a un nodo denominado localhost (que representa la conexión o tratamiento local de los datos), y finalmente se responde al dispositivo con un estado HTTP 200 mediante el nodo http response. Una vez almacenados los datos en InfluxDB, utilizamos Grafana para visualizarlos gráficamente mediante paneles personalizados, lo que nos permite monitorear en tiempo real las variables enviadas por el ESP32.

En este proyecto recibimos datos procedentes de un sensor de luz conectado a una placa ESP32-WROOM-32D. Estos datos se envían de forma periódica al servidor, donde son gestionados por Node-RED y almacenados en una base de datos InfluxDB. Desde allí, realizamos consultas (querys) directamente en Grafana para representar de manera simulada los valores del sensor de luz en tiempo real. Gracias a las capacidades de visualización de Grafana y la estructura temporal de InfluxDB, podemos observar cómo varía la intensidad lumínica a lo largo del tiempo mediante gráficas dinámicas, simulando así el comportamiento del entorno captado por el sensor.






## Uso
[Instrucciones de uso] 
