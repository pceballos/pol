# Kit de arranque: prompts listos para copiar

Cómo usarlo: cada bloque ```así``` se copia entero y se pega en Claude Code, abierto dentro de la carpeta del proyecto.
Contexto completo de cada proyecto: `ROADMAP.md` de este mismo repo.

---

## 0 · Preparación (10 min, una sola vez)

1. Instalar Claude Code en la PC y loguearse con el plan Max.
2. Crear una carpeta `~/proyectos/` con una subcarpeta por proyecto: `fabrica-ideas`, `coreano`, `canal-futbol`, `juego-mito`. Bombazo usa su carpeta actual.
3. Copiar `ROADMAP.md` y `PROMPTS.md` en `~/proyectos/`.
4. En cada carpeta: abrir una terminal → `claude` → pegar el prompt que corresponde.
5. Regla de oro: cada vez que corrijas algo dos veces, pedile *"guardá esto como regla en CLAUDE.md"*. Así no lo repetís nunca más.

**Orden sugerido para mañana:** 1 Fábrica (lo que más rinde) → 3 Coreano (rápido, lo usás esa misma noche) → 2 Bombazo → 6 Canal.

---

## 1 · Fábrica de ideas y guiones

**Antes:** juntá en `fabrica-ideas/voz/` de 3 a 5 transcripts de tus mejores videos y 2 de los peores (en archivos .txt). Si encontrás la conversación buena con Claude, guardala como `voz/conversacion-buena.md`.

```
Sos mi socio de contenido. Tengo dos canales de YouTube y redes en formato corto: Brawlconpol (Brawl Stars) y Clashconpol (Clash Royale), en español rioplatense.

OBJETIVO: armar una "fábrica de ideas" que todas las semanas me entregue 10 ideas de video que pasaron filtros de calidad, y para las que yo elija, un guion con mi voz y con datos verificados.

HERRAMIENTAS QUE YA TENGO (leelas primero y reutilizalas, no las reescribas):
- Scraper de leads/outliers de YouTube (mis nichos + otros nichos de gaming): [RUTA]
- Radar de noticias: [RUTA]
- Visualizador (para producción): [RUTA]

PIPELINE A CONSTRUIR:
1. Outliers: usar mi scraper para traer videos que rinden muy por encima del promedio de su canal.
2. Analista de formato: de cada outlier extraer el FORMATO, no el tema (gancho, estructura, por qué es novedoso, duración, ritmo). Guardar todo en una biblioteca de formatos (formatos.json o similar).
3. Ideador: cruzar formatos de OTROS juegos con Brawl/Clash + noticias del radar. Cada idea pasa el test "purple cow": ¿el espectador de mi nicho ya vio algo así? Si la respuesta es sí, se descarta. Puntuar cada idea de 1 a 10 en novedad, curiosidad del título y facilidad de producción.
4. Verificador: cada afirmación factual (meta, estadísticas, fun facts, lore, promociones) necesita una fuente: Supercell oficial, notas de parche, API oficial de Brawl Stars, Brawlify, etc. Si un dato no tiene fuente, no entra. Marcá cada dato con su link.
5. Guionista: escribir como hablo yo. Aprender de mis transcripts en ./voz/ (los buenos son el modelo y los malos el antiejemplo). Prohibido el tono de anuncio, los "¡No te lo vas a creer!" genéricos y el humor robótico. Tiene que sonar a una persona real hablando.

ENTREGABLES:
- Una skill de Claude Code (.claude/skills/fabrica/SKILL.md) con todas las reglas: purple cow, voz, verificación. Cada vez que yo te corrija algo, actualizala.
- Un comando que corra todo y deje en ./salida/AAAA-MM-DD.md las 10 ideas con puntaje, el formato de origen (con link al outlier) y por qué es purple cow.
- Un comando "guion <número de idea>" que genere el guion con fuentes al pie.

Empezá leyendo mis herramientas y mis transcripts. Después mostrame un plan corto antes de construir. Preguntame lo que necesites.
```

---

## 2 · Bombazo: distribución

Abrir Claude Code **dentro del repo de Bombazo**.

```
Contexto: Bombazo (bombazo.app / bombazo.com.ar) es mi juego web de trivia de fútbol. Desafío diario de 4 juegos que cambia a las 00:00 (hora Argentina). Stack: Cloudflare + Supabase. Login con Google o mail (con confirmación). El 78% de los jugadores no se loguea, ni siquiera regalándoles Bombazo+. Ya tengo botón de compartir el resultado.

Quiero 3 cosas. Hacelas en este orden y mostrame un plan antes de cada una:

1) MEDIR (primero de todo):
- Eventos de analítica: jugador anónimo vs logueado, vuelve al día siguiente (sí/no), racha, cuándo ve el aviso de login y si lo acepta.
- Un reporte simple (consulta SQL en Supabase o una página /admin) que responda: ¿el 78% anónimo vuelve o juega una sola vez?

2) LOGIN POR RACHA:
- Cuando un jugador anónimo llega a 3 días de racha, mostrar "No pierdas tu racha de X días: guardala con Google en 1 clic".
- Dejarlo detrás de una variable para poder prenderlo y apagarlo.

3) POSTS AUTOMÁTICOS EN X:
- Mi workflow genera videos mp4 de los juegos: [RUTA O DESCRIPCIÓN DEL WORKFLOW].
- Los videos se suben a Cloudflare R2 y un Worker con cron los publica en X 4 veces por día, con un texto + el link.
- Antes de construir, revisá los precios y límites actuales de la API de X para subir videos y decime qué plan necesito.
- Credenciales como secrets de Cloudflare, nunca en el código.
- Modo prueba: que primero me mande el post para revisarlo antes de publicarlo de verdad.
```

### 2C · Buscador de streamers y tuiteros (en Grok, no en Claude Code)

Pegalo en Grok. Si Grok permite tareas programadas, programalo diario; si no, pegalo cada mañana.

```
Sos mi buscador de promotores para Bombazo (bombazo.app), un juego web gratis de trivia de fútbol con desafío diario. Mi cuenta de X es @[TU_USUARIO].

Buscá en X y en la web 10 cuentas por día que cumplan:
- Streamers de fútbol o gaming en español (Twitch, Kick, YouTube) que hagan contenido de trivia, quizzes, FIFA/EA FC o charla futbolera.
- Tuiteros de fútbol con buena interacción (no solo seguidores) que publiquen quizzes, datos curiosos o debates.
- Priorizá cuentas parecidas a las que ya interactúan conmigo o que siguen a cuentas que yo sigo.
- Excluí cuentas que ya aparecieron en días anteriores, bots y cuentas que solo publican apuestas.

Para cada una entregá: usuario, plataforma, seguidores aproximados, por qué encaja (1 línea), un post reciente suyo como prueba, y un mensaje privado listo para mandar, en tono rioplatense, cercano y sin vender: mencioná algo concreto de su contenido, invitalo a jugar o a jugarlo en vivo, y ofrecele un código de regalo de Bombazo+ ([CÓDIGO]).
Formato: tabla.
```

---

## 3 · App de coreano

Abrir Claude Code en `coreano/`.

```
Construí una app web instalable en iPhone (PWA, se agrega a la pantalla de inicio) para aprender coreano. Todo gratis, sin servidor pago.

YO: leo hangul, sé muy poco más. Objetivo: conversar en Corea y leer artículos y redes en coreano. Estudio 15 min a la mañana y 15 min a la noche.

UX: un solo botón grande "Sesión de hoy". Según el día y la hora, me guía paso a paso sin que tenga que decidir nada:
- MAÑANA: 10 min de tarjetas con repaso espaciado (algoritmo tipo SM-2 o FSRS, con audio usando la voz coreana del iPhone por speechSynthesis) + 5 min de shadowing (escucho una frase, la repito en voz alta, marco "bien" o "repetir").
- NOCHE: Lun/Mié/Vie → misión de conversación: me muestra una situación de viaje (pedir comida, taxi, hacer amigos, etc.), 5 frases clave y un botón que copia un prompt listo para pegar en la app de Claude en modo voz y practicarla. Mar/Jue → lectura graduada: texto corto a mi nivel, con traducción al tocar cada palabra y botón "agregar a mis tarjetas". Sáb → repaso general. Dom → descanso o repaso opcional.

CONTENIDO:
- Fase 1 "Supervivencia" (meses 1-2): las 500 palabras y frases más útiles para viajar y socializar, en forma cortés (-요).
- Fase 2 "Conversación" (meses 3-4). Fase 3 "Lectura real" (mes 5 en adelante).
- Generá el contenido de la fase 1 completo ahora (en JSON) y dejá preparada la estructura para agregar las otras fases.

EXTRA: racha diaria, barra de progreso por fase, botón para exportar e importar el progreso (por si se borra la memoria del navegador). Diseño minimalista y lindo, modo oscuro.
Deploy gratis en Cloudflare Pages o GitHub Pages y explicame cómo agregarla al iPhone.
```

---

## 4 · Tía + Grok ⏸

Antes, preguntale a tu tía:
1. ¿Qué sistema usa para cargar los datos? ¿Acepta importar Excel/CSV o se carga todo a mano?
2. ¿Las facturas le llegan en PDF por mail, en papel o de las dos formas? ¿Cuántas por día?
3. ¿Qué campos carga de cada factura? (Pedile una captura de la pantalla de carga.)
4. ¿La empresa tiene alguna regla sobre usar IA con datos de clientes?

Con eso volvé a este chat y armamos su prompt y su flujo.

---

## 5 · Juego (cuando decidas): prototipos para comparar

Abrir Claude Code en `juego-mito/`. Las reglas completas de los dos conceptos están en `ROADMAP.md`, sección 5.

```
Leé ROADMAP.md, sección 5 (juego nuevo). Hay dos conceptos: "Runas del Oráculo" y "El Barquero", en un mundo de mitología griega + nórdica con nombres inventados (Ymbrós).

Hacé DOS prototipos jugables en navegador, uno por concepto, en carpetas separadas. Reglas:
- Feos a propósito: formas simples, cero arte. Lo único que importa es si el loop es divertido.
- Pero con "juice": que cada acción tenga feedback (temblor, número que salta, sonido simple).
- Una partida corta y completa: 3 rondas + 1 jefe + 1 tienda entre rondas.
- Para Runas: física 2D real (Matter.js o similar) al tirar las piedras.
- Al terminar, un botón "jugar otra vez".
Que ninguno tarde más de 1 hora. Después decime cómo correrlos.
```

---

## 6 · Canal faceless de fútbol (SUPERHOT en Blender)

**Antes (tu parte, unos 20 min):**
1. Entrar a mixamo.com (cuenta de Adobe gratis) → bajar el personaje **Y Bot** + animaciones: correr, trotar, pase, patada, festejo, caída, quieto (en formato FBX).
2. Guardar todo en `canal-futbol/assets/` junto con el video de referencia.
3. (Opcional, recomendado) Instalar **Blender MCP** para que Claude controle Blender en vivo. Pedíselo a Claude Code: *"ayudame a instalar blender-mcp"*.
4. Cuando llegues al paso de la voz: plan Creator de ElevenLabs (unos 22 USD por mes) → clonar tu voz con unos 30 min de audio limpio tuyo.

```
Vamos a crear un canal de YouTube faceless de fútbol en español: historias del fútbol, tácticas de partidos y de entrenadores legendarios, explicadas con animación 3D.

ESTILO: SUPERHOT. Jugadores = maniquíes blancos low-poly sin cara (Y Bot de Mixamo, en ./assets). Rojo para resaltar al rival o la jugada clave. Cancha minimalista, iluminación limpia, cámaras cinematográficas. Referencia visual: ./assets/[VIDEO]. Extraé frames con ffmpeg y analizalos antes de empezar.

FASE 1 · ESCENA BASE (por script de Python para Blender o con Blender MCP):
- Cancha reglamentaria estilizada, materiales SUPERHOT, luces, 5 cámaras template (aérea táctica, lateral TV, seguimiento a jugador, detrás del arco, cámara lenta dramática).
- Importar el Y Bot y las animaciones de ./assets.
- Mostrame renders de prueba para aprobar.

FASE 2 · MOTOR DE ESCENAS:
- Formato JSON que describa una jugada: jugadores (equipo, color, número), posiciones en el tiempo, acciones (correr, pasar, patear, festejar), trayectoria de la pelota, cortes de cámara, textos en pantalla.
- Script que lea ese JSON y anime todo en Blender automáticamente (mover maniquíes por la trayectoria + mezclar animaciones de Mixamo) y renderice en Eevee.
- Probalo con una jugada famosa (ej.: gol de Maradona a Inglaterra 1986).

FASE 3 · PIPELINE COMPLETO:
tema → investigación con fuentes → guion en español (voz cercana, nada robótico) → JSON de escenas → render → voz con ElevenLabs (API, mi voz clonada) → montaje con subtítulos (ffmpeg) → video final + versión short 9:16.
Yo solo apruebo el guion y el video final.

REGLAS: nada de imágenes reales de partidos ni escudos oficiales (derechos de autor). Cada video tiene que tener análisis original, no contenido repetitivo (para que YouTube no lo desmonetice).
Mostrame un plan antes de cada fase.
```

---

## Checklist de mañana
- [ ] Preparación (sección 0)
- [ ] Fábrica: transcripts + rutas → prompt 1
- [ ] Coreano: prompt 3 → primera sesión esa noche
- [ ] Bombazo: prompt 2 + Grok 2C
- [ ] Mixamo + video de referencia → prompt 6
- [ ] Preguntas a la tía
- [ ] Pensar el juego (1 o 2)
- [ ] Pendiente en este chat: ideas de ingreso pasivo (más allá del canal) y elegir concepto de juego
