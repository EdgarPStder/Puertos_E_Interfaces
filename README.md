# Programación de Puertos e Interfaces

![Arduino](https://img.shields.io/badge/Arduino-00878F?style=flat-square&logo=arduino&logoColor=white)
![ESP32](https://img.shields.io/badge/ESP32-E7352C?style=flat-square&logo=espressif&logoColor=white)
![C](https://img.shields.io/badge/C-A8B9CC?style=flat-square&logo=c&logoColor=black)
![C++](https://img.shields.io/badge/C%2B%2B-00599C?style=flat-square&logo=cplusplus&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)

Prácticas y proyectos de la materia **Programación de Puertos e Interfaces** (Ingeniería en Sistemas Computacionales, UAT — UAM Mante, 2025).

El eje del curso es la **comunicación entre una computadora y un microcontrolador**: puerto serie (UART) desde C y Python, Bluetooth, un servidor web en ESP32 y la lectura de sensores analógicos y digitales.

---

## Contenido

| Carpeta | Interfaz | Qué hace |
|---|---|---|
| [`Lector de sensor y control de led desde puerto serie/`](Lector%20de%20sensor%20y%20control%20de%20led%20desde%20puerto%20serie/) | UART (USB) | El Arduino envía la lectura de un sensor analógico; un programa en la PC la recibe y, si supera 500, ordena encender el LED. Hay tres clientes equivalentes: **C con `termios` en Linux**, Python en Linux y Python en Windows |
| [`LedBluetooth/`](LedBluetooth/) | Bluetooth (módulo serie) | Control de un LED desde el celular: `e` activa el parpadeo, `a` lo apaga |
| [`ServidorWebESP32/`](ServidorWebESP32/) | WiFi / HTTP | La ESP32 levanta un servidor web con botones para encender y apagar un LED |
| [`Examen/`](Examen/) | GPIO / ADC | EJ13: temperatura con LM35 · EJ14: alarma con sensor de inclinación y buzzer · EJ15: distancia con HC-SR04 que enciende un LED |
| [`Examen 2 PIP/`](Examen%202%20PIP/) | I²C + 1-Wire | **Monitor de ritmo cardiaco y temperatura**: sensor de pulso KY-039, termómetro DS18B20 y pantalla OLED SSD1306. Incluye reporte y fotos del prototipo |

---

## Cómo ejecutar

### Sketches de Arduino / ESP32

Abre la carpeta del sketch en **Arduino IDE 2.x** y cárgalo a la placa.

- **`ServidorWebESP32`** necesita tus credenciales WiFi: copia `arduino_secrets.example.h` como `arduino_secrets.h` en la misma carpeta y escribe tu red. Ese archivo está en `.gitignore`. Después abre en el navegador la IP que imprime el monitor serie.
- **`Examen 2 PIP`** usa las bibliotecas `OneWire`, `DallasTemperature`, `Adafruit GFX` y `Adafruit SSD1306` (instálalas desde el Gestor de bibliotecas).

### Cliente serie en C (Linux)

```bash
cd "Lector de sensor y control de led desde puerto serie/LinuxC"
gcc practica.c -o practica
./practica            # usa /dev/ttyUSB0
```

Si no tienes permiso sobre el puerto: `sudo usermod -aG dialout $USER` y vuelve a iniciar sesión.

### Cliente serie en Python

```bash
pip install pyserial
python "Lector de sensor y control de led desde puerto serie/LinuxPython/practica3er.py"
```

En Windows usa la versión de `WindosPython/` y ajusta el puerto (`COM4` por defecto).

---

## Autores

**Edgar Gael Pesina Santander** — Ingeniería en Sistemas Computacionales, Universidad Autónoma de Tamaulipas.
GitHub: [@EdgarPStder](https://github.com/EdgarPStder)

Varias prácticas se hicieron en equipo; los integrantes aparecen en cada reporte.

## Licencia

Código bajo licencia [MIT](LICENSE).
