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


# Consulta para buscar Cazadores cuyo rango comience entre A y H

```javascript
db.Cazadores.find({ "rango": { "$regex": "^[A-H].*" } })
```

Este método de consulta sirve para encontrar a todos los documentos en la colección Cazadores cuyo campo rango empiece por una letra entre la A y la H, según el orden alfabético.










