# BOM de electrónica — Megáfono Analógico

**Alcance:** lista de materiales electrónicos del diseño entregable, 8 Ω, techo de proyecto
$2,500 MXN. Documento generado 2026-09-30. Precios como **rangos estimados, sin cotizar de
mostrador, consultados el 2026-09-30** — cotiza en tu localidad antes de comprar. El transductor
(#33) tiene su propio documento: `puerta-de-compra-transductor.md`, y debe comprarse **primero**, no
al final — ver ese documento antes de comprar nada.

Referencias de componentes (R#, C#, Q1, U1...) según `esquematico.md`.

| # | Ref | Parte | Cant | Dónde (Morelia / en línea) | Precio aprox. MXN | Crítico |
|---|---|---|---|---|---|---|
| 1 | U1 | **LM386N-3** DIP-8 | 1 | AG Electrónica, Electrónica Punto, Mercado Libre | 25–45 | **El sufijo -3 importa**: el N-1 es de 6 V y da 3.3 dB menos de ganancia garantizada a esta alimentación |
| 2 | — | Zócalo DIP-8 | 1 | cualquiera | 5 | recomendado, protege el IC al soldar |
| 3 | Q1 | 2N3904 TO-92 | 1 (comprar 5) | cualquiera | 3 c/u | sustituible: BC547, 2N2222A, BC337 |
| 4 | MK1 | **Electret CMA-4544PF-W, 2 terminales, Ø9.7 × 4.5 mm** | 1 (comprar 2) | Mouser MX (exacta), Steren (genérica) | 15–120 | **El diámetro es requisito**: el grommet mecánico está dimensionado para Ø9.7 mm. Uno genérico de Ø6 mm pierde el aislamiento de vibración a menos que se cambie también el grommet |
| 5 | RV1 | Pot 10 kΩ log (A) + perilla, montaje de panel con tuerca | 1 | Steren, AG | 25–40 | sustituible por lineal (se sentirá desparejo). Va en el panel de la caja, no en la placa |
| 6 | R1 | 470 Ω 1/4 W | 1 | cualquiera | 1 | |
| 7 | R2 | 2.2 kΩ 1/4 W | 1 | cualquiera | 1 | fija la condición de hoja del micrófono, no cambiar |
| 8 | R3 | 82 kΩ 1/4 W | 1 | cualquiera | 1 | |
| 9 | R4 | 22 kΩ 1/4 W | 1 | cualquiera | 1 | |
| 10 | R5 | 4.7 kΩ 1/4 W | 1 | cualquiera | 1 | |
| 11 | R6 | 220 Ω 1/4 W | 1 | cualquiera | 1 | **no sustituir: fija la ganancia** |
| 12 | R7 | 1.8 kΩ 1/4 W | 1 | cualquiera | 1 | 2.2 kΩ aceptable |
| 13 | R8 | **10 Ω 1/2 W** | 1 | cualquiera | 2 | **crítico (red de Zobel)**, no omitir |
| 14 | C1 | 220 µF/16 V electrolítico | 1 | cualquiera | 3 | 100 µF aceptable |
| 15 | C2 | 100 nF cerámico o poliéster | 1 | cualquiera | 2 | |
| 16 | C3 | 22 µF/16 V electrolítico | 1 | cualquiera | 3 | 10–47 µF aceptable |
| 17 | C4 | 12 nF cerámico | 1 | cualquiera | 2 | 10 nF aceptable |
| 18 | C5 | 220 nF poliéster | 1 | cualquiera | 2 | 100 nF aceptable |
| 19 | C7 | **1000 µF/16 V low-ESR, altura ≤ 20 mm** | 1 | AG, Mercado Libre | 8–20 | **crítico**, no bajar de 470 µF. Comprar el de **16 V**, no el de 25 V (~25 mm de alto, no entra en la caja) |
| 20 | C8 | 100 nF cerámico | 1 | cualquiera | 2 | |
| 21 | C9 | 10 µF/16 V electrolítico | 1 | cualquiera | 2 | **crítico** (bypass pin 7) |
| 22 | C10 | 10 µF/16 V electrolítico | 1 | cualquiera | 2 | solo Config B |
| 23 | C11 | 100 µF/16 V electrolítico | 1 | cualquiera | 3 | 150 µF si se quiere el corte justo en 300 Hz |
| 24 | C12 | 47 nF cerámico | 1 | cualquiera | 2 | **crítico** (Zobel) |
| 25 | SW1 | Interruptor SPST ≥ 1 A, montaje de panel, R ≤ 0.05 Ω | 1 | Steren | 20–35 | **crítico** (44 % del consumo en reposo) |
| 26 | F1 | Polyfuse PTC 0.75 A hold, **R_max ≤ 0.15 Ω de hoja** (o portafusible + fusible 0.5 A) | 1 | AG, ML | 10–30 | seguridad. El R_max hay que leerlo de hoja: uno malo se come el presupuesto de caída de voltaje del camino de alimentación |
| 27 | — | Portapilas 6×AA con cable, **sin switch integrado** | 1 | Steren, ML | 40–80 | si trae switch, se puentea |
| 28 | — | Pilas AA alcalinas | 6 | cualquiera | 60–120 | no mezclar marcas ni pilas nuevas con usadas |
| 29 | — | Cable blindado 2 conductores, 28 AWG, OD ≤ 3 mm, flexible trenzado, 1 m | 1 | Steren (cable de micrófono), AG | 20–40 | **crítico**, se corta a 450 ± 50 mm. No sirve el de 1 conductor |
| 30 | — | Protoboard 830 pts + jumpers | 1 | AG, ML | 120–180 | $0 si ya lo tienes |
| 31 | — | Perfboard 50 × 70 mm (versión final) | 2 | AG, ML | 20–40 | placa final, cabe en la caja |
| 32 | — | Resistencia 10 Ω 5 W (carga de prueba) | 1 | AG | 8 | para la puesta en marcha sin arriesgar la bocina |
| 33 | MK2 | **TOA SC-615, trompeta re-entrante, 8 Ω, 15 W, 112–113 dB pico (1 W/1 m)** | 1 | distribuidor de audio profesional | 900–2,000 | **crítico y bloqueante de compra — ver `puerta-de-compra-transductor.md`** |

**Subtotal electrónica sin transductor: ~$420–750 MXN.** Versión frugal (si ya tienes protoboard,
transistor y resistencias comunes de banco): **~$205–615 MXN**, ahorro estimado $135–215 MXN.
**Total electrónica + transductor: ~$1,320–2,750 MXN** contra el techo de $2,500 MXN.

## Escenarios de presupuesto (electrónica + mecánica + transductor)

| Escenario | Electrónica | Mecánica | Transductor | **Total** | vs. techo $2,500 |
|---|---|---|---|---|---|
| Optimista (BOM frugal + trompeta barata) | 205 | 355 | 900 | **1,460** | sobran ~1,040 |
| Medio / realista | 585 | 437 | 1,350 | **2,372** | sobran ~128, ajustado |
| Peor caso (BOM alto + mecánica alta + trompeta al tope) | 750 | 520 | 2,000 | **3,270** | **excede por ~770** |

El peor caso combinado excede el techo. La mitigación es cotizar la trompeta de mostrador **antes**
de comprar cualquier otra cosa — ver `puerta-de-compra-transductor.md`, que incluye la compuerta de
presupuesto con el umbral de $1,800 MXN.
