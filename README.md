# The Desert Zone

Sitio web para emprendedores: herramientas, comunidad y servicios, en español e inglés.

## Archivos

| Archivo | Para qué sirve |
|---|---|
| `index.html` | El sitio completo (todo el diseño y el código están en este archivo) |
| `favicon.svg` | El ícono TDZ de la pestaña del navegador |
| `Codigo.gs` | El código de la hoja de Google. **No se sube a GitHub como parte del sitio**: se pega en la hoja, en Extensiones > Apps Script |

## Publicar con GitHub Pages

1. Crea un repositorio nuevo en GitHub (por ejemplo `desert-zone`).
2. Sube `index.html`, `favicon.svg` y este `README.md` a la raíz del repositorio.
3. Ve a **Settings > Pages**.
4. En **Source** elige **Deploy from a branch**, rama `main`, carpeta `/ (root)`, y guarda.
5. En uno o dos minutos el sitio estará en `https://TU-USUARIO.github.io/desert-zone/`.

### Usar tu propio dominio

En **Settings > Pages > Custom domain** escribe tu dominio (por ejemplo `thedesertzone.com`) y sigue las instrucciones de GitHub para configurar los registros DNS con tu proveedor del dominio. Activa **Enforce HTTPS** cuando aparezca.

## Conectar los formularios a la hoja de Google

Los tres formularios (Únete, Solicitar un servicio y Trabaja con nosotros) muestran "Solo vista previa" hasta que los conectes:

1. Abre la hoja **The Desert Zone · Servicios y profesionales** y ve a **Extensiones > Apps Script**.
2. Pega el contenido de `Codigo.gs`, guarda y ejecuta la función `instalar` (acepta los permisos).
3. Ve a **Implementar > Nueva implementación > Aplicación web**, con *Ejecutar como: Yo* y *Quién tiene acceso: Cualquier persona*. Copia la URL que termina en `/exec`.
4. En `index.html`, busca esta línea y pega la URL entre las comillas:

   ```js
   const SHEET_ENDPOINT = '';
   ```

5. Sube el cambio a GitHub. Envía una prueba desde cada formulario y revisa que aparezca en la hoja.

## Editar contenido

Todo el texto está en `index.html`, en español y en inglés:

- **Herramientas:** la lista `TOOLS`. Cada línea es una herramienta con su nombre, categoría, país, precio, enlace y descripción en inglés y español.
- **Herramientas de IA:** las líneas `A(...)` dentro de `TOOLS.push(...)`.
- **Textos del sitio:** el objeto `STR`, con una sección `en` y otra `es`.
- **Servicios, círculos y compromiso:** las listas `SERVICES`, `CIRCLES` y `PLEDGE`.
