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
8. Commit Video 003:
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
        useCreateIndex: true,
        useFindAndModify: false
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

1. Commit Video 007:
    + $ git add .
    + $ git commit -m "Creando controladores y rutas"
    + $ git push -u origin main


    ≡
    ```js
    ```

## Sección 3: Frontend

### Creando El Frontend con react

1. Commit Video 008:
    + $ git add .
    + $ git commit -m "Frontend con react"
    + $ git push -u origin main

### Solucionar error al crear el proyecto de react

1. Commit Video 009:
    + $ git add .
    + $ git commit -m "Solucionar error al crear el proyecto de react"
    + $ git push -u origin main