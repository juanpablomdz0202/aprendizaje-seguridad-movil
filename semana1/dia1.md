🔹 Título

Ejemplo: "Día 1 – Ciclo de vida en Android con Compose"

🔹 Qué hice hoy

Instalé/revisé Android Studio.

Creé una app con Jetpack Compose (SimpleToDoList).

Agregué logs (Log.d) para seguir el ciclo de vida.

Creé una segunda Activity (AboutActivity) y la abrí con un Intent desde Compose.

🔹 Qué aprendí / descubrí

onCreate() siempre se ejecuta al crear la Activity.

Cuando paso de MainActivity a AboutActivity, la primera entra en onPause → onStop y la segunda entra en onCreate → onStart → onResume.

Cuando vuelvo atrás, AboutActivity dispara onPause → onStop → onDestroy y MainActivity vuelve a la vida (onRestart → onStart → onResume).

Con Jetpack Compose no uso setContentView(...), sino setContent { ... }.

🔹 Problemas encontrados

Puse setContent sin paréntesis → error de compilación.

No sabía cómo lanzar otra Activity desde Compose → lo resolví usando LocalContext.current + Intent.

🔹 Próximos pasos

Seguir con manejo de permisos en Android (Día 2).

Ver cómo persisten datos las tareas (porque ahora si roto la pantalla, se pierden).

<img width="948" height="507" alt="logcat_dia1" src="https://github.com/user-attachments/assets/0c8bbc39-4222-4dc7-99a4-9d3c6d1e1d8e" />
<img width="942" height="505" alt="logcat_dia1 2" src="https://github.com/user-attachments/assets/8f86fb4d-13f2-400f-8d50-1a79cd90fbea" />
<img width="943" height="501" alt="logcat_dia1 3" src="https://github.com/user-attachments/assets/c3381656-1a62-4a21-ab1a-5a8e23bec9e5" />
