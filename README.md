## Deploy JSON Server to Vercel

A template to deploy [JSON Server](https://github.com/typicode/json-server) to [Vercel](https://vercel.com), allow you to run fake REST API online!

Demo from this repository: 




### How to use

1. Click "**Use this template**" or clone this repository.
2. Update or use the default [`db.json`](./db.json) in the repository.
3. Sign Up or login into [Vercel](https://vercel.com).
4. From the Vercel dashboard, click "**+ New Project**" then "**Import**" your repository.
5. In the "**Configure Project**" screen, leave everything default and click "**Deploy**".
6. Wait until deployment is done, and your own JSON server is ready to serve!

## Default `db.json`

```
{
 "product": [
        {
            "img": "https://www.claroshop.com/c/star-wars-day/img/categorias/TAZAS_CATEGORIAS_STAR_WARS.png",
            "name": "Trooper taza",
            "price": "$60.00",
            "Description": "Taza casco Trooper",
            "category": "starwars",
            "id": 1
        },
        {
            "img": "https://cdn1.coppel.com/images/catalog/mkp/1773/5000/17733590-1.jpg",
            "name": "Funko Vader",
            "price": "$60.00",
            "Description": "Funko coleccionable Darth vader",
            "category": "starwars",
            "id": 2
        }
 ]
}
```


## Do it by your own


If you want to create the project from scratch, I have a Youtube video [Tutorial (spanish) that teach you how to deploy your own fake API with db-json and vercel.]() 

### 1

create a new repository, (**alurageek-API**) for example. then clone that empty repository 

### 2

You need to run the npm init command:
```npm init -y```

This will generate a **package.json** now what you need to do is to change this line:

```"test": "echo\"Error:no test specified\" && exit 1" ```

For this one:

```"start": "node index.js"```

### 3

Now its time to run the command:

```npm install json-server cors```

![Alt text](image.png)

You will see that the **cors** and ***json-server*** was added to the package.json.

### 4

run the command:
```npm install json-serve```

add the ***.gitignore*** file, an add the ***node_modules***

###

create a ***db.json*** file. 
and add your own data.

Also, you will need to add this **index.js** file:

```const jsonServer = require("json-server"); // importing json-server library
const server = jsonServer.create();
const router = jsonServer.router("db.json");
const middlewares = jsonServer.defaults();
const port = process.env.PORT || 3001; // you can use any port number here; i chose to use 3001

server.use(middlewares);
server.use(router);

server.listen(port);
```

# Don't forget to commit & push your changes 🐣

Go to your vercel account, connect a new project with your repository and deploy it💙