# Pruebas mecánicas — Megáfono Analógico

**Alcance:** pruebas para verificar el criterio "resiste uso portátil" en el subsistema mecánico.
Documento generado 2026-09-30. Correr después de verificar las cotas de `cotas-de-control.md`.
Las pruebas del subsistema eléctrico (criterios "amplifica sin distorsión" y "no oscila") están en
`hardware/puesta-en-marcha.md`.

## D1 — Caída funcional

**Verdad primero: con ~1.74 kg y una trompeta en voladizo, este aparato no sobrevive 1.2 m sobre
concreto sin daño.** El criterio se fija en lo defendible, no en lo ideal.

**Método:** 3 caídas desde **0.75 m** sobre piso de madera, o concreto con tapete de hule de 10 mm,
en 3 orientaciones: empuñadura abajo, boca de trompeta abajo, boom abajo.

**Aprueba si:** sigue funcionando · ninguna pieza impresa agrietada · ninguna marca testigo rota · la
cota G1 sigue en 30 ± 3 mm · ninguna pila desalojada.

## D2 — Carga lateral del boom (estática)

**Método:** 30 N lateral en el borde de la jaula (colgar 3 kg, o empujar con báscula de gancho),
30 segundos.

**Aprueba si:** flecha ≤ 5 mm y recupera completo, sin grieta en la raíz. (Predicho por cálculo:
0.36 mm — debe pasar con margen amplio; si se flexiona más de 2 mm, el boom se imprimió parado o con
relleno insuficiente.)

## V1 — Vibración estructural al micrófono (la prueba que de verdad decide el criterio 3)

Sin instrumentos, y decisiva: un A/B contra el aislador deliberadamente anulado.

**Método:**

1. Al aire libre, sin paredes a menos de 3 m. Cápsula a 3 cm de la boca, trompeta apuntando lejos.
2. Subir la ganancia al máximo de trabajo y hablar. Anotar si pita y en qué punto del potenciómetro.
3. **Anular el aislamiento:** sustituir las 4 arandelas de neopreno por rondanas de acero del mismo
   espesor (5 min) y sustituir el grommet por un inserto rígido, o pegar la cápsula con cianoacrilato.
4. Repetir el paso 2 y comparar el umbral de pitido.
5. Volver a poner los aisladores.

**Aprueba si:** (a) con los aisladores puestos, no pita en ningún ajuste de ganancia con la cápsula a
3 cm y la trompeta apuntando al frente, al aire libre; y (b) el umbral de pitido con aisladores es
igual o mejor que sin ellos. Si es igual, el camino estructural no es el limitante — también se
aprueba, e indica que el camino aéreo es el que domina.

## V2 — Prueba del nudillo (30 segundos, hazla siempre)

Aparato encendido a ganancia de trabajo, nadie hablando. Golpear el flare de la trompeta con el
nudillo.

**Aprueba si:** el golpe se oye por la bocina **claramente más bajo** que la propia voz hablando
normal. Si el golpe suena igual de fuerte que la voz, el camino estructural está vivo: revisar apriete
del neopreno, tensión del cable y contacto cápsula-PETG.

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

**Aprueba si:** la punta del boom no se pandeó más de 2 mm (medir G1 antes y después) y ningún
aislador tomó deformación permanente mayor a 0.5 mm.

**Si falla con PLA, no es sorpresa: es la razón de la especificación de PETG** (ver
`cuerpo-portatil.md`).
