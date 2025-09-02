# 📱 Día 3 – Navegación entre Activities con Intents en Android

Hoy avancé en mi camino de **Seguridad Móvil / Desarrollo Android** repasando cómo funcionan los **Intents** para abrir nuevas pantallas (Activities) y pasar datos entre ellas.

---

## 🚀 Lo que hice
- Creé una nueva `AboutActivity` en mi proyecto **SimpleToDoList**.
- Implementé un **Intent explícito** desde `MainActivity` hacia `AboutActivity`.
- Usé `putExtra()` para enviar datos (`usuario = "Juan aprendiendo Intents 🚀"`).
- En `AboutActivity`, recuperé el dato con `getStringExtra()` y lo mostré en pantalla usando **Jetpack Compose**.
- Registré la nueva Activity en el `AndroidManifest.xml`.

---

## 📸 Evidencia
![Pantalla About](../imagenes/dia3_about.png)

> En la captura se ve la pantalla **About**, mostrando el mensaje recibido desde MainActivity.

---

## 🧠 Reflexión
Hoy entendí mejor cómo Android gestiona la navegación entre pantallas y el envío de información.  
Esto es clave porque en aplicaciones reales casi siempre necesitamos movernos entre varias pantallas (login → dashboard → perfil, etc.) y compartir datos entre ellas.

Lo interesante es que los Intents no solo sirven para nuestras propias Activities, sino también para interactuar con **otras apps** (por ejemplo, abrir la cámara o compartir texto).

---

## ✅ Próximos pasos
- Practicar el **regreso de datos** desde `AboutActivity` hacia `MainActivity` (con `setResult` y `ActivityResult`).
- Avanzar al **Día 4: Introducción a Fragments y navegación básica**.

---

📌 Repo: [aprendizaje-seguridad-movil](https://github.com/TU-USUARIO/aprendizaje-seguridad-movil)  
📌 Publicación: *Voy a compartir esto en LinkedIn para documentar mi progreso y motivar a otros 🚀*
