# Alice 0.2.1 — extensión multi-IA para Firefox (también Chrome/Edge)

Prototipo local sin API ni servidor: prepara preguntas, enfoca las pestañas de ChatGPT, Grok y Kimi y guarda **manualmente** respuestas para realizar críticas cruzadas. No lee conversaciones de terceros ni automatiza el envío de mensajes.

## Firefox: instalación para pruebas
1. Descarga el ZIP del repositorio en GitHub (Code → Download ZIP) y descomprímelo.
2. Abre `about:debugging#/runtime/this-firefox` en Firefox.
3. Pulsa **Cargar complemento temporal**.
4. Selecciona `extension/manifest.json` en la carpeta descomprimida.
5. Haz clic en el icono de extensiones o fija Alice en la barra de herramientas y abre el panel.

**Importante:** una extensión temporal se desinstala al reiniciar Firefox. Para instalar Alice de forma permanente habrá que empaquetarla y firmarla mediante Mozilla Add-ons (AMO), incluso si se distribuye sin listado público. El ID Gecko incluido facilita esa fase, pero **no** equivale a una firma.

## Prueba funcional
1. Abre sesión normalmente en ChatGPT, Grok o Kimi desde Firefox.
2. Abre Alice, escribe una tarea y pulsa **Preparar consulta**.
3. Pulsa **Abrir / enfocar** en un servicio. Pega allí el texto copiado y envíalo.
4. Copia la respuesta del servicio y pégala en el campo correspondiente de Alice. Pulsa **Guardar respuesta**.
5. Pulsa **Preparar crítica** para copiar otra consulta con esa respuesta y contrastarla en otro servicio.
6. Guarda la segunda respuesta y pulsa **Mostrar respuestas reunidas**.

## Compatibilidad y permisos
- Manifest V3; usa `action`, `tabs` y `storage`, compatibles con Firefox moderno.
- Se añade `clipboardWrite` para permitir copiar el texto del panel con mayor fiabilidad en Firefox.
- `browser_specific_settings.gecko.id` identifica la extensión para Firefox.
- El JavaScript del panel usa `chrome.*` con métodos que devuelven promesas en Firefox moderno; si alguna versión antigua falla, utilizar una capa `browser.*` con polyfill.
- No solicita acceso a dominios externos, ni permisos de lectura de páginas, ni al portapapeles de lectura.
- El estado se almacena en el perfil local del navegador sin cifrado adicional.
- Repositorio público: no subas chats privados, cookies ni credenciales.

## Chrome / Edge
También se puede instalar desde `chrome://extensions` / `edge://extensions`, activando Modo desarrollador y **Cargar descomprimida** (carpeta `extension`). El manifiesto incluye metadatos propios de Firefox, ignorados por otros navegadores Chromium compatibles.

## Limitaciones
Esta versión **no está validada en una instancia real de Firefox** y no funciona desatendida. Coordina transferencias manuales. Una conexión automática a interfaces ajenas requerirá estudiar permisos, términos de servicio y mantenimiento de cada integración.

## Código
- `extension/manifest.json`: permisos y compatibilidad.
- `extension/popup.html`: interfaz de Alice.
- `extension/popup.js`: tareas, pestañas y comparación local.
