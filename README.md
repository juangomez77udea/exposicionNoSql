# Exposicion NoSql
Vamos a crear una base de datos de la liga de futbol española del periodo 2022 - 2023.

<details>
  
  <summary>Posiciones Liga Española 2022 - 2023</summary>
  
  ![image](https://github.com/user-attachments/assets/d784af58-3c72-4677-bde7-2c6a3b84d4fe)
  
</details>



pasos:

1.  Crear base de datos:
   
    `use laLiga`

    ![image](https://github.com/user-attachments/assets/50c1573e-7caf-46a4-965f-3ad81bc31734)


3.  Se Crean las colecciones de la base de datos:

    `db.createCollection(“posiciones”)`
    
    `db.createCollection(“visita”)`
    
    `db.createCollection(“local”)`

     ![image](https://github.com/user-attachments/assets/13889c11-7f36-47ff-ab17-1a8f54d3f890)



5.  Se insertan los datos para cada coleccion:

      `db.posiciones.insertMany()`

      `db.casa.insertMany()`

      `bd.visita.insertMany()`

    Dentro de los parentesis se debe colocar los valores correspondientes a cada Gists:
    

   Posiciones:

    https://gist.github.com/juangomez77udea/91a0a7f97135f5a064f0ca8251a3a755

   

   Casa:

    https://gist.github.com/juangomez77udea/341aef9d2fc7ac9c26e392a1b36a8409

  Visita:

    https://gist.github.com/juangomez77udea/71f3cf97cf0a5a4d9895da99f1ffedd7

    

  ![image](https://github.com/user-attachments/assets/b7802d3b-6d3e-4b9b-956a-7c6000d5f9b8)

  Luego de insertar los elementos del Gist en cada colección, se obtiene un resultado similar a este:

![image](https://github.com/user-attachments/assets/853e75ff-ba2c-4cae-9d94-7d556fe0a72d)



5. Se puede revisar con el siguiente comando que los colecciones tengan la cantidad de equipos correcta, que en este caso son 20:

   `db.posiciones.countDocuments()`
   

  ![image](https://github.com/user-attachments/assets/ed3a74bc-9790-4a81-8da0-8e86344bd443)



7. Una manera de visualizar los datos de cada colección es con el siguiente comando:

   `db.posiciones.find().pretty`


   ![image](https://github.com/user-attachments/assets/f3931784-17df-4afe-959c-0285e0003442)

   

**Algunos Querys:**

7. Muestrar todos los objetos excluyende de estos el id:

    `db.posiciones.find({},{"_id":0})`
  
8. Ordenar los equipos por puntaje de menor a mayor:

    `db.posiciones.find({}, { "_id": 0, "nombre": 1, "pts": 1 }).sort({ "pts": 1 })`

9. Ordenar los equipos por puntaje de mayor a menor:

    `db.posiciones.find({}, { "_id": 0, "nombre": 1, "pts": 1 }).sort({ "pts": -1 })`

10. Teniendo en cuenta que los 4 equipos con mayor puntaje, van a champions League, encuentrar cuales son estos equipos en orden de puntos de mayor a menor:

    `db.posiciones.find({}, { "_id": 0, "nombre": 1, "pts": 1 })
                .sort({ "pts": -1 })
                .limit(4)`

11. Los tres últimos equipos en la tabla van directamente al descenso, encontrar los equipos que descienden:

    `db.posiciones.find({}, { "_id": 0, "nombre": 1, "pts": 1 })
    	.sort({ "pts": -1 }).limit(3)
    	.sort({ "pts": 1 })`


12. ¿Cuál es el equipo con menos goles en contra?:

    `db.posiciones.find({}, { "_id": 0, "nombre": 1, "gc": 1 })
    		.sort({ "gc": 1 })
    		.limit(1)`

    
13. ¿Cuál es el equipo con mayor cantidad de goles anotados?:

    `db.posiciones.find({}, { "_id": 0, "nombre": 1, "gf": 1 })
    .sort({ "gf": -1 })
    .limit(1)`

14. ¿De los 4 equipos que pasaron a champions, cual recibió más goles en contra como local?

    `const topEquipos = db.posiciones.find({}, { "_id": 0, "nombre": 1, "pts": 1 })
      .sort({ "pts": -1 })
      .limit(4)
      .toArray()
      .map(e => e.nombre);`

    `db.casa.find(
    			{ "nombre": { $in: topEquipos } },
    			{ "_id": 0, "nombre": 1, "gc": 1 }
        )
      .sort({ "gc": -1 });`

16. De los 3 equipos que descienden, ¿Cuál es el equipo más goleador como visitante?
    
    `const topTeams = db.posiciones.find({}, { "_id": 0, "nombre": 1, "pts": 1 })
    	.sort({ "pts": 1 })
    	.limit(3)
   		.toArray();`

    `const topAwayGoalsTeam = db.posiciones.find(
    { "nombre": { $in: topTeams.map(team => team.nombre) } },
    { "_id": 0, "nombre": 1, "gf": 1 }
    ).sort({ "gf": -1 }).limit(1);
      topAwayGoalsTeam;`


    



   
 
