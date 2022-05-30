# Solicitudes MongoDB

## 1.1. Desarrollar el Proyecto

A continuación, creará su propia base de datos de red social con las siguientes colecciones:

- Users
- Posts
    - Comments
```powershell
use firstSocialNetwork => Creamos la base de datos
db.createCollection('Users') => Creamos la coleccion Users
db.createCollection('Posts') => Creamos la coleccion Posts
```

## 1.2. Ejecute las siguientes consulta

A continuación tendrás que realizar las siguientes consultas MongoDB:

## 1.2.1 INSERTAR DATOS

Insertar al menos 15 publicaciones nuevas con almenos 2 comentarios por publicación:

- Title
- Body
- Username
- Comments
    - Username
    - Body
```powershell
db.Posts.insertMany([
    {title:"Lo mejor de la vida es...", body: "Lorem fistrum", username: "Shan", comments:[
        {username: "Rebeca", body: "Torpedo no te digo"},
        {username: "Fran", body: "XD."}
    ] },
    {title:"Los patos", body: "Ese hombree te voy a borrar el cerito.", username: "Rebeca", comments:[
        {username: "Fran", body: "Rodrigor se calle ustée ese."},
        {username: "Fran", body: "XD."}
    ] },
    {title:"Vayavaya", body: "Veyeveye.", username: "Rebeca", comments:[
        {username: "Vince", body: "Patatas."},
        {username: "Yorch", body: "XD."}
    ] },
    {title:"Holo", body: "Holo holi.", username: "Vice", comments:[
        {username: "Yorch", body: "Tuberculos varios."},
        {username: "Xavi", body: "XD."}
    ] },
    {title:"jajajaja", body: "Increible.", username: "Yorch", comments:[
        {username: "Xavi", body: "Vaya tela"},
        {username: "German", body: "XD."}
    ] },
    {title:"Aquaplaning", body: "Peligro.", username: "Xavi", comments:[
        {username: "German", body: "pegar."},
        {username: "Vanesa", body: "XD."}
    ] },
    {title:"Dale enter", body: "Not found.", username: "German", comments:[
        {username: "Vanesa", body: "Patatas."},
        {username: "Imanol", body: "XD."}
    ] },
    {title:"Salud", body: "Te lo dicen.", username: "Vanessa", comments:[
        {username: "Imanol", body: "Error."},
        {username: "Alex", body: "XD."}
    ] },
    {title:"Es en js", body: "Por eso te da error.", username: "German", comments:[
        {username: "Rebeca", body: "Cierto."},
        {username: "Shan", body: "XD."}
    ] },
    {title:"Ha petao mi ordenado", body: "Vaya tela.", username: "Vince", comments:[
        {username: "Yorch", body: "IDK."},
        {username: "Imanol", body: "XD."}
    ] },
    {title:"Espera espera", body: "Soy tonte.", username: "Rebeca", comments:[
        {username: "German", body: "One moment."},
        {username: "Imanol", body: "XD."}
    ] },
    {title:"En 15 minutos", body: "Teneis internet.", username: "Xavi", comments:[
        {username: "Rebeca", body: "Porque me salen estar rallitas ostias."},
        {username: "Imanol", body: "XD."}
    ] },
    {title:"Son arrays", body: "dentro de posts.", username: "Xavi", comments:[
        {username: "Fran", body: "Prueba de uno en uno viciosa."},
        {username: "Imanol", body: "XD."}
    ] },
    {title:"Ya no se que mas poner", body: "La clase ha dejado de hablar.", username: "German", comments:[
        {username: "Vanesa", body: "XD."}
    ] },
        {title:"Bueno", body: "es el ultimo.", username: "Alex", comments:[
        {username: "Vanesa", body: "flipo."},
        {username: "Imanol", body: "XD."},
        {username: "German", body: "XD."}
    ] }
])
```

Insertar al menos 10 nuevos usuarios:
Username
Email
Age
```powershell
db.Users.insertMany([
    {username:"Shan", email: "Shan@thebridge.dev", age: 55},
    {username:"Rebeca", email: "Rebeca@thebridge.dev", age: 92},
    {username:"Fran", email: "Fran@thebridge.dev", age: 23},
    {username:"Vince", email: "Vince@thebridge.dev", age: 64},
    {username:"Yorch", email: "Yorch@thebridge.dev", age: 23},
    {username:"Xavi", email: "Xavi@thebridge.dev", age: 43},
    {username:"German", email: "German@thebridge.dev", age: 75},
    {username:"Vanesa", email: "Vanesa@thebridge.dev", age: 12},
    {username:"Imanol", email: "Imanol@thebridge.dev", age: 35},
    {username:"Alex", email: "Alex@thebridge.dev", age: 23}
])
```

### 1.2.2 ACTUALIZAR DATOS
 
- Actualizar publicaciones:
    - Actualiza todos los campos de una publicación

    ```powershell
        db.Posts.updateOne({title:"Aquaplaning"},{
            $set:{title:"Seguimos picando", body: "Mucho picado bro.", username: "Xavi", comments:[
                        {username: "Rebeca", body: "Porque me salen estar rallitas ostias."},
                        {username: "Imanol", body: "XD."}
                    ] }
                })
    ```

    - Cambiar el body de una publicación.

    ```powershell
    db.Posts.updateOne({title: 'Bueno' },
        {
            $set:{
                body: "Y seguimos picando aun mas"
            }
        }
    )
    ```

- Actualizar comentarios:
    - Cambiar el body de un comentario.

    ```powershell
    db.Posts.updateOne({title: 'Bueno' },
        {
            $set:{
                comments:[
                        {username: "Rebeca", body: "A ver si funciona."},
                        {username: "Imanol", body: "XD."}   
                ]
            }
        }
    )
    ```

- Actualizar usuarios:
    - Actualiza todos los campos de un usuario

    ```powershell
    db.Users.updateOne({username: "Xavi"},
        {
            $set:{
                username: "Xavitar",
                email: "Xavitar@thebridge.dev",
                age: 18
            }
        }
    )
    ```

    - Cambiar el email de dos usuarios es decir hacer la query dos veces.

    ```powershell
    db.Users.updateOne({username:"Xavitar"},
        {
            $set:{
                email: "pam8f0709uc490r12@añjlfufoupq0mqwefasdg.gafeagasef"
            }
        }
    )
    db.Users.updateOne({username:"Rebeca"},
        {
            $set:{
                email: "patopato@pato.pato"
            }
        }
    )
    ```

    - Aumenta en 5 años la edad de un usuario
    
    ```powershell
    db.Users.updateOne({username: "Yorch"},
        {
            $inc:{
                age: 5
            }
        }
    )
    ```
    
### 1.2.3 OBTENER DATOS

- Seleccionar todas las publicaciones

```powershell
db.Posts.find()
```

- Selecciona las publicaciones que coincidan con el username indicado

```powershell
db.Posts.find({username: "German"})
```

- Seleccione todos los usuarios con una edad mayor a 20

```powershell
db.Users.find({age:{$gte:20}})
```

- Seleccione todos los usuarios con una edad inferior a 23

```powershell
db.Users.find({age:{$lte:23}})
```

- Seleccione todos los usuarios que tengan una edad entre 25 y 30 años

```powershell
db.Users.find({age:{$gt:25,$lt:30}})
```

- Muestra los usuarios de edad menor a mayor y viceversa

```powershell
db.Users.find().sort({age:1}) => De menor a mayor
db.Users.find().sort({age:-1}) => De mayor a menor
```

- Seleccione el número total de usuarios

```powershell
db.Users.find().count()
```

- Seleccione todas las publicaciones de la siguiente manera: Título de la publicación: "título de las publicaciones"

```powershell
db.Posts.find().forEach((post)=>print(`Título de la publicación: ${post.title}`))
```

- Selecciona solo 2 usuarios

```powershell
db.Users.find().limit(2)
```

- Busca por title 2 publicaciones

```powershell
db.Posts.find({$or:[{title:"Es en js"},{title:"Salud"}]})
```

### 1.2.4 BORRAR DATOS

Elimina a todos los usuarios con una edad mayor a 30

```powershell
db.Users.deleteMany({age:{$gte:30}})
```

## 1.3 Extra

Seleccione el número total de publicaciones que tienen más de un comentario

```powershell
db.Posts.find( { $where: "this.comments.length >= 2" } )
```

Seleccione la última publicación creada

```powershell
db.Posts.find().sort([['_id', -1]]).limit(1)
```

Selecciona 5 publicaciones y que sean las últimas creadas

```powershell
db.Posts.find().sort([['_id', -1]]).limit(5)
```

Elimina todas las publicaciones que tengan más de un comentario

```powershell
db.Posts.deleteMany( { $where: "this.comments.length >= 2" } )
```
