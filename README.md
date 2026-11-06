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

En el entorno clínico es necesario monitorear de forma continua variables como la frecuencia cardíaca (FC) y la saturación periférica de oxígeno (SpO₂), y que el monitor genere alarmas cuando sus variaciones puedan representar un peligro inmediato para el paciente [1]. La pulsioximetría es una alternativa no invasiva y rápida a la punción arterial para estimar la saturación de oxígeno [6].

El principio de medición es el siguiente: el sensor emite luz roja (≈660 nm) e infrarroja (≈940 nm) y un fotodetector mide cuánta luz atraviesa el tejido, porque la hemoglobina oxigenada y la desoxigenada absorben cada longitud de onda de forma distinta [6]. La señal se separa en un componente pulsátil (AC, sangre arterial) y uno no pulsátil (DC, tejidos, sangre venosa y capilar) [7]. Para cada longitud de onda se calcula el cociente AC/DC y luego la relación entre ambos, R = (AC_rojo/DC_rojo) / (AC_IR/DC_IR) [7]. Esa relación se convierte en SpO₂ mediante un algoritmo y una tabla construidos con datos de calibración [6], es decir, con una curva R propia de cada fabricante [8]. La frecuencia de pulso (PR) se obtiene de esa misma señal pulsátil; el manual del uMEC contempla ajustes de alarma y de fuente específicos para la PR (sección 12.7) [2].

Para comprobar que un monitor responde a estas condiciones sin usar pacientes se emplean simuladores o probadores. El Pronk OxSim OX-1 es un dispositivo electrónico que emula la saturación de oxígeno mediante una señal de luz óptica [4] y ofrece 5 modos de simulación con distintas combinaciones de saturación, frecuencia cardíaca e índice de perfusión [3]. Es importante precisar su alcance: la norma ISO 80601-2-61 distingue entre “simulador”, “calibrador” y “probador funcional”, y exige que los manuales de los pulsioxímetros indiquen que, en general, los probadores funcionales no sirven para medir la exactitud de la SpO₂ [8]. Por eso esta práctica evalúa el funcionamiento del monitor Mindray uMEC 100 (activación de alarmas y concordancia con los valores nominales del simulador) y no su calibración absoluta.

<h2 align="center">𝙤𝙗𝙟𝙚𝙩𝙞𝙫𝙤𝙨</h2>

𝙊𝙗𝙟𝙚𝙩𝙞𝙫𝙤 𝙜𝙚𝙣𝙚𝙧𝙖𝙡: 

Evaluar el funcionamiento del monitor de signos vitales Mindray uMEC 100 mediante el simulador de parámetros hemodinámicos Pronk OxSim OX-1, verificando la precisión de las mediciones y la respuesta del sistema de alarmas ante diferentes condiciones fisiológicas y patológicas.

 
𝙊𝙗𝙟𝙚𝙩𝙞𝙫𝙤𝙨 𝙀𝙨𝙥𝙚𝙘𝙞́𝙛𝙞𝙘𝙤𝙨:

1. Identificar los modos de operación y las características funcionales del simulador Pronk OxSim OX-1 y del monitor Mindray uMEC 100.

2. Verificar la activación y los tiempos de respuesta de las alarmas del monitor ante condiciones simuladas de bradicardia, hipoxia, baja perfusión y taquicardia.

3. Calcular los errores absolutos y porcentuales de las mediciones de frecuencia cardíaca y saturación de oxígeno, analizando las variaciones de las señales fotopletismográficas.
   
<h1 align="center"><i><b>𝐏𝐚𝐫𝐭𝐞 A 𝐝𝐞𝐥 𝐥𝐚𝐛𝐨𝐫𝐚𝐭𝐨𝐫𝐢𝐨</b></i></h1>
a. ¿Cómo colocar al uMEC 100 en modo “monitor”?

Según el manual del operador de la serie uMEC (60/70/80/100/120/150), el modo de monitoreo es el modo clínico de uso más frecuente y, cuando el equipo se enciende, entra automáticamente en él (sección 3.7.1, p. 3-9) [2]. En la práctica basta con:

Encender el monitor (sección 3.4 del manual) [2].
Comprobar que la pantalla muestre el monitoreo normal y no la pantalla de espera (standby).
Si el equipo estuviera en standby, salir de ese modo con Resume monitor (continúa con el paciente actual) o con Monitor (admite un paciente nuevo) (sección 3.7.4, p. 3-11) [2].

Precaución: según el manual, al salir del modo de espera y reanudar el monitoreo, las alarmas permanecen pausadas durante dos minutos [2]; conviene esperar ese tiempo antes de verificar alarmas. Además del modo de monitoreo, el manual describe los modos de privacidad, nocturno y de espera (secciones 3.7.2 a 3.7.4) [2].

Limitación: no revisé el procedimiento detallado de admisión de paciente (secciones 3.9 y 5.2 del manual); solo confirmé que existen [2].

b. ¿Qué tipo de parámetros o variables fisiológicas pueden simularse con el Pronk OxSim OX-1? Explique cada uno.

El OX-1 es un simulador óptico de SpO₂: detecta el LED rojo e infrarrojo del sensor, identifica automáticamente el tipo de sensor y devuelve la señal óptica simulada [4]. Ofrece 4 niveles de saturación, 3 frecuencias de pulso y simulación de baja perfusión [4], combinados en 5 modos fijos [3]. Los valores de cada modo, según el listado de un distribuidor que reproduce las especificaciones del fabricante [5], son:

###  Modos y Condiciones Prácticas

| Modo | SpO₂ (%) | Frecuencia de pulso (bpm) | Índice de perfusión (PI) | Condición usada en esta práctica |
| :---: | :---: | :---: | :---: | :--- |
| **1** | 85 | 80 | ≈ 2,0 | Hipoxia |
| **2** | 95 | 40 | ≈ 2,0 | Bradicardia |
| **3** | 98 | 80 | ≈ 2,0 | No utilizado |
| **4** | 98 | 140 | ≈ 2,0 | Taquicardia |
| **5** | 99 | 80 | ≈ 0,2 | Baja perfusión (*“Low Perfusion”*) |

Los tres parámetros que se simulan son:

Saturación periférica de oxígeno (SpO₂): porcentaje de hemoglobina oxigenada estimado a partir de la relación de absorciones R entre luz roja e infrarroja [6][7]. El OX-1 la emula mediante una señal de luz óptica [4], de modo que el monitor muestre el valor nominal de cada modo (85, 95, 98 o 99 %) [5].
Frecuencia de pulso (FC/PR): número de pulsos por minuto que el monitor detecta en la onda pletismográfica; el simulador ofrece 40, 80 y 140 bpm [5]. El OX-1 solo genera señal óptica de SpO₂ [4]; las señales de ECG, presión no invasiva o respiración corresponden a otros equipos de Pronk, como el SimCube [14]. Inferencia (verificar en la pantalla del uMEC 100): por esa razón, el valor que se lee en la práctica debería ser la frecuencia de pulso (PR) derivada del módulo de SpO₂, no una frecuencia cardíaca derivada de ECG.
Índice de perfusión (PI): porcentaje entre la señal pulsátil y la no pulsátil [10]; es un indicador de la intensidad del pulso y de la calidad de la señal de SpO₂ [10]. Para el módulo de SpO₂ de Mindray, un PI superior a 1 es óptimo, entre 0,3 y 1 es aceptable y por debajo de 0,3 indica baja perfusión [10]. El modo 5 del OX-1 (PI ≈ 0,2) cae por debajo de ese umbral, por lo que representa baja perfusión [5][10].

El fabricante también ofrece, de forma opcional y por separado, comunicación serial para ajustes personalizados de la simulación [3]; no se usó en esta práctica.

Limitación: no pude abrir el manual del operador del OX-1; los valores de los modos provienen de [3], [4] y [5]. El manual citado en [10] corresponde a un monitor Mindray con la misma numeración del capítulo 12 que el uMEC, pero no pude confirmar que sea el del uMEC 100.

c. En el ámbito clínico ¿Cuáles son las tolerancias o errores máximos permitidos (EMP) para cada parámetro fisiológico mencionado en la parte (b)?

### Especificaciones y Tolerancias

| Parámetro | Tolerancia / EMP | Fuente |
| :--- | :--- | :--- |
| **SpO₂** (especificación del fabricante, serie uMEC con módulo SpO₂ Mindray) | ±2 % en 70–100 % (adulto/pediátrico); ±3 % en 70–100 % (neonato); 0–69 % no especificado | [9] |
| **SpO₂** (requisito normativo de exactitud) | $A_{rms} \le 4\ \%$ en 70–100 % según ISO 80601-2-61 y $\le 3,5\ \%$ según la guía de la FDA | [11] |
| **Frecuencia de pulso** (especificación del fabricante, PR del módulo SpO₂ Mindray) | ±3 bpm, rango 20–254 bpm | [9] |
| **Frecuencia cardíaca derivada de ECG** (referencia normativa) | ±10 % o ±5 bpm, el que sea mayor (IEC 60601-2-27:2011, cl. 201.12.1.101.15) | [12] |
| **Índice de perfusión (PI)** | No puedo confirmar un EMP normativo. Mindray da umbrales de interpretación (>1, 0,3–1, <0,3), no una tolerancia de exactitud; el OX-1 lista el PI solo como “aproximado” (≈2,0 y ≈0,2) | [5][10] |

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

__DISCUSIÓN__

• __Pregunta 1: ¿Cuál es el principio de operación del Pronk OxSim OX-1 para simular una onda pulsátil?__

El principio de operación del simulador Pronk OxSim OX-1 radica en su capacidad para generar una onda pulsátil recreando electrónicamente la absorción de luz, lo que le permite simular el comportamiento de la fotopletismografía humana directamente sobre los fotodiodos del oxímetro. Esto es fundamental porque el algoritmo de un monitor médico requiere identificar dos variables para calcular la SpO2: la absorción de luz constante de los tejidos (componente DC) y el aumento pulsátil de sangre arterial con cada latido (componente AC). Al conectarse a la pinza del monitor, el OX-1 detecta la luz roja e infrarroja emitida por el equipo y utiliza componentes de estado sólido para atenuar y modular rítmicamente esta luz de regreso al detector. De esta manera, el simulador recrea con precisión las variaciones cíclicas, haciendo que el software del oxímetro procese la señal como si fuera la onda fisiológica del pulso arterial de un paciente real, permitiendo así evaluar su calibración exacta.

• __Pregunta 2: ¿Por qué la SpO2 baja puede ser un falso positivo (falsa alarma) en una situación de mala perfusión?__

Una lectura falsamente baja de SpO2 durante un estado de mala perfusión (como en casos de shock, hipotermia o vasoconstricción) se produce porque la debilidad extrema del pulso periférico destruye la relación señal-ruido del sensor. Fisiológicamente, el volumen de sangre arterial oxigenada que logra llegar a los capilares distales es tan bajo que la señal pulsátil (AC) se vuelve casi imperceptible frente a la absorción constante del tejido (DC). Ante la pérdida de un pulso arterial claro, el algoritmo del oxímetro compensa aumentando automáticamente su ganancia (amplificación) para intentar encontrar la onda faltante. Sin embargo, esta sobre-amplificación termina captando el "ruido de fondo", específicamente las pulsaciones del lecho venoso estancado, cuya saturación de oxígeno es naturalmente mucho menor (alrededor del 75%). Como resultado, el equipo procesa erróneamente esta sangre venosa amplificada como si fuera el pulso arterial principal, arrojando un cálculo matemático de hipoxia severa y disparando una falsa alarma a pesar de que la sangre a nivel central se encuentre correctamente oxigenada.

# <h2 align="center"> CONCLUSION </h2>

Con el simulador Pronk OxSim OX-1 se verificó el funcionamiento del monitor uMEC 100 en cuatro condiciones (bradicardia, hipoxia, baja perfusión y taquicardia). El monitor activó la alarma en las cuatro, con tiempos de respuesta de 0,12 a 1,34 s, y mostró la frecuencia con error de 0 bpm y la SpO₂ con errores de 0 a 1 punto (error porcentual máximo de 1,05 %), dentro de la especificación de ±2 % que el fabricante declara para la serie uMEC [9]. Estos resultados respaldan la confiabilidad del uMEC 100 para las pruebas realizadas, pero la muestra es pequeña (cuatro valores de SpO₂ y tres de frecuencia, un solo ensayo por condición) y las cifras del fabricante deben confirmarse en el manual del equipo. Por ser el OxSim un probador funcional, el resultado confirma que el monitor responde de forma coherente, no que su exactitud clínica esté calibrada [8].

Respecto a las limitaciones del módulo OxSim para simular condiciones patológicas: sus modos documentados combinan solo SpO₂, frecuencia de pulso e índice de perfusión en 5 configuraciones fijas [3][4][5]. Salvo con la comunicación serial opcional [3], que no se usó, no permiten por ejemplo evaluar baja perfusión a 140 bpm ni valores intermedios de SpO₂, y no incluyen ECG ni arritmias, que corresponden a otros equipos de Pronk [14]. En consecuencia, la “bradicardia” y la “taquicardia” de la práctica son variaciones de la frecuencia de pulso de la oximetría y no patologías del ritmo cardíaco.

<h2 align="center">𝘽𝙞𝙗𝙡𝙞𝙤𝙜𝙧𝙖𝙛𝙞𝙖</h2>

[1] Universidad Militar Nueva Granada, “Guía de Preparación Práctica de Laboratorio: Simulación y Monitoreo de Variables Cardiovasculares y Hemodinámicas,” GL-AA-F-1, Rev. 3, Bogotá, Colombia, 30 sep. 2025.

[2] Shenzhen Mindray Bio-Medical Electronics Co., Ltd., “uMEC 60/uMEC 70/uMEC 80/uMEC 100/uMEC 120/uMEC 150 Patient Monitor Operator’s Manual,” Rev. 2.0, jul. 2023. [En línea]. Disponible en: https://www.mindray.com/content/dam/xpace/en/site/mdr-sscp/patient-monitor/umec-series-60-70-80-100-120-150-safety-and-performance-information.pdf

[3] Medical IT, “OxSim OX-1” (página de producto). [En línea]. Disponible en: https://www.medicalitech.com/producto/ox-sim/

[4] Medical IT, “Ficha técnica OxSim OX-1,” 2026. [En línea]. Disponible en: https://www.medicalitech.com/wp-content/uploads/2026/09/Ficha-Tecnica-OxSim_2026.pdf

[5] McKesson Medical-Surgical, “Pronk Technologies Inc OX-1 – Pulse Oximeter Simulator OxSim” (ref. 1252995). [En línea]. Disponible en: https://mms.mckesson.com/product/1252995/Pronk-Technologies-Inc-OX-1

[6] U.S. Food and Drug Administration, presentación sobre pulsioxímetros (principios de operación y baja perfusión). [En línea]. Disponible en: https://fda.gov/media/176236/download

[7] Life in the Fast Lane, “Pulse Oximeter.” [En línea]. Disponible en: https://litfl.com/pulse-oximeter

[8] D. J. McMahon, “There’s no such thing as a SpO2 simulator,” White paper, Fluke Biomedical. [En línea]. Disponible en: https://www.flukebiomedical.com/sites/default/files/resources/6001759_0000_ENG_A_W.PDF

[9] U.S. Food and Drug Administration, notificación 510(k) K171901 (monitores de paciente Mindray serie uMEC). [En línea]. Disponible en: https://www.accessdata.fda.gov/cdrh_docs/pdf17/K171901.pdf

[10] Shenzhen Mindray Bio-Medical Electronics Co., Ltd., manual del operador de un monitor de paciente Mindray (capítulo 12, “SpO2 Display”; modelo no confirmado). [En línea]. Disponible en: https://storage.mtender.gov.md/get/4046b052-0495-4933-8050-f130c40a6257-1664865639784

[11] Estudio de exactitud de SpO2 de un pulsioxímetro de anillo (Movano Health), JMIR Formative Research, 2024, e54256. [En línea]. Disponible en: https://formative.jmir.org/2024/1/e54256

[12] Analog Devices, “Sensinel CPM System – FDA Data” (precisión de frecuencia cardíaca según IEC 60601-2-27:2011, cl. 201.12.1.101.15). [En línea]. Disponible en: https://sensinel.analog.com/wp-content/uploads/2024/04/FDA-Data-Final.pdf

[13] Respiratory-Therapy.com, “Pulse Oximetry and Low Perfusion.” [En línea]. Disponible en: https://respiratory-therapy.com/public-health/healthcare-policy/home-care/pulse-oximetry-and-low-perfusion/

[14] MedicalExpo, “Pronk heart rate simulators” (catálogo de simuladores Pronk, incluye SimCube). [En línea]. Disponible en: https://www.medicalexpo.com/product-manufacturer/pronk-heart-rate-simulator-14929-28341.html

[15] ZOLL Medical, “Functional testers and patient simulators,” Propaq M Rev B User Manual. [En línea]. Disponible en: https://www.manualsdir.com/manuals/355913/zoll-propaq-m-rev-b.html?page=127
