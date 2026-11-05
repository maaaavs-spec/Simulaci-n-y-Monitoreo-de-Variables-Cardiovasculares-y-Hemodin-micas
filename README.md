Universidad Militar Nueva Granada

Programa: Ingeniería Biomédica

Asignatura: Instrumentación Biomédica y Biosensores

Práctica: Simulación y Monitoreo de Variables Cardiovasculares y Hemodinámicas 

# **Integrantes**
>
* María Angélica Vargas Saldaña 5600820
* Samuel Esteban Fonseca Luna — 5600808
* Laura Daniela Triana Molano — 5600828

<h2 align="center">𝙞𝙣𝙩𝙧𝙤𝙙𝙪𝙘𝙘𝙞ó𝙣</h2>


<h2 align="center">𝙤𝙗𝙟𝙚𝙩𝙞𝙫𝙤𝙨</h2>

𝙊𝙗𝙟𝙚𝙩𝙞𝙫𝙤 𝙜𝙚𝙣𝙚𝙧𝙖𝙡: 

Evaluar el funcionamiento del monitor de signos vitales Mindray uMEC 100 mediante el simulador de parámetros hemodinámicos Pronk OxSim OX-1, verificando la precisión de las mediciones y la respuesta del sistema de alarmas ante diferentes condiciones fisiológicas y patológicas.

 
𝙊𝙗𝙟𝙚𝙩𝙞𝙫𝙤𝙨 𝙀𝙨𝙥𝙚𝙘𝙞́𝙛𝙞𝙘𝙤𝙨:

1. Identificar los modos de operación y las características funcionales del simulador Pronk OxSim OX-1 y del monitor Mindray uMEC 100.

2. Verificar la activación y los tiempos de respuesta de las alarmas del monitor ante condiciones simuladas de bradicardia, hipoxia, baja perfusión y taquicardia.

3. Calcular los errores absolutos y porcentuales de las mediciones de frecuencia cardíaca y saturación de oxígeno, analizando las variaciones de las señales fotopletismográficas.
   
<h1 align="center"><i><b>𝐏𝐚𝐫𝐭𝐞 A 𝐝𝐞𝐥 𝐥𝐚𝐛𝐨𝐫𝐚𝐭𝐨𝐫𝐢𝐨</b></i></h1>
a. ¿Cómo colocar al uMEC 100 en modo “monitor”? 

b. ¿Qué tipo de parámetros o variables fisiológicas pueden simularse con el 
Pronk OxSim OX-1? Explique cada uno. 

c. En el ámbito clínico ¿Cuáles son las tolerancias o errores máximos 
permitidos (EMP) para cada parámetro fisiológico mencionado en la parte 
(b)? 

<h1 align="center"><i><b>𝐏𝐚𝐫𝐭𝐞 B 𝐝𝐞𝐥 𝐥𝐚𝐛𝐨𝐫𝐚𝐭𝐨𝐫𝐢𝐨</b></i></h1>

bradicardia
<img width="433" height="268" alt="Captura de pantalla 2026-11-03 172025" src="https://github.com/user-attachments/assets/18459811-b88c-4982-9d54-6ae2b43503ad" />

hipoxia
<img width="328" height="182" alt="Captura de pantalla 2026-11-03 172325" src="https://github.com/user-attachments/assets/0c3394b4-4a87-4d94-9bb1-41b1c7b43176" />

low perfusion
<img width="367" height="208" alt="Captura de pantalla 2026-11-03 172432" src="https://github.com/user-attachments/assets/81961924-54d6-4a49-9b77-5eb42a8f0d9c" />

taquicardia
<img width="299" height="182" alt="Captura de pantalla 2026-11-03 172531" src="https://github.com/user-attachments/assets/6f16d7d4-181f-4523-9b78-6d2e91e4b86a" />

# Resultados

# Tabla No.1 
## Tabla para verificación de alarmas en el uMEC 100
| Prueba | Límite configurado | Valor simulado | ¿Alarma activa? | Tiempo de respuesta (s) |
|:---|:---|:---|:---:|---:|
| Bradicardia | N/A | FC: 40 bpm | Sí | 0,15 |
| Hipoxia | SpO₂ mínimo: 90% | SpO₂: 85% | Sí | 1,34 |
| Saturación elevada (Low Perfusion) | SpO₂ máximo: 97% | SpO₂: 99% | Sí | 0,12 |
| Taquicardia | N/A | FC: 140 bpm | Sí | 0,12 |

# Tabla No.2
## Tabla de erorres 
| Prueba | Variable | Referencia | Medición | Error absoluto | Error porcentual |
|:---|:---|---:|---:|---:|---:|
| Bradicardia | FC (bpm) | 40 | 40 | 0 | 0 % |
| Bradicardia | SpO₂ (%) | 95 | 96 | 1 | 1,05263 % |
| Hipoxia | FC (bpm) | 80 | 80 | 0 | 0 % |
| Hipoxia | SpO₂ (%) | 85 | 85 | 0 | 0 % |
| Low Perfusion | SpO₂ (%) | 99 | 100 | 1 | 1,01010 % |
| Taquicardia | FC (bpm) | 140 | 140 | 0 | 0 % |
| Taquicardia | SpO₂ (%) | 98 | 99 | 1 | 1,02040 % |


Link del excel donde se realizaron los calculos: https://docs.google.com/spreadsheets/d/e/2PACX-1vSNkSMJio5d5kaGgueQ4mV61JLNXuEeFwvLhDiPfeMh-Vd3pFvXy43zz13pNNbI_m8fOeDSbzksNlZf/pubhtml
# Análisis de resultados
A partir de los resultados obtenidos, se identificó que el monitor uMEC 100 presentó una correspondencia cercana con los valores configurados en el simulador OxSim OX-1.

En la prueba de bradicardia, la frecuencia cardíaca medida coincidió con el valor de referencia de 40 bpm, mientras que la SpO₂ presentó una diferencia de un punto porcentual. Para la simulación de hipoxia, ambas variables coincidieron con los valores configurados, obteniéndose un error porcentual de 0%.

En la prueba de baja perfusión (Low Perfusion), se observó una diferencia de un punto porcentual en la saturación de oxígeno. Esta condición permitió evaluar el comportamiento del monitor ante señales de menor calidad asociadas con una perfusión reducida. Por otra parte, durante la simulación de taquicardia, la frecuencia cardíaca registrada fue de 140 bpm, coincidiendo con el valor de referencia, mientras que la SpO₂ presentó una diferencia de un punto porcentual.

Respecto al sistema de alarmas, se registró su activación en las cuatro condiciones evaluadas. Los tiempos de respuesta obtenidos fueron diferentes entre las pruebas, siendo mayor en la simulación de hipoxia.


<h1 align="center"><i><b>𝐏𝐚𝐫𝐭𝐞 C 𝐝𝐞𝐥 𝐥𝐚𝐛𝐨𝐫𝐚𝐭𝐨𝐫𝐢𝐨</b></i></h1>

_DISCUSIÓN_

• Pregunta 1: ¿Cuál es el principio de operación del Pronk OxSim OX-1 para 
simular una onda pulsátil? 

• Pregunta 2: ¿Por qué la SpO2 baja puede ser un falso positivo (falsa 
alarma) en una situación de mala perfusión?

<h2 align="center">Conclusion</h2>

<h2 align="center">𝘽𝙞𝙗𝙡𝙞𝙤𝙜𝙧𝙖𝙛𝙞𝙖</h2>
