# Web de Edu Pereira — Fantasía oscura

Sitio estático (HTML/CSS/JS, sin build). Portada cine-monocromo con foto a pantalla
completa + página de mapa interactivo del Reino de Arkaria.

## Estructura
```
.
├── index.html          ← portada (hero, universo, sagas, mapa, bitácora, contacto)
├── mapa.html           ← mapa interactivo (Leaflet sobre tu mapa de Arkaria)
├── 404.html
├── assets/
│   ├── hero.jpg        ← tu retrato (fondo del hero)
│   └── map-arkaria.jpg ← tu mapa provisional
└── README.md
```

---

## Subirlo a GitHub

Crea primero un repositorio **vacío** en GitHub (p. ej. `edupereira-web`), sin README.
Luego, desde la carpeta del proyecto (terminal o Claude Code):

```bash
git init
git add .
git commit -m "Primera versión: portada + mapa de Arkaria"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/edupereira-web.git
git push -u origin main
```

(Cambia `TU_USUARIO`. Si usas la CLI de GitHub: `gh repo create edupereira-web --public --source=. --push`.)

## Conectarlo a Cloudflare Pages (gratis, sin build)

1. Panel de Cloudflare → **Workers & Pages** → **Create** → pestaña **Pages** → **Connect to Git**.
2. Elige el repo `edupereira-web`.
3. Configuración de build:
   - **Framework preset:** None
   - **Build command:** *(déjalo vacío)*
   - **Build output directory:** `/`
4. **Save and Deploy**. En un minuto tendrás tu URL `edupereira-web.pages.dev`.

A partir de ahí, **cada `git push` se publica solo**.

---

## Cómo actualizar cosas (sin saber código)

- **Añadir una novedad a la Bitácora:** en `index.html`, busca `<!-- BITÁCORA -->`,
  copia un bloque `<article class="entry">…</article>` y ponlo el primero. Cambia la
  fecha y el texto. Guarda y haz push.
- **Poner la portada de la novela:** cuando la tengas, mándamela y la coloco en el
  bloque de Sagas; o déjala en `assets/` y la enlazo.
- **Mover marcadores del mapa:** en `mapa.html`, cada lugar tiene `fx` y `fy`
  (fracción 0–1 desde la esquina superior izquierda). Para encontrar coordenadas
  exactas, descomenta el bloque `map.on('click'…)` del final, abre la consola del
  navegador (F12) y pulsa en el mapa: te imprime el `fx/fy` de ese punto.
- **Rellenar lugares del mapa:** los marcadores marcados «Por documentar» llevan
  texto provisional. Edita el campo `t:` de cada uno en `mapa.html`.

## Nota de canon (pendiente, no afecta a la web)
El mapa pone «Reino de Arkaria» y «Océano de las Tormentas»; el canon de BARDO venía
con «Lohengrem» y «Mar Crespo». Hay que unificar nombres en el hilo de la novela.

## Más adelante
Cuando quieras bitácora autoeditable en Markdown, galería de varios mundos y demás,
migramos esto a **Astro** (mismo hosting gratis). Esta versión estática ya deja la
tubería GitHub → Cloudflare montada y probada.
