# Presupuesto de potencia — Megáfono Analógico

**Alcance:** diseño entregable de **8 Ω**, 330 mA de pico, 0.26 W de disipación en U1. Documento
generado 2026-09-30. No incluye ninguna variante de 4 Ω: esa exploración quedó evaluada, archivada y
descartada cuando el techo del proyecto subió a $2,500 MXN y permitió comprar directamente un
transductor de 8 Ω (la TOA SC-615) dentro de presupuesto. **Nadie debe armar una variante de 4 Ω a
partir de este documento** — si necesitas esa exploración, no vive en este repositorio.

## Presupuesto de corriente y disipación

| Carga | V | I reposo | I pico | P | Estado |
|---|---|---|---|---|---|
| MK1 electret | 7.4 V | 0.5 mA | 0.5 mA | 3.7 mW | por verificar (hoja CUI da un máximo, no un típico) |
| Q1 + divisor R3/R4 | 8.46 V | 0.65 mA | 0.65 mA | 5.5 mW | derivado |
| U1 LM386N-3 reposo | 9 V | 4 mA | 4 mA | 36 mW | verificado (hoja TI) |
| U1 con señal, 0.431 W | 9 V | — | **330 mA** | disip. 0.26 W | derivado / verificado |
| **Total reposo** | | **~5.2 mA** | | 45 mW | |
| **Total con voz** (cresta 12 dB) | | | **330 mA** | | ~30–45 mA medios, estimado |

**Disipación de U1 = 0.26 W contra 1.25 W del encapsulado → sin disipador.**

**Autonomía: no es restricción.** 6×AA alcalinas, ~2000 mAh útiles / ~40 mA medios = decenas de
horas. Pero los 4 mA de reposo son ~44 % del consumo a ciclo de trabajo realista: **SW1 es
obligatorio**, no opcional — dejar el aparato "pausado" sin apagarlo lo drena en cuestión de días.

## El presupuesto de 0.3 Ω del camino de alimentación

Caída al pico: 330 mA × 0.3 Ω = **0.10 V**. Lo que entra en esos 0.3 Ω, con el polyfuse ya contado
(corrección aplicada en el gate — la primera versión de este presupuesto lo dejaba fuera):

| Elemento del camino | R máxima | Nota |
|---|---|---|
| Contactos del portapilas + cable | ≤ 0.10 Ω | 6 celdas = 12 contactos: es el que se descuida |
| SW1 | ≤ 0.05 Ω | cualquier interruptor de ≥ 1 A cumple |
| **F1 polyfuse** | **≤ 0.15 Ω** | hay que leerlo de la hoja de datos. Un PTC radial de 0.75 A anda entre 0.075 y 0.25 Ω: uno malo se come el presupuesto entero solo |
| **TOTAL del camino** | **≤ 0.30 Ω** | |

**Estos 0.3 Ω excluyen explícitamente la resistencia interna de las 6 celdas** (~0.6–1.2 Ω en
conjunto). Esa no se reduce comprando mejor ferretería: es la que absorbe C7 (1000 µF low-ESR), y es
la razón de que C7 sea un componente de primer orden, no un capacitor de "limpieza".

**Si el polyfuse que consigues no declara R_max en hoja de datos**, la alternativa es portafusible +
fusible de vidrio de 0.5 A (resistencia despreciable), aceptando que se quema una vez y hay que
reponerlo.

## Corriente de pico: por qué es 330 mA, no 285 mA

I_pico = V_p/R_L = 2.63 V / 8 Ω = **329 mA**, redondeado a **330 mA**, calculado para la potencia
limpia de diseño de 0.431 W. Fusible, portapilas y cableado están especificados al peor caso, 330 mA.
(La cifra de 285 mA que en algún momento circuló en el proyecto correspondía a un diseño de 4×AA a
6 V, ya descartado — no es un valor válido para este circuito de 9 V.)
