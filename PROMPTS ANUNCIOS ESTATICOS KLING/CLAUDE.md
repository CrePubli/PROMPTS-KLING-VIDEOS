# Proyecto: Prompts de video para Kling AI (image-to-video / motion poster)

> Este archivo se carga automáticamente al abrir Claude Code en esta carpeta.
> Sirve para retomar el flujo de trabajo en CUALQUIER PC sin perder nada.

## Qué hacemos aquí

El usuario crea videos **image-to-video en Kling AI** (3.0 y 2.6, también Veo-compatible):
toma anuncios/imágenes estáticas (productos, posters, UGC) y las anima SUTILMENTE (cinemagraph)
para que cobren vida sin deformar el diseño ni mover el texto. Les pone música y los publica como
contenido más llamativo que una imagen fija. Trabaja por **familias/colecciones de producto**.

El objetivo de mi rol: **analizar cada imagen y generar el prompt completo de Kling, listo para
copiar y pegar**, aplicando todo el modelo aprendido.

## ⚠️ LEE ESTO PRIMERO

**El archivo [`MODELO-KLING.md`](MODELO-KLING.md) (en esta misma carpeta) es la fuente de verdad.**
Contiene todo el sistema destilado de 23+ ejemplos reales y 6 fallos analizados:
- Principio central, 3 formatos, 3 familias, bloques modulares
- Tabla de decisión, 13 reglas de oro
- Anti-patrones (qué rompe el video)
- El "principio del pararrayos", jerarquía de motion-cue, palanca de modelo 3.0/2.6
- Frases de oro e índice de ejemplos

**Antes de generar cualquier prompt, ten presente ese archivo.** Si es una sesión nueva, conviene
releerlo para refrescar los matices.

También hay una **biblioteca de prompts reales** para reutilizar/adaptar:
- [`BIBLIOTECA-PROMPTS-1-ORIGINALES-Y-FALLOS.md`](BIBLIOTECA-PROMPTS-1-ORIGINALES-Y-FALLOS.md) —
  21 éxitos originales + 6 fallos con su corrección.
- [`BIBLIOTECA-PROMPTS-2-GENERADOS.md`](BIBLIOTECA-PROMPTS-2-GENERADOS.md) — prompts generados
  (fútbol, anillo cangrejo, cepillo perros, pulseras BFF, gorras One Piece).
Cuando una imagen nueva se parezca a una de la biblioteca, parte de ese prompt y adáptalo.

## Flujo de trabajo (cómo responder cuando el usuario sube una imagen)

1. **Diagnóstico breve:** identificar la familia (impreso / modelo real / producto+entorno /
   collage), qué cobra vida y qué se congela, y los riesgos de ESA imagen.
2. **Generar el prompt en inglés, Formato C** (secciones), listo para pegar en Kling.
3. **Indicar el modelo** (3.0 por defecto; 2.6 si hay texto diminuto/denso) y la duración (~5-6s).
4. **Avisar qué vigilar** (deformaciones probables) y ofrecer variante más segura si aplica.

## Reglas clave (resumen — el detalle está en MODELO-KLING.md)

1. **Texto = capa de píxeles congelados** ("frozen flat pixel layer, do not re-render/redraw"). No
   citar texto roto; con texto diminuto usar **Kling 2.6**.
2. **Cámara clavada** (cero movimiento) cuando hay texto pequeño — el movimiento de cámara lo degrada.
3. **Producto hero nunca se deforma**; protege logos/texto bordado sobre el producto por separado.
4. **Pararrayos:** si hay persona/animal real, anímalo a ÉL (con una acción CLARA) → absorbe el
   movimiento y protege el arte impreso. Sin humano (colección): motion sink lejos del texto +
   congelar la zona del texto. Caras impresas/banderas/fuego son los imanes de movimiento más fuertes.
5. **El movimiento se contagia a lo cercano** → no animar fondos/entornos pegados al texto pequeño.
6. **Cada capa con freno** ("no exaggerated..."). Clip CORTO (~5s) = menos deriva del texto.
7. **Brillos:** pedir glint/sparkle puede salir artificial → es opción del usuario (con/sin brillo).
8. **Habla:** mover labios suele verse raro → opción del usuario (con/sin habla). Boca: "mouth fixed,
   no lip-sync" si no debe hablar.
9. **Cámara lenta:** para evitar slow-mo, pedir "normal real-time speed" + movimiento definido +
   negativos "no slow motion".
10. **Iconos/flechas/callouts** se animan solos → congelarlos por nombre.

## Notas
- Idioma con el usuario: español. Prompts para Kling: en inglés.
- Cuando aprendamos algo nuevo (un fallo o un acierto), **actualizar `MODELO-KLING.md`**.
- La memoria automática vive fuera de esta carpeta (en `~/.claude/...`) y NO viaja entre PCs —
  por eso todo lo importante está aquí, en la carpeta.
