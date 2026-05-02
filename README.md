#  Petalot ESP32 Firmware (Ported Version)

Firmware modificado del proyecto original **Petalot**, adaptado de ESP8266 a ESP32 para mejorar rendimiento, compatibilidad y escalabilidad.

---

##  Descripción

Este repositorio contiene una versión adaptada del firmware del proyecto Petalot, una máquina capaz de convertir botellas PET recicladas en filamento para impresión 3D.

El firmware original fue desarrollado para ESP8266 (Wemos D1 Mini).
Esta versión ha sido completamente migrada a ESP32, manteniendo la funcionalidad original e incorporando mejoras de hardware.

 El proyecto Petalot es un sistema open-source que incluye electrónica, firmware y diseño mecánico para reciclaje de plástico PET en filamento utilizable en impresión 3D ([GitHub][1]).

---

## 🚀 Características

*  Interfaz web vía WiFi
*  Modo Access Point (AP) automático
*  Control de motor paso a paso (stepper)
*  Control de temperatura del hotend
*  Lectura de termistor
*  Almacenamiento en SPIFFS
*  Integración con IFTTT
*  Lógica de control optimizada para ESP32

---

## 🔧 Cambios respecto al firmware original

###  Migración de plataforma

* ESP8266 → ESP32 (WROOM32 / Linon32)

###  Librerías adaptadas

* `ESP8266WiFi` → `WiFi`
* `ESP8266WebServer` → `WebServer`
* `ESP8266mDNS` → `ESPmDNS`
* `ESP8266HTTPUpdateServer` → `HTTPUpdateServer`

###  Hardware

* Reasignación completa de pines
* Eliminación de pines tipo `Dx`
* Uso de GPIO reales del ESP32

###  Sistema de archivos

* Implementación de `SPIFFS` en ESP32

###  Control de potencia

* Adaptación de PWM para control del heater (LED PWM - ESP32)

---

##  Pines recomendados (ESP32)

```cpp
#define PIN_EN        14
#define PIN_STEP      26
#define PIN_DIR       27
#define PIN_HEATER    25
#define PIN_FILAMENT  33
#define PIN_THERMISTOR 34
#define LED_BUILTIN   2
```

---

##  Configuración en Arduino IDE

En Arduino IDE:

* Board: **ESP32 Dev Module**
* Partition Scheme: **Huge APP (3MB No OTA)** 
* Flash Mode: QIO
* Upload Speed: 115200

---

##  Consideraciones importantes

* OTA deshabilitado por limitaciones de memoria
* Requiere correcta calibración del termistor
* Verificar conexiones del heater antes de operar
* Uso bajo responsabilidad (control térmico)

---

##  Interfaz Web

El sistema crea una red WiFi:

```text
PETALOT-XXXXXX
```

Acceso desde navegador:

```text
http://192.168.4.1
```

Permite:

* Control de temperatura
* Control del motor
* Configuración WiFi
* Estado del sistema

---

## 🧪 Estado del proyecto

| Componente  | Estado            |
| ----------- | ----------------- |
| Compilación | ✅ OK              |
| WiFi        | ✅ OK              |
| Web Server  | ✅ OK              |
| Stepper     | ⚠️ Test requerido |
| Heater      | ⚠️ Test crítico   |
| Sensor      | ⚠️ Validar        |

---

##  Estructura del proyecto

```bash
Firmware/
 └── petalot/
     ├── petalot.ino
     ├── wifi.hpp
     ├── server.hpp
     ├── pins.hpp
     ├── hotend.hpp
     ├── stepper.hpp
     ├── conf.hpp
```

---

##  Créditos

* Proyecto original: Function3D (Petalot)
* Adaptación ESP32: DESSMOND968

---

##  Licencia

Este proyecto se basa en el trabajo original de Petalot.
Respeta los términos de uso y atribución del autor original.

---

##  Apoya el proyecto original

Si este proyecto te resulta útil, considera apoyar al creador original de Petalot.

---

##  Futuras mejoras

* Implementación de OTA en ESP32
* Control PID del heater
* Interfaz web mejorada
* Soporte para sensores adicionales
* Optimización de consumo

---

##  Contacto

Desarrollador: DESSMOND968
Proyecto: Petalot ESP32 Firmware Port

[1]: https://github.com/function3d/petalot?utm_source=chatgpt.com "GitHub - function3d/petalot: PET Bottle To 3D Filament"
