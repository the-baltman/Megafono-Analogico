# Cuerpo portátil — Megáfono Analógico

**Alcance:** diseño mecánico del cuerpo, Ruta A (trompeta de fábrica comprada + cuerpo casero).
Documento generado 2026-09-30. La Ruta B (flare casero de PVC sobre un driver desnudo) está
documentada pero no forma parte del diseño entregable — no se incluye aquí; si la necesitas, no vive
en este repositorio de la entrega estándar.

## Arquitectura general

**Espina estructural de pino cepillado, 19 × 38 mm, 330 mm de largo** — no carcasa impresa. Una
carcasa impresa de ese largo tomaría 6–10 h de impresión (choca con la restricción de "una tarde de
armado"). El aluminio sería más rígido pero conduce vibración mucho mejor que la madera, y la
vibración estructural que viaja de la trompeta al micrófono es el riesgo que este diseño evita. El
pino corta con serrucho, acepta tornillo directo y da una cara de 38 mm donde montar todo.

```text
        boca de trompeta
        X = -170 mm                                            capsula
            |                                                  X = +360
            |          [ driver ]                                  o
         \__|__________/       \__                            ___/ | jaula
          \ |          \  horn  \ \                          /     | O58
           \|___________\_______/_/                    boom /      | rim
   ------------------------------------------------------------------------
   |========================= ESPINA PINO 330 mm ==========================|
   X=0        ^bracket        ^portapilas 6xAA (arriba)      ^pie del boom
              20-80            X 130-235                     X 240-300
              |
         [ caja circuito ]  (abajo, X 150-250)
              |
         [[ EMPUÑADURA ]]  (abajo, X ~85-135, posicion final por balanceo)
```

| Zona | X (mm) | Cara | Contenido |
|---|---|---|---|
| Bracket de trompeta | 20–80 | arriba | U-bracket de fábrica + stack de aislamiento |
| Empuñadura | ~85–135 | abajo | bloque de pino 110×38×30 mm. Posición por balanceo, no por plano |
| Caja del circuito | 150–250 | abajo/lado | caja ABS comprada |
| Portapilas 6×AA | 130–235 | arriba | portapilas cerrado, tapa atornillada |
| Pie del boom | 240–300 | arriba | 2 pernos M4 |
| Armellas del strap | 70 y 280 | lado | 2 armellas Ø4 mm |

## El boom del microfono — la pieza crítica

**Principio: la distancia boca-cápsula se fuerza con una pieza física, no se pide con instrucciones
de uso.** Un boom que permite 20 cm hace pitar el aparato. La solución es un tope físico: una
**jaula de voz** cuyo anillo de borde toca el labio o el mentón del usuario, con la cápsula fija a
30 mm por detrás de ese plano.

**Geometría del boom, calculada:** material PETG, sección del brazo 16×24 mm, pie de montaje
60×30×8 mm con 2 barrenos Ø4.5 mm a paso 40 mm, trayectoria de 60 mm horizontal → codo R15 → 100 mm a
55°, filete en la raíz R ≥ 5 mm obligatorio, impresión con 4 perímetros y 30 % relleno gyroid.

**Por qué jaula abierta de 3 costillas, no copa cerrada.** Una copa cónica cerrada de 30 mm de
profundidad tiene resonancia de cuarto de onda en $f = c/(4L) \approx 2.86$ kHz — dentro de la
banda de voz y justo en la ventana de 1–3 kHz donde el lazo de realimentación tiene su pico. La jaula
da el mismo tope físico sin cerrar el volumen. **Los huecos entre costillas NO se tapan, nunca**: en
uso real los labios cierran parcialmente el volumen, pero muy fugado (Q bajísimo), un bulto ancho y
amortiguado en vez de una resonancia aguda. Cerrarlos con cinta, espuma o una pieza impresa reconstruye
exactamente el problema que se evitó.

## Cotas de la jaula de voz

| Elemento | Cota | Tolerancia |
|---|---|---|
| Placa trasera | disco Ø22 × 3 mm, barreno central para el grommet | Ø12.5 +0.2/−0 |
| Costillas | 3 piezas, 3 × 2.5 mm, a 120° | ±0.5 mm |
| Orientación de costillas | una abajo (hacia el mentón), dos arriba a los lados — arco superior abierto para la nariz | diseño |
| Largo de costillas | **30 mm** | **±1 mm — esta sí importa** |
| Anillo de borde | Ø exterior 58 mm, ancho 4 mm | ±3 mm |
| Canto del anillo | radio completo R2, lijado 220 | obligatorio: toca la cara |
| **Cápsula → plano del borde** | **30 mm** | **±3 mm. Cota de control del proyecto** |
| Unión a la punta del boom | encastre Ø20 mm + tornillo M3×12 autorroscante | holgado |

## Desacoplamiento elástico de la cápsula — cuatro etapas en serie, ninguna opcional

El margen aéreo contra el pitido (~37 dB) no cubre el camino estructural: vibración de la trompeta →
bracket → espina → boom → cápsula, que puentea ese margen por completo.

**Etapa 1 — aislar la trompeta de la espina** (la de mayor palanca, aguas arriba de todo). Stack por
cada perno del U-bracket, de arriba abajo: rondana de acero, arandela de neopreno OD18/ID6/3mm,
U-bracket (con buje de silicón ID5/OD8 dentro del barreno — el perno no toca el metal), arandela de
neopreno, cara superior de la espina, rondana de acero, tuerca nylock. Barreno del bracket ≥ 8.5 mm
para alojar el buje (agrandar con broca escalonada si el de fábrica es de 7 mm — **verificar contra
la unidad real comprada**). **Apretar solo hasta que el neopreno pase de 3.0 a 2.0 ± 0.3 mm, no más**
— sobre-apretar cortocircuita el aislador. Verificación a mano: la trompeta debe poder mecerse ~1 mm.

**Etapa 2 — suspender la cápsula** (nada rígido la toca). Grommet de hule de panel, OD 14–16 / ID
9.5 mm, para barreno de panel 12.5 mm, pared 1.5–2 mm. La cápsula entra a presión con 0.1–0.3 mm de
aprieto — se mete con la mano, sin herramienta ni pegamento. **Ninguna parte metálica de la cápsula
toca PETG**, se comprueba a la vista.

**Etapa 3 — antifona de espuma.** Disco de espuma de celda abierta de 8 mm delante de la cápsula,
retenido por las costillas. Mata explosivas (p, t, b).

**Etapa 4 — desacoplar el cable** (la que todo mundo olvida). Bucle de servicio de 40 mm libre
inmediatamente después del grommet. Primera cinta de amarre a 50 mm de la cápsula, sobre el brazo —
nunca amarrar en la cápsula. Cable blindado 2 conductores, 28 AWG, flexible trenzado, no rígido.

**Lo que se puede afirmar con estas cuatro etapas: ≥25 dB de atenuación estructural, pero solo en la
banda 1–3 kHz.** A 390 Hz (resonancia propia del boom) no se afirma atenuación —el boom amplifica ahí
por su propio factor de calidad—, pero es irrelevante porque a 390 Hz el lazo acústico casi no tiene
ganancia (la trompeta no radia bajo su corte de 280–486 Hz, y la electrónica corta en ~340 Hz). Un
pico de vibración donde el lazo no tiene ganancia no hace oscilar el sistema.

## Empuñadura y balanceo

Bloque de pino de recorte, 110×38×30 mm, cantos redondeados R8, lijado 220. Sujeción: 2 pernos M5×70
mm atravesando espina + bloque, rondana arriba y abajo, tuerca nylock, paso de pernos 70 mm.

**CG calculado con la masa verificada de la trompeta (1.1 kg de hoja de datos TOA):**

| Item | masa (g) | X (mm) | momento (g·mm) |
|---|---|---|---|
| trompeta + driver + bracket | 1100 | 60 | 66,000 |
| espina de pino | 119 | 165 | 19,635 |
| portapilas + 6 AA | 183 | 183 | 33,489 |
| caja + circuito | 110 | 200 | 22,000 |
| boom + jaula + cápsula | 75 | 300 | 22,500 |
| tornillería, cable, armellas | 90 | 180 | 16,200 |
| **suma (sin empuñadura)** | **1677** | | **179,824** |

**CG en X = 179,824 / 1677 = 107.2 mm. Masa total con empuñadura (63 g) = 1.74 kg.**

**Restricción de orden de armado: los barrenos de la empuñadura se taladran al final**, con todo
montado y las pilas puestas, apoyando la espina sobre un lápiz redondo para hallar el punto de
balance — no se taladran al inicio sobre un plano, porque el CG barre ~37 mm según la masa real de
la trompeta que se compre.

**Strap obligatorio, no accesorio.** 2 armellas Ø4 mm en la cara lateral (X = 70 y X = 280) + banda de
nylon 25 mm × 1.2 m con 2 mosquetones. Con el strap puesto, el aparato cuelga con la boca hacia
adelante, **nunca hacia la oreja del usuario**. 1.74 kg sostenidos con una mano a ~23 cm del cuerpo no
es cómodo más de uno o dos minutos.

## Alojamiento del circuito y del portapilas

Caja del circuito: se compra, no se imprime (caja de proyecto ABS ~100×60×35 mm exterior). Montaje:
2 tornillos #6×16 mm con rondana, desde dentro de la caja hacia la espina.

Portapilas 6×AA: cerrado, arreglo 2×3, tapa retenida por tornillo (no por fricción — en una caída las
pilas se salen). Montado en la cara superior, tapa hacia arriba.

**Flag eléctrico:** muchos portapilas de 6×AA traen switch deslizante integrado. Ese switch pelea con
el presupuesto de 0.3 Ω del camino de alimentación (ver `hardware/presupuesto-de-potencia.md`). Si el
portapilas trae switch, **puentearlo** y usar SW1 real aparte.

## Piezas impresas

Solo dos piezas, todo lo demás es stock o comprado.

| Pieza | Material | Orientación | Perímetros | Relleno | Tiempo est. |
|---|---|---|---|---|---|
| Boom | **PETG** | **acostado, toda la curva en el plano XY de la cama** | 4 | 30 % gyroid | ~2.5 h |
| Jaula de voz | PETG | anillo de borde sobre la cama | 4 | 20 % | ~40 min |

**Por qué PETG y no PLA:** un interior de coche puede pasar de 60–70 °C. La Tg del PLA es ~60 °C: el
boom se pandea permanentemente y la cota crítica de 30 mm se pierde. PETG tiene Tg ~80 °C, mejor
resistencia al impacto y menos creep bajo carga sostenida.

**La instrucción de orientación que no se puede saltar:** el boom se imprime **acostado**, con toda
su curva en el plano de la cama. Así los planos de capa quedan paralelos al plano de flexión. Si se
imprime parado, la raíz falla en la primera línea de capa la primera vez que el aparato se apoya
sobre el boom.

**Si no tienes impresora:** boom en solera de aluminio 3/4"×1/8" (19×3 mm) doblada en frío, o tubo
cuadrado de aluminio de 13 mm — más rígido y más conductor de vibración, así que el grommet de la
cápsula se vuelve obligatorio sin margen para omitirlo. Jaula en anillo de PVC de 2" cortado a 4 mm +
3 varillas de alambre de 2.5 mm + disco de PVC con barreno de 12.5 mm.

## Seguridad — resumen mecánico

| Riesgo | Mitigación de diseño |
|---|---|
| Ruido a terceros: 102 dB a 1 m, ~122 dB a 25 cm | Ver la advertencia acústica en `README.md`. Nunca apuntar a una cara a menos de 1 m |
| La trompeta girando hacia la cabeza del usuario | Apretar a fondo la mordaza de inclinación (esa no va aislada) + marca testigo |
| Canto filoso del flare de la trompeta | Inspeccionar y limar, o poner perfil de canto / tubo de silicón partido |
| Borde de la jaula contra la cara | R2 completo + lija 220, obligatorio |
| Rosca expuesta de la empuñadura | Cortar a ras o tuerca de bellota |
| Astillas de pino | Lijar 120 → 220 todas las caras y cantos |
| Pilas | Terminales no expuestas, tapa atornillada (no de fricción), switch real |
