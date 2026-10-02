# Cotas de control — Megáfono Analógico

**Alcance:** medidas que se deben verificar antes de dar por buena la mecánica y antes de correr las
pruebas de `pruebas.md`. Documento generado 2026-09-30. Referencias de piezas según
`cuerpo-portatil.md`.

## Las diez cotas

| # | Qué | Cómo se mide | Criterio |
|---|---|---|---|
| G1 | Cápsula → borde de la jaula | regla | **30 ± 3 mm** |
| G2 | Distancia bocina → cápsula ($D_{\text{lazo}}$): plano de la boca de la trompeta hasta la cápsula | cinta métrica | **≥ 400 mm** |
| G3 | En uso, con el borde de la jaula apoyado en el labio: labios → cápsula | regla, aparato en posición de uso real | 25–35 mm |
| G4 | Metal de la cápsula contra PETG | inspección visual | ningún contacto |
| G5 | Mecido de la trompeta a mano | prueba manual, empujar suave el driver | ~1 mm, no rígida |
| G6 | Marcas testigo en todos los tornillos y pernos | inspección visual | presentes en todos |
| G7 | Bucle del cable de la trompeta | comparar con el núcleo de cartón de un rollo de cinta (~76 mm) | no queda más cerrado que el núcleo (radio ≥ 36 mm) |
| G8 | Cable de la trompeta, de su salida al fin del bucle | deslizar el lápiz redondo (Ø ~7 mm) entre el cable y el bracket, los pernos, las tuercas y la espina | el lápiz pasa en todo el tramo sin empujar el cable |
| G9 | Recorrido del cable, de su salida al pasacable, bucle incluido | hilo tendido sobre el aparato armado | ≤ largo de chaqueta medido − 50 mm |
| G10 | Zona de agarre | tomar la empuñadura como en uso | los dedos no tocan el cable |

## Por qué importa cada una

**G1** es la cota que decide el margen contra el pitido: la distancia entre la boca del usuario y la
cápsula del micrófono fija el término dominante del presupuesto de realimentación acústica
(20·log(D_lazo/D_S)). Un error de unos milímetros aquí cambia varios dB de margen.

**G2** es el otro lado de la misma ecuación: entre más lejos esté la cápsula de la bocina, dentro del
propio cuerpo del aparato, más margen hay contra el pitido. El diseño de la espina de 330 mm logra
~536 mm calculados; el criterio verificable con cinta métrica exige al menos 400 mm, que deja 22.5 dB
de margen por este término.

**G3** confirma que la geometría de G1 se traduce correctamente al uso real con el aparato en la
posición en que de verdad se sostiene, no solo en la mesa de trabajo.

**G4** verifica que la etapa 2 del desacoplamiento de vibración (el grommet) esté realmente haciendo
su trabajo: si hay contacto metálico rígido entre la cápsula y el PETG del boom o la jaula, la
vibración estructural de la trompeta llega directo a la cápsula sin pasar por ningún aislador.

**G5** verifica la etapa 1 del desacoplamiento (el stack de neopreno del bracket de la trompeta). Si
la trompeta está rígida —no se mece ~1 mm al empujarla con suavidad— el aislador está sobre-apretado
y funcionalmente anulado.

**G6** es la verificación de que ningún tornillo se aflojó durante el armado o el transporte. Es
gratis de revisar y es la primera señal de aflojamiento por vibración en las pruebas de campo.

**G7 y G8** protegen la etapa 1 del desacoplamiento por el lado del cable de la trompeta. Ese cable
es PVC de 6 mm, unas 20 veces más rígido a flexión que un par de 20 AWG (estimado). En bucle libre
no puentea el neopreno; tenso, amarrado cerca de su salida o apoyado en el bracket o la espina, sí
lo hace. G7 cuida que el bucle no se cierre de más (radio ≥ 36 mm) y G8, que no toque nada rígido
entre la salida y el fin del bucle. Después del bucle el cable va pegado a la arista de la espina:
ahí G8 ya no aplica.

**G9** comprueba que el cable integral alcanza el pasacable sin quedar tenso: el recorrido, bucle
incluido, tiene que caber en la chaqueta que mediste con 50 mm de holgura (≤ 450 mm si tu chaqueta
mide 500 mm). Si no cabe, se usa la extensión de la fila 19 de `bom-mecanica.md`.

**G10** comprueba que el cable no pase por la zona de agarre, donde la mano lo jalaría.

## Qué hacer si una cota falla

| Cota fuera de rango | Revisar |
|---|---|
| G1 fuera de 30 ± 3 mm | Reajustar el montaje del grommet en la placa trasera de la jaula; confirmar que el tornillo M3 de la jaula al boom esté bien asentado |
| G2 menor a 400 mm | Confirmar la posición real de montaje de la trompeta (X = −170 mm de diseño); si la trompeta comprada tiene otra profundidad de flare, la boca puede sobresalir más o menos de lo calculado |
| G3 fuera de 25–35 mm | Revisar que el anillo de la jaula apoye limpio en el labio/mentón sin holgura ni presión excesiva |
| G4 con contacto metal-PETG | Desmontar y volver a montar el grommet; verificar que no haya rebabas de impresión dentro del barreno Ø12.5 mm |
| G5 rígida | Aflojar el apriete del stack de neopreno hasta que el espesor comprimido vuelva a 2.0 ± 0.3 mm |
| G6 con marca rota | Ese tornillo se aflojó: reapretar y volver a marcar |
| G7 más cerrado que el núcleo | Rehacer el bucle en omega alrededor del núcleo de cartón (~76 mm), sin tirar de la trompeta |
| G8 con contacto | Abrir o reubicar el bucle para que quede en el aire, detrás del bracket; si la primera cinta está a menos de 60 mm del fin del bucle, cortarla y volver a ponerla a 60–70 mm |
| G9 mayor que la chaqueta medida − 50 mm | Usar la extensión de la fila 19 de `bom-mecanica.md`: empalme soldado con termofit, a ≥ 100 mm después del bucle y amarrado a la espina, nunca dentro del bucle |
| G10 con el cable bajo los dedos | Llevar el cable por el costado derecho de la espina, pegado a la arista superior, lejos de la empuñadura |
