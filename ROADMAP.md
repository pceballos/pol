# Roadmap IA — Pol

Estado: ⬜ pendiente · 🟡 en curso · ✅ hecho

| # | Proyecto | Por qué en este orden | Estado |
|---|----------|----------------------|--------|
| 1 | Fábrica de ideas y guiones (outliers → análisis → guion verificado) | Ya genera ingresos; es el cuello de botella | 🟡 |
| 2 | Distribución automática de Bombazo (posts diarios, buscador de cuentas, mail) | Producto ya hecho, falta tráfico | ⬜ |
| 3 | Coreano en piloto automático (30-60 min/día) | Victoria rápida, poco esfuerzo | ⬜ |
| 4 | Grok para tu tía + testear Grok | Cuando tengas el plan | ⬜ |
| 5 | Juego nuevo estilo Balatro/Megabonk | Lo más grande; mejor con lo aprendido | ⬜ |
| 6 | Ingreso pasivo automatizado | Elegir idea y validar barato | ⬜ |

## Notas
- X: el bot *encuentra* cuentas y redacta mensajes; los DMs los enviás vos (los DMs automáticos violan las reglas de X y arriesgan la cuenta).

## 1 · Fábrica de ideas: diseño
Flujo: scraper (ya existe) → analizar formato de cada outlier → generar ideas "purple cow" → verificar datos → guion con tu voz.
- Las reglas se guardan en una skill de Claude en este repo: cada corrección queda guardada y no hay que repetirla.
- Prueba "purple cow": ¿el espectador ya vio esto en Brawl/Clash? Si la respuesta es sí, se descarta.
- Datos: cada afirmación lleva su fuente (Supercell oficial, notas de parche, API oficial). Si no hay fuente, el dato no entra.
- Voz: se aprende de los transcripts de tus mejores videos, con una lista de frases prohibidas que suenan a anuncio.
- Pendiente de Pol: acceso a las carpetas, 3-5 transcripts buenos + 2 malos, la conversación buena con Claude si se puede recuperar.

## 3 · Coreano: plan
Pol lee hangul. Objetivo: conversar en Corea y leer artículos y redes. iPhone, gratis, 15 min a la mañana y 15 a la noche.
- Mañana: 10 min de tarjetas de repaso + 5 min de audio (lección TTMIK o repetir en voz alta).
- Noche: Lun/Mié/Vie, conversación por voz con Claude simulando situaciones de viaje. Mar/Jue, lectura graduada. Sáb, repaso con un video en coreano.
- Fases: 1) supervivencia (meses 1-2) → 2) conversación básica (meses 3-4) → 3) lectura real (mes 5 en adelante).
- Sin fecha de viaje: plan equilibrado entre conversación y lectura.
- Se construye en Claude Code (en la PC de Pol), en un repo propio: app web instalable en el iPhone.
  - Botón "Sesión de hoy" que según el día y la hora arma: tarjetas → audio → conversación o lectura.
  - Tarjetas con repaso espaciado y audio con la voz coreana del iPhone.
  - Lectura: textos a su nivel generados de antemano; las palabras nuevas se agregan solas al mazo.
  - Racha diaria y progreso por fase.

## 2 · Bombazo: distribución
Datos: bombazo.app / bombazo.com.ar · 4 juegos diarios a las 00:00 · Cloudflare + Supabase · X: 132 seguidores y 800 seguidos.
- A. ✅ Ya hay botón de compartir.
- B. Automatizar los 4 posts diarios de X con los **mp4** que ya genera el workflow de Pol: guardarlos en R2 + Worker con cron que los sube a la API de X.
- C. Buscador con Grok: **streamers + tuiteros** de fútbol, partiendo de la red que Pol ya tiene. Código + mensaje redactado; el envío lo hace Pol.
- D. Login con Google y mail (con confirmación); no convierte ni con Bombazo+ de regalo. Primero medir: ¿el 78% vuelve o juega una sola vez? Si vuelve: pedir el login cuando la racha llegue a 3 o más días ("no pierdas tu racha"). Si no vuelve: el problema es la retención, no el login.
- E. ❌ Descartado: los shorts deberían salir de streamers jugando (se cubre con C).
- Crecimiento en X: dejar de seguir para que te sigan; responder a cuentas grandes de fútbol.

## 6 · Ingreso pasivo: canal faceless de fútbol en Blender
- Referencia: @ifologyfilms.
- En español. Pol sabe Blender. Estilo **SUPERHOT**: maniquíes blancos low-poly, rojo para resaltar, cancha minimalista.
- La escena base la arma Claude Code por script (o en vivo con Blender MCP), a partir del video de referencia (se extraen frames con ffmpeg). Pol solo baja los maniquíes de Mixamo (Y Bot) y aprueba el resultado.
- Pipeline: guion (Claude) → posiciones + acciones en JSON → bpy mueve los maniquíes con animaciones de Mixamo (correr, patear, festejar) → render en Eevee → voz de Pol clonada en ElevenLabs → Pol revisa y publica.
- Costo: unos 22 USD por mes (ElevenLabs Creator). Ritmo inicial: 1 video largo + 3-5 shorts por semana.
- Riesgos: política de YouTube contra contenido "repetitivo/masivo" y derechos de autor (no usar imágenes de partidos ni escudos).

## 4 · Grok para la tía (⏸ Pol le pregunta: sistema, formato de las facturas, volumen, reglas de la empresa)
Administradora en una concesionaria: carga datos de facturas a los sistemas de la empresa y usa OneDrive.
- Flujo: facturas en una carpeta de OneDrive → Grok con un prompt guardado → tabla con las columnas exactas del sistema → importar o pegar.
- Las facturas electrónicas argentinas (ARCA) traen un QR con los datos (CUIT, fecha, importe).
- Revisar la política de la empresa sobre subir facturas a una IA.

## 5 · Juego nuevo
Referencias: Balatro, Megabonk, Suika, Palworld, Hollow Knight.
Patrón común: un solo verbo simple, sinergias del tipo "una partida más", mucho feedback satisfactorio en cada acción, identidad visual fuerte, premisa que se explica en una línea.
Sin fútbol. Temática: mitología griega + nórdica mezclada, con nombres inventados.
Mundo: Ymbrós. Dioses: Kraeva (trueno), Odryx (padre tuerto), Fenrhos (lobo-titán), Morvane (mar), Skaldra (nornas), Nyxheim (inframundo).
Estilo visual: ánfora griega de figuras negras sobre terracota + talla de runas nórdicas.
Conceptos: Runas del Oráculo, El Barquero, Urna de Dioses, Último Einherjar, Hilo de las Nornas. Pendiente: elección de Pol + plataforma.
