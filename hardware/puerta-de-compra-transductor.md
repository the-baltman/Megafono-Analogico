# Puerta de compra del transductor (MK2) — Megáfono Analógico

**Alcance:** procedimiento obligatorio, con la trompeta ya en la mano, antes de destapar su caja o de
soldar nada. Documento generado 2026-09-30. El transductor especificado es **TOA SC-615, 8 Ω, driver
de compresión, 112–113 dB pico (1 W/1 m), 15 W**. Es el único componente crítico y de proveedor único
de todo el proyecto — sin él confirmado, no se arma el circuito.

## Compuerta de presupuesto — antes de comprar nada del proyecto

La trompeta es el 60–70 % del costo total del proyecto, de proveedor único y, en la práctica, no
retornable una vez fuera de la tienda. Todo lo demás del BOM es pasivo genérico o herramienta
reutilizable: dinero recuperable. El único orden de compra que deja a alguien a medias con dinero
gastado es comprar todo lo barato primero.

```text
PASO 1. Cotizar la TOA SC-615 de mostrador. COTIZAR, NO COMPRAR TODAVÍA.

PASO 2. <= $1,800 MXN  --> Comprar la trompeta primero, luego el resto del BOM.
        >  $1,800 MXN  --> PARAR. No comprar nada más. Avisar antes de seguir
                            y evaluar la salida alternativa de abajo.
```

**Salida alternativa** (solo si la cotización de la SC-615 excede $1,800 MXN): comprar una trompeta
de retail barata y **medirla** con sonómetro **clase 2**, exigiendo ≥103 dB/W medidos en 300 Hz–4
kHz. Regla de tamizado antes de pagar: rechazar cualquier producto que solo declare "PMPO", que
mencione "piezo" o "cristal", o que dé potencia sin impedancia — exigir que declare 8 Ω y potencia
RMS. **Esta salida no existe sin sonómetro clase 2 calibrado**: una aplicación de celular da ±5 a
8 dB de error sin calibrar, del tamaño de la incertidumbre completa que se quiere resolver.

## Los seis pasos de verificación, en este orden

1. **Multímetro primero, antes que cualquier papel.** Medir la resistencia DC entre las dos
   terminales del driver. **Esperado: 5–7 Ω.** Detecta por sí sola tres modos de falla aunque el
   vendedor se equivoque: la variante **SC-615M** con su transformador de línea todavía en el
   circuito (resistencia de cientos de ohms), una unidad **piezoeléctrica** (circuito abierto o
   megaohms), o una **impedancia equivocada** (4 Ω o 16 Ω dan lectura fuera de rango). **Si la
   lectura no cae en 5–7 Ω, PARAR** antes de seguir.
2. Confirmar que dice **"SC-615"** en el cuerpo o la caja — **no "TC-615"** (typo, otro producto) y
   **no "SC-615M"**.
3. Pedir la hoja de datos que acompaña la unidad y verificar que declare **"112 dB" o "113 dB"** como
   **nivel pico** ("peak level"), no como promedio, no como PMPO.
4. **Si la hoja del vendedor da otra cifra sin condición declarada** (por ejemplo "108 dB" a secas):
   **PARAR.** Confirmar contra la hoja oficial de TOA (toaelectronics.com) antes de continuar.
5. Confirmar **8 Ω** en etiqueta o hoja. Otra impedancia invalida el presupuesto de ganancia y el de
   potencia de este repositorio sin recalcular — no improvisar, detenerse y consultar.
6. **Con la trompeta sobre la mesa, aprovechar el momento**: anotar el patrón y el diámetro de
   barreno del U-bracket de montaje, y pesar la unidad completa. Es el único momento del proyecto en
   que la trompeta real está en la mano; estos dos datos son indispensables para `mecanica/
   cuerpo-portatil.md` y no se pueden posponer.

Si el paso 1 o el paso 4 fallan, **el circuito no se arma con esa unidad** hasta resolver la
discrepancia.

## SC-615M: por qué NO es una alternativa

**No es una versión "configurable" de la SC-615 — es otro producto.** La variante M lleva un
transformador de línea de 70.7 V / 25 V permanentemente cableado entre las terminales de entrada y el
driver de compresión. Conectar un amplificador directo a esas terminales pone el **primario del
transformador** frente a la salida de potencia, no el driver de 8 Ω: una carga mayormente reactiva,
de cientos de ohms a varios kilohms en la banda de audio, con riesgo de saturación de núcleo. Todo el
presupuesto de este repositorio (ganancia, potencia, red de Zobel) está construido sobre 1 W
entregado a una carga resistiva de 8 Ω — con el transformador en el camino, la sensibilidad en dB/W
deja de estar definida para este circuito.

**Si llega una SC-615M a la mano por error o confusión de modelo:**

- **(a) Primera opción, siempre: cambiarla por la SC-615 lisa.** Devolver una caja sellada es fácil;
  abrir una trompeta ya instalada no. Es exactamente la razón de que esta puerta esté antes de pagar.
- **(b) Solo si el cambio es imposible y se acepta modificar la pieza:** abrir la carcasa,
  desconectar por completo el transformador de línea (nunca dejarlo en paralelo ni usarlo como
  "atenuador"), cablear el amplificador directo a las dos terminales del driver, repetir la medición
  de 5–7 Ω del paso 1 sobre el driver ya desnudo para confirmar que quedó bien desconectado, y repetir
  la puesta en marcha completa (`puesta-en-marcha.md`) como si fuera una unidad nueva.
- **Cualquier otra cosa: parar y consultar.**

## Especificación final del transductor

| Campo | Valor | Fuente |
|---|---|---|
| Modelo | **TOA SC-615** (exacto) | — |
| Impedancia | 8 Ω | hoja TOA, verificado |
| Sensibilidad | **112 dB pico** (500 Hz–2.5 kHz), 113 dB en la página de producto de TOA | hoja TOA, verificado |
| Potencia | 15 W | hoja TOA |
| Respuesta | 280 Hz–12.5 kHz (double re-entrant) | hoja TOA |
| Masa | 1.1 kg (1.74 kg con el cuerpo completo montado) | hoja TOA |
