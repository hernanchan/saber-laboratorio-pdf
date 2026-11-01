# Librería Saber — Laboratorio aislado de recepción PDF

Proyecto público de **interfaz únicamente**. No es la web comercial ni el cotizador, no contiene archivos de clientes, claves privadas ni tokens de invitación.

## Prueba actual con dos PDF REALES

- Página: `/reales/` — dos PDF que el usuario selecciona (o arrastra), **máximo 20 MiB cada uno**.
- Antes de usar la invitación de una sola vez: verifica formato `%PDF-`, tamaño, páginas en navegador con pdf-lib y calcula SHA-256 del archivo original.
- Supabase Edge Function `lab-tus-one-use` v3 emite exactamente dos autorizaciones privadas de subida y transmite por **TUS** en paralelo, fragmentos de 6 MiB.
- Después de la subida, Supabase descarga los documentos desde el bucket privado, comprueba SHA-256 y páginas desde el servidor. **Si ambos se verifican, solicita eliminación de los dos objetos**, y avisa si no se confirma.
- Página de prueba sin secretos ni credenciales administrativas; se accede con invitación privada `#k=...` solo en el navegador.
- No hay cotización ni D1 ni Mercado Pago; cero pedidos y cero cobros.
- **Advertencia:** solo usar documentos propios o públicos sin datos confidenciales de clientes. Es un laboratorio, no un servicio apto para producción.

## Estado de pruebas (histórico)

La primera prueba real de red con dos PDF **sintéticos diminutos** verificó 2/2 en 6,19 s. La segunda invitación se consumió subiendo nuevamente PDF diminutos (2.252 bytes en total), por lo que no existe todavía un benchmark válido con archivos grandes. La página de PDFs reales fue preparada posteriormente y **aún necesita su primera prueba de usuario**.

## Configuración

GitHub Pages: rama `main` / `(root)` de **este** repositorio, no `COTIZADOR`. Backend Supabase Free aislado `qkbbqzbannyhuanngjpw`, bucket `saber-tus-lab` privado (20 MiB por archivo, sin INSERT abierto). Edge Function `lab-tus-one-use` con invitación SHA-256 de uso único y origen limitado a GitHub Pages.

Código del backend y documentación en la rama `experimento/uppy-tus-supabase-20261031` del repositorio `COTIZADOR`, **sin modificar la rama comercial `main`**. La página estática en este repo nuevo. El HTML público no contiene el token de invitación.

**No declarar aptitud comercial hasta comprobar archivos reales 2/2, cotizaciones, descarga y Central de Pedidos, seguridad, costos y limpieza de errores.**
