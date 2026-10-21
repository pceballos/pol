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
- B. Automatizar los 4 posts diarios de X (hoy manuales) con un Cloudflare Worker con cron + API de X + imagen de cada juego.
- C. Buscador con Grok: el objetivo pasa a ser **streamers** (Twitch, Kick, YouTube) que puedan jugarlo en vivo. Código + mensaje redactado; el envío lo hace Pol.
- D. El login no convierte, ni con Bombazo+ de regalo → pedir solo el mail (un campo) o activar notificaciones push. Medir en qué paso abandonan.
- E. ❌ Descartado: los shorts deberían salir de streamers jugando (se cubre con C).
- Crecimiento en X: dejar de seguir para que te sigan; responder a cuentas grandes de fútbol.

## 6 · Ingreso pasivo: canal faceless de fútbol en Blender
- Referencia: @ifologyfilms.
- Formato recomendado: tácticas en una pizarra 3D (fichas sobre la cancha) → la parte más automatizable.
- Pipeline: investigación y guion (Claude) → posiciones en JSON → Blender por script (bpy) → voz IA → edición → Pol revisa y publica.
- Riesgos: política de YouTube contra contenido "repetitivo/masivo" y derechos de autor (no usar imágenes de partidos ni escudos).
