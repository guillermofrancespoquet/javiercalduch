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
- Commits solo cuando Guille lo pida, con mensaje claro. No hagas push sin que lo pida.

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
- Mediciones registradas hasta ahora: 06/05, 15/06 y 25/08/2026. Próxima medición directa: la semana siguiente a la sesión online del 1/10/2026.

## Contexto de Javier

- Psicólogo, vive en Valencia. Cliente de NutriLogos con revisiones periódicas con Guille (la del 1/10/2026 fue online).
- **Objetivo deportivo:** media maratón (21K) de Valencia el **25 de octubre de 2026**.
- **Objetivo de composición:** ganancia muscular / recomposición con ingesta normocalórica o ligero superávit (el plan inicial era de déficit; se remodeló tras la bioimpedancia). Compagina carrera con fuerza.
- **Semana tipo:** jueves = **Fuerza** (cambiado de CrossFit; no debe quedar ningún "crossfit" residual en banner, notas, tabla semanal ni suplementación). Domingo = día de descanso con batch cooking opcional y recordatorio de suplementación.
- **Referencia de ritmo para el 21K (estimación de coaching, no dato medido):** 5:30–5:35 min/km, marca ~1h56'–1h58'. Se ajusta según sensaciones tras el simulacro y el tapering.
- **Simulacro 15K Nocturna Valencia:** sábado 26/09/2026, salida 22:30 h. Ya ejecutado; su estrategia nutricional (viernes, sábado, pre / intra / post-carrera) está en `documentos/Simulacro_15K_Javier_Calduch.pdf`, enlazado desde la sección "Próximos eventos".
- Calcio y vitamina D: hay pauta específica en el plan; no la retires al editar suplementación.

## Excepciones de Javier respecto a la plantilla v5.0

Son decisiones conscientes de Guille; no las "corrijas" sin preguntar:

- **"Próximos eventos"** va justo después del bloque Objetivo (la plantilla coloca las secciones personalizadas antes de "Próxima revisión"). Contiene el botón al PDF del simulacro.
- El PDF del simulacro se enlaza con ruta relativa a `documentos/` mientras la plantilla propone `./assets/`. Comprueba en qué carpeta está realmente el archivo antes de tocar cualquier `href`, y mantén la ruta que funcione en GitHub Pages.
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
