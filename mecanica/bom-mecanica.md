# BOM de mecánica — Megáfono Analógico

**Alcance:** lista de materiales del cuerpo portátil, Ruta A (trompeta de fábrica comprada).
Documento generado 2026-09-30. Precios **estimados, sin cotizar de mostrador, consultados el
2026-09-30** — cotiza en tu localidad antes de comprar. Columna "frugal" = mínimo si se recicla caja
y strap. **Antes de comprar nada de esta lista, ejecuta la compuerta de presupuesto de
`hardware/puerta-de-compra-transductor.md` — la trompeta se cotiza primero.**

| # | Item | Especificación | Cant | Dónde | $MXN est. | Frugal |
|---|---|---|---|---|---|---|
| 1 | Pino cepillado 1×2" | 19 × 38 mm, 1 m (espina 330 + empuñadura 110) | 1 | maderería / ferretería | 45 | 45 |
| 2 | Filamento PETG | ~70 g | — | ya lo tienes / servicio | 0–150 | 0 |
| 3 | Grommet de hule de panel | OD 14–16 / ID 9.5, barreno 12.5 mm | 2 (1 repuesto) | eléctrico / tlapalería | 15 | 15 |
| 4 | Arandela neopreno/EPDM | OD18 / ID6 / t3 mm | 6 | tlapalería; o cortadas de cámara de llanta | 25 | 0 |
| 5 | Tubo de silicón | ID5 / OD8, 100 mm (bujes de perno) | 1 | acuario / ferretería | 20 | 20 |
| 6 | Perno M5 × 70 + 2 rondanas + nylock | empuñadura | 2 | tornillería | 30 | 30 |
| 7 | Perno M5 × 60 + 2 rondanas + nylock | bracket de trompeta (**largo por verificar contra la unidad real**) | 2 | tornillería | 30 | 30 |
| 8 | Perno M4 × 45 + 2 rondanas + nylock | pie del boom | 2 | tornillería | 20 | 20 |
| 9 | Tornillo M3 × 12 autorroscante | jaula al boom | 2 | tornillería | 10 | 10 |
| 10 | Tornillo madera #6 × 16 + rondana | portapilas y caja | 6 | tornillería | 20 | 20 |
| 11 | Armella / screw eye Ø4 mm | anclajes de strap | 2 | tlapalería | 15 | 15 |
| 12 | Banda nylon 25 mm × 1.2 m + 2 mosquetones | strap | 1 | mercería / Steren | 70 | 0 (reciclar) |
| 13 | Caja de proyecto ABS | ~100 × 60 × 35 mm, con barreno Ø15.2 mm para el pasacable (fila 20) en la cara que mira a la trompeta | 1 | Steren / electrónica local | 60 | 0 (reciclar) |
| 14 | Portapilas 6×AA cerrado | arreglo 2×3, tapa con tornillo | 1 | Steren / Amazon MX | 80 | 80 |
| 15 | Espuma de celda abierta | recorte 50×50×10 mm (antifona) | 1 | tapicería / recorte | 10 | 0 |
| 16 | Cintas de amarre 100 mm + bases adhesivas | ruteo de cable | 10 | eléctrico | 20 | 20 |
| 17 | Perfil de canto / tubo de silicón partido, 1 m | solo si el canto del flare está filoso | 1 | ferretería | 30 | 30 |
| 18 | Lija 120 y 220 | acabado, canto de la jaula | 2 | tlapalería | 20 | 20 |
| 19 | Cable de la trompeta | La SC-615 trae **cable integral de PVC Ø6 mm × 600 mm con alivio de tensión** (hoja TOA SC-615, págs. 2 y 4). En el plano de la pág. 3, los 600 mm y los 100 mm de conductores sueltos van entre paréntesis: son de referencia. **Mide el tuyo con la trompeta en la mano, en la puerta de compra**: diámetro con vernier y largo de chaqueta, de la salida en la trompeta a donde empiezan los conductores sueltos; se espera ~500 mm de chaqueta + ~100 mm de conductores sueltos. Ese es el cable a la placa: **no se corta ni se cambia en la trompeta**. Forma el bucle libre (radio ≥ 36 mm) antes de la primera cinta. Cable de 2 conductores 20 AWG **con chaqueta redonda de 4–8 mm** (el rango del pasacable) solo como **extensión**, si el recorrido de la cota G9 no cabe en tu chaqueta: empalme soldado con termofit, **a ≥ 100 mm después del bucle y amarrado a la espina**, nunca dentro del bucle | 1 | incluido con MK2 (extensión: eléctrico) | incluido | incluido |
| 20 | Pasacable (prensaestopa) PG9 de nailon con contratuerca | Rango de sujeción que **incluya el diámetro que mediste del cable** (PG9 típico: 4–8 mm); rosca y barreno Ø15.2 mm. Alivio de tensión del cable de la trompeta, en la cara de la caja que mira a la trompeta. Si tu cable queda fuera de ese rango, compra el pasacable cuyo rango sí lo incluya y barrena el diámetro de su rosca | 1 | electrónica local / ferretería eléctrica | 10–25 | 10–25 |
| | **TOTAL** | | | | **~$545** | **~$365** |

Las filas 19 y 20 son las filas 50 y 51 del BOM del manual de armado.

## Presupuesto combinado con electrónica y transductor

| Rubro | Rango |
|---|---|
| Mecánica (esta lista) | $365–545 |
| Electrónica (sin transductor) | $205–750 (frugal ~$205–615; completa ~$420–750) |
| **Transductor TOA SC-615** | **$900–2,000** |
| **Techo del proyecto** | **$2,500** |

El escenario realista queda ajustado (~$2,372 calculado antes del pasacable, más sus $10–25) y el
peor caso combinado ($750 + $545 + $2,000) excede el techo por ~$795. No
hay margen para relajarse solo porque el techo subió de $1,500 a $2,500 — ver la compuerta de
presupuesto en `hardware/puerta-de-compra-transductor.md`.

**Orden de compra: la trompeta primero, por riesgo financiero, no por logística.** Es 60–70 % del
proyecto, proveedor único, en la práctica no retornable. Todo lo demás de esta lista es pasivo
genérico y herramienta reutilizable — dinero recuperable si algo no cierra.

## Herramienta necesaria (mecánica)

Serrucho, taladro con brocas 2.5 / 3 / 4.5 / 5.5 / 12.5 mm y broca escalonada (para el barreno
Ø15.2 mm del pasacable en la caja, y para agrandar el barreno del bracket si hace falta),
desarmadores, 2 llaves para M4/M5, llave ajustable (perica) para la contratuerca del pasacable, lija,
cúter, cautín, cinta métrica, vernier o calibrador (para medir el cable de la trompeta), lápiz
redondo (Ø ~7 mm; para hallar el punto de balance y para la cota G8), marcador para marcas testigo,
báscula (para pesar la trompeta al comprarla).
