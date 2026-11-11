## LAB # 24 · IA local con QV.AC frente a la nube

Hice la prueba en mi MacBook Pro M3 con 16 GB de RAM. Corrí Qwen2.5-1.5B (L1) y Llama-3.1-8B (L2) en QV.AC con el Wi-Fi apagado; después probé las mismas tres instrucciones de A.2 en ChatGPT (N) con internet. Usé únicamente los casos ficticios del documento de sesión.

### A.1 · Equipo, memoria y predicción

| Dato | Mi registro |
|---|---|
| Equipo y sistema | MacBook Pro M3, macOS, 16 GB de RAM |
| L1 | Qwen2.5-1.5B, ≈1.5 mil millones de parámetros |
| Memoria L1 a 4 bits | 1.5 × 4 ÷ 8 = **0.75 GB** de pesos, más margen de ejecución; cabe en 16 GB |
| L2 | Llama-3.1-8B, ≈8 mil millones de parámetros |
| Memoria L2 a 4 bits | 8 × 4 ÷ 8 = **4.0 GB** de pesos, más margen de ejecución; cabe en 16 GB |
| N | ChatGPT, versión en la nube |

Antes de medir predije que N ganaría en tiempo total y calidad; que L1 daría la primera palabra más rápido entre los modelos locales; y que L2 se acercaría más a la calidad de N. La predicción coincidió con los resultados. Los cálculos de memoria estiman solo los pesos a 4 bits: no son una medición del uso total de RAM.

### A.3 · Mis nueve mediciones

Medí los segundos hasta la primera palabra y hasta el final de cada respuesta. Los valores de tokens/s son los promedios que registré por modelo local, no una medición separada para cada instrucción; en N la app no mostró tokens/s.

| Configuración | Instrucción A.2 | Primera palabra (s) | Total (s) | Tokens/s | Calidad (1–5) | Mi nota de calidad |
|---|---:|---:|---:|---|---:|---|
| L1 | 1 · Resumir | 1 | 3 | ≈60, prom. L1 | 3 | Fue coherente, pero superficial e incompleta. |
| L1 | 2 · Calcular | 1 | 4 | ≈60, prom. L1 | 2 | Confundió los pasos y dio una cifra distinta de los **4 GB** de la clave A.2. |
| L1 | 3 · Redactar | 1 | 5 | ≈60, prom. L1 | 4 | Respetó casi todo el formato; el vocabulario fue básico. |
| L2 | 1 · Resumir | 2 | 8 | ≈35, prom. L2 | 5 | Resumió el aviso de manera completa y clara. |
| L2 | 2 · Calcular | 2 | 9 | ≈35, prom. L2 | 5 | Llegó a **4 GB** y explicó la cuenta correctamente. |
| L2 | 3 · Redactar | 2 | 13 | ≈35, prom. L2 | 4 | Buen tono y estructura; omitió un detalle menor. |
| N | 1 · Resumir | 1 | 2 | No muestra | 5 | La respuesta fue completa y fácil de leer. |
| N | 2 · Calcular | 1 | 3 | No muestra | 5 | Llegó a **4 GB** con una explicación paso a paso. |
| N | 3 · Redactar | 1 | 4 | No muestra | 5 | Cumplió la extensión, el contenido y el tono solicitados. |

La clave de la instrucción 2 es **8 × 4 ÷ 8 = 4 GB sin margen**. Califiqué las respuestas con A.4, no por su velocidad. Los dos modelos locales se ejecutaron con el Wi-Fi apagado; N necesitó conexión. No registré el nivel de batería ni las otras aplicaciones abiertas.

### Comparación

| Configuración | Primera palabra media | Tiempo total medio | Calidad media |
|---|---:|---:|---:|
| L1 | 1 s | 4 s | 3.00/5 |
| L2 | 2 s | 10 s | 4.67/5 |
| N | 1 s | 3 s | 5.00/5 |

N ganó en tiempo total medio por **1 s frente a L1** y **7 s frente a L2**. También ganó en calidad media por **0.33 puntos frente a L2** y **2 puntos frente a L1**. L1 igualó a N en tiempo hasta la primera palabra y fue el local más rápido en ese indicador. Mis resultados confirmaron la predicción, aunque no muestran cómo se comportarían otros equipos o redes.

### Mi reflexión de tres líneas

1. En mi prueba, N ganó en velocidad total (3 s de media) y calidad (5/5); L1 tardó 4 s y logró 3/5, mientras L2 tardó 10 s y logró 4.67/5, así que mi predicción se confirmó.
2. En Pactrail usaría L1 local para redactar o resumir ayuda general sobre el flujo escrow; no lo usaría para calcular importes, resolver disputas ni decidir liberaciones, pues falló la instrucción aritmética.
3. Sin internet, mis instrucciones en QV.AC quedaron en mi equipo, aunque sigo confiando en quienes entrenaron y distribuyeron los modelos; al usar N, envié las instrucciones al proveedor de la nube.

**Fuente de instrucciones y rúbrica:** [Sesión 27, Apéndice A](https://docs.google.com/document/d/1CzRYRiaWLoFYfJw13jm9MXUp15oglbIrDhGwq6qfq14/edit).
