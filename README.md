# Luminica (luminica.site)

Sitio estático de Luminica: iluminación, energía solar y pantallas LED. Cada página se publica en HTML y en Markdown, con el mismo texto en las dos versiones.

La documentación completa (decisiones, verificaciones y checklists) está en [`interno/DOCUMENTACION.md`](interno/DOCUMENTACION.md).

## Estructura

| Ruta | Qué contiene | Se publica |
| --- | --- | --- |
| `public_html/` | El sitio: 10 páginas en HTML (`slug/index.html`) y Markdown (`slug.md`), `404.html`, `css/estilos.css`, `img/`, `llms.txt`, `robots.txt`, `sitemap.xml`, `.htaccess` y `BingSiteAuth.xml` | Sí, en Hostinger |
| `interno/` | `catalogo-maestro.md` (fuente única de precios, plazos y valores), `CONTROL.md` (paridad HTML/MD por página), `DOCUMENTACION.md` y un `.htaccess` que bloquea el acceso | No |

Quedan fuera del repositorio (`.gitignore`): la carpeta `.claude/` y los documentos Word.

## Cómo funciona

- **Escrito a mano:** no hay generador, framework ni proceso de compilación. Cada cambio se hace directamente en el HTML y en su `.md`.
- **Sin JavaScript:** el único `<script>` de cada página es el bloque de datos estructurados JSON-LD. No hay cookies, analítica ni recursos externos.
- **Paridad HTML/MD:** las dos versiones de cada página tienen el mismo texto. Lo único que cambia es el código de referencia del final (`Referencia: LAMPARAS-H` en el HTML, `Referencia: LAMPARAS-M` en el `.md`).
- **Descubrimiento del Markdown:** cada página lo declara por tres vías: `<link rel="alternate" type="text/markdown">`, el enlace visible «Ver esta página en formato Markdown» y una línea en `llms.txt`.
- **Datos:** todo precio, plazo o valor sale de `interno/catalogo-maestro.md`. Si un dato cambia, se cambia primero ahí y después en todas las páginas, tablas y JSON-LD donde aparece.

## Páginas

| Página | HTML | Markdown | Código |
| --- | --- | --- | --- |
| Inicio | `/` | `/index.md` | INICIO |
| Quiénes somos | `/quienes-somos/` | `/quienes-somos.md` | QUIENES |
| Lámparas y luminarias LED | `/lamparas/` | `/lamparas.md` | LAMPARAS |
| Iluminación para interiores | `/iluminacion-interiores/` | `/iluminacion-interiores.md` | INTERIORES |
| Energía solar | `/energia-solar/` | `/energia-solar.md` | SOLAR |
| Pantallas LED | `/pantallas-led/` | `/pantallas-led.md` | LED |
| Envíos a todo el país | `/envios/` | `/envios.md` | ENVIOS |
| Solicitar pedido | `/solicitar-pedido/` | `/solicitar-pedido.md` | PEDIDO |
| Bases y condiciones | `/bases-y-condiciones/` | `/bases-y-condiciones.md` | BYC |
| Contacto | `/contacto/` | `/contacto.md` | CONTACTO |

## Ver el sitio en local

Los enlaces internos parten de la raíz (`/css/estilos.css`, `/lamparas/`), así que abrir `index.html` con doble clic no funciona: hay que levantar un servidor local. Desde la carpeta raíz del repositorio (la que contiene `public_html/`):

```
py -m http.server 8765 --directory public_html
```

Si se ejecuta desde otra carpeta, responde 404 a todo: en ese caso, pasar la ruta completa de `public_html` entre comillas.

Después, abrir http://localhost:8765/. En esta PC se usa `py` porque `python` abre el atajo de la Microsoft Store. El servidor local no aplica el `.htaccess`: las redirecciones y los tipos de contenido solo se pueden probar en Hostinger.

## Publicación en Hostinger

Se sube el **contenido** de `public_html/` (no la carpeta) al directorio `public_html` del plan, por el Administrador de archivos o por FTP. `index.html` tiene que quedar directamente en la raíz del dominio. La carpeta `interno/` no se sube.

No conviene usar el despliegue por Git del hPanel: copia el repositorio entero, con lo que el sitio quedaría en `public_html/public_html/` e `interno/` dentro de la web.

El `.htaccess` declara `text/markdown; charset=utf-8` para los `.md`, `text/plain; charset=utf-8` para `llms.txt` y `robots.txt`, redirige http y www a `https://luminica.site/`, desactiva el listado de directorios y define la página 404.

### Verificación después de publicar

```
curl -I https://luminica.site/lamparas.md          # 200, text/markdown; charset=utf-8
curl -I https://luminica.site/llms.txt             # 200, text/plain; charset=utf-8
curl -I https://luminica.site/interno/CONTROL.md   # 403 o 404, nunca 200
curl -I http://luminica.site/lamparas/             # 301 a https://luminica.site/lamparas/
curl -I https://www.luminica.site/lamparas/        # 301 a https://luminica.site/lamparas/
```

La lista completa y qué cambiar en `.htaccess` si algo no responde como se espera están en la sección 6 de `interno/DOCUMENTACION.md`.

## Cambios

**Al modificar una página:** aplicar el mismo cambio en el HTML y en su `.md`, revisar que los dos sigan con el mismo texto y actualizar la fila de la página en `interno/CONTROL.md`. Todo en un mismo commit.

**Al agregar una página:** crear `slug/index.html` y `slug.md` con un código de referencia nuevo (`-H` y `-M`), con `canonical`, `alternate` y el enlace visible al Markdown; sumarla a `llms.txt`, a `sitemap.xml`, a la navegación si corresponde y a `interno/CONTROL.md`.

**Restricciones de contenido:** el sitio no publica domicilio, localidad, teléfono, CUIT, certificaciones, marcas de terceros, nombres de personas ni reseñas. El único contacto es hola@luminica.site.

## Versiones

Versionado mayor.menor.parche, con una etiqueta `vX.Y.Z` por versión. El registro está en `interno/DOCUMENTACION.md`.

| Versión | Fecha | Descripción |
| --- | --- | --- |
| 1.0.0 | 2026-11-05 | Publicación inicial del sitio Luminica |
