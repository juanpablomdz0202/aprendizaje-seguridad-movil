# 🏛️ Día 3 – App de Noticias de Arquitectura con Fragments (enfoque seguridad)

Hoy construí una mini app “ArchiNews” para practicar **Fragments** y apliqué controles de **seguridad móvil** desde el diseño.

---

## 🎯 Objetivo
- Mostrar una lista de titulares de arquitectura en `NewsListFragment`.
- Al tocar un ítem, navegar a `NewsDetailFragment` con el título seleccionado.
- Mantener la superficie de ataque mínima (componentes no exportados, Intents explícitos, defaults seguros).

---

## 🧩 Lo técnico
**Estructura:**
- `MainActivity` con `FragmentContainerView`.
- `NewsListFragment` (ListView con titulares).
- `NewsDetailFragment` (muestra detalle).
- Navegación con `replace(...).addToBackStack(null)`.
- <img width="931" height="508" alt="archinews" src="https://github.com/user-attachments/assets/930b1035-0907-4e86-bb1f-65783213e6b3" />

🔐 Seguridad aplicada hoy (checklist)

AboutActivity no exportada (android:exported="false") y sin intent-filter.

MainActivity launcher con android:exported="true".

Intents explícitos (sin implicar otras apps).

Validación de extras con default (?: "Invitado" / "Sin noticia").

Nada sensible en logs (Log.d solo para pruebas).

Backups deshabilitados: android:allowBackup="false".

HTTP plano deshabilitado: android:usesCleartextTraffic="false".

Sin permisos innecesarios.

Sin fragment injection (clases de fragment no provienen de entradas externas).

🤔 Reflexión

Además de agregar Fragments y back stack, preparé la app con un baseline de seguridad: componentes no exportados, Intents explícitos y defaults al recibir datos. Esto reduce riesgos típicos (Intent spoofing, inyección, fuga por logs) y me deja listo para integrar red segura (HTTPS) y persistencia con encriptado más adelante.


**Código clave:**
```kotlin
// MainActivity: primer fragment
supportFragmentManager.beginTransaction()
    .replace(R.id.fragment_container, NewsListFragment())
    .commit()
// NewsListFragment: al tocar un item, navegar al detalle
listView.setOnItemClickListener { _, _, position, _ ->
    val frag = NewsDetailFragment.newInstance(noticias[position])
    parentFragmentManager.beginTransaction()
        .replace(R.id.fragment_container, frag)
        .addToBackStack(null)
        .commit()
}
// NewsDetailFragment: recibe el dato de forma segura (con default)
val titulo = arguments?.getString(ARG_NEWS) ?: "Sin noticia"

