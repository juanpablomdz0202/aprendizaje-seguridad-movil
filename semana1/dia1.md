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
semana1/logcat_dia1.png
