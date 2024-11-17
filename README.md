# Exposicion NoSql
Vamos a crear una base de datos de la liga de futbol española del periodo 2022 - 2023.

<details>
  
  <summary>Posiciones Liga Española 2022 - 2023</summary>
  
  ![image](https://github.com/user-attachments/assets/d784af58-3c72-4677-bde7-2c6a3b84d4fe)
  
</details>



pasos:

1.  Crear base de datos:
   
    `use laLiga`

2.  Se Crean las colecciones de la base de datos:

    `db.createCollection(“posiciones”)`
    
    `db.createCollection(“visita”)`
    
    `db.createCollection(“local”)`

4.  Se insertan los datos para cada coleccion:

      `db.posiciones.insertMany()`

      `db.casa.insertMany()`

      `bd.visita.insertMany()`

    Dentro de los parentesis se debe colocar los valores correspondientes a cada `Gists`:

    https://gist.github.com/juangomez77udea/91a0a7f97135f5a064f0ca8251a3a755

    *Casa: *

    https://gist.github.com/juangomez77udea/341aef9d2fc7ac9c26e392a1b36a8409

6.

    

5.
