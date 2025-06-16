# Anime_Personajes

Este repositorio contiene una base de datos documental en MongoDB basada en el universo de **Shingeki no Kyojin (Attack on Titan)** y otras franquicias de anime relacionadas como Demon Slayer. La base de datos está diseñada para servir como apoyo a una aplicación web tipo enciclopedia o sistema de fichas de personajes y poderes.

---

## Descripción del sistema

El sistema representa datos de distintos mundos de anime con información organizada en cinco colecciones principales:

1. **titanes**: Información de los titanes y sus portadores.  
2. **respiraciones**: Posturas y técnicas de los cazadores de demonios (Demon Slayer).  
3. **eldianos**: Personajes humanos de SNK y sus detalles.  
4. **demonios**: Demonios de distintas jerarquías y habilidades.
5. **cazadores**: informacion de los cazadores y sus detalles.


Cada colección contiene al menos 10 documentos variados con campos clave para el uso práctico de la información.

## Cómo crear la base de datos en MongoDB

1. Crea una cuenta en [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) o usa MongoDB Compass para trabajar localmente.
2. Crea un nuevo cluster (si usas Atlas).
3. Crea una nueva base de datos llamada: `Anime`
4. Dentro de la base de datos crea las siguientes colecciones:
   - titanes
   - eldianos
   - cazadores
   - demonios
   - respiraciones
  
## Cómo importar los archivos `.json`

Para importar los datos en MongoDB Compass o Atlas, sigue estos pasos:

1. Abre MongoDB Compass y conéctate a tu base de datos.
2. Selecciona la base de datos `Anime`.
3. Para cada colección:
   - Haz clic en `ADD DATA` → `Import File`.
   - Selecciona el archivo JSON correspondiente.
   - Asegúrate de que el formato sea JSON.
   - Importa el archivo.
  
  
**Archivos y colecciones correspondientes:**

| Archivo JSON           | Colección MongoDB |
|----------------------- |-------------------|
| titanes.json           | titanes           |
| eldianos.json          | eldianos          |
| cazadores.json         | cazadores         |
| demonios.json          | demonios          |
| respiraciones.json     | respiraciones     |

## Consultas Regulares

# 1. Consulta para buscar Eldianos que empiecen con "Eren"

```javascript
db.Eldianos.find({ "nombre": { "$regex": "^Eren" } })
```

Este método de consulta sirve para buscar a todos los documentos en la colección Eldianos cuyo campo nombre comience con "Eren".
En este caso, solo devolverá al protagonista, ya que su nombre empieza exactamente así.

# 2. Consulta para buscar Eldianos cuyo estado termine en "muerto"

```javascript
db.Eldianos.find({ 
  "estado": { 
    "$regex": "^muert[oa]$", 
    "$options": "i"  
  } 
})
```

Este método de consulta sirve para buscar a todos los documentos en la colección Eldianos cuyo campo estado termine exactamente en "muerto o muerta".

# 3. Consulta para buscar Eldianos afiliados al grupo de exploradores

```javascript
db.Eldianos.find({ "afiliacion": { "$regex": ".*ploradores" } })
```

Este método de búsqueda sirve para encontrar a todos los documentos en la colección Eldianos cuyo campo afiliacion contenga la palabra "exploradores" o cualquier variante que termine en "ploradores".

# 4. Consulta para buscar Eldianos con rol de protagonista

```javascript
db.Eldianos.find({ "rol": { "$regex": "protagonista" } })
```

Este método de búsqueda sirve para encontrar a todos los documentos en la colección Eldianos cuyo campo rol contenga la palabra "protagonista".

# 5. Consulta para buscar Eldianos que vivieron en murallas cuya inicial esté entre la M y la R

```javascript
db.Eldianos.find({ "muralla": { "$regex": "^[M-R]" } })
```

Este método de consulta sirve para encontrar solo a los documentos en la colección Eldianos cuyo campo muralla comienza con una letra entre la M y la R.
Este filtro ignora murallas como "Zina", ya que su inicial no está dentro del rango especificado.

# 6. Consulta para buscar Titanes cuyo nombre comienza por "C"

```javascript
db.Titanes.find({ "titan": { "$regex": "C..." } })
```

Este método de consulta sirve para buscar a todos los documentos en la colección Titanes cuyo campo titan comience con la letra "C" y tenga al menos tres caracteres más, sin importar cuáles sean.

# 7. Consulta para buscar Titanes cuyo estado sea exactamente "activo"

```javascript
db.Titanes.find({ "estado": { "$regex": "^activo$" } })
```

Este método de consulta sirve para buscar a todos los documentos en la colección Titanes cuyo campo estado sea exactamente "activo".

# 8. Consulta para buscar Titanes con la habilidad especial de "fundador"

```javascript
db.Titanes.find({ "habilidades": { "$regex": "fundador", "$options": "i" } })
```

Este método de consulta sirve para encontrar a todos los documentos en la colección Titanes cuyo campo habilidades contenga la palabra "fundador", sin importar si está en mayúsculas o minúsculas.

# 9. Consulta para buscar Titanes cuyo origen sea exactamente "Eldia"

```javascript
db.Titanes.find({ "origen": { "$regex": "^Eldia$" } })
```

Este método de consulta sirve para encontrar a todos los documentos en la colección Titanes cuyo campo origen sea exactamente "Eldia".
Ignora a los titanes cuyo origen sea "Marley" o cualquier otra variación.

# 10. Consulta para buscar Titanes con habilidades que terminan en "cia"

```javascript
db.Titanes.find({ "habilidades": { "$regex": ".*cia$" } })
```

Este método de consulta sirve para buscar a todos los documentos en la colección Titanes cuyo campo habilidades termine en la palabra "cia", como en "resistencia".
Ignora por completo a los titanes que no tienen habilidades con esa terminación.

# 11. Consulta para buscar Cazadores cuyos nombres comienzan por la letra "T"

```javascript
db.Cazadores.find({ "nombre": { "$regex": "T...." } })
```

Este método de consulta sirve para buscar a todos los documentos en la colección Cazadores cuyo campo nombre o segundo nombre comience con la letra "T" y tenga al menos cuatro caracteres más.

# 12. Consulta para buscar Cazadores con técnica de respiración que comience por "Respiracion" y luego una palabra que comience con "S"

```javascript
db.Cazadores.find({
  "Tenica": {
    "$regex": "^Respiracion.*\\s[Ss]",
    "$options": "i"
  }
})
```

Este método de consulta sirve para encontrar a todos los documentos en la colección Cazadores cuyo campo Tenica (técnica) empiece con la palabra "Respiracion" y luego tenga otra palabra que comience con la letra "S" (mayúscula o minúscula).


# 13. Consulta para buscar Cazadores cuyo estado sea "vivo"

```javascript
db.Cazadores.find({ "estado": { "$regex": "vivo$" } })
```

Este método de consulta sirve para encontrar a todos los documentos en la colección Cazadores cuyo campo estado termina en "vivo", es decir, aquellos que aún siguen con vida 😢.

# 14. Consulta para buscar Cazadores cuyo rango termine en "lar"

```javascript
db.Cazadores.find({ "rango": { "$regex": ".*lar$" } })
```

Este método de consulta sirve para encontrar a todos los documentos en la colección Cazadores cuyo campo rango termine en "lar", como por ejemplo "Pilar".


# 15. Consulta para buscar Cazadores cuyo rango comience entre A y H

```javascript
db.Cazadores.find({ "rango": { "$regex": "^[A-H].*" } })
```

Este método de consulta sirve para encontrar a todos los documentos en la colección Cazadores cuyo campo rango empiece por una letra entre la A y la H, según el orden alfabético.

# 16. Consulta para buscar Demonios cuyo nombre comience por "Muzan"

```javascript
db.Demonios.find({ "nombre": { "$regex": "^Muzan" } })
```

Este método de consulta sirve para buscar a todos los documentos en la colección Demonios cuyo campo nombre comience exactamente por "Muzan".

# 17. Consulta para buscar Demonios cuyo rol contenga la palabra "Demonio"

```javascript
db.Demonios.find({ "rol": { "$regex": "Demonio" } })
```

Este método de consulta sirve para buscar a todos los documentos en la colección Demonios cuyo campo rol contenga la palabra "Demonio" en cualquier parte del texto.


# 18. Consulta para buscar Demonios que han vivido más de 100 años

```javascript
db.Demonios.find({ "años_vivo": { "$regex": "\\d{3,}" } })
```

Este método de consulta sirve para encontrar a todos los documentos en la colección Demonios cuyo campo años_vivo contiene tres o más dígitos numéricos, es decir, demonios que han vivido 100 años o más.


# 19. Consulta para buscar Demonios con habilidades que terminan en "za"

```javascript
db.Demonios.find({ "habilidades": { "$regex": ".*za$" } })
```

Este método de consulta sirve para encontrar a todos los documentos en la colección Demonios cuyo campo habilidades termine en "za".

# 20. Consulta para buscar Demonios cuyo estado sea exactamente "muerto"

```javascript
db.Demonios.find({ "estado": { "$regex": "^muerto$" } })
```

Este método de consulta sirve para encontrar a todos los documentos en la colección Demonios cuyo campo estado sea exactamente "muerto", sin permitir texto adicional antes ni después.


# 21. Consulta para buscar una postura que contenga "Corte" dentro de una respiración

```javascript
db.Respiraciones.find(
  { "posturas.nombre": { $regex: "Corte" } },
  { "posturas.$": 1 }
)
```

Este método de consulta sirve para encontrar una respiración que tenga al menos una postura cuyo nombre contenga la palabra "Corte", y solo mostrará esa postura específica que coincide.


# 22. Consulta para buscar respiraciones con posturas cuya descripción mencione "dolor"

```javascript
db.Respiraciones.find({
  posturas: {
    $elemMatch: {
      descripcion: { $regex: "dolor", $options: "i" }
    }
  }
})
```

Este método de consulta sirve para encontrar todos los documentos en la colección Respiraciones que contengan al menos una postura cuya descripción mencione la palabra "dolor", sin importar si está en mayúscula o minúscula.


# 23. Consulta para buscar respiraciones con posturas cuyo nombre comience por "R" y tenga al menos 4 letras

```javascript
db.Respiraciones.find({
  posturas: {
    $elemMatch: {
      nombre: { $regex: "^R..." }
    }
  }
})
```

Este método de consulta sirve para encontrar todos los documentos en la colección Respiraciones que contengan al menos una postura cuyo nombre empiece por la letra "R" y tenga un mínimo de 4 caracteres.


# 24. Consulta para buscar respiraciones con posturas que comiencen por "S" o "s" seguida de una vocal

```javascript
db.Respiraciones.find({
  posturas: {
    $elemMatch: {
      nombre: { $regex: "^[Ss][aeiou]" }
    }
  }
})
```

Este método de consulta sirve para encontrar todos los documentos en la colección Respiraciones que tengan al menos una postura cuyo nombre comience por una "S" mayúscula o minúscula, seguida de una vocal (a, e, i, o, u).

# 25. Consulta para mostrar nombres de posturas que comienzan por letras específicas

```javascript
db.Respiraciones.find(
  { "posturas.nombre": { $regex: "^[A-HJSa-hjs]" } },
  { "posturas.nombre": 1, _id: 0 }
)
```

Este método de consulta sirve para mostrar los nombres de posturas dentro de la colección Respiraciones que comiencen por las letras A-H, J o S (mayúsculas o minúsculas).

### Trabajo echo por

- Manuel Larrotta Meneses
- Karina Sanabria Casas


















