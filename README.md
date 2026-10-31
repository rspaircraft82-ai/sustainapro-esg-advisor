# SustainaPro Aviation Sustainability Advisor

**Enlace a la app:** https://sustainapro-esg-advisor-3zl2ltblbddyb6aa2ym4qm.streamlit.app  
**Repositorio:** https://github.com/rspaircraft82-ai/sustainapro-esg-advisor

## 2. Problema y usuario
Los operadores aéreos regionales con flotas de turbohélices (como el ATR 42/72) operan bajo márgenes financieros sumamente estrechos donde la ineficiencia en la gestión de peso, los procedimientos de rodaje y los perfiles de ascenso/descenso penalizan gravemente la rentabilidad. Actualmente, estos análisis se realizan de forma manual y superficial, careciendo de un diagnóstico estandarizado que priorice iniciativas operativas viables sin requerir grandes inversiones de capital ni apostar por alternativas prematuras como el SAF. La herramienta resuelve la generación automatizada de este diagnóstico experto, mientras que la decisión de implementación operativa final y la supervisión de la tripulación quedan en manos del equipo humano.

## 3. Especificación
- **Funcionalidades:** Configuración de parámetros operativos (modelo de aeronave y cadencia de sectores diarios), generación de informe preliminar, cálculo automático de madurez ESG, iniciativas operativas y roadmap mensual.
- **Entradas:** Selección de flota (Turbohélice Regional ATR 42/72) y volumen de operación.
- **Salidas:** Informe ejecutivo de consultoría en formato de texto enriquecido y tablas Markdown limpias.
- **Criterios de aceptación (con caso límite):** Si el usuario genera el diagnóstico sin errores, la app muestra el reporte completo en menos de 10 segundos. Si el servicio de IA experimenta congestión o cuota agotada, el bloque `try/except` captura la excepción y muestra un mensaje de advertencia amigable.

## 4. La pieza de IA
- **Qué usa:** API de Google Gemini con el modelo `gemini-3.8-flash` y un límite de `max_output_tokens=4000`.
- **Por qué esa opción:** Ofrece una ventana de contexto amplia y la velocidad ideal para redactar informes de consultoría ejecutiva detallados sin latencias excesivas.
- **Qué pasa si falla:** La app cuenta con un bloque de control `try/except` que intercepta cualquier error de cuota o red, mostrando un mensaje claro en la interfaz.

## 5. Proceso con IA
- **Herramientas:** Cursor, Git, Streamlit Cloud y Google Gemini API.
- **Fichero de contexto del agente:** `AGENTS.md` (configurado en el repositorio).
- **Prompts clave:** Actúa como un Socio Director experto en consultoría ESG aeronáutica, estructura el informe con secciones numeradas y limpia los saltos de línea HTML.
- **Qué delegué al agente y qué revisé a mano:** Delegué la generación estructural del código base y la conexión con la API; revisé a mano los prompts del sistema y ajusté la limpieza de etiquetas HTML al vuelo.

## 6. Prueba y mejora
| Quién la probó | Qué probó | Qué pasó | Qué cambié |
|---|---|---|---|
| Francisco Esquivel y Darío Vélez | Flujo completo de la app y generación de reportes con distintas flotas | Se visualizaban etiquetas `<br>` en crudo dentro de las tablas markdown | Añadí una función de limpieza al vuelo en Python y configuré el renderizado mediante `st.markdown(..., unsafe_allow_html=True)` |

## 7. Pitch escrito
1. Las aerolíneas regionales con flotas turbohélice enfrentan altos costos operativos y márgenes reducidos por despilfarro de combustible y falta de estandarización ESG.
2. SustainaPro Aviation Sustainability Advisor es un sistema experto interactivo que audita la madurez operativa y genera un plan de choque a medida sin CapEx.
3. La IA permite estructurar diagnósticos técnicos complejos y hojas de ruta financieras adaptadas a normativas aeronáuticas en segundos.
4. A partir de las pruebas iniciales, optimizamos el renderizado y límite de tokens para soportar reportes ejecutivos completos sin cortes.
5. El siguiente paso consiste en integrar telemetría de vuelo QAR en tiempo real para calibrar automáticamente las métricas de consumo de combustible.
## Capturas
La app funcionando
<img width="1351" height="522" alt="image" src="https://github.com/user-attachments/assets/6440af3b-04b0-43b4-a90e-d37b1faafb37" />
La app ante un caso límite
<img width="1383" height="477" alt="image" src="https://github.com/user-attachments/assets/79ac7efe-97bb-4e60-abec-1df7a98d1a44" />
Un momento de vuestro trabajo con la IA
<img width="1096" height="989" alt="image" src="https://github.com/user-attachments/assets/6e6e3911-6c56-4b3d-93cf-9c0e19adb287" />
La prueba. Sin ninguna clave a la vista
<img width="1024" height="566" alt="image" src="https://github.com/user-attachments/assets/3f254523-4164-4f16-8842-d5645ab5c97a" />


