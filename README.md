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
| aldeanos.json          | aldeanos          |
| cazadores.json         | cazadores         |
| demonios.json          | demonios          |
| respiraciones.json     | respiraciones     |
