# labo_ihc_mala · Tienda "No accesible"

> ⚠️ **Los errores de accesibilidad de esta página son intencionales.** Es el caso "antes" de un
> ejercicio comparativo de IHC (Interacción Humano-Computadora). No abras issues ni PRs para
> corregirlos: son el objeto de estudio.

Ficha de producto (**Zapatillas Pro**) en HTML estático de un solo archivo, con cinco barreras de
accesibilidad deliberadas. Su par corregido es
[labo_ihc_buena](https://github.com/tejedasebastian/labo_ihc_buena).

- **Demo:** https://tejedasebastian.github.io/labo_ihc_mala/
- **Versión corregida:** https://tejedasebastian.github.io/labo_ihc_buena/

## Los 5 errores intencionales

| # | Elemento | Error | Efecto |
|---|----------|-------|--------|
| 1 | `<img>` | Sin atributo `alt` | El lector de pantalla no tiene texto alternativo que anunciar |
| 2 | `<p>Envío gratis 24h</p>` | Contraste bajo: `#999` sobre `#f0f0f0` ≈ **2.5:1** | Falla WCAG 2.2 AA (mínimo 4.5:1); cuesta leerlo con baja visión o a pleno sol |
| 3 | `<span class="boton-comprar">` | Elemento no semántico usado como botón | No se anuncia como botón y no se activa con Enter/Espacio |
| 4 | El mismo `<span>` | No es enfocable ni operable con teclado | Quien navega sin ratón no puede completar la compra |
| 5 | `<a href="#">Leer más</a>` | Texto de enlace poco descriptivo | Aislado de su contexto no dice a dónde lleva; con lector de pantalla se navega por lista de enlaces |

Además, la jerarquía de encabezados salta de `h1` a `h3`. Se deja así **a propósito** para que el
contraste con la versión buena resulte evidente.

## Arreglos estructurales aplicados

No forman parte de los 5 errores; se corrigieron para que la página fuera publicable:

- **Imagen rota:** el `src` era un enlace Markdown completo
  (`[https://placehold.co/…](https://placehold.co/…)`), que el navegador interpreta como ruta
  relativa y devolvía **404**. Ahora es una URL válida:
  `https://placehold.co/250x150/005088/f3f0df.png?text=Zapatillas` (responde `200 image/png`).
- **`lang="es"`** en `<html>` y contenido envuelto en **`<main>`**.

## Cómo verlo

- **En línea:** https://tejedasebastian.github.io/labo_ihc_mala/
- **En local:** clona el repo y abre `index.html` en el navegador
  (`git clone https://github.com/tejedasebastian/labo_ihc_mala.git`, luego `start index.html` en
  Windows u `open index.html` en macOS).
- **Contraste:** DevTools → inspecciona el párrafo → verificador de contraste (ratio ≈ 2.5:1).
- **Teclado:** recorre la página con `Tab`; el "botón" nunca recibe foco.
- **Lector de pantalla:** NVDA (Windows) o VoiceOver (macOS) para escuchar la imagen sin descripción.

## Estructura

```
index.html   # página única (HTML + CSS embebido)
README.md
```

Publicado con GitHub Pages desde la rama `gh-pages`.
