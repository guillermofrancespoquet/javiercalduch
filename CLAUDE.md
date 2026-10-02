# Javier Calduch — repo de planificación NutriLogos

Este repositorio es de **un único cliente: Javier Calduch**. Contiene su planificación nutricional en HTML (publicada en GitHub Pages) y los documentos asociados. Nunca se mezclan aquí datos de otros clientes.

Las instrucciones de estructura y estética **no son de este repo**: son generales para todos los clientes de NutriLogos y viven en el proyecto NUTRILOGOS de claude.ai como `INSTRUCCIONES_PLANTILLA_NUTRILOGOS_v5.0.txt` (versión vigente: **v5.0**, septiembre 2026). Este archivo explica cómo aplicarlas a Javier.

## Fuente de verdad

1. **Plantilla v5.0** (`docs/INSTRUCCIONES_PLANTILLA_NUTRILOGOS_v5.0.txt` si está copiada en el repo; si no, pídele el archivo a Guille). Antes de cualquier cambio estructural, de CSS, de JS o de bloques nuevos, léela. Si el repo y la plantilla discrepan, manda la plantilla, salvo las excepciones de Javier listadas más abajo.
2. **Metodología NutriLogos** (100% plant-based, flexible según individualización). Las decisiones nutricionales se apoyan en ella; no se improvisan criterios clínicos.
3. **Este archivo** para el contexto y las particularidades de Javier.

Si algo debería cambiar en el estándar general (no solo para Javier), no se corrige únicamente aquí: se lo señalas a Guille para que actualice la plantilla en el proyecto y todos los clientes sigan la misma línea.

## Reglas de la plantilla v5.0 que más se tocan

- Orden de bloques: cabecera → descripción del cliente (5 píldoras, incluida "Aversiones / exclusiones") → Objetivo (bloque azul) → Perfil de la persona → tabla resumen semanal (`id="printArea"`) → menú por días → lista de compra → suplementación → recetas → sección personalizada → Próxima revisión.
- CSS estándar: **no modificar**. Funciones JS de la sección 6.4: copiar exactamente. Todo el JS en **un único `<script>` al final del `<body>`**, con las llamadas (`buildTabs()`, `render()`, `buildShopTabs()`, `renderShop()`, `buildRecetas()`) después de que exista el HTML al que apuntan.
- Separación entre secciones: solo `margin-top:2.5rem` y el `border-bottom` de `.section-label`. **Sin `<hr>`**, sin `border-top`/`padding-top` en los wrappers.
- Espaciado interno del perfil (v5.0): `pn-perfil-grid-2` con `margin-bottom:1.75rem`; somatotipo con `margin-top:2rem;margin-bottom:1.75rem`; `pn-perfil-section-row` con `margin-top:1.75rem`; impresiones con `margin-top:1.75rem`; tarjetas antro secundarias con `margin-top:0.85rem`.
- Somatotipo: div con estilos inline (sección 4.3), no la clase `pn-soma-card`.
- Títulos: **"Datos bioimpedancia"**, sin nombres de marca de dispositivo (nunca "InBody"). El bloque "Control de peso (objetivo)" **ya no existe** en v5.0; esa información va en el Objetivo o en las impresiones.
- Badges: D / C / Me / Ce; A (Almuerzo, media mañana) solo si el cliente la lleva. C es mediodía, Ce es noche; no confundir A con C.
- Ingredientes de cada comida: píldoras (`\n` en `desc` crea una píldora). En la tabla semanal, texto plano.
- `sportBanner` con kcal/macros solo si aporta valor para Javier; decisión de Guille caso por caso.
- Botones de PDF en el perfil: estilo `#0d3d4f`, rutas relativas con `./` (sección 4.4).
- Botón de calendario de "Próxima revisión": si no hay fecha exacta, `pointer-events:none;opacity:0.4`. Fechas UTC `YYYYMMDDTHHMMSSZ`.

## Cómo se trabaja con Guille

- Orden: datos del cliente en el chat → criterios clínicos acordados → estructura confirmada → HTML → iteración visual. No se empieza a tocar HTML antes de que datos y criterios estén cerrados. Las interpretaciones clínicas las revisa y aprueba Guille antes de plasmarlas.
- Cambios **quirúrgicos**: ediciones dirigidas (`Edit`), nunca reescribir el archivo entero salvo necesidad real. Lee el HTML antes de tocarlo.
- Si Guille dice "no hagas nada", "de prueba" o "gracias", no ejecutes nada.
- No cambies convenciones establecidas (nombres de archivo, rutas) por tu cuenta mientras resuelves un problema; pregunta antes.
- Después de editar: valida el JS (`node --check` sobre el script extraído, o abre el HTML y revisa la consola). Dentro de strings JS solo `\n` como escape; un salto de línea literal rompe el script.
- Imágenes embebidas en HTML en base64 (portabilidad entre visor, local y GitHub Pages).
- Cuando Guille te da pautas de cambio para el repo, puedes hacer commit (mensaje claro) en tu rama de trabajo, push de esa rama y abrir un PR contra `main`. Guille lo revisa y hace el merge. Nunca hagas merge ni push directo a `main`. Si la rama ya se fusionó, reiníciala desde `main` antes de seguir. Sin pautas de cambio (preguntas, revisiones, exploración), no commitees.

## Redacción del contenido

- Todo lo dirigido al cliente va en **segunda persona del singular** (tú/te): notas de adaptación, impresiones, pautas, PDFs. Nunca tercera persona.
- Cantidades concretas (gramos, ml, minutos) en las pautas; nada de "un poco de".
- Alimentos crudos vs cocidos y origen del producto (arroz basmati en crudo, legumbre de bote o cocida, cuscús, crema de soja frente a leche de coco…) se especifican siempre; Guille revisa esos detalles uno a uno.
- Jerarquía de lácteos si aparecen: yogur de soja > queso fresco batido / yogur griego ligero > yogur griego normal / lácteos enteros (evitar). Huevo prácticamente fuera del plan base (en Javier existe como alternativa puntual a la tortilla de garbanzo, no como protagonista).
- Batch cooking siempre **opcional**. La cena libre nunca se elimina.

## Perfil de la persona: cómo se actualiza

- Cada vez que llegan nuevos PDFs de antropometría/bioimpedancia, se actualizan métricas, somatotipo, pliegues, perímetros, bioimpedancia, impresiones y los botones de PDF.
- Cada dato nuevo muestra la **comparativa con la medición anterior** con color verde (mejora) o rojo (empeora). Guille indica qué énfasis dar en las impresiones (p. ej. valor Z muscular, LDL); respétalo.
- Impresiones: concisas, sin sobreexplicar por qué se consiguieron los resultados. Colores semánticos de puntos: verde logro, azul cambio de objetivo, ámbar vigilar, coral alerta.
- Suplementación: sin nombres de marca (p. ej. pastillas de sodio). Geles: ofrecer también la opción de 55–60 g de CHO. Para guayaba, usar solo la forma sólida.
- Mediciones registradas hasta ahora: 06/05, 15/06 y 25/08/2026. Próxima medición directa: la semana siguiente a la sesión online del 1/10/2026. **Próxima revisión: miércoles 14/10/2026 a las 13:00 h** (ya reflejada en el HTML; si cambia la fecha o hay una nueva, actualizar texto y botón de calendario, y sin fecha exacta dejar el botón atenuado).

## Contexto de Javier

- Psicólogo, vive en Valencia. Cliente de NutriLogos con revisiones periódicas con Guille (la del 1/10/2026 fue online).
- **Objetivo deportivo:** media maratón (21K) de Valencia el **25 de octubre de 2026** (domingo, de buena mañana). **Objetivo de marca: bajar de 1h45'** (≈ 4:58–4:59 min/km), acordado en la consulta online del 1/10/2026.
- **Objetivo de composición:** ganancia muscular / recomposición con ingesta normocalórica o ligero superávit (el plan inicial era de déficit; se remodeló tras la bioimpedancia). Compagina carrera con fuerza.
- **Semana tipo:** jueves = **Fuerza** (cambiado de CrossFit; no debe quedar ningún "crossfit" residual en banner, notas, tabla semanal ni suplementación). Domingo = día de descanso con batch cooking opcional y recordatorio de suplementación.
- **Referencia de ritmo para el 21K:** la estimación inicial de coaching (5:30–5:35 min/km, ~1h56'–1h58') **queda sustituida** por el objetivo de bajar de 1h45'. Sigue siendo un objetivo de coaching, no un dato medido; se ajusta con las sensaciones de los entrenos y el tapering.
- **Simulacro 15K Nocturna Valencia (26/09/2026, 22:30 h):** ejecutado. Hubo más fatiga de la esperada, pero con calor, humedad y de noche, condiciones que no serán las de la media (de buena mañana). Su PDF de estrategia se retiró del repo (ya no se usa y no está enlazado).
- **Tirada larga de 19K (30/09/2026):** muy buenas sensaciones, a una hora más parecida a la de la carrera. Es la referencia más fiable de cara a la media.
- **Calendario de entrenos hasta la carrera (solo informativo; no se ajusta nada de momento):**
  - Quedan antes de la semana previa: series de 9K, rodaje de 10K y tirada de 14K (**test de sudoración**: Javier pasará peso antes y después, líquido ingerido, duración e intensidad).
  - Semana previa: series de 6×300 m, rodaje de 10K y tirada de 11K.
  - Semana de carrera: activación el miércoles (8K), fuerza de activación en varios días y paseo el viernes.
- **Ajustes de comida acordados el 1/10/2026:**
  - **Avena: nunca antes de entrenar.** Se aplica en el **documento de competición**, no en el plan base por ahora.
  - **Arroz:** le suele causar hinchazón. Se **reduce algo en el plan base** (menos apariciones y/o menos cantidad, con sustitutos como quinoa, patata, boniato, cuscús o pasta). **Aplicado en el HTML el 2/10/2026:** el arroz basmati pasa de 4 comidas a 2 (jueves cena y viernes almuerzo, 80 g en crudo cada una; el batch del domingo los cubre). Miércoles cena (curry) usa 200 g de patata en crudo y el sábado almuerzo usa cuscús integral precocinado; en intraentreno el vasito de arroz se cambió por cuscús o quinoa. Si se vuelve a tocar, mantener coherentes días, tabla `#printArea`, batch y lista de compra.
  - **Fibra:** controlarla un poco porque pasa por épocas de estreñimiento. Se consulta aparte; no tocar el plan hasta que Guille lo decida.
  - Pauta de líquidos/sodio e hidratos por hora para la media: a la espera de los datos del test de sudoración.
- Calcio y vitamina D: hay pauta específica en el plan; no la retires al editar suplementación.

## Excepciones de Javier respecto a la plantilla v5.0

Son decisiones conscientes de Guille; no las "corrijas" sin preguntar:

- **"Próximos eventos"** va justo después del bloque Objetivo (la plantilla coloca las secciones personalizadas antes de "Próxima revisión"). Tras el simulacro se retiró y **ahora contiene el 21K de Valencia (domingo 25/10/2026)**, **sin documento incrustado ni botón a PDF** (hecho el 2/10/2026): Guille preparará la estrategia de competición de otra forma, y la tarjeta del evento debe dejar claro que ese contenido llegará de forma parecida a como se hizo con el simulacro. Si en el futuro se enlaza un archivo, comprueba su carpeta real antes de tocar cualquier `href` y mantén la ruta que funcione en GitHub Pages (el repo usa `documentos/`; la plantilla propone `./assets/`).
- **Lista de compra:** el estado tachado se conserva **dentro de la sesión** al cambiar de pestaña (objeto JS `shopState`), pero no entre sesiones, para evitar desincronizaciones cuando el HTML se actualiza en GitHub. Verifica en el archivo cómo está implementado antes de modificarlo; la v5.0 de referencia solo usa `classList.toggle('done')` sin memoria al cambiar de pestaña.
- El HTML nació sobre v4.x y puede conservar restos (bloque "Control de peso", `<hr>`, espaciados antiguos). Alinearlo con v5.0 solo cuando Guille lo pida; no lo hagas de oficio dentro de otra tarea.
- Incluye recetas propias en el acordeón (ensalada de cuscús con gazpacho, gazpacho de remolacha, entre otras) y una sección de hidratación/intraentreno.

## PDFs de marca (simulacros, estrategias, recetas)

- Se generan con la skill `nutrilogos-brand` (paleta petróleo `#163a47`→`#1f4d5e`, camel `#c19a6b`/`#d9b88c`, crema `#f7f4ee`/`#e7dfd2`) y **WeasyPrint** (no wkhtmltopdf). Logo: `Logo_circular.png` en el hero, nunca el cuadrado.
- Fuente `'Liberation Sans', Arial, sans-serif`. Sin emojis (se renderizan mal; usar elementos CSS).
- **Sin `box-shadow`** en elementos con `border-radius`: WeasyPrint dibuja una línea vertical fantasma. Separar con `border: 1px solid`.
- Verifica el número de páginas antes de entregar y revisa siempre la vista previa. El contenido se aprueba en el chat antes de generar el PDF.
- Fichas de receta individuales: skill `nutrirecipe-generator` (marca NutriLogos). No usar `futedu-recipe-generator`.

## Checklist antes de dar un cambio por bueno

- El JS valida y no hay errores de consola; las pestañas de día y de compra funcionan.
- Segunda persona en todo texto nuevo; sin marcas de dispositivos; sin "crossfit" residual.
- La tabla semanal (`#printArea`) y los días del array `days` coinciden entre sí.
- Los enlaces a PDF abren en local y en GitHub Pages.
- No se ha tocado nada fuera de lo pedido.

*Mantén este archivo al día cuando cambie el contexto de Javier (fecha de revisión, objetivo, mediciones, eventos) o cuando Guille publique una nueva versión de la plantilla.*
