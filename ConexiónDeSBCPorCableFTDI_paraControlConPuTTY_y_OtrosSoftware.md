# Conexión de SBC por Cable FTDI para Control con PuTTY y Otros Software

## Introducción
Autor: [Gutierrez Cepeda Andres] y [pitonC]
Este documento explica cómo conectar una computadora de placa reducida (SBC) mediante un cable FTDI (USB a TTL) y controlarla desde PuTTY u otros programas.

## Requisitos
- **Computadora SBC** (Ejemplo: Raspberry Pi)
- **Adaptador FTDI (USB a TTL)**
- **Cables Dupont** para conexión
- **Software de terminal** (PuTTY, Minicom, Tera Term, etc.)

## Conexión del Cable FTDI a la SBC
El adaptador FTDI convierte USB en señales seriales TTL. Conéctalo de la siguiente manera:

![Adaptador FTDI](https://m.media-amazon.com/images/I/61Jh6BaSKvL.jpg)

| FTDI Pin | SBC Pin |
|----------|---------|
| TX (Transmisión) | RX (Recepción) |
| RX (Recepción) | TX (Transmisión) |
| GND | GND |

> ⚠ **Importante:** Si el adaptador FTDI tiene opción de voltaje, selecciona **3.3V o 5V** según la SBC (Ejemplo: Raspberry Pi usa 3.3V).

## Configuración en la PC
### **Windows**
1. Conecta el adaptador FTDI a un puerto USB.
2. Abre **Administrador de dispositivos** y busca el puerto asignado (Ejemplo: `COM3`).
3. Instala los drivers FTDI si es necesario.

### **Linux**
1. Conecta el adaptador FTDI.
2. Usa el siguiente comando para encontrar el puerto asignado:
   ```sh
   ls /dev/ttyUSB*
   ```
   Ejemplo de salida: `/dev/ttyUSB0`

## Configuración de PuTTY
1. Abre **PuTTY**.
2. Selecciona **Serial** en "Connection type".
3. Introduce el puerto correspondiente (Ejemplo: `COM3` en Windows o `/dev/ttyUSB0` en Linux).
4. Configura la velocidad en **115200 baudios** (o la que use tu dispositivo).
5. Da clic en **Open** y presiona **Enter**.

Si la conexión es correcta, verás la terminal de la SBC y podrás controlarla.

## Alternativas a PuTTY
### **Windows**
- **Tera Term**
- **RealTerm**

### **Linux/macOS**
- **Minicom**:  
  ```sh
  sudo minicom -D /dev/ttyUSB0 -b 115200
  ```
- **Screen**:  
  ```sh
  screen /dev/ttyUSB0 115200
  ```

## Comunicación Serial en Python con `pyserial`
Si deseas automatizar la comunicación, usa Python con `pyserial`:

```python
import serial

# Configura el puerto serie
ser = serial.Serial('/dev/ttyUSB0', 115200, timeout=1)

# Envía datos
ser.write(b'Hola desde la SBC\n')

# Lee respuesta
respuesta = ser.readline().decode().strip()
print(f"Recibido: {respuesta}")

# Cierra el puerto
ser.close()
```

## Conclusión
Siguiendo estos pasos, puedes conectar y controlar tu SBC mediante un adaptador FTDI y PuTTY u otras herramientas. 

🚀 **aqui termina la actividad**

