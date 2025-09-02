# 🏛️ Día 4 – App de Noticias de Arquitectura con Fragments (enfoque seguridad)

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
<img width="931" height="508" alt="archinews" src="https://github.com/user-attachments/assets/075239fe-8156-4714-bab2-a4f91be83a1e" />
