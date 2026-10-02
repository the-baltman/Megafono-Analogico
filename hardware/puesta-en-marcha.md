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

4. **SW1 en OFF.** Antes de montar, **mide cada resistor con el óhmetro, fuera del circuito**:

   | R1 | R2 | R3 | R4 | R5 | R6 | R7 |
   |---|---|---|---|---|---|---|
   | 440–500 Ω | 2.07–2.33 kΩ | 77–87 kΩ | 20.7–23.3 kΩ | 4.42–4.98 kΩ | 205–235 Ω | 1.69–1.91 kΩ (2.07–2.33 kΩ si usas el de 2.2 kΩ) |

   220 Ω y 2.2 kΩ, y también 470 Ω y 4.7 kΩ, solo se distinguen por la tercera banda. La tabla del punto 5 no
   atrapa un R5 de valor equivocado y el óhmetro sí. Con Q1: la base con el probador de diodos, y el
   emisor y el colector con el zócalo hFE si tu multímetro lo tiene (con la base en la B, prueba las
   dos orientaciones de las otras dos patas: la correcta lee de decenas a cientos, la invertida unas
   pocas unidades). Si no tiene zócalo hFE, lo deciden la base y el emisor del punto 5.
   Después monta R1, C1, R2, el cable de MK1, MK1, C2, R3, R4, Q1, R5, R6, R7, C3 y C4.
5. SW1 en ON. Medir en DC. Punta negra en el punto estrella, salvo en las filas de "caída": ahí van
   las dos puntas en las dos patas del resistor.

| Punto | Esperado | Qué significa si falla |
|---|---|---|
| Caída en R1 (puntas en las dos patas de R1) | 0.18–0.75 V | Menos de 0.18 V: casi no circula corriente (Q1 no conduce o el micrófono está abierto). Más de 0.75 V: corriente de más (Q1 saturado, R4 abierta, algún corto) |
| Caída en R2 (puntas en las dos patas de R2) | 0.1–2.0 V | Menos de 0.1 V: no pasa corriente por la cápsula (cable, soldadura o conductor 1 abiertos, o cápsula muerta). Drenaje (unión R2/C2) cerca de 0 V: corto en el cable o en la cápsula, o R2 abierta. Entre 2.0 V y ese extremo: la cápsula consume fuera de su hoja; revisa su polaridad por continuidad a la lata y prueba la cápsula de repuesto |
| Base de Q1 | 1.40–2.20 V | Base debajo de 1.4 V **y** emisor debajo de 0.75 V: emisor y colector de Q1 intercambiados. Apaga, **cambia Q1 por uno nuevo** (con el transistor al revés, la unión base-emisor recibe hasta ~8 V en inversa, más que los 6 V que garantiza la hoja de onsemi) y móntalo girado 180° (la base se queda en su sitio). Si girar Q1 no lo arregla: R4 de valor bajo, o R6 y R7 en corto. Cualquier otro valor fuera: divisor R3/R4 mal (valor, posición o soldadura) |
| Emisor de Q1 | 0.70–1.60 V | Ver la fila de la base |
| Caída en R6 (puntas en las dos patas de R6, rango de 2 V) | 0.05–0.20 V | Menos de 0.05 V: R6 en corto o de valor bajo (puente de soldadura, 22 Ω en vez de 220 Ω): el preamplificador gana de 11 a 15 dB de más y el aparato pita antes. Más de 0.20 V: R6 de valor alto (2.2 kΩ en vez de 220 Ω) o R7 de valor bajo |
| Colector de Q1 | 4.8–7.9 V | Más de 7.9 V: no circula corriente de colector (R6 o R7 abiertas o sin soldar, R5 de 1 kΩ o menos). Menos de 4.8 V: Q1 conduce de más o está saturado (R3 y R4 intercambiadas, R4 abierta, R7 de 180 Ω). **Un colector dentro de la ventana no descarta el pinout invertido: eso lo deciden la base y el emisor** |
| Corriente total (amperímetro en serie, como en el Paso 1) | 0.5–1.6 mA | Más de 1.6 mA: consumo de más (compárala con la caída en R1). Lee después de ~1 minuto encendido: la fuga inicial de C7 baja sola |

*Ventanas calculadas en esquinas para el 2N3904: hFE de 40 a 800, V_BE de 0.57 a 0.77 V, resistores de
5 % (R7 de 1.8 kΩ o de 2.2 kΩ), V+ de 9.0 a 9.7 V y cápsula de 0.05 a 0.6 mA. No busques el número
central: busca que caiga dentro.* **Nada de Q1 se suelda (en la perfboard) hasta que estas lecturas
salgan.**

**Sobre el drenaje del electret:** la hoja de CUI da 0.5 mA como máximo y no da mínimo. Por eso se
mide la caída en R2 (I = caída / 2.2 kΩ). Que el drenaje quede pegado a V_A solo prueba que no pasa
corriente; la polaridad de la cápsula se comprueba por continuidad a la lata antes de soldar.

6. **Prueba de señal, sin etapa de potencia:** multímetro en V AC, puntas en colector de Q1 y masa.
   Hablar fuerte a 3 cm de la cápsula. La lectura debe **moverse** de unos pocos mV a 100–200 mV.
   *(Un multímetro común promedia y no es preciso arriba de ~1 kHz — esto solo confirma "hay señal /
   no hay señal".)* Si no se mueve nada: revisar micrófono, C2 o Q1.

## Paso 3 — Etapa de potencia, con carga de prueba

7. **SW1 en OFF.** Insertar U1 en el zócalo, muesca hacia la fila 30. Montar C9, RV1, los puentes,
   R8, C12, C11. **Config A: dejar pines 1 y 8 sin nada.**
   **Antes de energizar:** gira RV1 a tope en sentido antihorario y mide con el óhmetro entre el
   cursor y el extremo que va al riel GND (GND-S): debe dar **~0 Ω**. Si da ~10 kΩ, intercambia los
   dos extremos. Así, "RV1 al mínimo" siempre es **tope antihorario**.
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

11. **SW1 en OFF.** Quitar la resistencia de prueba y conectar la trompeta: conductor **negro** (+,
    "Hot", hoja TOA SC-615) al (−) de C11; conductor **blanco** (−, "Com") directo al punto estrella.
    **Ojo: es al revés de la costumbre y del portapilas de este mismo aparato, donde el negro es el
    negativo.** *Con una sola bocina, la polaridad no cambia el sonido ni daña nada (C11 bloquea la
    DC), pero se respeta para que el aparato quede igual que los diagramas.*
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
