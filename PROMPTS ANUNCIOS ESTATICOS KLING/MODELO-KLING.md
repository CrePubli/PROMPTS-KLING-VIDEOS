# MODELO MAESTRO — Prompts Kling 3.0 (Image-to-Video / Motion Poster)

> **Objetivo:** Animar imágenes estáticas (anuncios, posters, productos) para que cobren vida
> sutilmente — SIN deformar el diseño, SIN mover el texto, SIN cambiar la escena.
> Resultado buscado: "el anuncio estático traído suavemente a la vida" (cinemagraph premium).
>
> **Estado:** EN CONSTRUCCIÓN — se actualiza con cada ejemplo nuevo. El usuario dirá cuándo cerrarlo.
> **Última actualización:** + G21 (persona de ESPALDAS con print en la espalda, atardecer): bloque
> BACK VIEW LOCK, tercer modo de cámara (handheld de otra persona) y alas/plumas en la jerarquía de
> motion-cue. Antes: serie F1 (portalapiceros) y serie BTS (playeras con caras impresas).
> Nuevos bloques reutilizables: CONTENTS LOCK, PRINTED ART LOCK + FABRIC, SELFIE POV (manos ancladas),
> HAND OVER PRINT, persona secundaria congelada/desenfocada. Ver sección "🧩 BLOQUES NUEVOS".

---

## 🧠 PRINCIPIO CENTRAL

El video NO es una escena nueva ni un multi-shot. Es **una sola composición continua y bloqueada**
(la imagen original) a la que se le añade **vida mínima y controlada**.

La pregunta clave ante CADA imagen:
> **¿Qué cobra vida y qué permanece CONGELADO?**

Todo el modelo gira en torno a separar esas dos cosas con precisión.

---

## 📐 LOS 3 FORMATOS (estructura del prompt)

Los tres funcionan. Se elige según gusto/complejidad.

| Formato | Estructura | Mejor para | Ejemplos |
|---|---|---|---|
| **A — Prosa** | Texto corrido + "Strict stability requirements" al final | Posters / cinemagraph | #1, #2 |
| **B — Timecodes** | `CRITICAL TEXT LOCK` + timeline `[00:00-00:02]` + `Negative prompt:` | Sujetos que se mueven | #3, #4, #6 |
| **C — Secciones** ⭐ | Encabezados en MAYÚSCULAS por capa | Ads complejos / máximo orden | #7–#16 |

⭐ **FORMATO C ES EL GANADOR** — el más ordenado, escaneable, modular y reutilizable.
Es el formato por defecto para generar prompts nuevos.

---

## 🗂️ LAS 3 FAMILIAS (según qué hay en la imagen)

| Familia | Qué se mueve | Qué permanece congelado | Ejemplos |
|---|---|---|---|
| 🅰️ **Todo impreso** (poster/arte) | Solo cámara + ambiente externo + sway físico del poster colgante | TODO el arte impreso + texto | #1 |
| 🅱️ **Modelo(s) real(es)** | Micro-gestos del sujeto + reflejos del producto | Texto + producto base + fondo | #2,#3,#4,#6,#8,#9,#11–16 |
| 🅲️ **Producto + entorno** | Entorno natural sutil (con freno) + glint en el producto | El producto + base + texto | #5 |

---

## 🧱 BLOQUES MODULARES (Formato C) — se combinan según la imagen

Plantilla base. Incluye SOLO los bloques que apliquen a la imagen concreta.

```
Image-to-video animation prompt for Kling or any Veo-compatible tool. Use the uploaded
[DESCRIPCIÓN] advertisement image as the exact reference frame. Preserve the original poster
composition, framing, text placement, [ELEMENTOS], and overall visual structure from start to
end. Do not define a fixed duration inside the prompt; the animation should adapt naturally to
the duration selected by the user in the video generation tool.

CRITICAL TEXT AND DESIGN LOCK:
Keep all text, graphic elements, icons, lines, and layout completely static, sharp, readable,
and unchanged for the entire video. This includes [CITAR TEXTO EXACTO DE LA IMAGEN]. Do not
move, animate, distort, flicker, reflow, or replace any text or graphic element. The composition
must remain identical throughout the video.

PRODUCT LOCK:
The [PRODUCTO] must keep its exact shape, proportions, texture, colors, and overall design.
[Si lleva texto/logo encima: The embroidered/printed "[PALABRA]" must remain sharp, stable, and
unchanged.] Do not deform the [PRODUCTO] in any way.

SUBJECT ANIMATION:   ← solo si hay persona real
Animate only [SUJETO]. [Micro-gestos NOMBRADOS: breathing, blink, slight head tilt, gaze shift,
posture shift...] oriented to keep [PRODUCTO] clearly visible. [Dial: "subtle/restrained" para
producto premium · "clearly visible so it doesn't feel stiff" para UGC/selfie.]

[PRODUCTO] PRESENTATION:   ← gesto orientado al producto
Body language should subtly highlight [PRODUCTO] as the hero product...

HAIR AND CLOTHING:   ← si hay pelo largo / ropa suelta
Allow very subtle natural movement... No exaggerated fluttering.

[ZONA] LOCK:   ← collages / imágenes partidas: congelar zonas de catálogo
The [zona inferior / flat-lay / close-up] must remain completely static. It should behave like
a still printed ad.

BACKGROUND / ENVIRONMENT:
Keep [fondo] stable, with only minimal ambient life or soft natural light variation.

MOTION STYLE:
Natural, premium, subtle, controlled, realistic. The ad should feel like a [tipo] poster brought
gently to life. Only [SUJETO] moves. No exaggerated movement. No warping. No floating elements.

CAMERA:
A very subtle cinematic push-in or micro parallax is allowed only if it does not alter the
composition or affect text readability. Framing remains essentially the same.

NEGATIVE INSTRUCTIONS:
Do not animate any text. Do not change the layout. Do not deform the [PRODUCTO]. [+ negativos
específicos de ESA imagen: no slide/spin/float, no warped hands, no exaggerated walking, etc.]
Do not add new elements. Do not turn this into a different scene.
```

---

## 📋 TABLA DE DECISIÓN (qué estrategia según la imagen)

| Lo que hay en la imagen | Estrategia | Ej. |
|---|---|---|
| Todo arte impreso (poster) | Solo cámara + ambiente externo; arte = congelado, usar palabra **"printed"** | #1 |
| Producto solo + entorno natural | Entorno sutil CON FRENO + producto quieto + glint en lente/superficie | #5 |
| 1 modelo | Micro-gestos nombrados + orientados al producto + reflejos | #3,#4 |
| 1 modelo en acción (pedalear/correr) | Acción cíclica **IN PLACE** (sin desplazarse) + negativos anatómicos | #6 |
| 1 modelo presentando accesorio | Gesto orientado a la zona del producto (torso/cadera/mano→hebilla) | #8 |
| Varios modelos | **Un bloque de gestos POR persona** (LEFT MODEL / RIGHT MODEL), cada uno distinto | #9 |
| Producto exhibido (foreground/catálogo) | DECISIÓN: congelar (seguro, #10) O float/rock mínimo IN-PLACE muy amarrado (#17); siempre "no slide/spin/bounce/jump" | #9,#10,#17 |
| Imagen partida en zonas | "Zona X se mueve / Zona Y frozen like printed poster" | #10 |
| Collage / moodboard | **1 (o pocas) ventana(s) viva(s) + todo lo demás "printed design layout"** | #12,#13 |
| Collage con verbos mixtos | Cada zona viva = su propio verbo (posar / caminar / ajustar) | #14 |
| Selfie con teléfono | Bloque que **ancla el teléfono** ("must not swing") + protege la mano | #16 |
| Texto/logo SOBRE el producto | Candado propio dentro de PRODUCT LOCK | #11 |
| Producto repetido en la imagen | Nombrar CADA instancia individualmente | #12 |
| Persona real sostiene ARTE/FOTO impresa (con caras dentro) | Híbrido: persona se mueve PERO "printed photo inside must remain still/unchanged" (máx. riesgo si son caras) | #2,#20 |
| Objeto sostenido (teléfono/poster) | DECISIÓN: firme "no swing" (#20) O sway sutil amarrado (#21). El contenido impreso adentro SIEMPRE congelado aunque el marco se meza | #16,#20,#21 |
| Varias personas, misma mirada | Bloque GAZE DIRECTION compartido (miran producto → miran cámara) | #20 |
| Producto con cosas sueltas dentro (porta-lápices) | **CONTENTS LOCK** (no spill/multiply/rearrange); vacío = omitir | F1 |
| Playera/tela con CARAS impresas | **PRINTED ART LOCK** + **FABRIC controlado**; caras = imán #1 → 2.6 si fallan | BTS |
| Mano que toca/desliza sobre arte impreso | **HAND OVER PRINT** (pasa por encima sin smear/drag) | BTS |
| Selfie en mano (se graba con su teléfono) | Cámara **NO locked** = handheld sway sutil + **manos ancladas** (brazo del tel. no baja, otra mano no desaparece) | BTS |
| Persona secundaria lejana al fondo | **Congelar + desenfocar**, NO animar (animarla la deforma) | F1 |
| Persona de ESPALDAS con print grande en la espalda | **BACK VIEW LOCK** (nunca se gira, cara nunca visible) + cámara siempre DETRÁS (sin orbital) | G21 |
| Print con ALAS / plumas / capa / listones | Igual que banderas: nombrar "wings do NOT flap/spread/ripple" + no animar nada cerca | G21 |

---

## 🏆 LAS 10 REGLAS DE ORO

1. **Texto/gráficos = overlay fijo.** "pinned in place like a fixed overlay" / "frozen like a
   printed poster". El blindaje GENÉRICO es lo que carga el peso (ver red de seguridad abajo).
2. **Cámara = locked-off.** Push-in (#3) o pull-back (#21) SOLO si NO hay texto pequeño en el cuadro.
   ⚠️ Con texto pequeño: **CERO movimiento de cámara** — push-in/pull-back re-renderizan el cuadro y
   DEGRADAN el texto (FALLO #5: "cuando se alejaba le puso una cosa rara al texto"). Pull-back es el
   peor (revela más área). Nunca pan/tilt/shake/zoom jumps.
3. **Producto hero = nunca se deforma.** Vive por reflejos/glint sutiles O por micro-movimiento.
   ⚠️ CAVEAT (opción): pedir "glint/shimmer/sparkle" a veces hace que Kling añada DESTELLOS
   artificiales/caricaturescos no deseados ("le pone brillos"). Si el usuario NO quiere brillos →
   quitar todo "glint/shimmer/sparkle" + negativo "no sparkles, glints, glitter, light/lens flares,
   shine effects"; dejar el producto con su luz natural y la vida en el micro-movimiento (giro,
   mecido de colgantes). Es DECISIÓN del usuario: con brillo sutil vs sin brillo.
4. **Sujeto = micro-gestos NOMBRADOS, finitos y orientados al producto.** Nunca "se mueve" a secas;
   siempre decir EXACTAMENTE qué gesto (respira, parpadea, ladea cabeza, ajusta...). El gesto
   "señala" dónde está el producto (gafas→mirada/cara, cinturón→torso/mano a hebilla, reloj→muñeca).
5. **Cada capa con FRENO explícito.** Pelo, ropa, entorno, embers → siempre "no exaggerated...".
6. **Catálogo / foreground → CONGELAR por defecto** (menos riesgo). EXCEPCIÓN creativa: float/rock
   mínimo IN-PLACE (#17) si quieres que "viva" — pero amarrarlo brutalmente ("do not slide, spin,
   bounce, jump, change position"). Animar objetos sueltos es de lo más propenso a fallar.
7. **Negative prompt nombrando los elementos CONCRETOS de esa imagen** (el jaguar impreso, las manos,
   el teléfono, los cinturones del suelo...). No genérico.
8. **Menos movimiento = más natural y replicable** (para producto/poster).
9. **EL DIAL DE MOVIMIENTO se ajusta al GÉNERO:**
   - Producto / catálogo / poster premium → movimiento **MÍNIMO** (máxima estabilidad).
   - UGC / selfie / lifestyle con persona → movimiento **CLARAMENTE VISIBLE** ("feel alive", "not
     stiff") → se ve MÁS real. Siempre sin "exaggerated".
10. **Modularidad de movimiento.** En multi-zona, cada zona viva = su bloque + su verbo. Movimientos
    de RIESGO (caminar, girar cuerpo, manos en acción) → blindar extra o evitar si se busca seguridad.
11. **AISLAMIENTO ESPACIAL del movimiento (CRÍTICO para el texto).** Solo anima zonas que estén
    FÍSICAMENTE LEJOS del texto pequeño. NUNCA animes un fondo/entorno que esté detrás o pegado a
    texto pequeño → el movimiento se contagia al texto y lo garabatea (FALLO #3). Animar entorno es
    seguro solo si esa región no tiene texto encima/cerca (#5). La protección de texto NO vence a la
    proximidad del movimiento.
12. **Texto pequeño/roto → tratarlo como PÍXELES CONGELADOS, no como palabras** (no citar, no leer,
    "do not re-render/redraw"). + animar 1 sola zona. Mata el efecto máquina de escribir (FALLO #2).
14. **🆕 PRODUCTO ASIMÉTRICO al GIRAR → Kling duplica/espeja el lado visible en el lado oculto.** Si
    un producto tiene diseño en UN lado y el otro es liso (gorra con bordado en un panel, taza con
    logo de un lado), al girarlo Kling "inventa" el lado oculto copiando el visible → le pone el mismo
    bordado/logo al lado que era liso. Fix: bloque "CAP SIDES / the two sides are DIFFERENT — the
    opposite side is PLAIN, no embroidery/logo; do NOT add, copy, mirror or duplicate it onto the
    blank side" + negativo "do not duplicate/mirror the design onto the other side" + LIMITAR el giro
    (que el lado liso apenas se revele) o solo inclinar en vez de girar.

13. **JERARQUÍA DE MOTION-CUE impreso (qué tiende a animarse solo, de más a menos):** BANDERAS (máx,
    peor que fuego) > **ALAS/plumas/capas/listones** > fuego/llamas > agua/olas/humo > nubes/cielo >
    caras/personas > objetos. Si el
    arte impreso tiene banderas/fuego, NO le des a la escena NINGÚN permiso de movimiento cerca —
    cualquier animación (hasta un ember) se contagia a ellos pese a los negativos (FALLO #6). Caso
    extremo (mucho motion-cue + texto) → 2.6 + movimiento casi nulo.

---

15. **🆕 ESTILO ACTUAL: SIN TIMECODES.** Las secuencias de acción se escriben en PROSA natural
    ("First she..., then she..., finally she...") — NO usar `[00:00-00:02]`. Es como trabajamos ahora.
16. **🆕 CÁMARA: TRES modos según quién graba.** (a) Tripié / producto / hay texto pequeño → `locked-off`
    (regla #2). (b) **Selfie en su propia mano** → cámara **NO locked** = handheld sway sutil continuo
    (si no, se siente falso); pero anclar el brazo del teléfono y no perder la otra mano (bloque E).
    (c) **🆕 Lo graba OTRA persona con el teléfono en la mano** → cámara handheld con **recorrido descrito
    en prosa** ("drifts slowly a little closer, then eases back out, then shifts gently to the right"),
    siempre con freno ("small, smooth, unhurried; no swooping, no spinning, no zoom jumps, no hard shake")
    y con el sujeto "clearly in frame and roughly centred the whole time". **Solo si NO hay texto pequeño**
    en el cuadro (regla #2 manda). Si el sujeto está de espaldas, añadir SIEMPRE "the camera stays BEHIND
    him at all times; it does NOT orbit, arc, or travel around to his side or in front" (si no, el
    desplazamiento lateral se convierte en orbital y le descubre la cara). Y con desplazamiento lateral,
    **candado ANTI-OUTPAINT** (revela área nueva → la inventa). (Ejemplo: G21 espaldas atardecer.)
17. **🆕 "MIRAR A CÁMARA" mueve la cámara (separar mirada vs cámara).** Si pides "glances up toward
    the camera" en un close-up (ej. de la playera), Kling sube/re-encuadra la cámara hacia su cara
    (asocia "mirar a cámara" = "plano de cara"). → Separar explícito: "ONLY her eyes/head glance up,
    the CAMERA does NOT move; do not tilt/pan/raise/re-frame the camera up to her face; framing stays
    locked on the [product] exactly as the first frame." Negativo gemelo en la lista. (Evidencia: toma
    BTS close-up "se ve hermosa con todo" — funcionó bien pero la cámara subió a la cara al mirar.)

---

## ⭐ PRINCIPIO DEL "PARARRAYOS DE MOVIMIENTO" (descubrimiento clave — validado)

**Kling vuelca su "presupuesto de movimiento" en el sujeto humano si lo hay; si no hay humano, ese
movimiento se ESCAPA hacia el contenido de alto motion-cue (banderas, fuego).**

Evidencia directa (misma familia de imagen, posters con banderas/fuego/mar adentro):
- **FALLO #6** — colección de posters SIN persona → animé ambiente (embers) → el movimiento se fue
  a las BANDERAS (se animaron). Texto roto.
- **ÉXITO (Selecciones legendarias, 3.0)** — MISMOS posters con banderas/fuego pero CON un hombre
  colgando el poster → animé al hombre → las banderas quedaron quietas. Funcionó perfecto en 3.0.

**Reglas que se derivan:**
1. **Si hay un humano real, anímalo a ÉL** (micro-gestos) y deja los posters/arte congelados — el
   humano "absorbe" el movimiento y protege el arte impreso, incluso con banderas/fuego adentro.
   Funciona hasta en 3.0.
2. **Si NO hay humano (colección/flat-lay puro con banderas/fuego), NO animes ambiente** — no hay
   pararrayos, el movimiento se escapa a las banderas. → Congelar casi todo (solo brillo en esquinas
   muy lejos) y/o usar 2.6.
3. El humano debe estar **espacialmente aislado del texto** + cámara clavada + ambiente (si lo hay)
   lejos del texto → así el texto aguanta incluso en 3.0 con bastante texto (validado aquí).
4. **🆕 El pararrayos necesita SUFICIENTE movimiento.** Si restringes demasiado al humano (apenas
   respira), el presupuesto sobrante se ESCAPA a las CARAS impresas (caras = imán: quieren
   parpadear/respirar). → Dale al humano UNA acción/movimiento CLARO (girar la cabeza, ajustar el
   poster) para que sea inequívocamente EL sujeto. (Evidencia: "Selecciones legendarias" #22 con
   hombre activo = caras quietas ✅; "se vive en tu pared" con hombre casi inmóvil = jugadores
   impresos se movieron ❌.) Además blindar caras impresas con "FLAT INK / still photograph, do NOT
   blink, breathe or turn".
5. **🆕 NO uses "congela TODO / casi nada se mueve" en colecciones sin humano.** Sin un destino de
   movimiento, el modelo IGUAL genera frames y "inventa" en la región más débil = el TEXTO PEQUEÑO.
   (Evidencia: la colección en 2.6 "casi congelada" quitó/cambió el texto de abajo y casi no se
   movió — PEOR que la versión con movimiento.) → En su lugar: **dar un "MOTION SINK" arriba**
   (luces/embers en la zona superior, lejos del texto) + **congelar la franja inferior** como "UI
   bar" (cero movimiento en el tercio de abajo, nada llega ahí). El movimiento necesita un destino
   SEGURO, no eliminarse.
6. **Texto chico en zona difícil que se resiste:** solución 100% = generar/animar SIN ese texto y
   ponerlo como capa real en Canva/CapCut DESPUÉS de animar. Ningún prompt lo garantiza al 100%.
7. **🆕 La figura impresa más GRANDE/PROMINENTE/en primer plano es la última en congelarse** — y más
   si una mano/sujeto está encima de ese poster (atrae la "atención" de Kling). → Nombrar el
   elemento exacto que falla ("the seated player holding the trophy in the Argentina poster is
   frozen flat ink"). Nombrar el elemento específico = Kling lo respeta mucho mejor que un genérico.
8. **🆕 Los ICONOS se animan solos** (Kling los lee como UI: pulse/spin/glow/fill). Congelarlos por
   nombre: "the eye icon, ball icon, frame icon are flat frozen graphics — do not spin/pulse/glow".
9. **🆕 DERIVA TEMPORAL: el video se degrada con el tiempo.** "Después en un rato cambia el texto" →
   mientras más largo el clip, más se rompe el texto en los frames finales. → **Clip CORTO (≈5s) =
   menos deriva.** Para texto crítico, fijar duración corta y añadir "do not change the text in the
   final frames".
11. **🆕 EVITAR EFECTO CÁMARA LENTA (UGC/personas).** Kling tiende a salir "slow-mo/dreamy". Si se ve
    lento: (a) bloque dedicado "PACING: normal real-time speed, everyday human pace"; (b) pedir
    movimiento MÁS DEFINIDO, no micro-movimientos diminutos (los gestos tiny + lentos = se leen como
    slow-mo); (c) negativos fuertes "no slow motion, no slow-mo, no dreamy floaty, no time-stretch/
    ramp"; (d) repetir "real-time speed" en intro, style y negativos. Clips cortos ayudan.

10. **🆕 BOCA HABLANDO = DECISIÓN (opción del usuario, NO regla fija).** Cuando pides movimiento
    natural de una persona, Kling tiende a hacerla "hablar" (mover labios). NO está tan mal — es
    cuestión de gusto. Dar SIEMPRE las dos opciones:
    - **CON habla** (default UGC): dejar el movimiento natural / "natural mouth movement as if
      speaking". Se ve dinámico de creador hablando a cámara.
    - **SIN habla** (si el usuario lo pide): congelar la boca ("mouth and lips stay FIXED in their
      current expression, no lip movement, no speech, no lip-sync") y sacar la vida de cabeza,
      cejas, parpadeo, pelo y manos.
    Preguntar/ofrecer ambas según lo que quiera para ese clip.

## 🧩 BLOQUES NUEVOS — productos sostenidos / playeras impresas / selfie POV

Bloques reutilizables destilados de la serie F1 (portalapiceros) y la serie BTS (playeras con 7 caras
impresas). Copiar/adaptar el que aplique. **Nota de estilo actual: SIN timecodes** — las secuencias de
acción se escriben en PROSA natural ("First she..., then..., finally...").

### A) CONTENTS LOCK — objetos sueltos dentro de un producto
Cuándo: el producto contiene cosas sueltas (plumas, lápices, clips, pines, AirPods...). Al mover/acercar
el producto, Kling las DERRAMA / multiplica / reordena. Lo metálico y pequeño (clips, pines) es lo
primero que falla.
```
CONTENTS LOCK — everything inside stays put (critical):
The [pens, pencils, clips, push pins, binder clips, AirPods case, eraser] and every small piece stay
EXACTLY in their compartments, stable and unchanged. As the [product] is moved and brought closer, they
do NOT spill, fall out, tip over, slide, lean, shift, multiply, duplicate, or rearrange.
```
⚠️ Si está VACÍO, no incluir este bloque (caso gorra/portalapiceros vacío = más fácil).

### B) PRINTED ART LOCK — playera/tela con caras impresas (imán #1)
Cuándo: arte impreso sobre tela con CARAS (lo que MÁS cobra vida: parpadean, sonríen, se derriten).
```
PRINTED ART LOCK — the shirt graphic is a frozen flat print (critical):
The entire graphic printed on the t-shirt — the [N] black-and-white faces, the red "[WORD]" text, the
stars and bolts — is a FLAT, FROZEN, PRINTED INK LAYER on the fabric. The printed faces must stay
completely still: they do NOT blink, smile, turn, talk, breathe, move their eyes, come to life, melt,
morph, or animate. Do NOT redraw, re-render, regenerate, sharpen, or alter the print. Treat it as a
static photograph printed on cloth[, even while she moves/turns the shirt].
```
+ negativo: `Do not animate, blink, move, turn, smile, talk, melt, morph, or bring to life the printed
faces.`

### C) FABRIC — movimiento controlado de la tela
Cuándo: la persona sube/gira/acomoda la playera → la tela ondula y deforma el print.
```
FABRIC — controlled movement:
The shirt may rise and turn gently as she presents it, but keep the fabric movement controlled and
smooth so the printed graphic stays flat and undistorted, with NO rippling, waving, billowing,
stretching, or warping of the faces or text.
```

### D) HAND OVER PRINT — mano que se desliza sobre el arte impreso
Cuándo: toca/desliza la mano SOBRE el diseño → la arrastra/embarra.
```
HAND OVER PRINT — glides without smearing (critical):
As her hand touches and slides across the shirt, the printed graphic stays completely flat, fixed and
undistorted underneath. The hand passes OVER the print like over a photo — it does NOT smear, drag,
stretch, ripple, blur, push, or distort the faces, stars, or lettering.
```

### E) SELFIE POV — cámara handheld + manos ancladas (regla validada)
Cuándo: la persona se graba con el teléfono en su propia mano. Aquí la cámara **NO va locked** (se siente
falso). PERO el fallo típico es: el brazo del teléfono **baja** (pierde sentido) y la **otra mano
desaparece**. Anclar ambas.
```
CAMERA — natural handheld selfie (NOT locked):
The frame is NOT locked-off. The camera has a continuous, gentle handheld selfie motion the whole time,
as if she films herself with the phone in her extended hand — subtle, natural, ongoing sway. Keep it
gentle, never frozen, but no zoom, no big pans, no swooping, no hard shake.

ARMS AND HANDS — both stay anchored (critical):
The arm holding the phone stays extended toward the camera, steady and holding the phone the ENTIRE time
— it does NOT lower, drop, relax, fold, or move out of frame. Her OTHER hand stays visible the entire
time [touching the design] — it does NOT disappear, vanish, fade, shrink, or morph away. Both hands stay
present and consistent from first to last frame.
```
⚠️ **Excepción a la regla "cámara clavada":** el sway handheld SOLO cuando es selfie en mano. Con texto/
caras impresas, mantenerlo MÍNIMO (o ir a 2.6 / cámara fija si se degrada). Si NO es selfie (la graban
con tripié/otra persona, las dos manos en el producto) → volver a `CAMERA: completely locked-off`.

### F) PERSONA SECUNDARIA AL FONDO — congelada y desenfocada
Cuándo: hay un segundo sujeto lejano (amigo en el sofá). Animarlo lo DEFORMA (está pequeño/borroso).
```
BACKGROUND FRIEND — FROZEN AND OUT OF FOCUS:
The friend in the background stays completely still and soft, blurred and out of focus the entire time,
like a frozen part of the background. He does NOT move, gesture, point, change pose or expression. Do
NOT deform, warp, or morph him.
```
Regla: **secundario lejano = congelar + dejar desenfocado, NO animar.** (Evidencia: el amigo señalando
salió deforme; al congelarlo se arregla.) Bonus: si subir/levantar el producto le tapaba los pies/cuerpo
al de atrás → negativo "do not raise/lift the product upward — keep it at the same height".

### G) BACK VIEW LOCK — la persona está de ESPALDAS y NO se puede girar
Cuándo: el print/producto está en la ESPALDA (playera, mochila, gorra por detrás) y el sujeto se ve de
espaldas. En cuanto le pides que "mire" algo, Kling tiende a **girarlo** y enseñar la cara (y con ello
se inventa/re-esculpe una cara que no existe en la referencia).
```
HE NEVER TURNS AROUND (most important rule):
The man is seen from BEHIND for the entire clip, exactly as in the reference frame. He does NOT turn
around, turn his body, pivot, swivel, rotate, or face the camera at any moment, and his face is NEVER
visible — not in profile, not over his shoulder, not even partially. Only the back of his head, his cap
and his back are ever seen. He also stays in exactly the same spot: he does NOT walk, step, or change his
standing position or distance from the camera.
```
+ pareja obligatoria en el bloque de cámara: `the camera stays BEHIND him at all times; it does NOT orbit,
arc, or travel around to his side or in front of him, and it never reveals his face.`
+ negativos gemelos: `Do not turn the man around... do not show his face or profile at any moment. Do not
orbit or move the camera around to his side or front.`
**Verbos seguros para "que mire el horizonte" estando de espaldas:** *lifts his head from looking down to
looking straight ahead, still facing completely away* (subir la cabeza = seguro; "look at / turn to see"
= peligro, lo gira).
**Acomodarse la ropa sin arruinar el print:** el tirón va al **dobladillo de abajo, al costado, sobre tela
lisa** (nunca la palma sobre el diseño → FALLO #7) + `ONE HAND ONLY` + candado de no inventar gráficos.

---

## 💎 FRASES DE ORO (vocabulario validado que funciona)

- `premium motion poster / cinemagraph, not a multi-shot video and not a recreated scene`
- `one continuous locked composition`
- `text pinned in place like a fixed overlay`
- `printed designs must remain static, flat, unchanged` (familia impreso)
- `behave like a still printed ad` / `printed design layout` (zonas congeladas)
- `micro-adjustment / shift of body weight / controlled glance` (sujetos reales)
- `completely locked-off camera. No zoom, no pan, no tilt, no handheld shake`
- `hero-frame version of the original ad`
- `consistent with gentle pedaling` + `no large subject displacement` (acción in-place)
- Negativos clave: `no floating panels`, `no slide/spin/float`, `no warped hands`,
  `no exaggerated walking/fluttering`, `no melting reflections`, `no unstable graphic elements`

---

## 🛡️ RED DE SEGURIDAD (hallazgo importante)

En #7 y #14 los prompts CITABAN texto que **NO coincidía** con la imagen (copy-paste heredado)
y **aun así funcionaron**. Conclusión:
- ✅ El **lock GENÉRICO** ("keep all text static, sharp, unchanged") es lo que realmente protege.
- ✅ Las citas literales son un REFUERZO, pero el sistema es robusto aunque la cita falle.
- ➡️ **Al generar prompts nuevos: citar SIEMPRE el texto EXACTO** (es lo correcto y más seguro),
  pero saber que hay red de seguridad.

Además (#14, #15): el **mismo prompt sirve para imágenes distintas de la MISMA familia** → las
plantillas son RECICLABLES. Crear una plantilla por familia de producto y reutilizarla ajustando
los textos citados.

---

## ⚙️ PARÁMETROS OBSERVADOS

- **Duración:** 6s, 8s, 10s — o "adaptativa" (no fijar duración, dejar que el usuario elija en Kling).
  6s suele ser más estable (menos tiempo para que el modelo "se invente" cosas).
- **Formato:** vertical 9:16 siempre.
- **Compatibilidad:** los prompts se escriben "Kling or any Veo-compatible tool" → sirven en ambos.
- **⚠️ ELECCIÓN DE MODELO (clave):** Kling **3.0** = más movimiento/vida pero ALUCINA texto pequeño/
  denso. Kling **2.6** = más fiel, preserva mejor el texto diminuto. → Texto grande/limpio o sin
  texto crítico = 3.0. Texto diminuto crítico (tracklists, letra fina) = **2.6**. (Ver FALLO #4.)

---

## 📚 ÍNDICE DE EJEMPLOS ANALIZADOS (éxitos ✅)

| # | Imagen | Familia | Aporte clave |
|---|---|---|---|
| 1 | Guatemala en tu pared (poster colección colgante) | 🅰️ | Base cinemagraph; separar printed vs ambiente; "printed" |
| 2 | KAIBIL (hombre sostiene poster) | 🅱️ | Sujeto real con micro-gestos nombrados; proteger pose |
| 3 | Máxima visión (gafas, modelo H) | 🅱️ | Timecodes 2s; "pinned like overlay"; Negative prompt separado |
| 4 | Tú sales el sol no te detiene (gafas, modelo M coche) | 🅱️ | Listar colores exactos del producto; proteger flecha gráfica |
| 5 | Así te ven todos (gafas sobre roca + mar) | 🅲️ | Entorno natural con FRENO; producto quieto + glint |
| 6 | Colección Velocidad (ciclista) | 🅱️ | Acción cíclica IN-PLACE; negativos anatómicos; "no floating panels" |
| 7 | Velocidad / Ve más allá (modelo + ad cargado) | 🅱️ | Formato C secciones; PRODUCT LOCK propio; red de seguridad texto |
| 8 | Cinchos tácticos / Advertencia (cinturón) | 🅱️ | Gesto orientado al producto; CLOTHING ANIMATION; duración adaptativa |
| 9 | Estilo x Función (2 modelos + cinturones suelo) | 🅱️ | Coreografía POR sujeto; foreground product "no slide/spin/float" |
| 10 | Estilo táctico + Ajuste (modelo arriba + catálogo abajo) | 🅱️ | LOWER SECTION LOCK; zona congelada "like printed poster" |
| 11 | Babygirl / El frío no te detiene (gorro selfie) | 🅱️ | Texto BORDADO en producto = candado propio; muy natural |
| 12 | Tu outfit pide este gorro (collage moodboard) | 🅱️ | "1 ventana viva" + COLLAGE ELEMENT LOCK; producto repetido |
| 13 | Babygirl collage UGC (2 paneles + flat-lay) | 🅱️ | 2 zonas vivas + zona congelada; bloque MOVEMENT FEEL (dial+) |
| 14 | Tu outfit pide esto / Y2K (collage) | 🅱️ | Verbos mixtos por zona (posa/camina/congelado) |
| 15 | El gorro que cambia todo (collage nocturno) | 🅱️ | Misma plantilla del #14 → confirma RECICLAJE de plantillas |
| 16 | Tu look pero más cute (selfie + detalle circular) | 🅱️ | Anclar TELÉFONO en selfies; consolidación plantilla selfie |
| 17 | Dos estilos una obsesión (2 modelos + 2 productos) | 🅱️ | Catálogo SÍ puede animarse (float/rock mínimo IN-PLACE muy amarrado); matiza #10 |
| 18 | Dos vibras un must (collage 2 chicas + 5 paneles) | 🅱️ | Enumerar con viñetas cada panel congelado (collages con 4+ zonas muertas) |
| 19 | Collage 3 chicas + 2 flat-lays | 🅱️ | (Repetición) confirma que coreografía por sujeto escala a 3 zonas |
| 20 | ¿Dónde hicieron ese póster? (pareja sostiene poster c/ foto) | 🅰️+🅱️ | Persona real + ARTE IMPRESO con caras dentro = proteger foto impresa; GAZE DIRECTION compartido; anclar agarre; género UGC story-reply |
| 21 | Tu recuerdo favorito (mano sostiene poster personalizado) | 🅰️+🅱️ | Cámara PULL-BACK/reveal (no solo push-in); poster CON sway sutil pero foto impresa congelada; plantilla "poster personalizado" |
| 22 ✅GEN | Selecciones legendarias (hombre cuelga poster Portugal) | 🅰️+🅱️ | PROMPT GENERADO por asistente, funcionó RE BIEN en 3.0. Valida el "pararrayos de movimiento": animar al hombre protege los posters (con banderas/fuego adentro). Hombre aislado del texto + cámara clavada = texto aguanta en 3.0 |
| 23 ✅GEN | El fútbol se vive en grande (colección SIN humano) | 🅰️ | PROMPT GENERADO funcionó en 3.0 tras varios intentos. RECETA GANADORA colección-sin-humano: motion sink ARRIBA (luces/embers en zona superior) + franja inferior FROZEN UI BAR con iconos nombrados + duración CORTA ~5s + flags/caras "frozen ink". (Antes fallaba: embers abajo rompían texto #6; "freeze todo" hacía alucinar texto.) |
| 23b ✅GEN | El fútbol se vive en tu pared (hombre cuclillas + Argentina gigante) | 🅰️+🅱️ | RESUELTO (aceptable) en 3.0 con: hombre = ÚNICO movimiento claro/dominante + estadio TOTALMENTE congelado + 5s + nombrar Messi+copa. Messi y lo principal quedaron quietos. RESIDUO: solo banderas y copas de posters SECUNDARIOS se mueven un poco → es el LÍMITE del modelo 3.0, no del prompt. Decisión correcta: parar ahí (forzar el último 5% exigiría 2.6 y sacrificar el movimiento del hombre). |

---

## ❌ ANTI-PATRONES (lo que ROMPE el video — de los fallos)

### FALLO #1 — "Linaje Guerrero" (poster con FUEGO + mano que lo mece)
**Qué falló:** se animó el fuego del poster + la cajita blanca de texto desapareció ~seg 2.
**Causa raíz:** PROMPT CONTRADICTORIO. Pidió mover el poster ("hand lift, release, side-to-side
sway, soft swing") Y a la vez "no animar el fuego impreso". Kling no puede separar el meneo rígido
del lienzo de la animación del fuego → el movimiento se contagia al arte. El fuego/humo es el
contenido que MÁS se asocia con movimiento. La caja de texto desapareció porque era un overlay
que se SOLAPABA con la mano/poster en movimiento → el modelo la soltó.

**Anti-patrones extraídos:**
1. **NUNCA pidas que un poster se MEZA si su arte tiene fuego/humo/acción/agua.** Movimiento del
   lienzo + imaginería de alto-movimiento = el arte cobra vida. → CONGELA EL POSTER COMPLETO.
2. **No envíes señales contradictorias** ("muévelo PERO no muevas lo impreso"). Kling resuelve la
   contradicción ANIMANDO. Si quieres el arte quieto → congela TODO el objeto, sin sway ni mano.
3. **El movimiento viene SOLO de cámara + ambiente de sala** (luces, plantas, polvo, push-in).
   El poster = roca inmóvil.
4. **Texto overlay NO debe solaparse con zonas de movimiento.** Declararlo "fixed screen overlay
   on top of everything, never occluded by the hand or poster, never part of the moving scene".
5. **A más movimientos distintos pedidos, más inestabilidad.** Este fallo pidió ~6 (mano lift +
   release + sway + cordón + entorno + push-in). Cada petición de movimiento = una oportunidad de
   romperse. CONFIRMA en negativo la regla "menos movimiento = más replicable".

**Regla derivada:** El "sway sutil de poster" SOLO es seguro cuando el arte impreso es de BAJO
movimiento (foto de personas quietas, #21) — y aun así con riesgo. Con fuego/humo/acción = JAMÁS
mover el poster.

### FALLO #2 — "Visión sin límites" (gafas, efecto MÁQUINA DE ESCRIBIR en el texto)
**Qué falló:** casi todos los textos pequeños se "escribían y borraban" solos (typewriter), se
deformaban, e iconos se movían raro.
**Causa raíz (NO es la cantidad de texto — ojo):** El usuario tiene ads con MUCHO texto que SÍ
funcionaron (#6,#7). La diferencia real son DOS cosas:
1. **El texto del origen YA ESTABA ROTO/garabato** (imagen IA con texto basura: "PROTECCIÓN CLMR≀",
   "VISIÓN T.LARA CÓMPRE"). Kling no puede "fijar" letras que no reconoce → intenta RE-DIBUJARLAS
   → efecto máquina de escribir. (#6,#7 tenían texto LIMPIO y legible.)
2. **Se animaron 5 zonas a la vez** (retrato + centro + 3 paneles + gotas) vs UNA zona en #6,#7.
   Mucho movimiento reparte el "presupuesto" de estabilidad → el texto frágil colapsa.
3. **Citar el texto roto EMPEORA** — al texto pequeño/roto, citar la palabra "correcta" invita a
   Kling a reescribir hacia ella → más typewriter. (La "red de seguridad" de citar mal SOLO aguanta
   con texto GRANDE y LIMPIO, #7/#14; con texto pequeño/roto, NO.)

**Anti-patrones / técnica de arreglo:**
1. **TEXTO ROTO o PEQUEÑO → tratarlo como PÍXELES CONGELADOS, no como palabras.** Frase clave:
   "Treat all text as a frozen flat graphic / still screenshot. Do NOT read, interpret, spell,
   re-render, redraw, regenerate or fix any text. Preserve exact pixels even if letters look
   unusual." → NO citar las palabras. Esto mata el efecto typewriter.
2. **Animar UNA sola zona** (o cero + solo cámara/reflejo). Nunca 5 zonas independientes. A menos
   animación, más estabilidad de texto.
3. **Negative explícito:** "no typewriter text effect, do not re-render/redraw/rebuild/type letters".
4. **Mejor aún (no-prompt):** texto limpio, grande, palabras reales EN la imagen base. Si la IA
   genera texto roto → ponerlo como capa real en Canva, o regenerar, o diseñar con menos texto y
   más grande. Ningún prompt salva texto micro+roto al 100%, pero la técnica de "píxeles congelados
   + 1 zona" lo reduce muchísimo.

**Regla derivada:** La estabilidad del texto NO depende de la cantidad, depende de (a) calidad/
tamaño del texto en el origen y (b) cuántas zonas animas. Texto limpio + 1 zona = aguanta mucho
texto (#6,#7). Texto roto + muchas zonas = colapsa (#2).

### FALLO #3 — "Velocidad" (MISMA imagen del #7, pero estos prompts la rompen)
**Qué falló:** animó el texto y escribió texto sin sentido. CLAVE: es la MISMA imagen que SÍ
funcionó en #7 — así que la diferencia está 100% en lo que pidió mover.
**Causa raíz (anti-patrón NUEVO):** Estos prompts animaron el **fondo de montañas de la mitad
inferior** ("cloud drift, haze, horizon shimmer") + reflejos en los 3 productos, ADEMÁS del hombre.
La mitad inferior tiene las etiquetas pequeñas ("ESPEJO SOLAR/NEGRO TOTAL/ESPEJO ÁRTICO") y la fila
"IDEALES PARA:" **encima/alrededor de ese fondo**. Animar el fondo contagió el movimiento al texto
pequeño pegado a esa zona → garabato. El #7 funcionó porque animó SOLO al hombre (zona aislada
arriba) y dejó la mitad inferior quieta.
**Nota:** el segundo prompt fallido tenía buena protección de texto ("flat static overlay" +
negativos fuertes) pero IGUAL animaba las montañas → falló. **La protección de texto NO vence a la
proximidad del movimiento.**

**Anti-patrón clave:** **NUNCA animes un fondo/entorno que esté DETRÁS o PEGADO a texto pequeño.**
El texto y el fondo comparten espacio → el movimiento del fondo desestabiliza el texto. Solo anima
zonas **espacialmente aisladas** del texto (ej. un retrato en una esquina lejos de las letras).
- Imagen "borderline" (texto pequeño) → tolera 1 zona animada AISLADA; añadir una 2ª zona pegada al
  texto la rompe.
- Esto explica por qué la familia 🅲️ (producto+entorno, #5) funciona: ahí el entorno NO tiene texto
  pequeño encima. Animar entorno es seguro SOLO si no hay texto en/cerca de esa región.

### FALLO #4 — "Póster personalizado / tracklist" (texto DIMINUTO imposible → solución: MODELO 2.6)
**Qué falló:** 5 prompts probados (varios casi perfectos: "fixed pixels", todo congelado menos la
mujer, cero cámara) y Kling 3.0 SEGUÍA inventando/reescribiendo texto. Solo funcionó cambiando a
**Kling 2.6**.
**Causa raíz:** El poster es estilo Spotify con un **tracklist de letra MICROSCÓPICA** + nombre
artista + fecha. Texto tan pequeño/denso que 3.0 NO puede preservarlo → lo re-genera → garabato
("Oaar Coutz", "MRNAA NO ESTTY"). **El prompt era correcto; el problema era el MODELO.**

**APRENDIZAJE CRÍTICO — PALANCA DE MODELO (3.0 vs 2.6):**
- **Kling 3.0** = más generativo/creativo (mejor movimiento, más "vida") PERO **alucina texto
  pequeño/denso** aunque el prompt sea perfecto. Bueno para texto GRANDE y limpio, o sin texto crítico.
- **Kling 2.6** = más fiel/estático, **preserva mucho mejor el texto diminuto**. Usar para imágenes
  con tracklists, letra fina, listas densas, fine print.
- **Regla:** texto diminuto/denso CRÍTICO en la imagen → usar **2.6**. Ningún prompt en 3.0 lo salva.
- Por qué #20/#21 (también posters personalizados) SÍ funcionaron en 3.0: su contenido impreso era
  una FOTO de personas (sin texto diminuto). La diferencia NO es "poster personalizado", es **si el
  contenido impreso tiene texto microscópico o no**. Foto→3.0 OK. Tracklist/letra fina→2.6.

**Receta de MÁXIMA fidelidad de texto** (cuando el texto es lo crítico): (1) modelo 2.6 si es
diminuto; (2) CERO movimiento de cámara (ni push-in); (3) animar UN solo sujeto aislado, congelar
TODO lo demás; (4) texto = "fixed pixels, do not re-render/redraw/regenerate", sin citar palabras
rotas; (5) sin animar nada pegado al texto.

### FALLO #5 — "Tu foto hecha póster" (callouts rotos + PULL-BACK destruye el texto)
**Qué falló:** cambiaba el texto y animaba raro. El 2º prompt "casi funcionó pero la cagó al final
CUANDO SE ALEJABA — le puso una cosa rara/fondo al texto 'Tela premium lista para colgar'".
**Causas:**
1. (Conocida) Callouts con texto pequeño roto en el origen ("CORDÓN RESISTEIITE", "OCRWAJW OEATE
   RI") → re-generado.
2. **🆕 EL PULL-BACK DE CÁMARA DEGRADA EL TEXTO.** La pista del usuario ("cuando se alejaba le puso
   una cosa rara") es prueba directa: mover la cámara re-renderiza el cuadro cada frame → el texto
   pequeño se deforma / le aparecen fondos raros. Pull-back es el peor (revela/redibuja más área).
3. (Menor) Animar las LÍNEAS de callout (tracing/pulse) — elementos gráficos finos conectados a
   texto → arrastran/desestabilizan el texto.

**Anti-patrones:**
1. **MOVIMIENTO DE CÁMARA = VENENO para texto pequeño.** Con texto pequeño en el cuadro → cámara
   100% clavada, cero push-in/pull-back. (Solo es seguro mover cámara si NO hay texto pequeño, #21.)
2. **No animar líneas/callouts/elementos gráficos finos** conectados a texto. Congelarlos.

### FALLO #6 — "El fútbol se vive en grande" (colección posters: BANDERAS animadas + texto abajo roto)
**Contexto:** prompt generado por el asistente (familia 🅰️) que parecía correcto. Falló igual.
**Qué falló:** se animaron las BANDERAS impresas de los posters + los labels chicos de abajo
("IMPACTO VISUAL"→"IMPACT VIISUAHL", "ESTILO FUTBOLERO"→"DEURA CFTON KIUE").
**Causas (2 lecciones grandes):**
1. **🆕 LAS BANDERAS SON EL "IMÁN DE MOVIMIENTO" MÁS FUERTE — más que el fuego.** El prior de Kling
   ("las banderas ondean") es tan fuerte que, EN CUANTO se le da permiso de animar ALGO en la
   escena (embers, luces), ese "modo movimiento" se CONTAGIA a las banderas, aunque haya negativos
   explícitos. → En imágenes llenas de banderas/fuego/agua, animar CUALQUIER cosa despierta las
   banderas. Los negativos NO bastan.
2. **El movimiento se puso PEGADO al texto chico.** Los embers "rising from the bottom" subían desde
   la base del podio = justo donde están los labels pequeños → los re-renderizó (FALLO #3 otra vez).
3. **3.0 es demasiado generativo para este caso extremo** (banderas+fuego+agua + texto arriba Y
   abajo, casi sin zona segura). → 2.6.

**Anti-patrones / reglas:**
1. **Contenido de ALTO MOVIMIENTO impreso (banderas > fuego > agua/humo) = NO darle a la escena
   NINGÚN permiso de movimiento cerca.** Si el poster está lleno de banderas/fuego, lo más seguro
   es animar CASI NADA (solo un brillo tenue en esquinas oscuras MUY lejos) o nada. Cuanto más
   "permiso de movimiento" das + más fuerte el motion-cue = más contagio.
2. **JERARQUÍA DE RIESGO de contenido impreso:** banderas (máx) > fuego > agua/olas/humo > nubes/
   cielo > caras/personas > objetos. A más arriba en la lista, más imposible de congelar y más hay
   que evitar animar cualquier cosa cerca.
3. **Caso extremo (mucho motion-cue + texto arriba y abajo) → usar 2.6 + movimiento casi nulo.**
4. Confirma: el movimiento NUNCA debe nacer/pasar cerca del texto pequeño (embers desde la base).

### FALLO #7 — "Playera colgada + mano toca el diseño" (2 bugs: 2ª mano + arte inventado)
**Contexto:** playera BTS (discos "ARIRANG" + nombres manuscritos) colgada en rack; se pidió que una
mano tocara el diseño. Prompt MARCADO COMO PROHIBIDO (no reutilizar).
**Qué falló (2 bugs):**
1. **Apareció una SEGUNDA mano.** El prompt decía literal "the **other hand** comes in to touch the
   design" → Kling METIÓ una mano nueva. (El usuario quería que tocara con la MISMA mano ya presente.)
2. **La mano "dibujó" diseños inexistentes** sobre la tela (garabatos rojos/negros nuevos).

**Causa raíz (2 lecciones grandes):**
1. **🆕 NUNCA digas "the other hand" / "la otra mano"** si quieres que actúe la que ya está. Kling
   instancia literalmente una mano nueva. → Decir "ONE hand only, the SAME hand; do NOT add/introduce
   a second or other hand."
2. **🆕 Una MANO PLANA que TAPA (ocluye) un gráfico impreso → Kling REGENERA/ALUCINA arte nuevo en esa
   zona.** Al ocultar parte del diseño con la palma, el modelo "rellena" el área oculta inventando
   dibujos (y re-dibuja lo de alrededor). Combinado con la palabra **"trace"** (que Kling lee como
   "dibujar/trazar") = inventa garabatos. → Fix triple: (a) la mano NO cubre el print con la palma,
   solo roza con las YEMAS por el borde / tela lisa; (b) quitar "trace"/"traces"; (c) bloque candado
   **"NO INVENTED GRAPHICS"**: "do NOT draw, add, create, generate, paint, sketch, or invent any new
   shapes/doodles/lines/patterns/graphics anywhere on the shirt — under or around the hand; the only
   graphics are the original; when the hand moves, the print underneath stays EXACTLY the original."

**Reglas derivadas (válidas para CUALQUIER mano sobre arte impreso):**
- **Oclusión = alucinación.** No tapar arte detallado con la palma. Tocar con yemas en el borde, o tocar
  zona lisa/hombro/hem, lejos del gráfico denso.
- **Vocabulario veneno:** "trace", "draw", "the other hand". Evitarlos.
- Si aun así inventa → la mano solo toca el hombro/borde inferior (sin acercarse al diseño) o usar 2.6.

**✅ SOLUCIÓN VALIDADA (gorra bordada, selfie: señalar y TOCAR el diseño — "de los mejores resultados"):**
combo de 3 bloques que resuelve el fallo #7 de raíz. Ver prompt completo en `G20` de la BIBLIOTECA-2.
1. **`ONE HAND ONLY`** — "Only ONE hand is used, it is the SAME hand throughout. Do NOT add, introduce, or
   generate a second or extra hand or extra fingers at any point. Her other arm stays extended holding the
   phone and stays OUT of frame — it does NOT come into frame." (Mata el bug de la 2ª mano.)
2. **`TOUCH WITHOUT COVERING — no invented graphics`** — "the fingertip only touches lightly at the EDGE
   beside the emblem, on PLAIN fabric — it does NOT cover, press onto, or hide the emblem with the palm or
   fingers... Do NOT draw, add, create, generate, paint, or invent any new shape/line/pattern/logo anywhere
   — under or around the hand; when the hand moves, the design underneath stays EXACTLY the original."
3. **`CAP SIDES`** (Regla #14) + producto descrito **genérico** (sin nombrar marca/banda).
- **Regla destilada:** para "señalar/tocar el diseño" → **UNA sola mano nombrada + yema al BORDE sobre tela
  lisa + candado de no inventar gráficos**. Con eso sí se puede tocar arte impreso sin que alucine.

---

### FALLO #8 — "Pareja con anillos: dedos se entrelazan + dedo cambia de forma"
**Contexto:** pareja en barco, cada uno con su anillo (Luffy / Chopper), manos muy juntas (la de él toma
la de ella + otra mano abajo). Se pidió que "los dos giren las manos para presentar/enseñar los anillos
a la cámara". Resultado: los dedos se **entrelazaron/entrecruzaron** y el **dedo de la mujer cambió de
forma**.
**Causa raíz:**
- **🆕 Pedir "girar/presentar las manos para enseñar" con DOS manos muy juntas = imán de entrelazado.**
  El giro acerca dedos de ambas manos y Kling los teje entre sí y re-esculpe (cambia forma/largo/grosor)
  el dedo que queda al frente. **Cuanto más movimiento de manos pides en un racimo de manos, más se
  deforma.**
**Fix (racimo de manos muy juntas → CASI CONGELAR):**
1. **NO pedir girar/presentar/levantar/reposicionar las manos.** Que se queden EXACTAS como en la foto,
   solo respiración y micro-settle. La vida la ponen el fondo sutil (agua) y la respiración, no las manos.
2. **FINGER LOCK explícito:** "do NOT interlace, intertwine, weave, lace, cross, or thread the fingers
   together; do NOT change the shape, length, or thickness of any finger; fingers keep their exact
   positions and gaps; stay separate."
3. **Bajar el énfasis en "los anillos".** Mucha instrucción de "enseñar los anillos" empuja a mover las
   manos. Basta "keep the rings exactly as shown".
4. Si aún se entrelazan → **2.6** (más fiel/estático).
- **Regla general:** en composiciones con VARIAS manos juntas, el default es **manos quietas** (motion
  sink al fondo), NO manos que actúan. Ver Bloque F / regla de "no animar racimos de manos".

---

### FALLO #9 — "Anillo gira de más → inventa el lado oculto del aro"
**Contexto:** anillos One Piece (aro abierto/ajustable) sostenidos con los dedos. Se pidió inclinar/girar
el anillo lado a lado o al mostrarlo. Al **rotar de más**, Kling **inventa la parte trasera / interior /
banda abierta del aro** — mete metal y esmalte que NO existen en la imagen.
**Causa raíz:**
- **🆕 Rotar un objeto de aro/anillo revela superficie oculta → Kling la ALUCINA.** Es primo de la Regla
  #14 (CAP SIDES / no duplicar lado oculto): cualquier giro que descubra una cara no visible en el frame
  hace que el modelo la "rellene" inventando. En aros abiertos/ajustables es peor (la banda abierta se
  cierra o se inventa metal nuevo).
**Fix:**
1. **Misma cara al frente todo el tiempo.** Solo acercar/alejar con **cambio de ángulo mínimo**; NADA de
   girar/rotar para "ver otros lados".
2. **HIDDEN-SIDE LOCK:** "keep the SAME face pointed at camera; do NOT rotate/turn/tilt enough to reveal
   the back, inner band, or open gap; do NOT invent, generate, add, or reveal any part of the ring not
   visible in the reference — no new band sections, no hidden side, no extra metal/enamel."
3. Si aún inventa → solo acercar recto (sin ángulo) o **2.6**.
- **Regla general:** vale para CUALQUIER objeto 3D que se gira (figuras, aros, tazas, productos). Si el
  giro descubre cara oculta → o no lo gires, o candado de "no inventar el lado que no se ve". Ver Regla
  #14 y "solid static toy / no duplicate hidden side".

**⚠️ AMPLIACIÓN VALIDADA (figura de PERSONAJE → inventa su ACCESORIO CANÓNICO oculto — Luffy Gear 5):**
serie de la figura de Luffy en columpio (carro / borde de monitor / mano). Falló DOS veces igual (mecido
lateral que se volvió giro, Y orbital de cámara): en cuanto se revela la ESPALDA/costado de la figura,
Kling **inventa el sombrero de paja de Luffy** en la espalda (accesorio que la figura NO tiene). 
**Lección nueva:**
1. **🆕 Con una figura de personaje conocido, Kling rellena el lado oculto con el ATRIBUTO CANÓNICO del
   personaje** (sombrero de Luffy, capa, arma, cola, etc.), no solo con "geometría genérica". El prior del
   personaje es fortísimo. → Además del HIDDEN-SIDE LOCK, poner un **candado NOMBRANDO el accesorio**:
   *"This figure has NO hat. Do NOT add, invent, or reveal a straw hat or any hat on its back, head, or
   anywhere."* Nombrar el accesorio exacto que inventa = clave (igual que nombrar el elemento que falla).
2. **🆕 El MECIDO LATERAL de un objeto colgante (columpio, cordón) se convierte en GIRO.** Pedir "sway
   left-right / de izquierda a derecha" en algo que cuelga → Kling lo interpreta como péndulo que rota y
   descubre la espalda. → O quitar el lateral (solo acercar), o "VERY slight pure lateral translation, NOT
   a pendulum, NOT a turn; hands hold the base FIRMLY so it cannot spin".
3. **🆕 ORBITAL sobre figura de personaje = descubre la espalda = inventa el accesorio.** El orbital solo
   es seguro en producto SIN cara/sin personaje (ej. pulsera en rocas). Con figura de personaje: orbital
   **solo FRONTAL y superficial** ("stays strictly IN FRONT, never to the side or behind, back/head-back
   never in view") o cambiarlo por **push-in frontal recto** (cero riesgo). 
4. Tras 2 fallos → **2.6**. **Regla destilada:** figura de personaje = NUNCA revelar su espalda (ni por
   giro, ni por mecido de colgante, ni por orbital) + candado NOMBRANDO el accesorio canónico que no tiene.
5. **🆕🔑 LA RAÍZ: NO NOMBRAR AL PERSONAJE.** Escribir "Luffy / One Piece / Gear 5" **activa el prior del
   personaje** → Kling "sabe" que Luffy lleva sombrero de paja y lo inventa en el primer hueco (la espalda).
   Igual que nombrar algo lo invoca, nombrar al personaje invoca sus atributos canónicos. → **Describir la
   figura de forma GENÉRICA por sus atributos VISIBLES** ("a small collectible PVC figure of a smiling
   character with fluffy white hair, hand over one eye, open white coat, red X mark on the chest, purple
   sash, yellow sandals, on a black swing") + "reproduce ONLY what is visible; do not add any hat/accessory
   not in the reference". Sin el nombre, el modelo no tiene de dónde sacar el sombrero. Aplica a CUALQUIER
   figura/producto de personaje conocido (anime, cómic, videojuego): describir lo que se VE, no quién ES.

---

### FALLO #10 — "POV muñeca: dio la vuelta completa + el brazo NO se acercó"
**Contexto:** pulsera puesta en la muñeca, POV mirando hacia abajo (piscina). Se pidió "rotar la mano
suave y acercarla a la cámara". Resultado: (1) la muñeca **dio la vuelta completa**; (2) el brazo **no
subió / no se acercó** (todo quedó congelado).
**Causa raíz (2 lecciones):**
1. **🆕 El verbo "rotate/rotar" = giro completo para Kling.** Aunque digas "suave/poco", el verbo la
   empuja a rotación total (y en pulsera/aro invita al FALLO #9). → NO usar "rotate". Decir **"tilt/angle
   just a little"** + candado **"the SAME top face stays pointed at the camera the whole time; do NOT
   turn it over / flip / spin / roll"**.
2. **🆕 En POV, sobre-bloquear "camera does NOT move" CONGELA también el brazo.** Si el acercamiento
   depende de que el brazo/antebrazo suba hacia el lente y a la vez machacas "no movement / camera
   fixed", Kling no mueve NADA. → Hay que declarar el **gesto del brazo como ACCIÓN PRINCIPAL y explícita**
   ("the forearm RISES up toward the camera lens, the bracelet grows a little larger in frame; this is
   the main action and MUST clearly happen") y aclarar que **lo que se mueve es el BRAZO, no la cámara**
   (no congelar el brazo). Añadir negativo: "do NOT keep the arm frozen/static — the forearm MUST rise."
**Regla general (acercar en POV / selfie):**
- "Acercar a la cámara" en POV = **subir/extender el brazo hacia el lente**, NO mover la cámara. Redáctalo
  como acción física clara del brazo, y separa "el brazo se mueve" de "la cámara no se mueve". Si sólo
  dices "closer" + "camera locked", se congela. Emparejar con "closer = hand/arm, NOT camera" (Bloque
  acercamiento) pero SIEMPRE con el gesto del brazo explícito y afirmativo.
- **Vocabulario veneno:** "rotate"/"rotar" (→ vuelta completa). Preferir "tilt / angle slightly / turn
  just a little" + candado de cara fija.

**⚠️ AMPLIACIÓN (2º intento del mismo POV muñeca falló igual):** aún con "tilt solo un poco" **volvió a
dar la vuelta completa** Y activó **"Extender desde el marco" (outpaint) → inventó una SEGUNDA pulsera /
segundo charm** (al voltear la muñeca descubre el lado oculto y lo rellena con otra pulsera).
**Lección reforzada:**
1. **En muñeca/pulsera POV, cualquier permiso de inclinación = vuelta completa.** El fix definitivo es
   **CERO rotación**: "do NOT rotate, turn, roll, twist, tilt, pivot, or spin the wrist AT ALL — not even
   slightly; the wrist keeps the EXACT same orientation the whole time." Único movimiento = **antebrazo
   sube RECTO hacia el lente (traslación pura)**, misma vista de la pulsera de principio a fin.
2. **Girar la muñeca dispara outpaint + duplicado de producto.** Añadir SIEMPRE en estos casos: candado
   anti-outpaint ("do NOT extend, expand, outpaint, zoom out, or reveal new area beyond the frame; frame
   borders fixed") + **"ONE bracelet, ONE charm only; do NOT create/duplicate a second bracelet or
   charm."**
3. **Si a la 2ª–3ª sigue girando/duplicando → 2.6 directo.** No insistir en 3.0 con muñeca+pulsera+POV;
   el 2.6 es fiel y no rota ni inventa. Es la carta segura documentada para este combo.

**✅ AMPLIACIÓN VALIDADA (pulsera JJK: enganchar + enseñar sin girar — FUNCIONÓ en 2.6):** serie de la
pulsera de dijes de Jujutsu Kaisen. Se pidió: la mano baja a **enganchar** el broche en la muñeca, luego
la muñeca **enseña la pulsera** a la cámara **sin girar el brazo**. En 3.0 falló 2 veces (el brazo giraba
+ el enganche se veía raro). Se resolvió con 3 fixes combinados:
1. **ENGANCHE POR DEBAJO, nunca "por detrás" ni arriba.** Decir *"passing behind the wrist"* hace que Kling
   **gire la muñeca** para "llegar atrás". Y enganchar arriba (donde cuelga la cadenita) **se ve raro/falso**.
   → El broche se cierra en la **cara INFERIOR de la muñeca**: *"the fingers reach just UNDER the wrist and
   fasten the clasp on the UNDERSIDE — not on top, not floating above, not behind."*
2. **🆕 FOREARM ORIENTATION LOCK (describir la orientación EXACTA = mata la rotación).** No basta decir "no
   rotes"; hay que **fijar la pose**: *"the forearm stays horizontal and the back of the wrist stays facing
   UP and toward the camera, in the EXACT same orientation as the reference frame, for the entire clip; do
   NOT rotate/turn/roll/twist/tilt/pivot/angle the wrist, forearm, palm or back of the hand — not even to
   'show' the bracelet."* El "enseñar" = **levantamiento recto MÍNIMO** (traslación pura), NO acercamiento
   grande (mientras más "closer" pides, más tiende a girar para angular la pulsera).
3. **Tras 2 fallos de rotación en 3.0 → 2.6** (confirmó la regla del punto 3 de arriba). En 2.6 con estos
   dos candados: funcionó re bien.
- **Plan B si aún falla:** quitar el enganche (lo más difícil, 2 manos + oclusión) y dejar SOLO el
  levantamiento recto mínimo con la pulsera ya puesta. Menos manos = casi imposible que deforme o gire.
- **Regla destilada:** para "enganchar pulsera" el broche va **por debajo de la muñeca**; para "enseñar sin
  girar" **describe la orientación exacta de la mano** (no solo "no rotes") + levantamiento mínimo + 2.6.

---

## 🔜 PENDIENTE
- [ ] Recibir y analizar los FALLOS ❌ → extraer anti-patrones (qué rompe el video).
- [ ] (Opcional) Éxitos de tipos aún no vistos: comida/bebida, cosmético líquido, electrónica
      con pantalla, humo/vapor, packaging.
- [ ] El usuario confirmará cuándo el modelo está CERRADO.
