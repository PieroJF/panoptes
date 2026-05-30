# GitHub Maquillaje — "Mi Rutina Gym" (codename `panoptes`)

- **Fecha:** 2026-05-31
- **Repo:** `PieroJF/panoptes`
- **Objetivo:** Convertir un repo pelado (solo `index.html`) en una presentación de GitHub cuidada: README bilingüe con banner y capturas reales, metadata (descripción + topics), social preview y licencia.

## Contexto

`Mi Rutina Gym` es un tracker de rutina de gimnasio en un único `index.html` (~945 líneas, HTML+CSS+JS vanilla). Dark theme, verde neón `#4ade80`, glassmorphism, mobile-first. Semana Lun–Dom con categorías codificadas por color (push, pull, legs, cardio, upper, hiit, rest), ejercicios con notas de técnica, warm-ups, check-off semanal persistido en `localStorage` (`gym_checks`, `weekId`), notas plegables, botón de reinicio. UI en español. Desplegado en Cloudflare Workers.

El repo en GitHub no tiene README, descripción, topics, licencia ni social preview.

## Decisiones (acordadas)

| Eje | Decisión |
|-----|----------|
| Alcance | Pack completo (README + banner + capturas + descripción + topics + social preview + LICENSE) |
| Idioma | Bilingüe ES/EN (ES primero, toggle con anclas) |
| Estilo | Dark fitness — negro `#0a0a0b` + verde neón `#4ade80` + dots de categoría, coherente con la app |
| Capturas | Reales, navegador headless a viewport móvil (390×844), múltiples estados |
| Banner | SVG vectorial versionable, rasterizado a PNG vía navegador |

## Identidad

- **Título:** Mi Rutina Gym · codename del repo: `panoptes`
- **Tagline ES:** "Tu semana de entreno, sin fricción. Una pantalla, cero cuentas, todo local."
- **Tagline EN:** "Your training week, zero friction. One screen, no accounts, all local."
- **Paleta:** bg `#0a0a0b`, accent `#4ade80`; dots push `#f97316`, pull `#3b82f6`, legs `#a855f7`, cardio `#14b8a6`, upper `#eab308`, hiit `#ef4444`, rest `#6b7280`.

## Entregables (archivos)

```
README.md
LICENSE                      # MIT, Piero JF, 2026
.gitignore                   # ignora .wrangler/
docs/superpowers/specs/2026-05-31-github-maquillaje-design.md
assets/
  banner.svg                 # banner vectorial dark-fitness
  banner.png                 # rasterizado, ancho README
  social-preview.png         # 1280x640 para GitHub social preview
  screenshots/
    *.png                    # capturas reales móvil de varios estados
```

## README — estructura

1. Banner (link a `assets/banner.png`)
2. Badges: tech (HTML/CSS/JS vanilla), single-file, offline-first, deploy Cloudflare, license MIT
3. Toggle idioma 🇪🇸 / 🇬🇧 (anclas internas)
4. Tagline
5. Capturas (galería)
6. Características (semana, categorías por color, check-off semanal, notas de técnica, persistencia local, mobile-first/PWA-ish)
7. Cómo funciona (modelo de datos en `localStorage`, reseteo por semana)
8. Stack
9. Uso / Deploy (abrir local; deploy en Cloudflare Workers)
10. Estructura del proyecto
11. Licencia

Bloque EN espeja el ES bajo su propia ancla.

## Metadata del repo (`gh repo edit`)

- **Descripción:** "📋 Tracker minimalista de rutina de gym — single-file HTML, offline-first, deploy en Cloudflare / Minimalist gym routine tracker."
- **Topics:** `gym`, `fitness`, `workout-tracker`, `vanilla-js`, `single-file`, `pwa`, `cloudflare-workers`, `localstorage`, `offline-first`, `spanish`

## Plan de ejecución (fases)

1. **Fundación** — este spec, `LICENSE`, `.gitignore`, commit.
2. **Capturas reales** — servir `index.html` en localhost, navegador headless 390×844, capturar 3–4 estados → `assets/screenshots/`.
3. **Banner + social preview** — `assets/banner.svg`, rasterizar a `banner.png` y `social-preview.png` (1280×640).
4. **README bilingüe** — ensamblar con banner, badges y capturas.
5. **Metadata + push** — `gh repo edit` (descripción + topics), commit final, push.

## Restricción conocida

La **social preview image** no se puede subir por API/CLI de GitHub. Se genera el PNG y se versiona en el repo; el usuario lo sube manualmente en *Settings → Social preview* (un clic). Todo lo demás se automatiza.

## No-objetivos (YAGNI)

- No reescribir ni refactorizar la app.
- No añadir build system, framework ni dependencias.
- No publicar el enlace a la demo en vivo en el README salvo que el usuario lo pida (la URL desplegada tiene tráfico bot y reglas de seguridad activas).
