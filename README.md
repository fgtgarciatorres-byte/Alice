# Alice — navegador multi-IA (v0.2 experimental)

Extensión local para Chrome/Edge sin API ni servidor. Permite preparar preguntas, abrir ChatGPT, Grok y Kimi, copiar consultas y reunir **manualmente** respuestas para compararlas. No extrae conversaciones, cookies ni contraseñas, ni automatiza sitios de terceros.

## Instalación
1. Descarga el repositorio como ZIP desde GitHub (Code → Download ZIP) y descomprímelo.
2. Abre `chrome://extensions` (Chrome) o `edge://extensions` (Edge).
3. Activa **Modo desarrollador** y pulsa **Cargar descomprimida**.
4. Selecciona la carpeta `extension` que contiene `manifest.json`.
5. Fija Alice en la barra de extensiones. Abre sesión normalmente en los servicios que desees utilizar.

## Prueba
- Escribe una tarea y pulsa **Preparar consulta**. Se copia una instrucción en el portapapeles (según permiso del navegador).
- Pulsa **Abrir ChatGPT**, **Abrir Grok** o **Abrir Kimi**. Pega el texto en la web y envíalo.
- Copia la respuesta desde la web al cuadro del servicio en Alice y pulsa **Guardar respuesta**.
- Pulsa **Preparar crítica cruzada** y selecciona otro servicio: se copia una consulta que incluye la respuesta anterior y pide revisar sus supuestos.
- Al guardar dos respuestas, Alice muestra ambos textos para contrastarlos.

## Privacidad y limitaciones
- Los datos se guardan localmente usando `chrome.storage.local` dentro del perfil del navegador; no están cifrados por Alice. Evita incluir información confidencial.
- Usa únicamente permisos `storage` y `tabs`. No solicita permisos para leer páginas externas.
- No ejecuta tareas desatendidas ni accede a los chats abiertos. Las sesiones web no son equivalentes a una API.
- Las condiciones de algunos servicios limitan la automatización y la extracción programática de contenidos.
- El repositorio es público: nunca añadas claves, historiales privados o datos personales.
- Las llamadas al portapapeles pueden estar sujetas a permisos; si fallan, selecciona y copia el texto del campo de salida.

## Próximos pasos
Con autorización y soporte de los proveedores, añadir adaptadores para automatización permitida; instalar una app local opcional para colas, tareas y agentes especializados. No depender de la extracción de la interfaz web como interfaz estable.

Licencia: prototipo de evaluación.
