# Puesta en marcha — Megáfono Analógico

**Alcance:** procedimiento de energizado y verificación por etapas del circuito, en protoboard.
Documento generado 2026-09-30. Regla general: **la bocina se conecta al final, y el IC se inserta
siempre con la alimentación desconectada.**

**Dónde encaja este procedimiento en el armado completo del aparato:** es el **Bloque 2** del orden
maestro de 4 bloques del proyecto. El **Bloque 1** —el conjunto de micrófono, cápsula ya montada en
su jaula a 30 ± 3 mm de distancia forzada— va **antes** de este procedimiento, porque el umbral de
pitido (paso 4 de este documento) solo significa algo con la geometría real del aparato, no con la
cápsula suelta en la mano. Ver `mecanica/cuerpo-portatil.md` para el Bloque 1.

## Paso 1 — Alimentación, sin nada más

1. Montar SW1, F1, el punto estrella, C7 y C8 (ver `colocacion-protoboard.md`).
2. Revisar dos veces la polaridad de C7 antes de energizar. Un electrolítico de 1000 µF al revés se
   calienta, se hincha y puede reventar.
3. Poner pilas, SW1 en ON. Medir:

| Punto | Esperado | Si no |
|---|---|---|
| Riel V+ al punto estrella | 9.0–9.7 V (fresco) | pilas, SW1 o F1 |
| Corriente total | < 1 mA | hay un corto |

## Paso 2 — Micrófono y preamplificador, sin U1

4. Montar R1, C1, R2, cable del micrófono, MK1, C2, R3, R4, Q1, R5, R6, R7, C3, C4.
5. Energizar y medir en DC (negro del multímetro en el punto estrella):

| Punto | Esperado | Qué significa si falla |
|---|---|---|
| V_A (unión R1/R3/R5) | 8.2–8.7 V | si está en ~9 V, no circula corriente: Q1 o el micrófono no conducen |
| Drenaje de MK1 (unión R2/C2) | 6.5–8.2 V | pegado a 8.5 V = micrófono al revés o abierto; cerca de 0 V = en corto |
| Base de Q1 | 1.70–1.90 V | divisor R3/R4 mal |
| Emisor de Q1 | 1.00–1.25 V | |
| Colector de Q1 | 5.5–6.1 V | ~8.5 V = Q1 en corte (pinout invertido); ~1.2 V = saturado (revisar R5, R3/R4) |
| Corriente total | 0.8–1.5 mA | |

**Sobre el rango del drenaje del electret**: el valor exacto depende del consumo real de tu cápsula,
y la hoja de datos de CUI da 0.5 mA como **máximo**, no como típico. Lo que importa no es acertar un
número exacto, es que **no** esté pegado a 8.5 V (micrófono abierto o invertido) ni cerca de 0 V (en
corto). Para el dato real de tu cápsula, mide la caída en R2 y divide entre 2.2 kΩ.

6. **Prueba de señal, sin etapa de potencia:** multímetro en V AC, puntas en colector de Q1 y masa.
   Hablar fuerte a 3 cm de la cápsula. La lectura debe **moverse** de unos pocos mV a 100–200 mV.
   *(Un multímetro común promedia y no es preciso arriba de ~1 kHz — esto solo confirma "hay señal /
   no hay señal".)* Si no se mueve nada: revisar micrófono, C2 o Q1.

## Paso 3 — Etapa de potencia, con carga de prueba

7. **SW1 en OFF.** Insertar U1 en el zócalo, muesca hacia la fila 30. Montar C9, RV1, los puentes,
   R8, C12, C11. **Config A: dejar pines 1 y 8 sin nada.**
8. En lugar de la bocina, conectar la resistencia de 10 Ω 5 W. RV1 al mínimo.
9. SW1 en ON. Medir:

| Punto | Esperado | Si no |
|---|---|---|
| Pin 6 a pin 4 | 9.0–9.7 V | |
| Pin 5 en DC | 4.2–4.9 V (~V+/2) | 0 V o ~9 V: apagar de inmediato. IC al revés, pin 2 sin masa, o U1 dañado |
| Corriente de reposo total | 4.5–6.5 mA | > 20 mA = está oscilando. Revisar red de Zobel, C8, largo de patas del pin 5 |
| Pin 5 en AC, en silencio | < 20 mV | ruido u oscilación |

**El pin 7 no lleva medición de voltaje.** No hay valor de hoja verificado para su tensión DC, y un
valor que no se verificó no va en una tabla de mediciones. C9 (pin 7) se comprueba por su **efecto**,
no por su voltaje: con C9 puesto hay menos zumbido de fondo que sin él.

10. Subir RV1 poco a poco hablando a 3 cm. Debe oírse un zumbido débil en la resistencia (normal que
    casi no suene: es una resistencia, no un transductor).

## Paso 4 — Bocina

11. **SW1 en OFF.** Quitar la resistencia de prueba y conectar la trompeta: (+) a C11, (−) directo al
    punto estrella.
12. **Antes de encender: la trompeta apuntando lejos de cualquier cara y de cualquier pared cercana.**
13. SW1 en ON, RV1 al mínimo, subir despacio hablando a 3 cm.
14. **Con Config A va a faltar volumen: es lo esperado**, no una falla — Config A queda 3.2 dB corta
    ya a 94 dB SPL en la cápsula (ver `presupuesto-de-ganancia.md`). Apagar, **agregar C10 (Config B,
    + al pin 1)** y volver a subir RV1 **desde el mínimo**. Config B es la configuración de trabajo.
15. **Anotar la posición de RV1 que funcionó.** Es el dato que se transfiere a la placa final en
    perfboard y el punto de partida de la prueba de margen de realimentación (`mecanica/pruebas.md`,
    prueba V1).

## Cómo evitar el pitido, si aparece

El chillido ocurre cuando la ganancia de lazo llega a 0 dB: la bocina mete en el micrófono tanto
nivel como el que el micrófono necesitaba producir. Variables que mueven el margen, de mayor a menor
efecto:

| Variable | Cuánto mueve | Dirección |
|---|---|---|
| Distancia boca-micrófono | de 2.5 a 10 cm: **−14 dB**; a 20 cm: **−18 dB** | la dominante — se fija mecánicamente, no se pide |
| RV1 | dB a dB | el control que se tiene en la mano |
| Config A en vez de B | +20 dB de margen | pero A solo alcanza hablando fuerte a 2–3 cm |
| Notch en 1–3 kHz | no se hace | esa banda es donde vive la inteligibilidad de las consonantes |

Si pita, en este orden: (1) bajar RV1; (2) acercar la boca a la cápsula; (3) verificar que la cápsula
esté detrás del plano de la boca de la trompeta, sin superficie reflectante a menos de 1 m enfrente;
(4) pasar de Config B a Config A. Para distinguir un pitido acústico real de un problema de masa: tapa
la cápsula con el dedo — si se apaga, es acústico (arriba); si sigue, es masa/rail (revisar el punto
estrella, C7, C9, filtro R1/C1).
