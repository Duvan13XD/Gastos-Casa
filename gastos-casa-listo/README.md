# Cuentas de casa · Compartidas

App estática preparada para GitHub Pages + Firebase Authentication + Cloud Firestore, para **3 usuarios** con permisos iguales de lectura, creación, edición y borrado.

## A. Publicar en GitHub Pages
1. Abre tu repositorio `gastos-casa` y usa **Add file → Upload files**.
2. Sube **index.html**, **styles.css**, **app.js**, **firebase-config.js** (después de configurarlo) y opcionalmente este README. No subas respaldos con gastos personales.
3. **Settings → Pages → Build and deployment → Deploy from a branch → main / (root) → Save**.
4. Abre `https://TU_USUARIO.github.io/gastos-casa/`.

## B. Preparar Firebase antes de usar la página
1. En https://console.firebase.google.com/ crea un proyecto.
2. **Project settings → Your apps → Web (</>)** y registra la app. Copia la configuración en `firebase-config.js`, sustituyendo los ejemplos. Sube el archivo actualizado al repositorio.
3. **Authentication → Sign-in method → Email/Password → Enable**.
4. **Authentication → Users → Add user**: crea una cuenta con correo y contraseña para cada una de las tres personas. Guarda cada UID que aparezca.
5. **Firestore Database → Create database**; elige una ubicación adecuada y configura las reglas de seguridad inmediatamente, **nunca dejes habilitada la lectura pública**.
6. **Firestore Database → Rules**: copia el contenido de `firestore.rules`, sustituye `UID_MAURICIO`, `UID_VICTOR`, `UID_DUVAN` por los UID reales y pulsa **Publish**. El archivo `.rules` dentro de GitHub es solo una copia de referencia, **no activa las reglas automáticamente**.
7. **Authentication → Settings → Authorized domains**: verifica que `TU_USUARIO.github.io` esté permitido y agrégalo si hace falta.
8. Inicia sesión con una de las cuentas en tu página. Los gastos quedan en Firestore y los otros dos dispositivos los verán al instante.

## C. Datos existentes
Tu HTML original guardaba datos en `localStorage` de un solo navegador, por eso **no se importan automáticamente**. En el equipo donde están los datos, abre el HTML original y pulsa **Descargar respaldo**. Dentro de esta app nueva, ya conectado a Firebase, pulsa **Restaurar respaldo**, elige el JSON y confirma. Esto reemplaza los datos existentes en la nube, así que hazlo una sola vez, de preferencia antes de que otros registren gastos. **Nunca subas ese JSON a un repositorio público.**

## D. Uso diario
Los tres entran al mismo enlace con sus cuentas. Cualquiera puede ingresar, editar, borrar, crear períodos, cerrarlos y generar PDF o respaldo.

## Nota importante
Si falla una operación, no asumas que los datos se guardaron. Verifica que figure «Sincronizado» y actualiza la página. Evita ediciones simultáneas del mismo registro. No compartas contraseñas entre usuarios. La base de datos requiere conexión para persistir cambios.
