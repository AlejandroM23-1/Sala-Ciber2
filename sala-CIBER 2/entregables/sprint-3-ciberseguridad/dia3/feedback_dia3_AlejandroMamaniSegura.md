## A — Verificación de estado + setup de Wireshark
Logré configurar mi entorno de red y levantar Wireshark en la interfaz correcta. Superé los problemas iniciales de resolución de nombres forzando el DNS a 8.8.8.8 para asegurar que las peticiones llegaran a OpenRouter.

## B — Captura de tráfico en reposo
Mantuve el sniffer activo sin interactuar con la app. Confirmé que OpenClaw es "silencioso": no hubo conexiones salientes ni telemetría oculta hacia dominios externos mientras no lo usaba. Esto valida la higiene de privacidad del agente.

## C — Captura de tráfico activo
Realicé peticiones reales y, aunque obtuve errores HTTP 401/402 por falta de saldo, pude capturar el Handshake TLS. Verifiqué que todo el contenido del chat viaja como Application Data cifrado, por lo que mi API Key y mensajes son ilegibles para terceros en la red.

## D — Análisis de permisos del sistema operativo
Usé ProcMon para rastrear el proceso. Identifiqué que corro bajo el usuario boshi con privilegios estándar. Detecté accesos a rutas fuera de la carpeta de instalación, específicamente en AppData\Local y archivos de configuración como .gitconfig, lo cual representa un riesgo de visibilidad de datos personales.

## E — Documentación de riesgos para los 34 estudiantes
Redacté un análisis con 4 riesgos clave:

Fallo de DNS (Disponibilidad).

Exposición de perfil de usuario (Privacidad).

Agotamiento de cuota (Operacional).

Análisis de metadatos TLS (Seguridad pasiva).
Propuse mitigaciones basadas en el aislamiento con Docker y el uso de reglas de Firewall.

## F — Exploración con IA
Investigué conceptos avanzados para fortalecer el reporte, como el Principio de Mínimo Privilegio (PoLP) y las diferencias de seguridad entre correr un agente de forma local (soberanía total de datos) frente a uno en la nube (dependencia de terceros).

## G — Evaluación entre pares + Cierre
Completé la evaluación de mi compañero, analizando sus hallazgos en Wireshark y corrigiendo conceptos sobre la diferencia entre cifrado y aislamiento. Con esto, cierro la fase de auditoría técnica.
