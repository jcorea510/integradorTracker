*Las comunicaciones inalámbricas han evolucionado significativamente, permitiendo la transmisión de datos en tiempo real a través de distintos protocolos y tecnologías. Uno de los sistemas más utilizados en este ámbito es el Automatic Packet Reporting System (APRS), que permite la comunicación digital bidireccional entre estaciones de radioaficionados, sensores y otros dispositivos.*

*En este documento se exploran los fundamentos de APRS, su integración con Internet a través de APRS-IS, y el uso de distintos protocolos de transmisión, incluyendo AX.25 y LoRa. Particularmente, LoRa ha ganado popularidad en aplicaciones de Internet de las Cosas (IoT) gracias a su capacidad de transmitir datos a largas distancias con bajo consumo energético.*

*Finalmente, se revisa el Plan Nacional de Atribución de Frecuencias (PNAF) en Costa Rica, el cual regula el uso del espectro radioeléctrico y define categorías de asignación de frecuencias según su aplicación. Esta regulación es fundamental para garantizar el correcto funcionamiento de los sistemas de comunicación inalámbrica en el país.*


# Estado del Arte

## ¿Qué es APRS?

Un Sistema Automático Reporte de Paquetes (APRS) es una comunicación bidireccional digital en tiempo real entre todos los miembros de una red compartiendo información. Esto implica que cualquier cosa de "valor" en el área local va a ser capturada por el dispositivo APRS, y al mismo tiempo, este también estará enviando información de "valor" a la red [1].

Los datos de los dispositivos APRS son típicamente transmitidos a frecuencia compartida y son repetidos por estaciones de relé para consumo local esparcido. Todos los datos se ingresan a un sistema de Internet APRS (APRS-IS) vía receptor conectado a Internet (IGate) y se distribuyen para acceso por todos los usuarios de la red. Pueden servir para telemetría, transmisión en redes LAN, GPS, etc.

Existe una gran variedad de protocolos de comunicación. La elección del protocolo depende de la aplicación específica. El más usado es el protocolo AX.25, derivado de X.25, pero adaptado para radioaficionados. Sin embargo, no es el único protocolo disponible.

### Protocolos de comunicación en APRS

1. **AX.25**  
   - Soporta comunicación a través de Packet Radio.  
   - Funciona con Modems AFSK a 1200 bps y enlaces VHF (30 a 300 MHz [144.39 MHz en Costa Rica]).  

2. **APRS-IS**  
   - Integra APRS con Internet.  
   - Utiliza TCP/IP para conectar las estaciones APRS, IGates y servidores APRS.  

3. **LoRa**  
   - Se usa cuando se quiere comunicación a larga distancia con baja velocidad de transmisión de datos y cuando la aplicación requiere consumo de baja potencia.  

Los elementos principales de los sistemas APRS incluyen las estaciones de usuario, que pueden ser móviles o fijas: estaciones de censado y radios, repetidores que restauren y amplifiquen la señal, Internet gateways que conecten la red a Internet y dispositivos LoRa.

## LoRa

LoRa es una técnica de modulación para transmisiones eléctricas sin hilos derivada de Espectro Expandido en Chirps. Esto significa que utiliza una señal sinodal moduladora cuya frecuencia no es fija, sino que oscila en un rango de frecuencias. Esto la vuelve robusta contra interferencias en comunicaciones a larga distancia.

LoRa es ideal para aplicaciones en las que se desea transmitir conjuntos de datos pequeños o con baja tasa de transmisión. Ejemplos incluyen:

- Aplicaciones de agricultura y riego, donde se requiere transmitir instrucciones a larga distancia y tomar decisiones en espacios abiertos con baja supervisión.
- Soluciones en ciudades inteligentes, como logística de transporte, medición de variables ambientales y sistemas de seguridad.
- Monitorización de infraestructuras: puentes, edificios, supervisión de paneles solares, etc.

Los datos pueden ser transmitidos a distancias más largas en comparación con tecnologías como Bluetooth o WiFi. Estas características la vuelven ideal para aplicaciones IoT y censado en dispositivos que deben ser dejados en operación sin supervisión durante largos periodos de tiempo. LoRa opera en frecuencias libres de VHF. En el caso de Costa Rica, abarca las frecuencias de 902 MHz a 928 MHz.

Existen diversos módulos disponibles en el mercado con soporte para LoRa. Por ejemplo, el **ESP32 Doit**, una tarjeta de desarrollo creada por DOIT, que puede usarse con el módulo **ESP32-WROOM-32**. Este módulo permite comunicación WiFi y Bluetooth con frecuencias de reloj ajustables en el rango de 80 MHz a 240 MHz.

## PNAF

El **Plan Nacional de Atribución de Frecuencias (PNAF)** es un instrumento que permite la regulación nacional de manera óptima, racional, económica y eficiente del espectro radioeléctrico nacional. Su objetivo es satisfacer oportuna y adecuadamente las necesidades de frecuencias para el desarrollo de redes de telecomunicaciones y responder eficientemente a la demanda de segmentos de frecuencias para redes que hagan uso del espectro radioeléctrico. Para ello, se promueve el uso de tecnologías que optimicen su utilización, conforme al marco legal y reglamentario vigente y los acuerdos internacionales ratificados por Costa Rica.

### Clasificación del espectro radioeléctrico

- **Uso comercial**: Para la prestación de servicios de telecomunicaciones disponibles al público a cambio de una contraprestación económica.
- **Uso no comercial**: Para operaciones de carácter temporal, experimental, científico, servicios de radiocomunicación privada, banda ciudadana, radioaficionados o redes de telemetría de instituciones públicas.
- **Uso oficial**: Para establecer las comunicaciones de las instituciones del Estado, con uso exclusivo para el servicio asignado y no comercial.
- **Uso para seguridad, socorro y emergencia**: Para radionavegación, seguridad aeronáutica, marítima y otros servicios de ayuda.
- **Uso libre**: No requiere concesión, autorización o permiso, estando sujeto a las características técnicas establecidas en el Adendum VII del PNAF.

# Metodología y organización:



# Procedimiento:

Luego de descargar el firmware de LoRa APRS Tracker se procede a crear el proyecto.
Para ello en platform.io (Extensión de VS Code) se inicia un proyecto. Se importa proyecto,
y luego se selecciona la targeta de desarrollo y la dirección del proyecto (ubicación del firmware); 
tal como se observa en las siguientes imagenes.

<image src="/doc/images/importproy.png" alt="Import project">

<image src="/doc/images/boardselect.png" alt="Selec board">

Posteriormente, en el fichero tracker_conf.json
se sustituye, en callsing, NOCALL por el callsign asignado; en nuestro caso TI0IE6.

<image src="/doc/images/callsing.png" alt="Callsing">

Luego se realizan varios pasos. Primero compilar el programa. Se presina un botón de esquina inferior izquierda
y se espera hasta al resultado que se observa en terminal.

<image src="/doc/images/bottoupload.png" alt="Button upload firmware">

<image src="/doc/images/upload.png" alt="Upload">

El segundo paso consiste en cargar el programa al modulo. Se corrobora la carga en terminal.

<image src="/doc/images/bottonCompilar.png" alt="Button Compilado">

<image src="/doc/images/compilado.png" alt="Compilado">

Finalmente se carga la imagen a la placa de desarrollo.

<image src="/doc/images/buttonUploadImage.png" alt="Button upload image">

<image src="/doc/images/uploadimage.png" alt="Upload image">

Luego hay que esperar que el módulo se reinicie; y entonces se debería poder observar
su callsign en el display.

<image src="/doc/images/loradisplay.jpeg" alt="ESP32 lora display">

Finalmente, se busca el modulo en el mapa LoRa APRS.

<image src="/doc/images/map.png" alt="mapa lora aprs">

# Referencias

1. APRS Foundation. Automatic Packet Reporting System. Disponible en: https://www.aprs.org/
