# Las bases para desarrollar una aplicación full stack MERN
+ [URL del curso en Udemy](https://www.udemy.com/course/las-bases-para-desarrollar-una-aplicacion-full-stack-mern/)
+ [URL del repositorio en GitHub](https://github.com/petrix12/mern_2021.git)

## Antes de iniciar:
1. Crear proyecto en la página de [GitHub](https://github.com) con el nombre: **mern_2021**.
    + **Description**: Proyecto para seguir el curso de 'Las bases para desarrollar una aplicación full stack MERN', creado por Luis Trujillo Sanchez en Udemy.
    + **Public**.
2. En la ubicación raíz del proyecto en la terminal de la máquina local:
    + $ git init
    + $ git add .
    + $ git commit -m "Antes de iniciar"
    + $ git branch -M main
    + $ git remote add origin https://github.com/petrix12/mern_2021.git
    + $ git push -u origin main

## Sección 1: Introducción

### Que vamos a desarrollar
+ **Contenido**: Breve introducción sobre el curso.
1. Commit Video 001:
    + $ git add .
    + $ git commit -m "Que vamos a desarrollar"
    + $ git push -u origin main

## Sección 2: Backend

### La arquitectura de nuestro Backend
+ **Contenido**: Explicación de la arquitectura MVC.
1. Commit Video 002:
    + $ git add .
    + $ git commit -m "La arquitectura de nuestro Backend"
    + $ git push -u origin main

### Instalar herramientas del curso
1. Programas requeriods:
    + [MongoDB](https://www.mongodb.com)
    + [Node.js](https://nodejs.org/en)
    + [Postman](https://www.postman.com)
    + [Robo 3T](https://robomongo.org)
    + [Visual Studio Code](https://code.visualstudio.com)
    + [Google Chrome](https://support.google.com/chrome/answer/95346?hl=es&co=GENIE.Platform%3DDesktop)
2. Crear directorio **C:\data\db**.
3. En **Windows**, ir a **Propiedades del sistema** y en las pestaña de **Opciones avanzadas** presionar el botón **Variables de entorno...**.
4. En el grupo de Variables de usuario agregar la ruta **C:\Program Files\MongoDB\Server\5.0\bin** en **Path**.
5. Para iniciar los servicios de MongoDB, ejecutar en una terminal de Windows:
    + $ mongod
    + **Nota**: MongoDB correra en el puerto 27017.
6. Conexión para administrar **MongoDB** desde **Robo 3T**:
    + Nombre: localhost
    + Puerto: 27017
7. Extensiones recomendadas en **Visual Studio Code**:
    + ES7 React/Redux/GraphQL/React-Native snippets
        + dsznajder
        + Simple extensions for React, Redux and Graphql in JS/TS with ES7 syntax
    + generate-react-component
        + joshjg
        + Generate component structure from easily customizable templates
    + Reactjs code snippets
        + charalampos karypidis
        + Code snippets for Reactjs development in ES6 syntax
    + Simple React Snippets
        + Burke Holland
        + Dead simple React snippets you will actually use
8. Extensión recomendanda para instalar en **Google Chrome**:
    + React Developer Tools
        + **Nota**: al terminar instalar reiniciar el ordenador.
9. Commit Video 003:
    + $ git add .
    + $ git commit -m "Instalar herramientas del curso"
    + $ git push -u origin main

### Backend
1. Crear carpeta **backend** y ubicarse en ella.
2. Ejecutar:
    + $ npm init
    + **Nota**: para todas las peticiones presionar **ENTER**.
3. Crear dependencias del proyecto:
    + $ npm i express nodemon mongoose cors morgan body-parser
4. Crear la estructura MVC:
    + Crear carpetas:
        + backend\src\controllers
        + backend\src\models
        + backend\src\routes
    + Crear archivos:
        + backend\src\index.js
        + backend\src\database.js
5. Configurar servidor en **backend\src\index.js**:
    ```js
    const express=require('express')
    const app=express()
    const morgan=require('morgan')
    const cors=require('cors')
    const bodyparser=require('body-parser')

    app.set('Port', 4000)

    // app.use(morgan('dev'))

    // app.use(bodyparser.urlencoded({extended:true}))

    // app.use(bodyparser.json())

    // start server

    app.listen(app.get('Port'), ()=>{
        console.log('escuchando por el puerto ', app.get('Port'))
    })
    ```
6. Levantar servidor:
    + $ node src/index.js
7. Crear archivo .gitignore: 
    ```gitignore
    /backend/node_modules
    ```
8. Commit Video 004:
    + $ git add .
    + $ git commit -m "Backend"
    + $ git push -u origin main

### Configurando Nodemon
1. Modificar el archivo **backend\package.json**:
    ```js
    ≡
    "scripts": {
        "test": "echo \"Error: no test specified\" && exit 1",
        "dev": "nodemon src/index.js"
    },
    ≡
    ```
2. Ejecutar el script **dev** definido en **backend\package.json**:
    + $ npm run dev
3. Commit Video 005:
    + $ git add .
    + $ git commit -m "Configurando Nodemon"
    + $ git push -u origin main

### Creando la conexión a la base de datos mongodb
1. Levantar los servicios de MongoDB:
    + $ mongod
2. Configura la conexión con la base de datos MongoDB en **backend\src\database.js**:
    ```js
    const mongoose=require('mongoose')

    URI=('mongodb://localhost/ensayo')

    mongoose.connect(URI, {
        useNewUrlParser: true,
        useUnifiedTopology: true,
        /* useCreateIndex: true,
        useFindAndModify: false */
    })
        .then(db => console.log('base de datos conectada'))
        .catch(error => console.log(error))

    module.exports=mongoose
    ```
3. Importar la conexión con la base de datos en **backend\src\index.js**:
    ```js
    ≡
    const bodyparser=require('body-parser')

    require('./database')
    ```
4. Ejecutar:
    + $ npm run dev
5. Commit Video 006:
    + $ git add .
    + $ git commit -m "Creando la conexión a la base de datos mongodb"
    + $ git push -u origin main

### Creando controladores y rutas
1. Crear controlador **backend\src\controllers\prueba.controllers.js**:
    ```js
    const PruebaCtrl={}

    PruebaCtrl.obtener=(req, res) => {
        res.send('funcionando desde get')
    }

    PruebaCtrl.crear=(req, res) => {
        res.send('funcionando desde post')
    }

    PruebaCtrl.actualizar=(req, res) => {
        res.send('funcionando desde put')
    }

    PruebaCtrl.eliminar=(req, res) => {
        res.send('funcionando desde delete')
    }

    module.exports=PruebaCtrl
    ```
2. Crear archivo de ruta **backend\src\routes\prueba.route.js**:
    ```js
    const {Router} = require('express')
    const route=Router()
    const PruebaCtrl=require('../controllers/prueba.controllers')

    route.get('/', PruebaCtrl.obtener)
    route.post('/', PruebaCtrl.crear)
    route.put('/', PruebaCtrl.actualizar)
    route.delete('/', PruebaCtrl.eliminar)

    module.exports=route
    ```
3. Indicar rutas en **backend\src\index.js**:
    ```js
    const express=require('express')
    const app=express()
    const morgan=require('morgan')
    const cors=require('cors')
    const bodyparser=require('body-parser')

    require('./database')

    app.set('Port', 4000)

    app.use(morgan('dev'))

    // app.use(bodyparser.urlencoded({extended:true}))

    // app.use(bodyparser.json())

    // Rutas
    app.use('/api/', require('./routes/prueba.route'))

    // start server

    app.listen(app.get('Port'), ()=>{
        console.log('escuchando por el puerto ', app.get('Port'))
    })
    ```
4. Probar la aplicación con la url: http://localhost:4000/api
5. Commit Video 007:
    + $ git add .
    + $ git commit -m "Creando controladores y rutas"
    + $ git push -u origin main

## Sección 3: Frontend

### Creando El Frontend con react
1. Crear proyecto **frontend** en react:
    + $ npx create-react-app frontend
2. Ubicarse en la carpeta del nuevo proyecto **frontend** y levantar un servidor:
    + $ npm start
3. Modificar el archivo **frontend\public\index.html** para agregar los CDN de Bootstrap:
    ```html
    <!DOCTYPE html>
    <html lang="es">
    <head>
        ≡
        <title>React App</title>
        <!-- CSS only -->
        <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
    </head>
    <body>
        ≡
        <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
    </body>
    </html>
    ≡
    ```
    + **CDN Bootstrap**: https://getbootstrap.com
4. Eliminar los siguientes archivos:
    + frontend\src\App.css
    + frontend\src\App.test.js
    + frontend\src\logo.svg
    + frontend\src\setupTests.js
    + frontend\src\reportWebVitals.js
5. Modificar el archivo **frontend\src\App.js**:
    ```js
    import React from 'react';
    import Formulario from './components/Formulario';

    function App() {
        return (
            <div className="App">
                <Formulario/>
            </div>
        );
    }

    export default App;
    ```
6. Modificar el archivo **frontend\src\index.js**:
    ```js
    import React from 'react';
    import ReactDOM from 'react-dom';
    import './index.css';
    import App from './App';

    ReactDOM.render(
        <React.StrictMode>
            <App />
        </React.StrictMode>,
        document.getElementById('root')
    );
    ```
7. Instalar Axios:
    + $ npm i axios
8. Crear componente **frontend\src\components\Formulario.js**:
    ```js
    import React, { useState } from 'react'
    import Axios from 'axios'
    import Swal from 'sweetalert2'

    export default function Formulario() {
        // Declaración de variables (estados)
        const [nombre, setNombre] = useState('')
        const [apellido, setApellido] = useState('')
        const [salario, setSalario] = useState('')

        // Conexión con el backend
        const registrar = async(e) => {
            e.preventDefault()
            const NuevoEmpleado = {nombre, apellido, salario}
            const respuesta = await Axios.post('http://localhost:4000/api', NuevoEmpleado)
            /* console.log(respuesta) */
            const mensaje = respuesta.data.mensaje
            /* alert(mensaje) */
            Swal.fire({
                icon: 'success',
                title: mensaje,
                /* showConfirmButton: false,
                timer: 1500 */
            })
        }

        return (
            <div className="container col-md-3 mt-4">
                <form onSubmit={registrar}>
                    <div className="mb-3">
                        <input type="text" className="form-control" required placeholder="Nombre" onChange={e => setNombre(e.target.value)}/>
                    </div>
                    <div className="mb-3">
                        <input type="text" className="form-control" required placeholder="Apellido" onChange={e => setApellido(e.target.value)} />
                    </div>
                    <div className="mb-3">
                        <input type="text" className="form-control" required placeholder="Salario" onChange={e => setSalario(e.target.value)} />
                    </div>
                    <button type="submit" className="btn btn-primary">Guardar</button>
                </form>   
            </div>
        )
    }
    ```
    + **Nota 1**: en React este archivo también su pudo llamar con la extensión **jsx**.
    + **Nota 2**: para crear la estructura del componente se puede utilizar el atajo de **rfc**.
9. Modificar controlador **backend\src\controllers\prueba.controllers.js**:
    ```js
    const PruebaCtrl={}

    PruebaCtrl.obtener=(req, res) => {
        res.send('funcionando desde get')
    }

    PruebaCtrl.crear = async(req, res) => {
        const {nombre, apellido, salario} = req.body 
        const NuevoRegistro = new Empleado({
            nombre,
            apellido,
            salario
        })
        await NuevoRegistro.save()
        res.json({
            mensaje: 'Empleado guardado'
        })
    }

    PruebaCtrl.actualizar=(req, res) => {
        res.send('funcionando desde put')
    }

    PruebaCtrl.eliminar=(req, res) => {
        res.send('funcionando desde delete')
    }

    module.exports=PruebaCtrl
    ```
10. Instalar Sweetalert2 en el frontend:
    + $ npm install sweetalert2
11. Commit Video 008:
    + $ git add .
    + $ git commit -m "Frontend con react"
    + $ git push -u origin main

### Solucionar error al crear el proyecto de react
1. Abri una terminal de Windows y crear un proyecto de React:
    + $ npx create-react-app frontend
2. dddd
3. Commit Video 009:
    + $ git add .
    + $ git commit -m "Solucionar error al crear el proyecto de react"
    + $ git push -u origin main

    ≡
    ```js
    ```