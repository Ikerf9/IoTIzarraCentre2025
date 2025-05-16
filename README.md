# Formación IoT

Este repositorio está diseñado para impartir formación práctica en IoT, utilizando dispositivos finales, TTGO con Lora, Arduino y Raspberry Pi. Los ejemplos están estructurados para proporcionar una base sólida en el desarrollo de aplicaciones IoT, permitiendo a los estudiantes aprender y experimentar con diferentes tecnologías y conceptos.

Cada grupo deberá crear una carpeta "Grupo N", donde añadirá toda la información del proyecto. Debe incluir obligatoriamente el decodificador/codificador de Chirpstack y el código necesario para la aplicación.

# Instrucciones para Trabajo en Equipo con Git

## 1. Configuración Inicial (una sola vez)
```bash
# Clonar el repositorio
git clone https://github.com/tuusuario/IoTIzarraCentre2025.git
cd IoTIzarraCentre2025

# Configurar usuario de Git
git config user.name "Tu Nombre"
git config user.email "tu.email@ejemplo.com"
```

## 2. Crear Branch para tu Grupo
```bash
# Crear y cambiar a tu rama
git checkout -b grupo-N  # Donde N es el número de tu grupo
```

## 3. Flujo de Trabajo Diario
```bash
# 1. Actualizar tu rama con los últimos cambios
git checkout main
git pull origin main
git checkout grupo-N
git merge main

# 2. Realizar tus cambios en la carpeta de tu grupo
# Grupos/Grupo N/...

# 3. Añadir y commitear cambios
git add Grupos/Grupo\ N/
git commit -m "Descripción clara del cambio"

# 4. Subir cambios a GitHub
git push origin grupo-N
```

## 4. Visdualización
En este proyecto hemos utilizado la placa ESP32-WROOM-32D para captar datos y enviarlos mediante peticiones HTTP hacia un servidor local donde empleamos Node-RED como intermediario. Node-RED recibe las solicitudes a través de una ruta específica (/grupo6) y redirige los datos a una base de datos InfluxDB, donde se almacenan con marcas de tiempo para su posterior análisis. En la captura de pantalla de Node-RED se puede observar un flujo en el que el nodo [GET] /grupo6 recibe las peticiones del ESP32, las envía a un nodo denominado localhost (que representa la conexión o tratamiento local de los datos), y finalmente se responde al dispositivo con un estado HTTP 200 mediante el nodo http response. Una vez almacenados los datos en InfluxDB, utilizamos Grafana para visualizarlos gráficamente mediante paneles personalizados, lo que nos permite monitorear en tiempo real las variables enviadas por el ESP32.

En este proyecto recibimos datos procedentes de un sensor de luz conectado a una placa ESP32-WROOM-32D. Estos datos se envían de forma periódica al servidor, donde son gestionados por Node-RED y almacenados en una base de datos InfluxDB. Desde allí, realizamos consultas (querys) directamente en Grafana para representar de manera simulada los valores del sensor de luz en tiempo real. Gracias a las capacidades de visualización de Grafana y la estructura temporal de InfluxDB, podemos observar cómo varía la intensidad lumínica a lo largo del tiempo mediante gráficas dinámicas, simulando así el comportamiento del entorno captado por el sensor.

## 🌟 Características

- Ejemplos básicos y avanzados para Arduino
- Ejemplos básicos y avanzados para Raspberry Pi
- Comunicación MQTT, HTTP y WebSockets
- Sensores de temperatura, humedad, movimiento y luz
- Comunicación LoRa y WiFi
- Control de LEDs y GPIO
- Timers y triggers
- Almacenamiento de datos en bases de datos
- Visualización de datos en tiempo real
- APIs RESTful

## 📁 Estructura del Repositorio

```
IoTIzarraCentre2025/
│
├── Ejemplos/
│   ├── Arduino/
│   │   ├── Basico/
│   │   │   ├── Blink_LED/
│   │   │   └── Button_Input/
│   │   ├── Sensores/
│   │   │   ├── DHT11_Temperature/
│   │   │   └── LDR_Light/
│   │   ├── Comunicacion/
│   │   │   ├── MQTT_Publish/
│   │   │   └── LoRa_Communication/
│   │   └── Proyectos/
│   │       └── Weather_Station/
│   │
│   └── RaspberryPi/
│       ├── Basico/
│       │   ├── GPIO_Basics/
│       │   └── Blink_LED/
│       ├── Sensores/
│       │   └── DHT11_Temperature/
│       ├── Comunicacion/
│       │   ├── MQTT_Publish/
│       │   ├── REST_API/
│       │   └── LoRa_Communication/
│       ├── Datos/
│       │   └── SQLite_Storage/
│       ├── Timers_Triggers/
│       │   ├── timer_example.py
│       │   └── trigger_example.py
│       └── Proyectos/
│           ├── Data_Dashboard/
│           └── Home_Security/
│
├── Grupos/
│   └── Grupo 1..N/
│       ├── Chirpstack/
│       └── Aplicacion/
│       └── Readme.md
│
└── docs/
    └── chirpstack/
        ├── configuracion_inicial.md      # Guía de configuración en ChirpStack Ermua
```

## 🛠️ Requisitos Previos

### Para Arduino:
- Arduino IDE instalado
- Bibliotecas necesarias (ver archivo `libraries.txt` en cada proyecto)

### Para Raspberry Pi:
- Python 3.7 o superior
- pip3

Cada proyecto de Raspberry Pi tiene su propio archivo `requirements.txt` con las dependencias específicas necesarias. Los principales tipos de dependencias incluyen:

- **Proyectos Básicos**: RPi.GPIO, schedule
- **Proyectos Web**: Flask, Flask-RESTful, Flask-SocketIO
- **Bases de Datos**: SQLAlchemy, pandas
- **Comunicación**: paho-mqtt, requests
- **Visualización**: plotly, dash
- **Sensores**: Adafruit-DHT, picamera

### Configuración ChirpStack Ermua:
- Credenciales de acceso a ChirpStack
- Información del Gateway de Ermua:
  - Frecuencia: EU868
  - Canales disponibles
  - Configuración regional: EU868

## 📥 Instalación

1. Clona este repositorio:
   ```bash
   git clone https://github.com/tuusuario/IoT-Prototyping-Examples.git
   cd IoT-Prototyping-Examples
   ```

2. Para proyectos de Raspberry Pi, instala las dependencias específicas del proyecto:
   ```bash
   cd ruta/al/proyecto  # Ejemplo: cd Ejemplos/RaspberryPi/Proyectos/Home_Security
   pip install -r requirements.txt
   ```

3. Para proyectos de Arduino:
   - Abre Arduino IDE
   - Ve a `Herramientas > Administrar Bibliotecas...`
   - Instala las bibliotecas listadas en el archivo `libraries.txt` del proyecto

## 🚀 Uso

### Arduino
1. Abre el archivo `.ino` correspondiente en Arduino IDE
2. Selecciona tu placa Arduino
3. Compila y carga el código

### Raspberry Pi
1. Navega al directorio del ejemplo
2. Ejecuta el script Python:
   ```bash
   python3 nombre_del_script.py
   ```

### Creación de un servicio para Raspberry Pi

Para crear un servicio que lance el script Python automáticamente al iniciar el sistema y se reinicie automáticamente a los 30 segundos, sigue los siguientes pasos:

1. Crea un nuevo archivo de servicio en el directorio `/etc/systemd/system/`:
   ```bash
   sudo nano /etc/systemd/system/mi_servicio.service
   ```
2. Añade el siguiente contenido:
   ```
   [Unit]
   Description=Mi Servicio
   After=network.target

   [Service]
   User=pi
   ExecStart=/usr/bin/python3 /ruta/al/script.py
   Restart=always
   RestartSec=30

   [Install]
   WantedBy=multi-user.target
   ```
   Reemplaza `/ruta/al/script.py` con la ruta real del script Python que deseas ejecutar.
3. Guarda y cierra el editor.
4. Recarga la configuración de systemd:
   ```bash
   sudo systemctl daemon-reload
   ```
5. Inicia y habilita el servicio:
   ```bash
   sudo systemctl start mi_servicio
   sudo systemctl enable mi_servicio
   ```

El servicio se iniciará automáticamente al arrancar el sistema y se reiniciará cada 30 segundos si falla.

## 📚 Documentación

Cada carpeta contiene ejemplos específicos con comentarios en el código. Los ejemplos incluyen:

### Ejemplos Básicos
- Control de LED y GPIO
- Lectura de botones y entradas digitales
- Comunicación serial

### Sensores
- Temperatura y humedad (DHT11/DHT22)
- Movimiento (PIR)
- Luz (LDR)
- Cámara (Raspberry Pi Camera)

### Comunicación
- MQTT
- HTTP/REST API
- WebSockets
- LoRa
- WiFi

### Almacenamiento y Visualización
- Base de datos SQLite
- Logging en CSV
- Dashboard web
- Gráficos en tiempo real

### Proyectos Completos
- Estación meteorológica
- Sistema de seguridad
- Jardín inteligente
- Dashboard de datos

## Instalación de Dependencias

### Proyectos Python (Raspberry Pi)

1. Asegúrate de tener Python 3.7 o superior instalado:
   ```bash
   python --version
   ```

2. Instala las dependencias usando pip:
   ```bash
   cd ruta/al/proyecto  # Ejemplo: cd Ejemplos/RaspberryPi/Proyectos/Home_Security
   pip install -r requirements.txt
   ```

### Proyectos Arduino

1. Abre el Arduino IDE
2. Ve a `Herramientas > Administrar Bibliotecas...`
3. Instala las siguientes bibliotecas:

#### Sensores
- DHT sensor library by Adafruit (3.1.0 o superior)
- Adafruit BMP085 Library (1.2.1 o superior)

#### Pantalla LCD
- LiquidCrystal I2C by Frank de Brabander (1.1.2 o superior)

#### Almacenamiento
- SD (incluida en Arduino IDE)
- SPI (incluida en Arduino IDE)

#### WiFi y MQTT
- ESP8266WiFi (2.7.4 o superior)
- PubSubClient by Nick O'Leary (2.8.0 o superior)

#### Utilidades
- ArduinoJson by Benoit Blanchon (6.19.4 o superior)

Nota: Cada proyecto puede requerir un subconjunto específico de estas bibliotecas. Consulta el archivo `libraries.txt` en cada proyecto Arduino para ver las dependencias específicas.

## Ejemplos Disponibles

### Arduino
- **Básico**: Ejemplos fundamentales de Arduino (LED, botones, etc.)
- **Sensores**: Ejemplos de uso de diferentes sensores
- **Comunicación**: Ejemplos de protocolos de comunicación (MQTT, LoRa, etc.)
- **Proyectos**: Proyectos completos (Estación meteorológica, jardín inteligente, etc.)

### Raspberry Pi
- **Básico**: Ejemplos fundamentales de Raspberry Pi (GPIO, etc.)
- **Sensores**: Ejemplos de uso de diferentes sensores
- **Comunicación**: Ejemplos de protocolos de comunicación
- **Proyectos**: Proyectos completos (Sistema de seguridad, dashboard de datos, etc.)


## 🔒 Conexión SSH a Raspberry Pi

### Configuración Inicial

1. Habilitar SSH en la Raspberry Pi:
   ```bash
   sudo raspi-config
   # Ir a Interface Options > SSH > Enable
   ```

2. Encontrar la IP de tu Raspberry Pi:
   ```bash
   hostname -I
   # o
   ip addr show
   ```

### Método con Contraseña

1. Conectar usando el cliente SSH:
   ```bash
   ssh pi@192.168.1.100  # Reemplazar con la IP de tu Raspberry
   ```

### Método con Claves SSH (Recomendado)

1. Generar par de claves con PuTTYgen:
   - Abrir PuTTYgen
   - Clic en "Generate"
   - Mover el ratón para generar aleatoriedad
   - Establecer una passphrase (opcional pero recomendado)
   - Guardar la clave privada (.ppk)
   - Copiar la clave pública (texto que comienza con "ssh-rsa")

2. Configurar la clave en la Raspberry Pi:
   ```bash
   # En la Raspberry Pi
   mkdir -p ~/.ssh
   nano ~/.ssh/authorized_keys
   # Pegar la clave pública y guardar
   chmod 700 ~/.ssh
   chmod 600 ~/.ssh/authorized_keys
   ```

3.1 Conectar usando PuTTY:
   - Abrir PuTTY
   - Introducir la IP de la Raspberry
   - Ir a Connection > SSH > Auth > Credentials
   - Seleccionar la clave privada (.ppk)
   - Guardar la sesión (opcional)
   - Clic en "Open"

3.2 Conectar con PuTTY y Pageant:
   - Abrir Pageant y cargar la clave
   - Abrir PuTTY
   - Introducir la IP de la Raspberry
   - Guardar la sesión (opcional)
   - Clic en "Open" 

### Consejos de Seguridad

1. Cambiar el puerto SSH por defecto (opcional):
   ```bash
   sudo nano /etc/ssh/sshd_config
   # Cambiar: Port 22
   # Por: Port 2222 (u otro número)
   sudo systemctl restart ssh
   ```

2. Deshabilitar login con contraseña (después de configurar claves SSH):
   ```bash
   sudo nano /etc/ssh/sshd_config
   # Modificar o añadir:
   PasswordAuthentication no
   ChallengeResponseAuthentication no
   sudo systemctl restart ssh
   ```

3. Configurar un firewall básico:
   ```bash
   sudo apt install ufw
   sudo ufw allow 2222/tcp  # O el puerto que hayas configurado
   sudo ufw enable
   ```

### Solución de Problemas

1. Verificar el estado del servicio SSH:
   ```bash
   sudo systemctl status ssh
   ```

2. Verificar los logs:
   ```bash
   sudo tail -f /var/log/auth.log
   ```

3. Problemas comunes:
   - **Conexión rechazada**: Verificar IP y puerto correctos
   - **Permission denied**: Verificar permisos de ~/.ssh y authorized_keys
   - **Host key verification failed**: Eliminar la entrada antigua en ~/.ssh/known_hosts

### Automatización de Conexión

1. Crear un alias en Windows (crear archivo .bat):
   ```batch
   @echo off
   start putty.exe -ssh pi@192.168.1.100 -i "C:\ruta\a\tu\clave.ppk"
   ```

2. Crear alias en Linux/Mac (añadir al ~/.bashrc o ~/.zshrc):
   ```bash
   alias raspi='ssh pi@192.168.1.100 -i ~/.ssh/id_rsa'
   ```
