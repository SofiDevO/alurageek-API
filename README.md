## Despliega JSON Server en Vercel

Una plantilla para desplegar [JSON Server](https://github.com/typicode/json-server) en [Vercel](https://vercel.com), ¡permitiéndote ejecutar una API REST falsa en línea 🐣!

Demo desde este repositorio:
https://alurageek-api.vercel.app/

### Cómo usar (resumen)

1. Haz clic en "**Use this Template**" o clona este repositorio.
2. Actualiza o usa el [`db.json`](./db.json) predeterminado en el repositorio.
3. Regístrate o inicia sesión en [Vercel](https://vercel.com).
4. Desde el panel de Vercel, haz clic en "**+ Nuevo Proyecto**" y luego "**Importar**" tu repositorio.
5. En la pantalla "**Configurar Proyecto**", deja todo como está por defecto y haz clic en "**Desplegar**".
6. Espera hasta que el despliegue esté completo, ¡y tu propio servidor JSON estará listo para funcionar!

## `db.json` Predeterminado

```json
{
 "producto": [
        {
            "img": "https://www.claroshop.com/c/star-wars-day/img/categorias/TAZAS_CATEGORIAS_STAR_WARS.png",
            "nombre": "Taza Trooper",
            "precio": "$60.00",
            "descripción": "Taza con casco de Trooper",
            "categoría": "starwars",
            "id": 1
        },
        {
            "img": "https://cdn1.coppel.com/images/catalog/mkp/1773/5000/17733590-1.jpg",
            "nombre": "Funko de Vader",
            "precio": "$60.00",
            "descripción": "Funko coleccionable de Darth Vader",
            "categoría": "starwars",
            "id": 2
        }
 ]
}
```

## Créalo por Ti Mismo

Si deseas crear el proyecto desde cero, tengo un [video tutorial en YouTube (en español) que te guía a través de cómo desplegar tu propia API falsa con db-json y Vercel.](https://www.youtube.com/channel/UC36_js-krsAHAEAWpEDhHtw) 

### Paso 1

Crea un nuevo repositorio, por ejemplo, **alurageek-API**. Luego clona ese repositorio vacío.

### Paso 2

Necesitas ejecutar el comando npm init:
```
npm init -y
```

Esto generará un **package.json**. Ahora, lo que necesitas hacer es cambiar estas líneas:

Cambia esta línea:
``` 
 "main": "index.js",
```

A esto:

```
  "main": "api/server.js",
```

Y esto:

```
"test": "echo \"Error: no test specified\" && exit 1"
```

A esto:

```
"start": "node api/server.js"
```

### Paso 3

Ahora es el momento de ejecutar el comando:

```
npm install json-server cors
```

![Alt text](image.png)

Verás que tanto **cors** como ***json-server*** se han agregado al package.json.

### Paso 4

Ejecuta el comando:
```
npm install json-serve
```
PON ATENCIÓN, YA QUE EL COMANDO DICE ***SERVE*** NO SERVER

Agrega el archivo ***.gitignore*** y agrega ***node_modules***.

### Paso 5

Crea un archivo ***db.json*** y agrega tus propios datos.

Además, necesitarás agregar una nueva [Carpeta llamada ***api***](./api/)  y, dentro de ella, este archivo [**server.js**](./api/server.js):

```javascript
// Ver https://github.com/typicode/json-server#module
const jsonServer = require('json-server')
const server = jsonServer.create()
const router = jsonServer.router('db.json')
const middlewares = jsonServer.defaults()

server.use(middlewares)
// Agrega esto antes de server.use(router)
server.use(jsonServer.rewriter({
    '/api/*': '/$1',
    '/producto/:recurso/:id/ver': '/:recurso/:id'
}))
server.use(router)
server.listen(3000, () => {
    console.log('El servidor JSON está funcionando')
})

// Exporta la API del Servidor
module.exports = server
```

### Paso 6

Crea un archivo nuevo llamado [***vercel.json***](./vercel.json)

```json
{
  "functions": {
    "api/server.js": {
      "memory": 1024,
      "includeFiles": "db.json"
    }
  },
  "rewrites": [
    {
      "source": "/(.*)",
      "destination": "api/server.js"
    }
  ]
}
```

# No olvides hacer commit y hacer push a  tus cambios 🐣

Ve a tu cuenta de Vercel, crea  un nuevo proyecto desde tu repositorio y despliégalo💙

## Debes tener paciencia

Puede tomar varios minutos para que funcione correctamente. ⏰🥹

