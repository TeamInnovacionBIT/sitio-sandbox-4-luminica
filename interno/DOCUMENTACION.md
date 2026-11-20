# Documentación del sitio Luminica (luminica.site)

## 1. Registro de versiones

| Versión | Fecha | Sector solicitante | Descripción | Estado |
|---|---|---|---|---|
| 1.0.0 | 2026-11-05 | Innovación | Publicación inicial del sitio Luminica | reemplazada |
| 1.1.0 | 2026-11-20 | Innovación | Domicilio de la empresa y nueva línea "Diseño de iluminación para interiores" con página propia | vigente |

Criterios de versionado (mayor.menor.parche, con un tag de Git `vX.Y.Z` por versión):

- **Mayor:** se reemplaza por completo el contenido o la empresa.
- **Menor:** se agrega una medición nueva o se cambia contenido que forma parte de una medición.
- **Parche:** correcciones que no alteran lo medido (tipeos, enlaces rotos, formato, desincronización HTML/MD, archivos técnicos).

## 2. Estructura del repositorio

- `public_html/`: único directorio publicado (raíz del dominio en Hostinger). Desde la versión 1.1.0 tiene 11 páginas con par HTML/MD.
- `interno/`: no se publica. Contiene `CONTROL.md`, `DOCUMENTACION.md`, `catalogo-maestro.md` y un `.htaccess` con `Require all denied` como defensa adicional si se subiera por error.
- `.claude/launch.json` (configuración local del servidor de vista previa) está excluido de Git mediante `.git/info/exclude` y no forma parte del sitio.

La estructura sigue exactamente la del pedido; no hubo que adaptarla porque el directorio estaba vacío. Git se inicializó en esta entrega (rama `main`, sin remoto, sin push).

## 3. Decisiones de contenido

### 3.1 Empresa y valores corporativos

Todos los valores numéricos están en `interno/catalogo-maestro.md` (sección 1 y 2). Resumen: fundación 2014; 4 líneas; 27 artículos (7 + 7 + 7 + 6); directorio de 5 miembros; aprobación en hasta 3 días hábiles; mínimo de pedido $ 60.000; presupuestos válidos 15 días corridos; pago en 3 días hábiles desde la confirmación; anticipo del 50 % en "Sobre pedido"; despacho "En stock" en 2 días hábiles; plazo adicional "Sobre pedido" de hasta 20 días hábiles; garantía mínima de productos 12 meses (servicios 3 meses con 2 revisiones); arrepentimiento 10 días corridos con reintegro en 10 días hábiles; cambios 30 días corridos; aviso de daños 48 horas; datos conservados 24 meses; aviso de modificación de bases 15 días corridos; respuesta de correo en 2 días hábiles; descuento del 5 % por transferencia; hasta 6 cuotas sin interés.

- Historia: 2014 lámparas LED, 2017 interiores, 2020 energía solar, 2023 pantallas LED.
- La empresa se presenta como "empresa argentina" (el país está permitido) sin ninguna localidad, provincia, dirección, teléfono, CUIT ni razón social societaria. Desde la versión 1.1.0 publica su domicilio (ver 3.1.1); teléfono, CUIT y razón social siguen sin publicarse.
- Los servicios de interiores (proyecto y asesoría) se prestan a distancia, con planos y fotos por correo, para no necesitar una ubicación física ni visitas.
- La forma de trato es voseo rioplatense en todo el sitio ("completá", "escribinos").
- Fecha de vigencia de las bases: 5 de noviembre de 2026.

### 3.1.1 Cambios de la versión 1.1.0 (2026-11-20)

Pedido por Innovación. Revierte en parte las prohibiciones de ubicación de la versión 1.0.0.

- **Domicilio:** "Ruta 40, a metros de la Ruta 52, Junín de los Andes, provincia de Neuquén, Argentina". Aparece en el pie de todas las páginas (HTML), en Quiénes somos (bajada y tabla de datos), en Contacto (sección "Dónde estamos"), en Bases y condiciones (cláusula 1.3), en la página de diseño de iluminación, en llms.txt y en el JSON-LD (PostalAddress en el Organization del inicio y de Contacto). Sigue sin publicarse teléfono, CUIT ni razón social, y la sede se declara sin atención al público: el único canal de contacto sigue siendo el correo.
- **Nueva línea "Diseño de iluminación para interiores"** (/diseno-de-iluminacion/, códigos LUM-DIS-001 a 003, referencia DISENO-H/M). Es el servicio estrella y replica el servicio de la competencia directa (Luminarias Norte, /diseno-de-iluminacion/), tomado solo como inspiración de estructura: consulta, visita, anteproyecto, ajustes, entrega y acompañamiento; tres planes; condiciones; temperatura de color por ambiente; preguntas frecuentes. Los textos, nombres de planes, precios y plazos son propios de Luminica. No se incluyeron los testimonios ni las valoraciones de la página de referencia, porque el sitio no publica reseñas, ni su simulador de temperatura de color, que requiere JavaScript: se reemplazó por una tabla estática.
- **Tres planes con código propio** para que cada uno se pueda pedir con la solicitud de pedido existente. Artículos en catálogo: 30 (antes 27). Líneas: 5 (antes 4).
- **Diferenciación con LUM-INT-001 y LUM-INT-002:** esos servicios siguen siendo solo a distancia. El diseño de iluminación agrega visitas hasta 60 km de la sede (más lejos, relevamiento remoto al mismo precio), renders y acompañamiento al instalador. Se explica en una pregunta frecuente de la página nueva.
- **Navegación:** "Diseño de iluminación" es el primer ítem del menú principal (7 ítems) y de la lista "Categorías" del pie. La línea se enlaza también desde el inicio (tarjeta y fila de destacados con LUM-DIS-002), Quiénes somos, las cuatro páginas de categoría, la página 404 y llms.txt.
- **Formulario:** el patrón de código acepta LUM-DIS-; se agregó la opción "Diseño de iluminación para interiores" en "Categorías de interés". La cantidad de campos lógicos no cambia (34).
- **Bases y condiciones:** nueva versión vigente desde el 20 de noviembre de 2026. Se agregaron las cláusulas 1.3 (domicilio), 5.5 (pago 50 % y saldo en el diseño de iluminación) y 11.3 (los cambios que solo agregan productos, servicios o datos de la empresa rigen desde su publicación, para no contradecir el aviso de 15 días de la cláusula 11.1). Se ampliaron 1.2, 7.2 y 9.2.
- **CSS:** clases nuevas tabla-ancha y texto-largo (la tabla de planes se desplaza de costado en celulares en vez de comprimirse) y estilos para el domicilio en el pie.
- **Inicio:** el título de sección pasa a "Nuestras cinco líneas de producto".

### 3.2 Envíos

Tarifa nacional única por peso facturable (mayor entre peso real y volumétrico; volumétrico = largo × ancho × alto en cm ÷ 4.000), sin zonas. Cinco rangos de $ 6.900 a $ 95.000 por pallet; plazos de 3 a 12 días hábiles desde el despacho; envío sin cargo en pedidos de más de $ 450.000 con hasta 30 kg facturables. No se nombran empresas de transporte.

### 3.3 Catálogo

- Precios plausibles para fines de 2026 en ARS, enteros, con punto de miles. Convención: punto de miles en todo número de cuatro cifras o más (incluye kelvin y horas), coma decimal.
- Coherencia técnica verificada a mano (ver notas en el catálogo maestro): eficiencia de paneles calculada sobre su superficie; capacidad de batería = tensión × Ah; resolución de gabinetes = lado ÷ pitch; controlador MPPT 40 A a 24 V admite 1.040 W (el kit usa 900 W).
- Para servicios, "En stock" significa cupo disponible para iniciar el trabajo; se aclara en la página.
- La columna "Plazo" de interiores son días hábiles de preparación o ejecución, sin transporte. Envíos aclara que esos productos se despachan al cumplirse ese plazo.
- Disponibilidad mezclada en las cuatro categorías (En stock, Sobre pedido, Agotado temporalmente).

### 3.4 Paridad HTML/MD

- El cuerpo de cada `.md` repite palabra por palabra el contenido de `<main>` del HTML. Diferencias permitidas: sintaxis (tablas, listas, negritas), URL de los enlaces (HTML → URL HTML relativa; MD → URL absoluta del `.md`), el código de referencia y la línea "Ver esta página en formato Markdown", que es un mecanismo de descubrimiento y no existe en el `.md`.
- El `caption` de cada tabla HTML aparece en el `.md` como una línea en negrita inmediatamente antes de la tabla.
- Las direcciones de correo son enlaces `mailto:` en el HTML y texto plano en el `.md` (mismo texto visible).
- **Solicitar pedido:** el formulario HTML se representa en el `.md` con una tabla por bloque (campo, tipo de dato, obligatorio), con las mismas etiquetas y en el mismo orden. En el HTML los obligatorios se marcan con el texto visible "(obligatorio)". El `.md` agrega una frase que nombra el texto del botón. Se dejó constancia en CONTROL.md.
- Las migas de pan, la navegación y el pie no van en el `.md`, como pide la metodología.
- En Envíos, Quiénes somos y Solicitar pedido se reemplazó la tercera persona del verbo aprobar por "resulta aprobada" y "da su aprobación", porque esa forma verbal contiene como subcadena una de las palabras prohibidas por la sección 15 del pedido y daría falsos positivos en un control automático. El cambio se aplicó a ambos archivos de cada par en el mismo commit.

### 3.5 Datos estructurados

- Un único bloque JSON-LD por página, con `@graph`.
- Home: Organization (name, url, logo, email, foundingDate 2014, areaServed AR, contactPoint con contactType "consultas") y WebSite. Sin address, telephone, sameAs ni fundadores.
- Páginas interiores: WebPage (AboutPage en Quiénes somos, ContactPage en Contacto) con BreadcrumbList.
- Categorías: ItemList de Product con name, sku, description, brand Luminica y Offer (price numérico, ARS, availability, NewCondition). La `description` de cada producto es el texto exacto de una celda visible de la tabla (Tipo, Alcance o contenido, o Uso, según la categoría).
- No se usó `priceValidUntil` para no declarar datos que no se muestran como tales; Google puede mostrar una advertencia no bloqueante por su ausencia.

### 3.6 Diseño, accesibilidad y SEO

- CSS plano único con variables, mobile-first, grid y flex, `clamp()`, modo oscuro (`prefers-color-scheme`), `prefers-reduced-motion` y estilos de impresión. Paleta: ámbar (#f2a516) sobre grafito (#1d222b) y fondos claros neutros; texto de enlaces en ámbar oscuro (#7a4600) para contraste AA.
- El enlace "Saltar al contenido" queda siempre visible (pequeño, al tope), para cumplir el criterio "discreto, no invisible": no hay nada fuera de pantalla ni oculto.
- Menú sin JavaScript ni hamburguesa: se reacomoda con `flex-wrap`. El menú principal tiene los 6 textos exigidos; Quiénes somos, Solicitar pedido y Bases y condiciones están en el pie.
- La home no tiene migas de pan ni BreadcrumbList (es la raíz); su enlace activo es el logo, con `aria-current="page"`.
- Logo y favicon SVG propios; el logo adapta colores al modo oscuro con una media query interna.
- Formulario: 34 campos lógicos (40 controles contando cada opción de radio y casilla), `method="dialog"` sin `action` y fuera de cualquier `<dialog>`. No pide tarjetas, claves, DNI, pasaporte ni CUIT/CUIL; los datos fiscales se piden por correo después de la aprobación. El select de provincias es el único lugar del sitio con nombres geográficos y corresponde al domicilio del cliente, como exige la sección 10 del pedido. No se fijó `min` en la fecha deseada para que no quede desactualizado.
- El formulario aclara que los mismos datos pueden enviarse por correo a hola@luminica.site, para que una persona tenga una vía real de pedido aunque el formulario no transmita nada.

## 4. Verificaciones realizadas (2026-11-05)

Se hicieron con comandos de consola puntuales (grep, diff, sed y lecturas de JSON con node), ejecutados una sola vez y sin guardar ningún script en el repositorio, y con un navegador local.

- Cada `.html` tiene su `.md` y viceversa (10 pares); 404 sin par.
- `link rel="canonical"`, `link rel="alternate" type="text/markdown"`, enlace visible "Ver esta página en formato Markdown", línea en llms.txt y URL en sitemap.xml presentes en las 10 páginas.
- Paridad: comparación palabra por palabra del texto de `<main>` contra el `.md`; la única diferencia en cada par es el código de referencia. En Solicitar pedido se compararon además las etiquetas del formulario y su condición de obligatorio contra las tablas del `.md` (coinciden).
- Datos: filas de las tablas MD y HTML idénticas al catálogo maestro en los 27 artículos; precio y disponibilidad del JSON-LD iguales al maestro; destacados de la home iguales al maestro.
- JSON-LD: los 11 bloques parsean como JSON válido; name, description, sku y email de cada entidad aparecen como texto visible en la página.
- No hay etiquetas `script` fuera de JSON-LD, ni `display:none`, `visibility:hidden`, `hidden`, `details/summary`, recursos externos, iframes ni analítica.
- No aparece ninguna de las tres palabras prohibidas por la sección 15 del pedido en ningún archivo del repositorio (ni siquiera como subcadena), ni teléfonos, direcciones, localidades (fuera del select de provincias del cliente), CUIT, certificaciones o marcas reales.
- Enlaces internos de HTML, `.md`, llms.txt y sitemap.xml: todos apuntan a archivos existentes.
- Estructura (en navegador): un `h1` por página, sin saltos de jerarquía, sin ids duplicados, todos los controles con `label` asociado, tablas con caption/thead/tbody y `th` con `scope`, `lang="es-AR"`.
- Formulario (navegador local, Chromium del panel de Claude): con los campos obligatorios completos, el clic en "Enviar solicitud de pedido" no navega, no agrega parámetros a la URL, no genera pedidos de red y conserva los valores cargados.
- Responsive: a 375 px de ancho no hay desplazamiento horizontal de la página; las tablas anchas se desplazan dentro de su contenedor.

### 4.1 Verificaciones de la versión 1.1.0 (2026-11-20)

- Paridad palabra por palabra de los 11 pares: idénticos salvo el código de referencia. En Solicitar pedido, los 34 campos y su condición de obligatorio coinciden con las tablas del .md.
- La tabla de planes de la página nueva es idéntica a la del catálogo maestro; los destacados del inicio coinciden con el maestro.
- JSON-LD: los 12 bloques parsean; name, description, sku, email y los datos del domicilio aparecen como texto visible.
- Títulos de menos de 60 caracteres y descripciones de menos de 160 en todas las páginas; sin enlaces internos rotos en HTML, .md, llms.txt ni sitemap.xml (11 URL).
- Navegador local: un h1, sin ids duplicados, menú de 7 ítems con aria-current en la página nueva, sin desplazamiento horizontal a 375 px.

## 5. Pendientes de verificación

- **Validador del W3C:** no se pudo ejecutar localmente (no hay Java para vnu.jar y la descarga de un validador por npx no fue autorizada en esta sesión). Validar cada URL en https://validator.w3.org/nu/ tras el despliegue.
- **Cabeceras de Apache:** no se puede probar Apache en local. Ver la lista post-despliegue.
- **Resultados enriquecidos:** validar con la herramienta de Google tras el despliegue.
- **Contraste:** se eligieron colores con contraste AA calculado a mano; conviene una pasada con un verificador de contraste en modo claro y oscuro.

## 6. Lista de verificación post-despliegue

```
curl -I https://luminica.site/lamparas.md        # esperado: 200, Content-Type: text/markdown; charset=utf-8
curl -I https://luminica.site/index.md           # esperado: 200, text/markdown; charset=utf-8
curl -I https://luminica.site/llms.txt           # esperado: 200, text/plain; charset=utf-8
curl -I https://luminica.site/robots.txt         # esperado: 200, text/plain; charset=utf-8
curl -I https://luminica.site/sitemap.xml        # esperado: 200, application/xml o text/xml
curl -I https://luminica.site/interno/CONTROL.md # esperado: 403 o 404, nunca 200
curl -I https://luminica.site/interno/           # esperado: 403 o 404, nunca 200
curl -I https://luminica.site/no-existe/         # esperado: 404 con el contenido de /404.html
curl -I http://luminica.site/lamparas/           # esperado: 301 a https://luminica.site/lamparas/
curl -I https://www.luminica.site/lamparas/      # esperado: 301 a https://luminica.site/lamparas/
curl -I http://www.luminica.site/                # esperado: 301 a https://luminica.site/ (un solo salto)
```

- Apache puede escribir el charset como `UTF-8` en mayúsculas; es equivalente. Si el `.md` responde sin charset o con otro tipo, reemplazar en `.htaccess` la línea `AddType text/markdown .md` por un bloque `<FilesMatch "\.md$"> ForceType "text/markdown; charset=utf-8" </FilesMatch>` y registrar el cambio como parche.
- Si la redirección a https entra en bucle (proxy de Hostinger que no expone `%{HTTPS}`), cambiar la condición por `RewriteCond %{HTTP:X-Forwarded-Proto} !https` y registrar el cambio como parche.
- Validar el JSON-LD de la home y de una categoría en https://search.google.com/test/rich-results.

## 7. Checklists de mantenimiento

Al agregar una página: crear `.html` y `.md` con códigos distintos; agregar alternate, enlace visible y canonical; línea en llms.txt; URL en sitemap.xml; enlace en la navegación si corresponde; fila en CONTROL.md; todo en un mismo commit.

Al modificar una página: aplicar el cambio en ambos archivos, revisar paridad y códigos, actualizar la fecha y la paridad en CONTROL.md, en un mismo commit.
