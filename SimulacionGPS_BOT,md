# GPS Bot: Simulación de Sensor GPS Nombre: [Gutierrez Cepeda Andres] Usuario: [pitonC]

**GPS Bot**: ¡Hola! Soy una simulación de un sensor GPS. Te ayudaré con la cadena de datos NMEA y la configuración del puerto serial para explorar la información que obtienes del sensor.

![Imagen del Sensor GPS](https://cdn.prod.website-files.com/5e098b0d74360832f6e51991/5e5b82890e170645a180686f_800x800_shadowGPS.png)

## Conexión Serial

### Requisitos
Para conectarte al sensor y comenzar a recibir datos NMEA a través del puerto serial, sigue estos pasos:

1. **Conexión física**:
   - Usa un cable FTDI o un adaptador USB a serial para conectar el dispositivo con el sensor GPS a tu computadora o microcontrolador (como una Raspberry Pi).
   - Asegúrate de que el dispositivo tenga configurado el puerto serial adecuado (por ejemplo, `/dev/ttyUSB0` en Linux o `COM1` en Windows).

2. **Configuración del puerto serial**:
   - Configura el puerto serial para que la comunicación funcione correctamente. Los parámetros comunes son:
     - **Velocidad de baudios**: 9600 bps (común para muchos sensores GPS).
     - **Bits de datos**: 8
     - **Bits de parada**: 1
     - **Paridad**: Ninguna

### Ejemplo de Código en Python para Leer Datos NMEA

```python
import serial

# Configura el puerto serial
ser = serial.Serial('/dev/ttyUSB0', 9600, timeout=1)

while True:
    # Lee una línea del sensor GPS
    line = ser.readline().decode('ascii', errors='replace')
    
    # Muestra la línea NMEA
    print(line)
    
    # Agrega lógica adicional para analizar las sentencias NMEA si es necesario

# Sentencias NMEA Comunes  

Los datos enviados por el sensor GPS suelen estar en formato NMEA. Aquí te doy ejemplos de las sentencias más comunes:  

- **$GPGGA**: Información básica de la posición.  
- **$GPGLL**: Datos de latitud y longitud.  
- **$GPRMC**: Información de fecha, hora, velocidad y rumbo.  

## Ejemplo de una sentencia NMEA  
```plaintext
$GPGGA,123519,4807.038,N,01131.000,E,1,08,0.9,545.4,M,46.9,M,,*47

##Explorar la Cadena del Sensor en codigo
def parse_gpgga(data):
    """Parse the $GPGGA NMEA sentence"""
    fields = data.split(',')
    if fields[0] == "$GPGGA":
        latitude = fields[2]
        longitude = fields[4]
        altitude = fields[9]
        return latitude, longitude, altitude
    return None

# Ejemplo de cómo llamar la función de análisis
gps_data = "$GPGGA,123519,4807.038,N,01131.000,E,1,08,0.9,545.4,M,46.9,M,,*47"
lat, lon, alt = parse_gpgga(gps_data)
print(f"Latitud: {lat}, Longitud: {lon}, Altitud: {alt}")
