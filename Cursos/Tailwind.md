De acuerdo de los videos de tailwind de *youtube* se ha realizado un proyecto.

Se crea un proyecto desde *Laragon* en el cual se inicia creando un index.html. 

Para poder utilizar tailwind en el proyecto de *Laragon*, dentro de la consola se escribe
`npm install -D tailwindcss@latest postcss@latest autoprefixer@latest`

Se puede incluir
`<link href="https://unpkg.com/tailwindcss@^2/dist/tailwind.min.css" rel="stylesheet">`
para recuperar los estilos desde la página.

Dentro de un archivo css se guarda
```
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
```
De nuevo en consola se escribe:
```
    npx tailwindcss-cli build css/tailwind.css -o build/tailwind.css
```
`npm init -y`
`npm install -D tailwindcss postcss autoprefixer vite`

Dentro de *package.json* se incuye dentro del apartado script 
```
"scripts": {
"dev": "vite"
  },
```

`npx tailwindcss init -p`

INSTALAR PACKETES DE TAILWIND EN CASO DE VSCODE


----------------------—
npm init -y
npm install -D postcss postcss-cli
npm install -D autoprefixer

