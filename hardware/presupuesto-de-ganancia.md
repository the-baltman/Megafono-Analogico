# Presupuesto de ganancia — Megáfono Analógico

**Alcance:** derivación completa, dB por dB, de la ganancia de la cadena de audio del diseño
entregable (8 Ω). Documento generado 2026-09-30, verificado en el gate y el re-gate de C Morty
(arbitraje A8: 21.6 dB, no 21.8 dB — el hallazgo físico de fondo no cambió, solo el último dígito de
la aritmética). Referencias de componentes según `esquematico.md`.

## La cadena, etapa por etapa

| # | Etapa | Ganancia | Estado |
|---|---|---|---|
| 1 | MK1 CMA-4544PF-W: −44 dBV/Pa = 6.31 mV rms a 94 dB SPL | referencia | verificado (hoja CUI) |
| 2 | Pérdida de carga MK1 (2.2 kΩ) → Z_in de Q1 (12.1 kΩ): 12.1/14.3 = 0.846 | **−1.4 dB** | derivado |
| 3 | Q1 emisor común, con carga AC de 3.20 kΩ | **+21.6 dB** | derivado |
| 4 | RV1 al máximo | 0 dB | |
| 5a | U1 Config A | **+26.0 dB** | verificado (hoja TI) |
| 5b | U1 Config B | **+46.0 dB** | verificado (hoja TI) |
| | **TOTAL Config A** | **+46.2 dB (×204)** | |
| | **TOTAL Config B** | **+66.2 dB (×2042)** | |

**De dónde sale la ganancia del preamplificador (Q1):** la carga que ve el colector en corriente
continua es R5 = 4.7 kΩ (fija el punto de operación), pero en **corriente alterna** el
potenciómetro RV1 de 10 kΩ cuelga del colector a través del capacitor de acoplo C5, así que la carga
real de señal es R_ac = R5 ‖ RV1 = 3.20 kΩ:

$$A_{v1} = \frac{R_{ac}}{r_e + R6} = \frac{3197}{266} = 12.02 \Rightarrow \mathbf{21.6\ dB}$$

con $r_e = 26\,\text{mV}/I_C = 46\ \Omega$ (I_C = 0.565 mA, del punto de operación de Q1) y R6 = 220 Ω
sin capacitor de desvío. El error del primer borrador de esta cuenta (24.9 dB) venía de usar la carga
DC (R5 sola) en vez de la carga AC — dos tablas del mismo documento usaban dos impedancias distintas
para el mismo nodo.

## Cuánta ganancia hace falta

Potencia limpia de diseño 0.431 W en 8 Ω → V_out = √(0.431 × 8) = **1.857 V rms** (2.63 V pico).
Ganancia requerida = 1.857 V / tensión que entrega la cápsula a ese nivel de SPL.

| SPL en la cápsula | V de MK1 | Ganancia requerida | Config A (46.2 dB) | Config B (66.2 dB) |
|---|---|---|---|---|
| 105 dB (grito a 2 cm) | 22.4 mV | 38.4 dB | +7.8 dB de sobra | +27.8 dB |
| 100 dB | 12.6 mV | 43.4 dB | +2.8 dB de sobra | +22.8 dB |
| 94 dB | 6.31 mV | 49.4 dB | **−3.2 dB: no alcanza** | **+16.8 dB** |
| 90 dB (voz fuerte a 5 cm) | 3.98 mV | 53.4 dB | −7.2 dB: no alcanza | **+12.8 dB** |
| 85 dB (voz normal cerca) | 2.24 mV | 58.4 dB | −12.2 dB: no alcanza | **+7.8 dB** |
| 75 dB (voz normal a 30 cm) | 0.71 mV | 68.4 dB | −22.2 dB | **−2.2 dB: no alcanza** |

**Config A entrega la potencia limpia completa a partir de 97.2 dB SPL en la cápsula** (hablar fuerte
a 2–3 cm). **Config B, a partir de 77.2 dB SPL** (voz normal de cerca).

## Conclusiones operativas

1. **Config B es la configuración normal de trabajo, no la reserva.** Config A queda 3.2 dB corta ya
   a 94 dB SPL en la cápsula: solo alcanza hablando fuerte y muy cerca. El manual de armado no puede
   prometer que Config A alcanza en uso normal.
2. **Config A se conserva por dos razones**: es el arranque seguro de la puesta en marcha (20 dB
   menos de ganancia de lazo mientras se verifica que todo está bien conectado), y es la salida si en
   el recinto real Config B silba o sisea demasiado. El precio de Config B es más siseo en los
   silencios — 20 dB más de ganancia con el volumen bajado.
3. **El techo útil de la cadena ya no es la ganancia disponible, es el margen contra la
   realimentación acústica.** El margen de lazo cae de ~32 dB a 2.5 cm de distancia boca-cápsula a
   ~14 dB a 20 cm. Config B tiene ganancia de sobra a 20 cm; lo que no alcanza ahí es la acústica.
   La distancia boca-cápsula la fija la mecánica (jaula del boom) en 30 ± 3 mm por esta razón.
4. **Reserva real de RV1:** con Config B y la cápsula a 3 cm de la boca (~95–100 dB SPL en la
   cápsula) sobran 17–23 dB, que es exactamente lo que RV1 recorta para recuperar margen contra el
   pitido. La cadena está dimensionada para trabajar con el potenciómetro a media carrera.
