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
