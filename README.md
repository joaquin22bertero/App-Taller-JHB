# Taller JHB — App independiente (PWA)

## Qué es esto
Versión independiente y privada del sistema, sin depender de Claude. Guarda todo en **tu propio Google Drive**, funciona en PC/Android/iOS como una app instalada, y no tiene ningún costo de hosting ni de API.

## Antes de subir: poné tu Client ID
1. Abrí `app.js` con un editor de texto.
2. Buscá `TU_CLIENT_ID_ACA` (aparece una sola vez) y reemplazalo por tu Client ID real de Google Cloud (el que termina en `.apps.googleusercontent.com`).
3. Guardá el archivo.

Si todavía no tenés ese Client ID, seguí estos pasos:

### Crear el Client ID (una sola vez, gratis)
1. Andá a **console.cloud.google.com** → creá un proyecto nuevo (ej. "Taller JHB").
2. **APIs y servicios → Biblioteca** → buscá **"Google Drive API"** → **Habilitar**.
3. **APIs y servicios → Pantalla de consentimiento de OAuth** → **Externo** → completá nombre y tu email → guardar.
4. En **Público/Audiencia**, agregate como **usuario de prueba** con tu Gmail.
5. **APIs y servicios → Credenciales → Crear credenciales → ID de cliente de OAuth**.
6. Tipo: **Aplicación web**.
7. En **Orígenes autorizados de JavaScript**, agregá la URL de GitHub Pages (paso siguiente) — algo como `https://tu-usuario.github.io`.
8. Copiá el Client ID.

## Subir a GitHub Pages (gratis)
1. Creá un repositorio en GitHub (puede ser público — el código no tiene datos tuyos, ver nota de seguridad abajo).
2. Subí todos los archivos de esta carpeta: `index.html`, `manifest.json`, `sw.js`, `app.js`, y la carpeta `icons/`.
3. **Settings → Pages** → Source: rama principal → guardar. Te da una URL tipo `https://tu-usuario.github.io/nombre-repo/`.
4. Confirmá que esa URL es la misma que pusiste en el paso 1.7 de Google Cloud.

## Primer uso
1. Entrá a tu URL de GitHub Pages.
2. Apretá "Conectar con Google", elegí tu cuenta.
3. Empezá a cargar clientes, vehículos, repuestos y fichas — todo se guarda solo en tu Drive.
4. Para instalarla como app: en el celu, "Agregar a pantalla de inicio" desde el menú del navegador. En la compu, el navegador va a mostrar un ícono de instalación en la barra de direcciones.

## Qué falta probar en vivo (no lo pude probar yo desde mi entorno)
- **Login real con tu cuenta de Google** (la lógica ya la probamos con un login simulado — ahora falta la real).
- **Lectura de texto de fotos (OCR)**: usa una librería gratuita (Tesseract.js) que se carga por internet. Puede tardar unos segundos la primera vez. Probalo con una foto de scanner real y contame la precisión.
- **Importar Excel**: la librería también se carga por internet (xlsx). Probá con uno de tus archivos de Contagram.
- Ambas requieren conexión a internet la primera vez que se usan (después el navegador las cachea).

## Notas de seguridad
- El código de la app es público si el repo es público — no contiene ningún dato tuyo, es solo el programa.
- Tus datos reales (clientes, fichas, fotos) viven únicamente en tu Google Drive, con tu cuenta.
- Solo vos podés autenticarte mientras el proyecto de Google esté en modo "Prueba" con tu cuenta como única autorizada.

## Qué quedó pendiente / mejoras futuras
- Sincronización más robusta si algún día cargás datos desde dos dispositivos exactamente al mismo tiempo (caso raro para un solo usuario).
- Comando de voz para completar campos automáticamente (charlado como próximo paso, todavía no construido).
- Ajustar colores/logo exacto si me pasás el archivo original del logo con más detalle.
