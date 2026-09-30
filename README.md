# Megáfono Analógico

**Alcance:** diseño entregable, aprobado por el gate de C Morty el 2026-09-30. Repositorio de
hardware y mecánica de un megáfono portátil, 100 % analógico (sin microcontrolador, sin una sola
línea de código), construido por Baltasar como proyecto personal. Si llegaste aquí desde un código
QR impreso en el manual de armado: este repositorio es la fuente de verdad de los documentos
técnicos citados en ese manual — los números aquí y los del manual impreso deben coincidir.

---

## ⚠ Advertencia acústica — léela antes de construir o de energizar el circuito

Este aparato, en su configuración de trabajo (ver `hardware/esquematico.md`), produce:

> **~122 dB SPL a 25 cm** (pico instantáneo) y **102 dB SPL a 1 m** (promedio en la banda de voz,
> 300 Hz–4 kHz).
>
> Las dos cifras son correctas y **no se convierten una en la otra con la ley de la distancia**:
> una es un pico instantáneo, la otra un promedio de banda, y no hay factor de 1/r que las
> relacione — extrapolar 102 dB a 25 cm daría 114 dB, que **no** es la cifra de seguridad correcta.
> **Para seguridad manda siempre la cifra de pico.**
>
> **NO APUNTAR A MENOS DE 1 m DE LA CARA DE NADIE. NUNCA HACIA EL PROPIO OÍDO.** Arriba de ~75 dB en
> el oído del receptor la inteligibilidad **empeora**: apuntar de cerca aturde, no comunica. Probar
> siempre **al aire libre**, nunca en un cuarto chico.
>
> No hay riesgo de red eléctrica de 127 V en este proyecto — el peligro real de este aparato es
> acústico, no eléctrico.

---

## Qué es

Micrófono electret (cápsula MK1) → preamplificador de un transistor (Q1, 2N3904) → etapa de
potencia con un solo circuito integrado de audio (U1, LM386N-**3**) → trompeta PA con driver de
compresión de 8 Ω (MK2, TOA SC-615). Alimentado con 6 pilas AA (9.0 V nominal). Cuerpo portátil de
espina de pino con un boom impreso en PETG que fuerza la distancia entre la cápsula del micrófono y
la boca del usuario a 30 ± 3 mm — esa distancia forzada es, más que cualquier filtro electrónico, lo
que evita que el aparato pite.

Objetivo de diseño verificado: amplificar la voz a ≥92.3 dB SPL a 1 m (10 dB arriba de un grito
sostenido), sin distorsión audible, sin oscilar por realimentación acústica, con pilas comunes.
Resultado logrado: **102.4 dB SPL a 1 m con pilas frescas, 98.3 dB al fin de su vida útil.**

## Qué hay en este repositorio

| Carpeta | Contenido |
|---|---|
| `hardware/` | Esquemático completo, presupuesto de ganancia, presupuesto de potencia, BOM de electrónica, puerta de compra del transductor, colocación en protoboard, procedimiento de puesta en marcha |
| `mecanica/` | Diseño del cuerpo portátil, BOM mecánico, cotas de control, pruebas mecánicas |
| `docs/` | Vacío por ahora. Los dos manuales completos (científico y de armado) se publican aquí después de la maquetación final |

## Lo que este repositorio NO contiene

Ningún cálculo archivado o superado. El diseño entregable del transductor es **8 Ω** con la trompeta
**TOA SC-615**; cualquier recálculo para una variante de 4 Ω, o cualquier búsqueda de transductor con
el techo de presupuesto anterior ($1,500 MXN, ya superado), vive en las bitácoras de trabajo de los
agentes de diseño, no aquí — un documento archivado al que apunta un código QR es una variante que
alguien va a construir por error.

## Terminología y cifras fijadas

Nombres de componentes y cifras que se repiten idénticas en todos los documentos de este repositorio
y en los dos manuales: **MK1** (cápsula electret CMA-4544PF-W, Ø9.7 mm), **MK2** (trompeta TOA
SC-615, 8 Ω), **Q1** (2N3904), **U1** (LM386N-3), **RV1** (volumen), **SW1** (encendido), **F1**
(polyfuse), Config A (26 dB) / Config B (46 dB, configuración normal de trabajo), ganancia del
preamplificador **21.6 dB**, ganancia total **46.2 dB** (Config A) / **66.2 dB** (Config B),
corriente de pico **330 mA**, distancia cápsula–borde de la jaula **30 ± 3 mm**, techo de
presupuesto **$2,500 MXN**.
