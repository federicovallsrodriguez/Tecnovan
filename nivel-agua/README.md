# Medidor de nivel de agua con ESP32 y boya resistiva

Este proyecto permite medir el nivel de un depósito de agua en una furgoneta camper usando un ESP32, una boya resistiva de 0–190 Ω, y un divisor de tensión. El sistema se integra con Home Assistant para ver el porcentaje de llenado en tiempo real.

📦 **Componentes necesarios:**
- ESP32 DevKit
- Boya resistiva 0–190 ohm (400 mm)
- Resistencia de 220 ohm (1/4 W)
- Cables dupont / protoboard / caja de conexiones
- Home Assistant (instalado en un mini PC a 12V)

📐 **Cómo funciona:**
1. La boya cambia su resistencia en función del nivel de agua.
2. Formamos un divisor de tensión con una resistencia fija.
3. El ESP32 mide el voltaje y calcula el porcentaje con una función calibrada.
4. El dato se muestra en Home Assistant.

📁 Archivos incluidos:
- `nivel_agua_esp.yaml`: código ESPHome funcional.
- `tabla_calibracion.csv`: valores medidos reales de altura/voltaje.
- `esquema_conexion.jpg`: conexiones del sistema.
- `notas_extra.md`: consejos de montaje, problemas comunes y soluciones.

🔧 **Configuración completa en el archivo `nivel_agua_esp.yaml`.**

 Más consejos y notas en [notas_extra.md](./notas_extra.md)

## 🔌 Esquema de conexiones

Este proyecto puede probarse inicialmente en simulación con Tinkercad antes de montarlo físicamente en la furgoneta camper.

![Esquema simulado en Tinkercad](./montaje_tinkercad.png)

🔗 Puedes abrir y editar el esquema en Tinkercad con este enlace:  
👉 [Ver esquema interactivo en Tinkercad](https://www.tinkercad.com/things/cCpKPm8uOsk-exquisite-jaban-kasi/editel?returnTo=https%3A%2F%2Fwww.tinkercad.com%2Fdashboard&sharecode=BV8qEtDc70B2P_7Hoq8YbehSrz2DRoChgAIa5x-gDt8)

---

### ⚠️ Advertencias importantes:

> ⚠️ **1. El montaje en Tinkercad está hecho con un Arduino UNO, pero el circuito real utiliza un ESP32 DevKit.**  
> Los pines de conexión deben adaptarse como se describe a continuación.

> ⚠️ **2. La resistencia usada en el divisor de tensión del esquema original ha sido sustituida por una resistencia de 220 Ω en el montaje final.**  
> Esto mejora la precisión en la lectura del voltaje que genera la boya resistiva.

---

### 🔁 Cómo sustituir Arduino UNO por ESP32 DevKit:

| Función         | En Arduino UNO      | En ESP32 DevKit (recomendado) |
|------------------|----------------------|-------------------------------|
| Pin de lectura ADC | `A0`                 | `GPIO34`                      |
| Alimentación     | `5V`                 | `3V3`                         |
| GND             | `GND`                | `GND`                         |

📌 **Importante:**  
- El ESP32 **trabaja a 3.3 V**, así que no alimentes el divisor desde 5V.  
- `GPIO34` es una entrada analógica válida y segura en el ESP32.

---

