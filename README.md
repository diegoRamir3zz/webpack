<h2>My notes <img src="https://img.icons8.com/external-tal-revivo-bold-tal-revivo/24/4a90e2/external-webpack-a-module-bundler-its-main-purpose-is-to-bundle-javascript-files-for-usage-in-a-browser-logo-bold-tal-revivo.png"/></h2>

<h3>Empezando el proyecto.</h3>
<p>
Para empezar nuestro projecto con webpack debemos instalar la
dependencia, esto lo hacemos corriendo el siguiente comando en la
terminal:

  <i><b>npm install webpack webpack-cli -D</b></i>

esto nos instalara webpack en modo desarollo.
Para ejecutar ahora webpack corremos el siguiente comando en la termianl.

<i><b>npx webpack --mode production</b></i>

Tras haber compilado con webpack, este reconocerá nuestro archivo index.js
y crea una carpeta llamada <i>'dist'</i> con un archivo <i>'main.js'</i> donde se hallara nuestro codigo y en caso de ser redundante nuestro codigo, lo webpack lo corregirá.
</p>