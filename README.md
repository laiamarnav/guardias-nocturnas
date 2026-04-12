# 🌙 Guardias Nocturnas

App web compartida para gestionar guardias, subidas nocturnas, horas y fiestas del equipo.

---

## 🚀 Cómo publicar (15 minutos, gratis)

### Paso 1 — Crear el proyecto Firebase (base de datos gratuita)

1. Ve a **[console.firebase.google.com](https://console.firebase.google.com)**
2. Haz clic en **"Añadir proyecto"**
3. Ponle un nombre (ej: `guardias-nocturnas`) y sigue los pasos
4. En el menú lateral ve a **Firestore Database** → **Crear base de datos**
5. Elige **"Comenzar en modo de prueba"** (permite acceso sin login durante 30 días; luego puedes extenderlo)
6. Selecciona la región `eur3 (europe-west)` y confirma

### Paso 2 — Obtener las credenciales Firebase

1. En Firebase Console, haz clic en el engranaje ⚙️ → **Configuración del proyecto**
2. Baja hasta **"Tus apps"** y haz clic en el icono `</>`  (web)
3. Ponle un nombre (ej: `guardias-web`) y haz clic en **Registrar app**
4. Verás un objeto así — copia estos 3 valores:

```js
const firebaseConfig = {
  apiKey: "AIzaSy...",        // ← este
  projectId: "guardias-xxx",  // ← este
  appId: "1:123:web:abc...",  // ← este
  ...
};
```

### Paso 3 — Publicar en GitHub Pages

1. Crea una cuenta en **[github.com](https://github.com)** si no tienes
2. Haz clic en **"New repository"**
   - Nombre: `guardias-nocturnas`
   - Visibilidad: **Public** (necesario para Pages gratis)
3. Sube el archivo `index.html`:
   - Haz clic en **"uploading an existing file"**
   - Arrastra el `index.html`
   - Haz clic en **"Commit changes"**
4. Ve a **Settings** → **Pages** → Source: **"Deploy from a branch"** → Branch: `main` / `root`
5. Espera 1-2 minutos y tendrás tu URL:
   ```
   https://TU-USUARIO.github.io/guardias-nocturnas/
   ```

### Paso 4 — Primera vez que abres la app

1. Abre la URL
2. Te pedirá las 3 credenciales de Firebase (API Key, Project ID, App ID)
3. Introdúcelas → **Conectar y entrar**
4. Ve a **Ajustes** → añade los nombres del equipo
5. Comparte la URL con tus compañeros — ya está todo sincronizado

---

## 📱 Cómo usarlo

### Fichar
- **Iniciar turno**: pulsa el botón verde al empezar la guardia
- **Finalizar turno**: pulsa al acabar — calcula las horas automáticamente
- **Entrada manual**: si olvidaste fichar, añádela manualmente con fecha, hora inicio/fin y tipo

### Calendario
- Haz clic en cualquier día para ver los detalles
- Cualquiera puede **asignarse una guardia** haciendo clic en el día
- Se ven las guardias asignadas, subidas reales y fiestas cogidas

### Registros
- Historial completo con filtro por compañero
- Puedes eliminar registros incorrectos

### Estadísticas del equipo
- Horas por persona, porcentaje del total, subidas, fiestas ganadas y disponibles

### Ajustes
- Añadir/eliminar compañeros
- Cambiar la tasa de remuneración (por defecto 1.75 h de fiesta / h trabajada)
- Registrar fiestas cogidas

---

## 💡 Cómo ampliar las reglas de Firestore (después de 30 días)

En Firebase Console → Firestore → **Reglas**, sustituye por:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```

Esto mantiene el acceso abierto (sin login). Para un equipo pequeño y privado es suficiente.

---

## 🔧 Tecnologías usadas

- HTML/CSS/JS puro — sin frameworks, sin build step
- Firebase Firestore — base de datos en tiempo real gratuita
- GitHub Pages — hosting gratuito
