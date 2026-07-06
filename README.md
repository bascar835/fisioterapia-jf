# fisioterapia-jf

Sitio web oficial de Fisioterapia y Osteopatía JF (Benidorm) desarrollado con HTML, CSS y JavaScript para GitHub Pages, con panel de edición de contenidos en `/cms/`.

## Primeros pasos (crear el repositorio)

1. Crea un repositorio nuevo en GitHub llamado, por ejemplo, `fisioterapia-jf` (puede ser público o privado).
2. Sube todos estos archivos a la rama `main` de ese repositorio.
3. Edita `cms/config.yml` y sustituye `TU-USUARIO/fisioterapia-jf` por `tu-usuario-de-github/nombre-real-del-repo`.
4. Edita `build/generate-seo-pages.py` y sustituye la constante `BASE` por la URL real donde vivirá la web (normalmente `https://tu-usuario.github.io/nombre-del-repo/`).
5. En GitHub, ve a *Settings → Pages* y en "Build and deployment" elige **GitHub Actions** como origen (no "Deploy from a branch").
6. Con el primer `push` a `main`, la GitHub Action ya desplegará la web automáticamente.

## Panel de edición (`/cms/`)

Una vez desplegado, entra en `https://tu-usuario.github.io/nombre-del-repo/cms/` e inicia sesión con tu cuenta de GitHub. Desde ahí puedes editar, sin tocar código:

- **Página principal**: la foto o vídeo de portada.
- **Servicios**: categorías y tratamientos de la clínica, con foto, descripción y precio opcional.
- **Galería**: las fotos que se muestran en la web.
- **Blog · Artículos**: crear, editar o borrar artículos de salud y bienestar.

## SEO automático

Cada vez que se publica un cambio en `main` (por ejemplo, al editar algo desde el panel `/cms/`), la GitHub Action `.github/workflows/deploy.yml` ejecuta `build/generate-seo-pages.py` y despliega el resultado en GitHub Pages. Este script:

- Genera una página HTML propia por cada artículo del blog (`post-<slug>.html`) con su título, imagen/vídeo, descripción y datos estructurados para que se vea bien al compartir en WhatsApp/redes y para buscadores.
- Escribe directamente en `index.html` los servicios, la galería y los últimos artículos, y en `blog.html` el listado completo.
- Regenera `sitemap.xml` y `robots.txt` con las URLs reales del sitio.

No hace falta ejecutarlo a mano ni antes ni después de publicar: el despliegue en GitHub Pages siempre lo hace por ti. Si quieres previsualizarlo en tu ordenador antes de subir cambios, puedes correr `python3 build/generate-seo-pages.py` localmente.

## Datos a revisar antes de publicar

- **Email de contacto**: se ha usado `info@fisioterapiajf.es` como marcador de posición. Cámbialo por un email real en `index.html`, `blog.html`, `post.html` y `content/home.json` si tienes uno.
- **Precios de servicios**: en `content/services.json` los precios se han dejado en blanco a propósito; añádelos desde el panel `/cms/` cuando quieras mostrarlos.
