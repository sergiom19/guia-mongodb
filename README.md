## ❓ ¿Qué es Mongoose?
> Mongoose es un NPM basado en modelos para la base de datos MongoDB.
> En esta introducción te enseñaré como usarlo, al final te parecerá fácil :D.

## ❓ ¿Qué es MongoDB?
> Es una base de datos NoSQL creada en 2009 en Estados Unidos.
> Es considerada una de las bases de datos más modernas, ya que guarda sus datos en documentos JSON, los cuales son muy flexibles.

### 📦 Empezando
> Vamos a crear un Atlas. Para crear un atlas, haz click [aquí](https://mongodb.com/cloud/atlas).
Dale al botón que pone "Start free". Te pedirá que pongas varios datos, sería hacer un login.
(puedes buscarlo en google si no sabes)

> Una vez nos hayamos registrado, nos aparecerá esto:
<br>
<br>
<img src="https://pays.host/uploads/21097a79-b022-44e0-8c0d-511d4da18ec9/Xg0k3H3W.png" width="500">
<br>
Dale al botón verde en el que pone CONNECT y elige la segunda opción: `Connect your application.`
Crea unas credenciales, después, en Driver pones `Node.js` y en versión pon la última.

En la sección 2, pega la URL que te da la ventana, reemplaza `<dbname>` por algo (ejemplo: miPrimerDatabase)
y `<password>` por la contraseña que previamente creaste.

### 👨‍💻 Creando nuestro proyecto
>Ahora crea una app node.js y simplemente escribe estas dos líneas:
y también instala mongoose
```js
const mongoose = require('mongoose')

mongoose.connect('mongodb+srv://usuario:<password>@cluster0.gresm.gcp.mongodb.net/<dbname>?retryWrites=true&w=majority')
```
> Ahora reemplaza las variables `<dbname>` y `<password>` por tus credenciales.

### 📊 Creando mi primer Schema
> Crea una carpeta en tu proyecto donde vas a guardar tus esquemas, yo la llamaré "models". Dentro de ella crearé un archivo llamado "miPrimerSchema.js".

> Ahora en el archivo "miPrimerSchema.js" haremos un esquema de esta manera:
```js
const mongoose = require('mongoose')

const Esquema = new mongoose.Schema({
    Nombre: String, 
    Apellido: String,
    Edad: Number
})

const Schema = module.exports = mongoose.model('usuarios', Esquema)
```
>Bien, ahora te explico lo que has hecho:
>- En el constructor Schema, has puesto que `Nombre` y `Apellido` sean un `texto` y `Edad` sea un `número`,
por lo que al insertar datos en nuestra colección, se reiniciará de un modo u otro.
>- Al poner ``const modelo``, exportarlo, y después asignarle la función model, estamos modelando nuestro
schema para adaptarlo a **JSON** y después, al poner el **String** 'usuarios', estamos dando nombre a nuestra colección,
que se llamará **usuarios**.

### ➡ Insertando documentos en el Schema
>Ahora después de hacer esto, volvemos a nuestro archivo principal y lo enlazamos:
```js
const modelo = require('./models/miPrimerSchema.js') 
//En los paréntesis iria nuestra ruta de nuestro modelo.
```
>Aquí requererimos el modelo, y después para insertar sería:
```js
const nuestros_datos = new modelo({
    Nombre: 'Sergio', // Aquí ponemos nuestro dato que queramos coger, en mi caso, mi nombre.
    Apellido: 'Márquez', // Lo mismo, estamos requiriendo datos.
    Edad: 18 
})
datos.save() // Aquí guardamos los datos que hemos cogido a nuestra colección.
```

### 📄 Obteniendo documentos del Schema
>Ahora queremos ver si hemos hecho todos estos pasos correctamente.

>Vamos a probar:
```js
const data = await modelo.findOne({
    Nombre: 'Sergio'
}) // Aquí estamos diciendo que encuentre el dato de la variable 'Nombre' llamada 'Sergio'

if (!data) return console.log('No existen los datos.') 
// Con este if le estamos retornando que si no esta data (osea nuestra búsqueda de la variable de nuestro modelo) no se ha encontrado haga un log en la consola.

else if (data){
    console.log(data.Nombre + data.Apellido)
}
// Sin embargo, si data se encuentra en nuestro dato en el modelo, nos va a hacer un log de nuestro Nombre, Apellido



```

### 🔄 Actualizando documentos del Schema
> ¿Pero qué pasa si quiero actualizar en vez de crear más documentos?
Yo te explico.
```js
await modelo.findOneAndUpdate({
    Nombre: 'Sergio',
    Edad: 25
})
```
>Vamos a ponernos en situación de que Sergio (Yo) haya cumplido años y por eso haya que actualizar nuestra base de datos.

## 👤 Guia realizada por Sergio.
 Si esta guía te ha ayudado hazmelo saber. Y me alegro que te haya ayudado.
  
> Discord tag: twenifive#1111

> [Discord Server](https://discord.gg/tCYAPYbK3x)

> Si me pudieras apoyar dando una estrella al documento te lo agradecería. ⭐ 

