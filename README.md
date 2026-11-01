# Librería Saber — Laboratorio aislado de recepción PDF

**Este repositorio no contiene la web comercial ni el cotizador.** La prueba sirve exclusivamente para comprobar la recepción privada de dos documentos sintéticos mediante **Uppy/TUS + Supabase Storage**.

## Estado

- Sitio estático: `index.html`, con archivos PDF de 16 y 94 páginas generados automáticamente en el navegador.
- Bucket privado en el proyecto Free `saber-tus-lab`: `public=false`, sin permisos públicos de escritura o lectura.
- Backend `lab-tus-one-use` de Supabase: emite dos firmas de carga con invitación temporal y verifica SHA-256, bytes y páginas.
- **GitHub Pages requiere activación en la configuración de este repositorio; no se ha confirmado la publicación.**
- **No se ha ejecutado aún una prueba TUS completa.** La página negra anterior fue causada por `text/plain` forzado por Supabase Edge y se evita alojando aquí el HTML.

## Publicar GitHub Pages

GitHub → Settings → Pages → Build and deployment → Deploy from a branch → `main` / `(root)` → Save.

Esto afecta únicamente el repositorio `hernanchan/saber-laboratorio-pdf`, no a `hernanchan/COTIZADOR`, que tiene su propio Pages en producción.

**No hay tokens de acceso dentro del código público.** Para probar se utiliza una URL temporal con token en el fragmento `#k=`, emitida por el laboratorio, no registrada en Git.

## Reglas

No usar PDF de clientes ni datos personales. No registrar pedidos, no activar pagos, no contratar servicios pagos. Una invitación permite **un único inicio** y una sola tanda de dos PDF; si falla, revisar logs antes de intentar nuevamente. Los PDFs pequeños de esta primera prueba no demuestran rendimiento con archivos grandes.

El código de recepción, tests y documentación técnica permanecen en la rama `experimento/uppy-tus-supabase-20261031` del repositorio original `COTIZADOR`, sin promover a su `main`.
