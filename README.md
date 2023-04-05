# Hoja de presentación

El presente documento es para conoce lo básico de crear un markdown

# Windmill Dashboard

A multi theme, completely accessible, with components and pages examples, ready for production dashboard.

🧪 [See it live](https://windmill-dashboard.vercel.app/)

- 🦮 Thoroughly accessible
- 🌗 Light and dark themes
- 💅 Styled with Tailwind CSS
- 🧩 Various components
- (soon React and Vue versions)

## 🚀 Usage

Clone or download this repo and everything you need is inside the `public` folder.

## 🦮 Accessibility

This dashboard was developed with a11y in mind since the beginning.

1. Every text passes the WCAG Level AA (at least)
2. It is completely keyboard navigable
3. I actually used [NVDA](https://www.nvaccess.org/) to read my screen during development

Everybody can benefit with good accessibility practices, like the modal, for example ([test it live](https://windmill-dashboard.vercel.app/modals.html)). It uses focus trap techniques to not loose focus when navigating via keyboard and thinking of mobile users with large screen devices, it is placed in the bottom of the screen.

## 🌗 Multi theme

It uses Tailwind CSS for styling, and some may say it is totally biased, but it uses the most simple theming plugin there is for it, [Tailwind Multi Theme plugin](https://github.com/estevanmaito/tailwindcss-multi-theme#tailwind-css-multi-theme) (made by me). The result is that, as with regular Tailwind, you have control over every style in your pages.

You can see that by navigating through the examples, changing theme and going visiting pages like login or create account, to see different images served for different themes.

Theme auto detection based on user's OS preferences and local settings storage are enabled by default.

## 🔮 Future

Para crear lista de selección se agrega `-[]`

TODO

- [ ] 

- [ ] Make charts accessible through hidden data

- [ ] Refactor and split `shadow-outline-<color>` plugin

- [ ] Paginate tables with Alpine

- [ ] Focus first element when dropdowns are opened

- [ ] Add roles to the table

## OSS used

(TODO: add links)

- Tailwind CSS
- Tailwind Multi Theme
- Tailwind Custom Forms
- PostCSS
- Alpine.js
- Chart.js (charts)
- UI Faces (avatars)
- Heroicons (icons)

# Esto es un H1

## Esto es un H2

### Esto es un H3

#### Esto es un H4

*Esto es cursiva*

Negrilla
**Esto es negrilla**

- Esto es viñeta 1.
  - Viñeta 1.1 con sangria.
  - Viñeta N.

Insertar imagenes
![texto cualquiera por si no carga la imagen](url completa de la imagen)

Insertar enlaces
[texto a mostrar](url completa)

Hacer anclaje
Usar los títulos con la almohadilla # y para anclar el título a una tabla de contenido, ponemos lo siguiente:

[texto a mostrar](#mi-titulo-a-anclar)

Insertar una linea de codigo  "`s`"
Encerrar la linea de código entre la tilde al revés ` Código en ASCII: alt96
`mysql `mysql -uroot`

Ejemplo:

`tu linea de codigo`
Insertar un bloque de codigo
Encerrar el bloque de código entre tres tildes al revés ``` Código en ASCII: alt96

Ejemplo:

        ```
    
        //bloque de codigo...
    
        ```

Resaltar el codigo
Encerramos el bloque de código con las tres tildes al revés ``` y le ponemos al lado el lenguaje que se está usando, ejemplo:

        ```java
    
        //bloque de codigo...
    
        ```

Insertar tablas

| TITULO1             | TITULO2             |
| ------------------- | ------------------- |
| CONTENIDO COLUMNA 1 | CONTENIDO COLUMNA 2 |

[**VER MÁS SÍMBOLOS DE LATEX.**](http://metodos.fam.cie.uva.es/~latex/apuntes/apuntes3.pdf)
