# Pruebas mecánicas — Megáfono Analógico

**Alcance:** pruebas para verificar el criterio "resiste uso portátil" en el subsistema mecánico.
Documento generado 2026-09-30. Correr después de verificar las cotas de `cotas-de-control.md`.
Las pruebas del subsistema eléctrico (criterios "amplifica sin distorsión" y "no oscila") están en
`hardware/puesta-en-marcha.md`.

**Nota:** la hoja de la SC-615 pide evitar los lugares que vibren mucho y da −20 a +55 °C. Un aparato
portátil, con caídas y que se queda en un coche al sol, trabaja fuera de esa especificación. D1, F1 y
C1 verifican que lo resista; no es un uso que TOA especifique.

## D1 — Caída funcional

**Verdad primero: con ~1.74 kg y una trompeta en voladizo, este aparato no sobrevive 1.2 m sobre
concreto sin daño.** El criterio se fija en lo defendible, no en lo ideal.

**Método:** 3 caídas desde **0.75 m** sobre piso de madera, o concreto con tapete de hule de 10 mm,
en 3 orientaciones: empuñadura abajo, boca de trompeta abajo, boom abajo.

**Aprueba si:** sigue funcionando · ninguna pieza impresa agrietada · ninguna marca testigo rota · la
cota G1 sigue en 30 ± 3 mm · ninguna pila desalojada · el pasacable no se aflojó y el cable de la
trompeta no se desplazó más de 1 mm respecto a su marca (la de la prueba 3.2b).

## D2 — Carga lateral del boom (estática)

**Método:** 30 N lateral en el borde de la jaula (colgar 3 kg, o empujar con báscula de gancho),
30 segundos.

**Aprueba si:** flecha ≤ 5 mm y recupera completo, sin grieta en la raíz. (Predicho por cálculo:
0.36 mm — debe pasar con margen amplio; si se flexiona más de 2 mm, el boom se imprimió parado o con
relleno insuficiente.)

## 3.2b — Tirón del cable de la trompeta (subsistema electrónico)

**Método:** marca el cable con marcador a ras del pasacable. Con una mano sujeta el cable del lado de
la trompeta, entre el pasacable y la cinta más cercana, para que el tirón no llegue a la trompeta ni
a sus aisladores. Con la otra, o con báscula de gancho, jala ~20 N (2 kgf) durante 10 s en el eje del
pasacable, hacia afuera. **No cuelgues una pesa del cable:** la carga se reparte hacia la trompeta.

**Aprueba si:** la marca no se mueve más de 1 mm (el alivio de tensión retiene) y, encendido y con
voz a volumen bajo, no hay cortes ni crujidos. 20 N es criterio propio, no de norma.

## V1 — Vibración estructural al micrófono (la prueba que de verdad decide el criterio 3)

Sin instrumentos, y decisiva: un A/B contra el aislador deliberadamente anulado.

**Método:** al aire libre, sin paredes a menos de 3 m. Cápsula a 3 cm de la boca, trompeta apuntando
lejos.

1. Subir la ganancia al máximo de trabajo y hablar. Anotar si pita y en qué punto del potenciómetro.
2. Sin mover el cable de la trompeta (con su bucle libre y sus cintas como quedaron), sustituir las 4
   arandelas de neopreno por rondanas de acero del mismo espesor y el grommet por un inserto rígido
   (o pegar la cápsula con cianoacrilato), 5 min.
3. Repetir (1) y comparar el umbral de pitido.
4. Volver a poner los aisladores.
5. **Prueba del cable.** Con los aisladores puestos, deja RV1 justo en el umbral de pitido de (1) (si
   en (1) no pitó en ningún ajuste, RV1 al máximo de trabajo). Corta la primera cinta del cable de la
   trompeta y sostén el cable en el aire con los dedos, sin tocar el bracket ni la espina, desde su
   salida hasta pasar el bucle. Si el pitido **desaparece** o el umbral sube, el cable estaba
   puenteando los aisladores: rehaz el bucle (radio ≥ 36 mm, cota G8, sin tirar de la trompeta),
   vuelve a amarrarlo (primera cinta a 60–70 mm del fin del bucle, las demás cada 80 mm) y repite V1
   completa. Si nada cambia, el cable no es un camino de vibración. Reemplaza la cinta cortada.

**Aprueba si:** (a) con los aisladores puestos, no pita en ningún ajuste de ganancia con la cápsula a
3 cm y la trompeta apuntando al frente, al aire libre; y (b) el umbral de pitido con aisladores es
igual o mejor que sin ellos. *Si en (3) el umbral sale igual, solo se concluye que "domina el camino
aéreo" cuando en (5) liberar el cable no cambió nada. Si en (5) algo mejoró, ese "igual" no es
aprobación: el cable estaba anulando los aisladores.*

## V2 — Prueba del nudillo (30 segundos, hazla siempre)

Aparato encendido a ganancia de trabajo, nadie hablando. Golpear el flare de la trompeta con el
nudillo.

**Aprueba si:** el golpe se oye por la bocina **claramente más bajo** que la propia voz hablando
normal. Si el golpe suena igual de fuerte que la voz, el camino estructural está vivo: revisar apriete
del neopreno, tensión del cable del micrófono, **bucle del cable de la trompeta (radio ≥ 36 mm, sin
contacto con el bracket, sin cinta a menos de 60 mm del bucle)** y que ningún metal de la cápsula
toque el PETG.

Repetir el golpe con el cable de la trompeta liberado (primera cinta cortada, cable sostenido en el
aire desde su salida hasta pasar el bucle). Si así el golpe suena claramente más bajo que con el cable
como quedó, el cable es un camino vivo: revisar la cota G8 y la primera cinta, y reponer la cinta.

## B1 — Reemplazo de pilas

**Aprueba si:** las 6 pilas se cambian en menos de 60 segundos, con máximo un desarmador, sin quitar
ninguna otra pieza, sin tocar ninguna soldadura y sin alterar la geometría del boom. Después: no
suena a cascabel al agitar, y el aparato enciende.

## T1 — Marcas testigo

Después de D1 y de 30 minutos de cargarlo: ninguna marca testigo rota. Es la prueba de aflojamiento
por vibración, y es gratis.

## F1 — Carga y caminata

Colgado del strap, 15 minutos caminando, incluyendo escaleras.

**Aprueba si:** nada flojo · G1 sin cambio · no pita al encenderlo después.

## C1 — Creep térmico (la que todos se saltan, y la que mata al PLA)

Dejar el aparato armado, con la trompeta en voladizo, 4 horas dentro de un coche cerrado al sol.

**Aprueba si:** la punta del boom no se pandeó más de 2 mm (medir G1 antes y después), ningún
aislador tomó deformación permanente mayor a 0.5 mm y el bucle del cable de la trompeta recuperó su
forma (radio ≥ 36 mm) sin quedar aplastado. **Aviso:** la hoja de la SC-615 da +55 °C como máximo de
operación, y el interior de un coche puede pasar de eso. Al terminar, deja que el aparato vuelva a
temperatura ambiente antes de encenderlo.

**Si falla con PLA, no es sorpresa: es la razón de la especificación de PETG** (ver
`cuerpo-portatil.md`).
