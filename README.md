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
}
```