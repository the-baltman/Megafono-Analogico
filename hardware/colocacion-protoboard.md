# Colocación en protoboard — Megáfono Analógico

**Alcance:** mapa de zonas y tabla de colocación para armar el circuito completo en protoboard,
como paso previo a soldarlo en perfboard. Documento generado 2026-09-30. Componentes según
`bom-electronica.md`, conexiones según `esquematico.md`.

Protoboard de 830 puntos (63 filas, columnas a-e / f-j, canal central, dos pares de rieles). Riel
superior = V+, riel inferior = GND **de señal**. **El GND de potencia no va por el riel** — usa el
punto estrella descrito más abajo.

## Mapa de zonas

```text
   fila 1 ............ 20 .......... 28 ...... 36 ......... 50 ...... 63
   +--------------------------------------------------------------------+
   | ZONA MIC/PREAMP     |  ZONA      | ZONA U1  |  ZONA SALIDA        |
   | MK1 (cable), R1,C1  |  RV1       | LM386    |  C11, R8, C12,      |
   | R2, C2, R3, R4, Q1  |  volumen   | C7,C8,C9 |  cables de bocina   |
   | R5, R6, R7, C3, C4  |            | C10/JP1  |                     |
   +--------------------------------------------------------------------+
     ^ entrada de baja senal, alta Z            ^ salida de 330 mA pico
     ----------- separacion fisica maxima: esto ES el diseno ------------
```

## Tabla de colocación

| Ref | Valor | De (fila/col) | A (fila/col) | Nota |
|---|---|---|---|---|
| R1 | 470 Ω | riel V+ | 4a | |
| C1 | 220 µF/16V | 4b (+) | riel GND (−) | revisar polaridad |
| R2 | 2.2 kΩ | 4c | 7a | |
| MK1 (+) | conductor 1 del cable de 2 vías | 7b | — | señal (drain de la cápsula) |
| MK1 (−) | conductor 2 del cable de 2 vías | riel GND | — | retorno de la cápsula. No es la malla |
| Malla del cable | blindaje | riel GND | — | aterrizada **solo en este extremo**. En el extremo de la cápsula queda al aire, aislada con termofit |
| C2 | 100 nF | 7c | 11a | no polarizado |
| R3 | 82 kΩ | 4d | 11b | del rail filtrado V_A |
| R4 | 22 kΩ | 11c | riel GND | |
| Q1 | 2N3904 | E=14a, B=11e, C=17a | — | base con probador de diodos; emisor y colector con el zócalo hFE, o con las lecturas de base y emisor del Paso 2 de `puesta-en-marcha.md` |
| R6 | 220 Ω | 14b | 16a | |
| R7 | 1.8 kΩ | 16b | riel GND | |
| C3 | 22 µF/16V | 16c (+) | riel GND (−) | puentea solo R7 |
| R5 | 4.7 kΩ | 4e | 17b | del rail filtrado V_A |
| C4 | 12 nF | 17c | riel GND | |
| C5 | 220 nF | 17d | 22a | |
| RV1 | 10k log | ext.3=22b, wiper=24a, ext.1=riel GND | — | ext.1 es el lado de "mínimo" (tope antihorario, visto de frente). Confirmar con óhmetro: a tope antihorario, cursor a riel GND ≈ 0 Ω. En la versión final va montado en el panel de la caja |
| U1 | LM386N-3 | pin1=e30, pin2=e31, pin3=e32, pin4=e33, pin5=f33, pin6=f32, pin7=f31, pin8=f30 | — | a caballo del canal, muesca hacia la fila 30 |
| — | puente | 24a (wiper) | e32 (pin 3) | cable corto |
| — | puente | e31 (pin 2) | riel GND | lo más corto posible |
| C10 | 10 µF/16V (Config B) | e30 (+, pin 1) | f30 (−, pin 8) | omitir en Config A |
| C9 | 10 µF/16V | f31 (+, pin 7) | riel GND (−) | |
| C7 | 1000 µF/16V | f32 (+, pin 6) | **punto estrella** | patas cortas, pegado al chip |
| C8 | 100 nF cerám. | f32 (pin 6) | **punto estrella** | |
| R8 | 10 Ω 1/2W | f33 (pin 5) | 40f | |
| C12 | 47 nF | 40g | **punto estrella** | |
| C11 | 100 µF/16V | f33 (+, pin 5) | 44f (−) | |
| Bocina (+) | conductor **negro** de la SC-615 ("Hot") | 44g | — | negro = (+): al revés que el portapilas |
| Bocina (−) | conductor **blanco** de la SC-615 ("Com") | **punto estrella** | — | no al riel |
| SW1 | interruptor | (+) de pila | F1 | en la versión final va en el panel de la caja |
| F1 | polyfuse 0.75 A, R_max ≤ 0.15 Ω | SW1 | riel V+ | va en la placa |
| Pila (−) | cable | **punto estrella** | — | |

## El punto estrella

```text
   Un solo punto físico: una fila libre, por ejemplo la 63, columnas a-e,
   a menos de 3 cm del pin 4 de U1.

        fila 63  ->  * -------- pin 4 de U1 (cable corto)
                     * -------- (-) de C7 1000u
                     * -------- C8 100n (pata de masa)
                     * -------- (-) de la BOCINA
                     * -------- (-) de C12 (Zobel)
                     * -------- (-) del PAQUETE DE PILAS
                     * -------- riel GND de señal (UN solo cable, aquí)
```

**Por qué.** Cada contacto de protoboard tiene 50–100 mΩ y los rieles son tiras largas. El retorno de
la bocina lleva picos de 330 mA. Si ese retorno comparte camino con la masa del micrófono,
330 mA × 50 mΩ = 16.5 mV de caída en el riel, que el micrófono ve como señal de entrada. A la
ganancia de este circuito eso se amplifica hasta 3.4 V a la salida en Config A y 34 V en Config B —
ambos números por arriba del recorte de 2.63 V pico. Se oye como un motor fuera de borda o un aullido
continuo que **no se apaga tapando el micrófono** (a diferencia del pitido acústico real). Con el
punto estrella, el retorno de potencia nunca pasa por la masa de señal.

## Los cuatro problemas reales de protoboard a esta ganancia

1. **Lazo de masa por el riel** (arriba). El más común y el que más se confunde con pitido acústico.
2. **Acoplamiento por cercanía.** El nodo MK1/base de Q1 es de ~12 kΩ: 10 cm de pata al aire captan
   campo de cables cercanos. Patas cortas; R2 y C2 pegados al extremo del cable del micrófono; el
   cable de bocina cruzando el del micrófono a 90°, nunca en paralelo.
3. **El cable del micrófono debe ser blindado de 2 conductores**, 28 AWG, 450 ± 50 mm, malla
   aterrizada solo en el extremo de la placa. Con un solo conductor la malla tendría que ser el
   retorno de la cápsula y llevaría corriente de señal en los dos extremos — la regla de "un solo
   extremo" se vuelve imposible de cumplir.
4. **La bocina no se apoya sobre el protoboard.** El imán del driver y sus cables irradian, y la
   vibración abre contactos.

**El protoboard no pasa la prueba de uso portátil.** Sus contactos de resorte se abren con vibración
y se oxidan; a 46–66 dB de ganancia, un contacto intermitente en el nodo del micrófono suena a
chicharra. El protoboard es para la puesta en marcha; el aparato que se carga en la mano va en
perfboard punto a punto, con un alambre desnudo grueso de masa recorriendo la placa hasta el punto
estrella.
