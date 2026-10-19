# Javier Calduch — repo de planificación NutriLogos

Este repositorio es de **un único cliente: Javier Calduch**. Contiene su planificación nutricional en HTML (publicada en GitHub Pages) y los documentos asociados. Nunca se mezclan aquí datos de otros clientes.

Las instrucciones de estructura y estética **no son de este repo**: son generales para todos los clientes de NutriLogos y viven en el proyecto NUTRILOGOS de claude.ai como `INSTRUCCIONES_PLANTILLA_NUTRILOGOS_v5.0.txt` (versión vigente: **v5.0**, septiembre 2026). Este archivo explica cómo aplicarlas a Javier.

## Fuente de verdad

1. **Plantilla v5.0** (copiada en la raíz del repo como `INSTRUCCIONES_PLANTILLA_NUTRILOGOS_v5.0.txt`; si falta, pídele el archivo a Guille). Antes de cualquier cambio estructural, de CSS, de JS o de bloques nuevos, léela. Si el repo y la plantilla discrepan, manda la plantilla, salvo las excepciones de Javier listadas más abajo.
2. **Metodología NutriLogos** (100% plant-based, flexible según individualización). Las decisiones nutricionales se apoyan en ella; no se improvisan criterios clínicos.
3. **Instrucciones de estilo app v1.0** (`INSTRUCCIONES_ESTILO_APP_NUTRILOGOS_v1.0.txt`, en la raíz del repo): capa visual solo de estilo (CSS y colores) sobre la plantilla v5.0. **`index.html` es la versión app**: estructura y JS de v5.0, estilo de app v1.0 (ver excepciones).
4. **Este archivo** para el contexto y las particularidades de Javier.

Si algo debería cambiar en el estándar general (no solo para Javier), no se corrige únicamente aquí: se lo señalas a Guille para que actualice la plantilla en el proyecto y todos los clientes sigan la misma línea.

## Reglas de la plantilla v5.0 que más se tocan

- Orden de bloques en `index.html` (variante app): cabecera → Objetivo (bloque teal) → Próximos eventos → Impresiones del profesional → tabla resumen semanal (`id="printArea"`) → menú por días → lista de compra → suplementación → recetas → intraentreno (desplegable). **No están en el HTML** descripción del cliente, perfil de la persona con métricas ni próxima revisión: los muestra la app; sus datos viven en la sección "Datos del cliente" de este archivo.
- CSS estándar: **no modificar**. Funciones JS de la sección 6.4: copiar exactamente. Todo el JS en **un único `<script>` al final del `<body>`**, con las llamadas (`buildTabs()`, `render()`, `buildShopTabs()`, `renderShop()`, `buildRecetas()`) después de que exista el HTML al que apuntan.
- Separación entre secciones: solo `margin-top:2.5rem` y el `border-bottom` de `.section-label`. **Sin `<hr>`**, sin `border-top`/`padding-top` en los wrappers.
- Badges: D / C / Me / Ce; A (Almuerzo, media mañana) solo si el cliente la lleva. C es mediodía, Ce es noche; no confundir A con C.
- Ingredientes de cada comida: píldoras (`\n` en `desc` crea una píldora). En la tabla semanal, texto plano.
- `sportBanner` con kcal/macros solo si aporta valor para Javier; decisión de Guille caso por caso.

## Cómo se trabaja con Guille

- Orden: datos del cliente en el chat → criterios clínicos acordados → estructura confirmada → HTML → iteración visual. No se empieza a tocar HTML antes de que datos y criterios estén cerrados. Las interpretaciones clínicas las revisa y aprueba Guille antes de plasmarlas.
- Cambios **quirúrgicos**: ediciones dirigidas (`Edit`), nunca reescribir el archivo entero salvo necesidad real. Lee el HTML antes de tocarlo.
- Si Guille dice "no hagas nada", "de prueba" o "gracias", no ejecutes nada.
- No cambies convenciones establecidas (nombres de archivo, rutas) por tu cuenta mientras resuelves un problema; pregunta antes.
- Después de editar: valida el JS (`node --check` sobre el script extraído, o abre el HTML y revisa la consola). Dentro de strings JS solo `\n` como escape; un salto de línea literal rompe el script.
- Imágenes embebidas en HTML en base64 (portabilidad entre visor, local y GitHub Pages).
- Cuando Guille te da pautas de cambio para el repo, puedes hacer commit (mensaje claro) en tu rama de trabajo, push de esa rama y abrir un PR contra `main`. **Guille te autorizó el 19/10/2026 a hacer también el merge del PR** una vez acordados los cambios en el chat. Nunca hagas push directo a `main`; si el merge falla por conflicto o checks, no lo fuerces y avísale. Si la rama ya se fusionó, reiníciala desde `main` antes de seguir. Sin pautas de cambio (preguntas, revisiones, exploración), no commitees.

## Redacción del contenido

- Todo lo dirigido al cliente va en **segunda persona del singular** (tú/te): notas de adaptación, impresiones, pautas, PDFs. Nunca tercera persona.
- Cantidades concretas (gramos, ml, minutos) en las pautas; nada de "un poco de".
- Alimentos crudos vs cocidos y origen del producto (arroz basmati en crudo, legumbre de bote o cocida, cuscús, crema de soja frente a leche de coco…) se especifican siempre; Guille revisa esos detalles uno a uno.
- Jerarquía de lácteos si aparecen: yogur de soja > queso fresco batido / yogur griego ligero > yogur griego normal / lácteos enteros (evitar). Huevo prácticamente fuera del plan base (en Javier existe como alternativa puntual a la tortilla de garbanzo, no como protagonista).
- Batch cooking siempre **opcional**. La cena libre nunca se elimina.

## Perfil de la persona: dónde vive y cómo se actualiza

- El perfil (métricas, somatotipo, pliegues, perímetros, bioimpedancia) **ya no está en el HTML**: se ve en la app. Aquí, en "Datos del cliente", queda solo como referencia histórica de la valoración del 25/08/2026. Lo que sigue en el HTML y se actualiza cuando Guille lo pida son las **Impresiones del profesional** (se nombra el cambio de dato frente a la medición anterior).
- Cada dato nuevo muestra la **comparativa con la medición anterior** con color verde (mejora) o rojo (empeora). Guille indica qué énfasis dar en las impresiones (p. ej. valor Z muscular, LDL); respétalo.
- Impresiones: concisas, sin sobreexplicar por qué se consiguieron los resultados. Colores semánticos de puntos: verde logro, azul cambio de objetivo, ámbar vigilar, coral alerta.
- Suplementación: sin nombres de marca (p. ej. pastillas de sodio). Geles: ofrecer también la opción de 55–60 g de CHO. Para guayaba, usar solo la forma sólida. **Excepción acordada con Guille el 19/10/2026:** se mantiene "IsoDrink" en la sección de intraentreno.
- Mediciones registradas: 06/05, 15/06, 25/08 y 14/10/2026 (la de 14/10 es la línea base actual, ver "Datos del cliente"). Javier las ve en la app; las revisiones ya no se muestran en el HTML. **El 19/10/2026 Guille pidió no señalar la masa muscular en las impresiones** (la considera bien). En el Objetivo el % de grasa se da con **Durnin**, no con Yuhasz.

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
  - **Avena: nunca antes de entrenar.** Se aplica en el **documento de competición**, no en el plan base por ahora (excepto la semana de competición, ver más abajo).
  - **Arroz:** le suele causar hinchazón. Se **reduce algo en el plan base** (menos apariciones y/o menos cantidad, con sustitutos como quinoa, patata, boniato, cuscús o pasta). **Aplicado en el HTML el 2/10/2026:** el arroz basmati pasa de 4 comidas a 2 (jueves cena y viernes almuerzo, 80 g en crudo cada una; el batch del domingo los cubre). Miércoles cena (curry) usa 200 g de patata en crudo y el sábado almuerzo usa cuscús integral precocinado; en intraentreno el vasito de arroz se cambió por cuscús o quinoa. Si se vuelve a tocar, mantener coherentes días, tabla `#printArea`, batch y lista de compra.
  - **Fibra:** controlarla un poco porque pasa por épocas de estreñimiento. Se consulta aparte; no tocar el plan hasta que Guille lo decida.
  - Pauta de líquidos/sodio e hidratos por hora para la media: a la espera de los datos del test de sudoración.
- Calcio y vitamina D: hay pauta específica en el plan; no la retires al editar suplementación.
- **Referencias de gasto energético (estimación del 19/10/2026, ±10 %):** TMB 1.576 kcal (bioimpedancia, equivale a Katch-McArdle con LBM 55,8 kg) × 1,33 ≈ 2.100 kcal sin entreno; rodaje ≈ 60 kcal/km netas; fuerza ≈ +300–350 kcal; 21K ≈ 1.340 kcal. Sobre el papel el plan base queda ~400 kcal corto en rodajes de ~10 km, pero el peso sube (+0,8 kg en 7 semanas, ≈ +120 kcal/día), así que **no se suben kcal**: manda la tendencia de peso y composición, no la ecuación.
- **Semana de competición (19–25/10/2026) — cambios TEMPORALES en los días del plan, a revertir tras la carrera:** el resto de días es casi descanso activo (fuerza de activación suave si toca), miércoles = activación de 8 km, viernes = paseo, sábado = víspera, domingo = carrera 21K. Se cambiaron etiquetas, banners, la cena libre y (20/10) **las comidas, ligeramente**, por dos indicaciones de Javi: **nunca avena antes de entrenar** (se quita en lun–jue, por si entrena, y en el desayuno del domingo) y **el arroz solo en días sin entreno o con entreno suave** (se mantiene en la cena del jueves y el almuerzo del viernes; las tortitas de arroz del miércoles también). Cambios: desayunos de lun–jue pasan a tostadas con yogur de soja y 250 ml de bebida enriquecida en calcio; lun aguacate de ½ a ¼ (almuerzo y merienda); mar merienda sin granola (yogur 150 g, plátano y 30 g de nueces); mié cuscús 220 g y 4 tortitas de arroz; jue desayuno con tomate en las tostadas y las semillas en el yogur (nunca mezcladas con el pan), nueces 15 g y smoothie con 1 plátano y sin los 50 g de avena; jue cena (poke bowl) con 60 g de mango en cubitos en vez de zanahoria rallada; domingo desayuno = placeholder que remite al documento de la app. Banners: lun ~2.200, mar ~2.300, mié ~2.450, jue ~2.200 kcal; vie sin cambios; el texto del banner no repite la etiqueta del deporte (se muestran juntas: `🧘 Descanso activo — …`). Domingo, suplementación: vitamina D = "1 perla de 2.000 UI hoy. En meses de baja exposición solar (oct–marzo) recomendable." (la sección "Suplementación recomendada" no se tocó). Lista de compra ajustada (avena ~100 g, plátano 7–8, mango 1 pequeño o 100 g congelado, yogur de soja 8–9 botes, pan 700 g, aguacate 2, bebida vegetal 2 L, sin granola ni impulsor). **Subida progresiva de hidratos (20/10), cambiando tofu/seitán por hidratos de kcal parecidas (hidratos +8/+17/+36 g, proteína −3/−8/−9 g, kcal ≈ 0/+15/+40 en mié/jue/vie):** mié tofu del almuerzo 150→120 g y patata del curry 200→250 g; jue tofu del poke 160→130 g, arroz del poke 80→90 g, boniato del almuerzo 250→300 g y smoothie con ¾ de scoop de proteína; vie tofu de la cena 180→150 g, boniato 250→300 g, seitán 180→140 g, arroz 80→100 g, desayuno con 4 rebanadas en vez de 3 y ¼ de aguacate en vez de ½. Banners: mié ~2.450 kcal · ~92 g proteína, jue ~2.200 · ~92, vie ~2.450 · ~91, con frase de hidratos más altos. Lista de compra: seitán 140 g, arroz 190 g, boniato ~800 g, patata ~650 g. Sábado y domingo no se tocan (el documento de la app marca la carga). Valores originales: mié ~2.450 kcal · ~95 g (tofu 150 g, patata 200 g); jue tofu 160 g, arroz 80 g, boniato 250 g, scoop completo; vie tofu 180 g, boniato 250 g, seitán 180 g, arroz 80 g, 3 rebanadas, ½ aguacate, ~2.400 kcal · ~100 g. Sábado (overnight oats) y viernes (smoothie de avena) no se tocaron. Sábado y domingo remiten al documento de competición de la app, que manda sobre las comidas del día previo y del día de carrera. La **cena libre se movió del sábado al domingo** (el gazpacho de remolacha pasó a la cena del sábado, y en la tabla semanal también). **Para volver a la semana base**: Lun rodaje (~2.300 kcal), Mar fuerza (~2.400), Mié rodaje (~2.250), Jue fuerza (~2.400), Vie fuerza (~2.400), Sáb "Sáb ★" rodaje + cena libre (~2.200 sin cena), Dom descanso (~1.900, 3 comidas), gazpacho de remolacha en la cena del domingo (y su nota en la lista de compra). Comidas originales: Lun overnight oats con crema de cacahuete (60 g de avena); Mar tortitas de avena (80 g) y merienda con 200 g de yogur y 30 g de granola; Mié overnight oats con manzana (60 g), cuscús 200 g, 3 tortitas de arroz; Jue bowl con 60 g de avena, smoothie con 50 g de avena y 1 plátano, nueces 20 g, poke con zanahoria rallada; vitamina D del domingo con "no saltarse. En verano con buena exposición diaria se puede valorar reducir con el nutricionista"; Dom tortitas de avena (70 g); aguacate ½ en lun almuerzo y merienda. Banners originales: lun ~2.300, mar ~2.400, mié ~2.250, jue ~2.400 kcal. El historial de git (commit anterior a este PR) tiene los textos exactos.

## Datos del cliente (retirados del HTML el 19/10/2026)

Fuente: valoración del 25/08/2026 por Guillermo Francés. Entre paréntesis, la medición previa (15/06/2026) cuando existe. Referencia histórica: los datos vigentes están en la app.

**Descripción:** hombre · 27 años · 173,5 cm · 62,70 kg. Psicólogo, vida activa, buena disponibilidad para cocinar. No fuma, no bebe, sueño sin registrar. Aversiones/exclusiones: sin alubias, sin marisco, sin quesos fuertes.

**Métricas principales:** condición física 88,9/100 (89,5) · peso 62,70 kg (63,05), IMC 20,83, normopeso · talla/envergadura 173,5/169,5 cm, braquicórmico, E. relativa 0,98 · % masa grasa Yuhasz 8,49 % (8,88), 5,32 kg, Σ6 pliegues 50,00 mm · % masa muscular 47,72 % (47,40), 29,92 kg, Z Phantom +0,90 · LBM 55,5 kg (55,8), músculo esquelético 35,9 kg (36,1) · TMB 1.568 kcal (1.573), edad metabólica 25 años (24) · % tejido adiposo 24,12 % (25,10), 15,12 kg (Ross y Kerr, 1993) · ratio cintura/cadera 0,88 (0,93), riesgo cardiovascular bajo (antes moderado).

**Pliegues (mm):** tríceps 10,00 (10,00) · subescapular 7,50 (7,50) · bíceps 2,00 (1,50) · cresta ilíaca 7,00 (7,00) · supraespinal 5,50 (6,50) · abdominal 12,00 (13,50) · muslo 9,00 (11,00) · pierna 6,00 (5,50) · Σ6 50,00 (54,00) · Σ8 59,00 (62,50).

**Perímetros (cm):** cintura 76,90 (78,50) · cadera 87,00 (84,70) · brazo relajado/contraído 30,00/32,50 · muslo/pierna 50,54/34,70 (muslo +0,94).

**Valoración del 14/10/2026 (línea base actual; entre paréntesis, 25/08/2026):** peso 63,5 kg (62,7) · IMC 21,1 · % grasa Durnin 11,7 % (11,3), 7,42 kg · tejido adiposo Ross-Kerr 25,0 % (24,1) · masa muscular Lee 46,4 % (47,7), 29,43 kg · Σ6 pliegues 54,3 mm (50,0) · Σ8 64,8 mm (59,0) · cintura/cadera 0,87 (0,88), riesgo bajo · perímetros: cintura 77,1, cadera 88,2, brazo relajado/contraído 29,4/31,9, muslo 50,6, pierna 35,0 · bioimpedancia: puntuación 90,7/100 (88,9), masa grasa 7,61 kg (7,21), PBF 12,0 % (11,5), músculo esquelético 36,0 kg (35,9), LBM 55,8 kg (55,5), TMB 1.576 kcal (1.568), edad metabólica 24 (25), grasa visceral 4 (3), agua 40,3 L, proteína 12,8 kg, masa ósea 2,79 kg · equilibrio muscular superior, inferior y entre ambos: ligeramente desequilibrado · fuerza normal. El bloque "Control de peso" de la bioimpedancia (65,69 kg, +2,24 kg) se ignora por obsoleto.

## Excepciones de Javier respecto a la plantilla v5.0

Son decisiones conscientes de Guille; no las "corrijas" sin preguntar:

- **"Próximos eventos"** va justo después del bloque Objetivo (la plantilla coloca las secciones personalizadas antes de "Próxima revisión"). Tras el simulacro se retiró y **ahora contiene el 21K de Valencia (domingo 25/10/2026)**, **sin documento incrustado ni botón a PDF** (hecho el 2/10/2026): Guille preparará la estrategia de competición de otra forma, y la tarjeta del evento dice: "Tu estrategia nutricional para la carrera (días previos, pre, intra y post) llegará en un documento aparte dentro de la APP." Si en el futuro se enlaza un archivo, comprueba su carpeta real antes de tocar cualquier `href` y mantén la ruta que funcione en GitHub Pages (el repo usa `documentos/`; la plantilla propone `./assets/`).
- **Lista de compra:** el estado tachado se conserva **dentro de la sesión** al cambiar de pestaña (objeto JS `shopState`), pero no entre sesiones, para evitar desincronizaciones cuando el HTML se actualiza en GitHub. Verifica en el archivo cómo está implementado antes de modificarlo; la v5.0 de referencia solo usa `classList.toggle('done')` sin memoria al cambiar de pestaña.
- **`index.html` es la versión app (19/10/2026):** estilo de las instrucciones app v1.0 (tokens `:root`, Inter, CSS completo de la sección 4) sobre la estructura y el JS de v5.0. El antiguo `index.html` v5.0 (con descripción, perfil y próxima revisión) se eliminó; sigue en el historial de git y sus datos están en "Datos del cliente". "Próximos eventos" se mantiene a petición de Guille. "Nutrición intraentreno — bici larga (>2h)" es un **desplegable** (`<details>` con los modelos A/B/C anidados como acordeón; se usa `<details>` porque el CSS `.pn-receta.open .pn-receta-body` abriría todos los acordeones anidados). Tabla semanal y su leyenda con el estilo original v5.0.
- **Estilo alineado con v5.0 el 2/10/2026** (sin `<hr>` ni `border-top`/`padding-top` en wrappers, un único `<script>` al final, leyenda en la tabla semanal). El contenido no se toca al alinear estilo: cada planificación es distinta. Ante nuevas versiones de la plantilla o del estilo app, alinear solo cuando Guille lo pida.
- Incluye recetas propias en el acordeón (ensalada de cuscús con gazpacho, gazpacho de remolacha, entre otras) y una sección de hidratación/intraentreno (bici larga >2h) cuyos modelos A/B/C son **desplegables**, reutilizando las clases del acordeón de recetas (`pn-receta`, sin CSS nuevo).

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
