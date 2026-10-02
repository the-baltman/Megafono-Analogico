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
El cable de la trompeta cruza esta etapa: es PVC de 6 mm, unas 20 veces más rígido que un par de
20 AWG (estimado). Si va tenso o amarrado cerca de su salida, conecta la trompeta a la espina por
fuera de las arandelas de neopreno. Por eso se deja en un bucle libre de radio ≥ 36 mm (ver "Cable de
la trompeta", abajo), y la prueba V1 tiene un paso que lo comprueba.

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
2 tornillos #6×16 mm con rondana, desde dentro de la caja hacia la espina. Lleva un barreno Ø15.2 mm
para el pasacable PG9 (`bom-mecanica.md`, fila 20) en la cara que mira a la trompeta.

**Barreno del pasacable, antes de meter la perfboard en la caja:** presenta dentro de la caja la
perfboard y el pasacable con su contratuerca. Entre el extremo interior del pasacable y la placa o
cualquier componente tiene que quedar espacio para que la chaqueta asome 5–10 mm y los dos
conductores doblen hacia la placa sin forzarse. **Si no cabe, PARAR y consultar.** Si cabe, barrena
con la broca escalonada el diámetro de la rosca del pasacable (Ø15.2 mm para PG9) en la cara de la
caja que va a mirar a la trompeta, a media altura de esa cara. Quita la rebaba con lija 220, monta el
cuerpo del pasacable con la contratuerca por dentro y deja el capuchón suelto.

## Cable de la trompeta

La SC-615 trae cable integral de PVC Ø6 mm con alivio de tensión (hoja TOA SC-615, págs. 2 y 4); sale
por la parte baja de la tapa trasera de la trompeta y es el cable a la placa: no se corta ni se
cambia en la trompeta. La hoja marca la polaridad: **negro = (+), "Hot"; blanco = (−), "Com"**. Es
al revés de la costumbre y del portapilas de este mismo aparato, donde el negro es el negativo.

**Ruteo, antes de atornillar la caja de circuito.** El cable del micrófono va por el lado izquierdo de
la espina; el cable de la trompeta y el de las pilas, por el lado derecho. Si se cruzan en algún
punto, que sea a 90°, nunca en paralelo. En este orden:

1. No lo jales ni lo dobles pegado a la salida de la trompeta: ahí está su alivio de tensión.
2. Forma un **bucle libre en omega**: tres cuartos de vuelta alrededor del núcleo de cartón de un
   rollo de cinta canela o masking (~76 mm de diámetro). El cable nunca debe quedar más cerrado que
   ese núcleo (radio ≥ 36 mm). El bucle queda en el aire, detrás del bracket, y **no toca el bracket,
   los pernos, las tuercas ni la espina** (cotas G7 y G8).
3. Después del bucle, llévalo por el costado derecho de la espina, pegado a la arista superior y
   lejos de la zona de agarre, hasta la cara de la caja que mira a la trompeta.
4. **Todavía no le pongas ninguna cinta de amarre:** se amarra con la inclinación ya fijada (punto 7).
5. **SW1 en OFF y sin pilas.** Pasa primero el capuchón del pasacable por los conductores sueltos;
   luego mete el cable por el pasacable hasta que la chaqueta asome 5–10 mm adentro. Aprieta el
   capuchón hasta que el cable no se deslice al jalarlo con los dedos, sin hundir la chaqueta.
6. Suelda el conductor **negro** (+, "Hot") al nodo SAL, la pata (−) de C11, y el conductor
   **blanco** (−, "Com") al punto estrella, con ~30 mm de holgura. Dentro de la caja, llévalos
   directo, sin correr junto a los cables de RV1 ni al del micrófono.
   Verificación: con SW1 en OFF, entre SAL y el punto estrella el óhmetro lee **5–7 Ω** (la
   trompeta); el recorrido, de la salida de la trompeta al pasacable con el bucle incluido, no pasa
   del largo de chaqueta medido menos 50 mm (cota G9).
7. Con la inclinación de la trompeta ya fija, pon la primera cinta a **60–70 mm** de donde termina el
   bucle (nunca más cerca) y las demás cada 80 mm. Aprieta cada cinta solo hasta que no se deslice,
   sin hundir la chaqueta. Si después cambias la inclinación, corta primero la primera cinta: si no,
   el cable jala la trompeta y anula el aislador.

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
| Cable de la trompeta rígido (PVC Ø6 mm), que hace resorte: se engancha con la ropa, el strap o la mano y jala el aparato; si se cierra de más, se daña | No cerrarlo a menos de radio 36 mm; no jalar la trompeta del cable ni colgar nada de él; fuera del bucle, mantenerlo a menos de 50 mm de la espina (cota G10) |
| Rebaba en el barreno de la caja y en el pasacable: cortes al armar; la rebaba también corta la chaqueta del cable | Lija 220 en el barreno antes de montar el pasacable |
