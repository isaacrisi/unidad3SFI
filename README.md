# Unidad3

Isaac Pineda Múnera 
000509927


Un protocolo binario es lo que define el como se organizan los bits para una transmision de datos . Los datos son transmitidos en formato hexadecimal, pero realmente son binarios, ya que el sistema interpreta esos hexadecimales como cadenas de bits.
Y normalmente se divide en las siguientes partes.

- **Encabezado (Start byte)**: Indica el inicio de un mensaje válido, ayudando a diferenciar entre datos útiles y ruido.
  
- **Longitud**: Define el tamaño total del mensaje para que el receptor sepa cuántos bytes debe procesar.

- **Dirección**: Identifica el dispositivo con el que se está comunicando, útil cuando varios dispositivos comparten la misma red.

- **Comando**: Es la instrucción que le indica al dispositivo qué acción realizar, como leer o configurar algo.

- **Datos**: Es la información real que se está enviando o recibiendo, como un ID de tag o configuraciones.

- **Checksum**: Verifica que el mensaje no se haya alterado durante la transmisión, garantizando su integridad.

# Ejercicio 4

Los datos se estan tranmitiendo en little endian ya que el dato que se se envia primero es el de menor peso y para transmitir ese dato en el endian contrario se hace de la siguiente forma 
 ``` c++
  void setup() {
      Serial.begin(115200);
  }
  
  void loop() {
      static float num = 3589.3645;

      if(Serial.available()) {
          if(Serial.read() == 's') {
              uint8_t *ptr = (uint8_t *) &num;
              // Enviar en orden inverso (big-endian)
              Serial.write(ptr[3]); // Byte más significativo
              Serial.write(ptr[2]);
              Serial.write(ptr[1]);
              Serial.write(ptr[0]); // Byte menos significativo
          }
      }
  }
 ```
