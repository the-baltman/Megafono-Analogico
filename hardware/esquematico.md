# Esquemático — Megáfono Analógico

**Alcance:** diseño electrónico entregable, 8 Ω, aprobado por el gate de C Morty. Documento generado
2026-09-30. Este es el circuito completo: micrófono, preamplificador y etapa de potencia. Si llegaste
aquí desde un código QR de un paso de armado, este documento se sostiene solo — no necesitas tener
abierto ningún otro archivo para entender las conexiones.

---

## Diagrama de bloques

```text
  6xAA (9.0 V)      SW1        F1 0.75A                    V+ = 9.0 V
   +--------+      _/_      +--[polyfuse]--*----------------------------> U1 pin 6
   | 6 x AA |-----o   o-----+              |
   +--------+                          [C7] 1000u   [C8] 100n
       |  (-)                              |            |
       *-------------------- STAR GND ------*------------*----------> U1 pin 4
                                            |
                                     [R1] 470  (filtro de rail de señal)
                                            |
                                            *---- V_A = 8.46 V -----> MK1 y Q1
                                            |
                                        [C1] 220u
                                            |
                                          STAR GND

   MK1 electret --> Q1 (CE, +21.6 dB) --> RV1 10k log --> U1 LM386N-3 --> bocina 8 ohm
   -44 dBV/Pa        LP 4.1 kHz          volumen         26 o 46 dB       HP 199 Hz
                                         (en panel)      B = normal
   Cadena completa: Config A = 46.2 dB  ·  Config B = 66.2 dB (la de trabajo)
```

Flujo de señal de izquierda a derecha, alimentación arriba, masa abajo. **La masa es estrella en un
solo punto físico**, junto al pin 4 de U1 — ver la sección de masa más abajo. No es estética: es la
diferencia entre que el circuito funcione limpio y que produzca un sonido de motor fuera de borda
("putt-putt") que no se apaga tapando el micrófono.

---

## Bloque A — Micrófono y su rail filtrado

```text
                    V+ = 9.0 V
                        |
                      [R1] 470 ohm 1/4W
                        |
        V_A = 8.46 V ---*---------------*-------> a Bloque B (R3, R5)
                        |               |
                     [C1] 220u/16V   [R2] 2.2k 1/4W
                        |               |
                       GND              *---- V_drain = 7.36 V
                                        |
                                        |  <-- nodo de ALTA IMPEDANCIA (~2 kohm):
                                        |      aqui entra todo el zumbido
                                     [MK1] electret CMA-4544PF-W
                                        |      (+ = terminal aislada,
                                       GND      - = carcasa metalica)

        Acoplo a la base de Q1:
        V_drain ----[C2] 100n ----> base de Q1      (f_HP = 111 Hz)
```

MK1 es una cápsula electret CMA-4544PF-W, Ø9.7 × 4.5 mm, 2 terminales. R2 = 2.2 kΩ conserva la
impedancia de carga de la hoja de datos del fabricante (2.2 kΩ), condición bajo la cual está
especificada la sensibilidad de −44 dBV/Pa. R1 + C1 filtran el rail de alimentación de MK1 y Q1:
sin este filtro, el rizo de alimentación de U1 (picos de 330 mA) entraría por el sesgo del micrófono
y se amplificaría 46–66 dB. Atenuación de este filtro a 300 Hz: **−45.8 dB**.

## Bloque B — Preamplificador de un transistor (emisor común)

```text
              V_A = 8.46 V
                  |
        *---------*---------*
        |                   |
     [R3] 82k            [R5] 4.7k
        |                   |
        |   V_B=1.79V       *---- V_C = 5.80 V ---[C5] 220n --> RV1
        *---+---------------|--+
        |   |               |  |
     [R4] 22k           C  /   [C4] 12n  (paso bajas, f = 4.14 kHz)
        |   |              /    |
        |   +--[C2]--> B  |Q1  GND
        |     100n         \   2N3904
        |                 E \
        |                   |
        |                   *---- V_E = 1.14 V
        |                   |
        |                [R6] 220 ohm      <-- SIN bypass: aqui se fija la ganancia
        |                   |
        |                   *----------+
        |                   |          |
        |                [R7] 1.8k  [C3] 22u/16V
        |                   |          |
        *-------------------*----------*
        |
       GND (estrella)
```

Punto de operación: V_B = 1.79 V, V_E = 1.14 V, I_C ≈ 0.565 mA, r_e = 46 Ω, V_C = 5.80 V. La carga
que ve el colector **en AC** no es R5 sola: RV1 (10 kΩ) cuelga del colector a través de C5, así que
**R_ac = R5 ‖ RV1 = 4.7k ‖ 10k = 3.20 kΩ**. Con esa carga:

$$A_{v1} = \frac{R_{ac}}{r_e + R6} = \frac{3197}{266} = 12.02 \Rightarrow \mathbf{21.6\ dB}$$

R6 (220 Ω) no lleva capacitor de desvío: la ganancia queda fijada por dos resistencias, no por la
corriente de colector ni por beta del transistor. Pinout del 2N3904 (TO-92, cara plana hacia el
armador, patas hacia abajo, de izquierda a derecha): **Emisor, Base, Colector**. Verificar con
probador de diodos antes de soldar.

## Bloque C — Etapa de potencia LM386N-3

```text
        LM386N-3 (DIP-8, vista superior, muesca a la izquierda)
            +----U----+
   GAIN  1 -|         |- 8  GAIN
    -IN  2 -|         |- 7  BYPASS
    +IN  3 -|         |- 6  V_S
    GND  4 -|         |- 5  V_OUT
            +---------+
```

```text
                                          V+ = 9.0 V
                                              |
   de C5                                      |          +--- JP1 / C10 ---+
     |        RV1 10k log                     |          |  (ver ganancia)  |
     *--------[ \ ]                           |          |                  |
              |  \___ wiper ___             pin 6      pin 1              pin 8
              |                |              |          |                  |
             GND               |        +-----*----------*------------------*
                               +----> pin 3   |      U1  LM386N-3
                                              |
                        GND ----------> pin 2 |
                                              |
                   STAR GND ----------> pin 4 |
                                              |
                                        pin 7 *--[C9] 10u/16V----> STAR GND
                                              |
                                        pin 5 *--[C11] 100u/16V--> (+) BOCINA 8 ohm
                                              |                          |
                                              *--[R8] 10 ohm 1/2W        |
                                              |                          |
                                           [C12] 47n                     |
                                              |                          |
                                         STAR GND <--------------------- (-) BOCINA

   En el pin 6, físicamente pegados al chip:  [C7] 1000u/16V low-ESR  y  [C8] 100n cerámico
```

| Red | Valor | Función |
|---|---|---|
| R8 + C12 (Zobel) | 10 Ω + 47 nF | mantiene la carga resistiva en HF y evita oscilación por la inductancia de la bocina y del cable |
| C9 (pin 7, bypass) | 10 µF | PSRR 50 dB; sin él, el rizo del rail entra directo al lazo interno del IC |
| C7 | 1000 µF/16 V low-ESR | convierte el pico de 330 mA en rizo pequeño |
| C8 | 100 nF cerámico | mata el transitorio de conmutación de alta frecuencia del par de salida |
| C11 | 100 µF/16 V | acoplo de salida, paso altas a 199 Hz |
| RV1 | 10 kΩ log (audio) | volumen; también es la carga AC del colector de Q1 |

**Ganancia de U1, dos posiciones, las dos con respaldo de hoja de datos del fabricante:**

| Config | JP1 pines 1-8 | A_V | dB | Cuándo |
|---|---|---|---|---|
| **A** | abierto | 20 | **26** | arranque de puesta en marcha; salida si Config B silba |
| **B** | C10 = 10 µF, + a pin 1 | 200 | **46** | **configuración normal de trabajo** |

Cadena completa: **Config A = 46.2 dB · Config B = 66.2 dB.** Ver `presupuesto-de-ganancia.md` para
la derivación completa y por qué Config B —no A— es la configuración normal.

## La masa en estrella

Un único punto físico reúne, y solo reúne: pin 4 de U1, (−) de C7, (−) de la bocina, (−) de C12
(Zobel) y (−) del paquete de pilas. Ningún otro retorno de masa lo toca por un camino distinto. El
retorno de la bocina lleva picos de 330 mA; si comparte camino resistivo con la masa de señal del
micrófono, la caída resultante se amplifica 46–66 dB y produce un motorboating que **no** se apaga
tapando el micrófono — a diferencia del pitido acústico real.

## Respuesta en frecuencia — banda 300 Hz–4 kHz

| Polo | Elemento | f | Aporte a 300 Hz |
|---|---|---|---|
| Paso altas | C11 100 µF (8 Ω bocina) | 199 Hz | −1.58 dB |
| Paso altas | C2 100 nF | 111 Hz | −0.56 dB |
| Paso altas | C5 220 nF | 49 Hz | −0.12 dB |
| Paso altas | C3 22 µF | 31 Hz | −0.05 dB |
| Paso bajas | C4 12 nF | 4.14 kHz | — |

Esquina compuesta de paso altas ~340 Hz. Deliberado: la trompeta no radia por debajo de su propio
corte (280–486 Hz), así que recortar ahí no cuesta SPL útil y compra margen contra el pitido.
