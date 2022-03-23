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

<h2>Depurar</h2>

<p>
En caso de necesitar depurar para saber que fue lo que fallo en nuestro codigo, podemos hacerlo con el siguiente codigo de webpack.

  <i><b>npx webpack --mode development</b></i>

Esto nos mostrara un codigo más completo, de lo que esta sucediendo.
Para volver al modo de produccion utilizamos el siguiente comando.

  <i><b>npx webpack --mode production</b></i>
</p>

<h2>Confirgurar webpack</h2>
<p>
Inicialemente creamos un archivo en la raiz de nuestro proyecto y lo nombramos de la siguiente manera.

<i><b>webpack.config.js</b></i>

Luego dentro del archivo que se creo. escribimos el siguiente codigo para condigurarlo.
</p>

	const path = require('path');

	module.exports = {
	    entry: './src/index.js',
	    output: {
	        path: path.resolve(__dirname, 'dist'),
	        filename: 'main.js'
	  },
	    resolve: {
	        extensions: ['.js']
	  }
	}
<i><b>Explicación del código.</b></i>
<p>
1. path es un recurso de node. <br>
2. En entry se especifica la ruta de la raiz de nuestro proyecto.<br>
3. en path.resove(__dirname, 'dist') le podemos camvbiar el nombre a la camperta donde se almacenará nuestro codigo despues de ser compilado. Lo recomendable es dejarlo en dist.<br>
4. filename indica el nombre en el que se va a guardar el codigo despues de ser compilado por webpack. En este caso le pusimos main.js<br>
5. En extensions le tenemos que especificar las extenciones que estamos utilizando en nuestro proyecto.<br>
</p>
<b>Guardar las configuraciones.</b>
<p>
Por ultimo corremos en la consola el siguiente comando.

<i><b>npx webpack --mode production --config webpack.config.js </b></i>

Estas son algunas configuraciones basicas que le hacemos a nuestro webpack
</p>

<h2>Configurar Babel</h2>
<p>
Inicialmente instalamos las dependecias que necesitamos, para eso corremos el siguiente comando en nuestra termianl.

<i><b>npm install babel-loader @babel/core @babel/preset-env @babel/plugin-transform-runtime -D</b></i>

1. <i>babel-loader</i> nos permite usar babel con webpack <br>
2. <i>@babel/core</i> es babel en general<br>
3. <i>@babel/preset-env </i> permite usar las ultimas características de JavaScript<br>
4. <i>@babel/plugin-transform-runtime</i> te permite trabajar con todo el tema de asincronismo como async y await<br>

Ahora crearemos un archivo de configuracion de babel en la raiz de todo nuestro poryecto, el archivo debe llamarse .babelrc y escribimos el siguiente codigo en el.
</p>

{
  "presets": [
    "@babel/preset-env"
  ],
  "plugins": [
    "@babel/plugin-transform-runtime"
  ]
}
<p>
Tambien debemos realizar algunas configuraciones en nuestro archivo <i><b>webpack.config.js</b></i>

Todo nuestro codigo debe quedar de esta manera. (Incluyendo el codigo previo que habiamos escrito)
</p>

const path = require( 'path' );

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'main.js',
  },
  resolve: {
    extensions: ['.js']
  },
  module: {
    rules: [
      {
        test: /\.m?js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader'
        }
      }
    ]
  }
}
<p>
Asi le estamos indicando a webpack que queremos hacer uso de babel.
<a hreft="https://platzi.com/blog/que-es-babel/?utm_source=google&utm_medium=cpc&utm_campaign=12915366154&utm_adgroup=&utm_content=&gclid=Cj0KCQjw5-WRBhCKARIsAAId9FmhXFA6fobPhQXLjC8yfP0PrPQ-xV1dcxUPh81l7wJNwyOzp1MigBEaAuqZEALw_wcB&gclsrc=aw.ds ">Saber más</a>
</p>
