# Vortex — Landing Page

Landing page oficial de **Vortex**, la plataforma impulsada por Agentes de IA para la
administración de edificios/PHs. Página **autocontenida** (un solo `index.html` con HTML +
CSS + JS vanilla), **sin CDN ni dependencias externas**. Desplegable en GitHub Pages tal cual.

---

## 🎯 Qué contiene

Un `index.html` con las secciones del brief (optimizado a ~9.6 pantallas):

1. **Navbar sticky** — logo SVG tipo vórtice, anclas, CTA "Solicitar demo", línea de energía animada.
2. **Hero de dos actos** (estética HUD "command center" tipo Iron Man/JARVIS, con boot-up al cargar):
   - **Acto 1 (Un PH):** torre residencial como holograma — anillos HUD giratorios con ticks,
     haz de escaneo recorriendo los pisos, halo/constelación que *respira*, burbujas de reporte
     con ciclo de vida (coral "nuevo" → Agente IA → verde "✓ Resuelto"), heartbeat y parallax/tilt.
   - **Acto 2 (Varios PHs):** **GLOBO TERRÁQUEO holográfico en Canvas 2D** (100% vanilla, sin
     librerías): rota continuamente, hace zoom cinematográfico a ciudades administradas y
     enciende las **luces de los PHs** pulsando por estado (verde/ámbar/coral). Target-lock
     coral sobre la ciudad enfocada + readout HUD con telemetría (ciudad, PHs, % al día,
     coordenadas). Se puede **arrastrar para rotar** y **clic en una ciudad** para enfocarla.
     Se pausa fuera de viewport; con `prefers-reduced-motion` muestra un frame estático de
     Ciudad de Panamá. Ciudades y cifras **ilustrativas** (marcadas "DEMO ILUSTRATIVA").
   - **Toggle manual** "Un PH / Varios PHs" + auto-alternancia (se detiene al interactuar).
   - **Signos vitales** con contadores animados y telemetría viva (cifras ilustrativas).
   - Sistema HUD global: corner brackets en paneles, kickers numerados (01-09) en fuente mono,
     scanline en el escenario, labels de datos en monospace.
3. **Dos soluciones** — tarjetas de peso equivalente (Para tu PH / Para Empresas) con mockups.
4. **Personalizado, no genérico** (`#personalizado`) — tus áreas, tus reglas, tu marca, tus flujos.
5. **Agentes de IA · Cómo funciona** (`#como`, fusionadas) — chips de capacidades de los agentes +
   4 pasos orientados al beneficio administrativo + **chat de WhatsApp animado**.
6. **Para empresas (Mother Dashboard)** (`#empresas`) — mockup con KPIs, mapa con pines, alertas.
7. **Desempeño medible · KPIs** (`#desempeno`) — KPIs del edificio (tiles con tendencia y sparkline)
   + **tablero de ranking y evaluación de administradores** con puntaje comparable ("evalúa por datos,
   no por opiniones"). Diferenciador central del producto.
8. **Confianza y legal** (`#confianza`, banda compacta) — aislamiento, proveedor de tecnología, Ley PH Panamá.
9. **CTA final** — incluye "estés donde estés" y el roadmap comprimido en chips (Hoy · En camino · Visión).
10. **Formulario** (`#contacto`) — nombre, email, PH, ¿individual o empresa?, mensaje (envía por `mailto`).
11. **Footer** con disclaimer legal.

### ⌘ Modo Dashboard (consola)
Botón flotante **"⌘ MODO DASHBOARD"** (abajo a la derecha): transforma la landing en una consola
tipo command center con tabs (INICIO · SOLUCIONES · OPERACIÓN · EMPRESAS · DESEMPEÑO · CONTACTO).
Las **secciones reales se mueven** a los paneles (cero duplicación de contenido) y se restauran al
salir (botón "Salir", el mismo toggle o tecla `Esc`). La página misma funciona como demo de la
experiencia Vortex.

> Nota: la página se recortó de 12.3 a ~9.6 pantallas eliminando la franja de stats (duplicaba los
> vitales del hero), fusionando Agentes IA dentro de Cómo funciona, absorbiendo "Sin fronteras" y
> "Vanguardia" en el CTA final, y compactando la sección legal.

Accesibilidad: contraste alto, roles/aria en zonas clave, foco visible, y **respeta
`prefers-reduced-motion`** (desactiva animaciones y muestra estados finales).

---

## ✏️ Datos configurados

Ya están puestos en `index.html`:

| Dato | Valor actual | Dónde |
|---|---|---|
| WhatsApp | `https://wa.me/50761640089` (+507 6164 0089) | hero, CTA final, contacto, footer |
| Email | `hola@vortexadmin.com` | `mailto:` del formulario, contacto y footer |
| Dashboard en vivo | `https://jdv1418.github.io/vortex-mother-dashboard/` | navbar, hero, sección empresas |
| Dominio | `vortexadmin.com` (archivo `CNAME`) | GitHub Pages lo toma automáticamente |

Pendiente de reemplazar cuando existan datos reales:

| Placeholder | Dónde | Con qué |
|---|---|---|
| `[CIFRA_ILUSTRATIVA]` | notas bajo las métricas | métricas reales |

### Formulario
Hoy el formulario abre el correo del visitante vía `mailto:[EMAIL_CONTACTO]`. Para producción,
reemplaza esa línea (marcada con `// TODO producción`) por un POST a tu backend o a un servicio
tipo Formspree.

---

## 🏢 Asset opcional del edificio (refuerza "personalizado")

Por defecto se muestra una **silueta SVG** de respaldo. Para usar el render real del edificio del
cliente (fondo transparente):

1. Coloca la imagen en `./assets/edificio.webp` (o `.png`).
2. En `index.html`, dentro de `<div class="hero-building">`, **descomenta** la línea `<img ...>`
   y elimina/oculta el `<svg class="building">`.

Ideal: usar el render real de **SU** edificio en cada cliente.

---

## 🚀 Cómo desplegar

### GitHub Pages
1. Crea un repo (ej. `vortex-landing`) y sube el contenido de esta carpeta (incluye el archivo `CNAME`).
2. En **Settings → Pages**, elige la rama `main` y carpeta `/root`.
3. La landing queda en `https://<usuario>.github.io/vortex-landing/`.

No requiere build ni servidor: es HTML estático.

### Dominio propio — vortexadmin.com
El archivo **`CNAME`** ya contiene `vortexadmin.com`, así que GitHub Pages lo detecta solo. Falta el DNS:

1. En **Settings → Pages → Custom domain** confirma `vortexadmin.com`.
2. En el panel DNS de tu proveedor (Namecheap/GoDaddy/Cloudflare):
   - 4 registros **A** → `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
   - 1 registro **CNAME** para `www` → `<tu-usuario>.github.io`
3. Marca **Enforce HTTPS** (certificado SSL gratis; tarda unos minutos).

Propaga de minutos a ~24 h. Alternativas equivalentes: Cloudflare Pages o Netlify.

### Correo @vortexadmin.com
Para recibir en `hola@vortexadmin.com`: Google Workspace (~$6/mes), Zoho Mail (plan gratis)
o Cloudflare Email Routing (gratis, reenvía a tu Gmail). Requiere agregar registros MX en el DNS.

### Prueba local
Cualquier servidor estático sirve. Por ejemplo con Node:
```bash
npx serve .
```
o con Python:
```bash
python3 -m http.server 8080
```
Luego abre `http://localhost:8080`.

---

## 🎨 Paleta ("building intelligence")

- Fondo navy `#0A1E2E → #0D2438`, spotlight `#123049`
- Superficies `#12293B`, bordes `#1E3A4F`
- Acento coral `#F26B4E` · datos `#5B9BD5` · ok `#3FB98A` · aviso `#F0A64E` · teal `#14b8a6`
- Texto `#F2F6F9` / apagado `#8FA6B5`

Todas las variables están al inicio del `<style>` en `:root`, fáciles de ajustar.

---

## ⚖️ Nota de marca (no negociable)

**Vortex = proveedor de tecnología, nunca administrador de facto.** El copy evita sobreprometer,
describe la IA como asistencia/automatización, y nunca mezcla datos de PHs/empresas distintas
(Ley de Propiedad Horizontal de Panamá).
