# The Desert Zone · Herramientas de la comunidad

Directorio de herramientas para emprendedores, ordenado por la comunidad. La gente vota por sus favoritas, las más votadas forman el Top 10 y cualquiera puede proponer herramientas nuevas, que se publican cuando tú las apruebas. En español e inglés.

## Archivos

| Archivo | Para qué sirve |
|---|---|
| `index.html` | El sitio completo |
| `favicon.svg` | El ícono TDZ de la pestaña del navegador |
| `Codigo.gs` | El código de la hoja de Google. **No se sube a GitHub**: se pega en la hoja, en Extensiones > Apps Script |

## Publicar con GitHub Pages

1. Crea un repositorio nuevo en GitHub (por ejemplo `desert-zone`).
2. Sube `index.html`, `favicon.svg` y este `README.md` a la raíz del repositorio.
3. Ve a **Settings > Pages**, elige **Deploy from a branch**, rama `main`, carpeta `/ (root)`, y guarda.
4. En uno o dos minutos el sitio estará en `https://TU-USUARIO.github.io/desert-zone/`.

Para usar tu propio dominio: **Settings > Pages > Custom domain**, sigue las instrucciones de DNS y activa **Enforce HTTPS**.

## Conectar los votos y las propuestas a la hoja de Google

Mientras no lo conectes, el sitio funciona en vista previa: los votos se guardan solo en el navegador de cada persona y las propuestas no se envían.

1. Abre la hoja **The Desert Zone · Servicios y profesionales** y ve a **Extensiones > Apps Script**.
2. Borra el código anterior, pega el contenido de `Codigo.gs`, guarda y ejecuta la función `instalar` (acepta los permisos).
3. Implementa como aplicación web:
   - Si ya tenías una implementación: **Implementar > Administrar implementaciones > Editar > Versión: Nueva versión > Implementar**. La URL no cambia.
   - Si es la primera vez: **Implementar > Nueva implementación > Aplicación web**, con *Ejecutar como: Yo* y *Quién tiene acceso: Cualquier persona*.
4. Copia la URL que termina en `/exec` y pégala en `index.html`, en esta línea:

   ```js
   const SHEET_ENDPOINT = '';
   ```

5. Sube el cambio a GitHub. Vota por una herramienta y propone otra para comprobar que aparezcan en las pestañas **Votos** y **Propuestas**.

## Cómo se maneja

- **Propuestas:** llegan como *Pendiente* y te llega un correo. Cámbialas a *Aprobada* para que aparezcan en el sitio (en menos de un minuto). Si la persona dejó su correo, recibe un aviso.
- **Votos:** una fila por voto, con un código anónimo del dispositivo. Un dispositivo vota una vez por herramienta y puede retirar su voto. Para anular votos sospechosos, borra esas filas.
- **Panel:** la pestaña Panel muestra el total de votos, las propuestas pendientes y el Top 10.

## Editar contenido

Todo está en `index.html`:

- **Herramientas base:** la lista `TOOLS` (y las de IA en `TOOLS.push(...)`), con nombre, categoría, país, precio, enlace y descripción en inglés y español. El país de cada una está en `ORIGIN`.
- **Textos:** el objeto `STR`, con una sección `en` y otra `es`.
- **Newsletter:** el popup aparece cada vez que alguien entra al sitio, tiene su propio selector ES / EN, y envía al formulario real de noticias.youngdesert.com: `/suscribirse` en español y `/en/subscribe` en inglés. Las direcciones están en `NEWSLETTER`.
- **Gratis para empezar:** el filtro usa el precio de cada herramienta (`PRICE`); cuenta como gratis todo precio que empieza con `free` y los programas públicos (`gov`).
