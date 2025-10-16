<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="120" alt="Nest Logo" /></a>
</p>

# Ejecutar en desarrollo

1. Clonar el repositorio

2. Ejecutar:

```
yarn install
```

3. Tener Nest CLI instalado

```
npm i -g @nestjs/cli
```

4. Levantar la base de datos

```
docker-compose up -d
```

5. Clonar el archivo **.env.template** y renombrar la copia a **.env**

6. Llenar las variables de entorno definidas en el ```.env````

7. Ejecutar la aplicación en dev:

```
yarn start:dev
```

8. Reconstruir la base de datos con la semilla (seed)

```
http://localhost:3000/api/v2/seed
```

# Prod Build

1. Crear archivo ```.env.prod````
2. Llenar variables de entorno para producción
3. Crear nueva imagen

```
docker-compose -f docker-compose.prod.yaml --env-file .env.prod up --build
```

## Funcionalidades Implementadas

### 📦 Seed de Pokémon

- **Endpoint**: `GET /api/v2/seed`
- **Descripción**: Limpia la base de datos y la puebla con 650 Pokémon obtenidos de la PokéAPI
- **Funcionalidades**:
  - Elimina todos los Pokémon existentes antes de la inserción
  - Obtiene datos de 650 Pokémon desde la PokéAPI
  - Inserta todos los Pokémon de manera eficiente usando `insertMany()`
  - Extrae automáticamente el número del Pokémon desde la URL de la API

### 🎯 CRUD de Pokémon

- **Endpoint base**: `/api/v2/pokemon`
- **Funcionalidades**:
  - ✅ **CREATE**: `POST /api/v2/pokemon` - Crear nuevo Pokémon
  - ✅ **READ**: `GET /api/v2/pokemon` - Listar todos los Pokémon con paginación
  - ✅ **READ**: `GET /api/v2/pokemon/:term` - Obtener Pokémon por ID, nombre o número
  - ✅ **UPDATE**: `PATCH /api/v2/pokemon/:term` - Actualizar Pokémon
  - ✅ **DELETE**: `DELETE /api/v2/pokemon/:id` - Eliminar Pokémon

#### Características avanzadas:

- **Búsqueda flexible**: Buscar por ID de MongoDB, número de Pokédex o nombre
- **Paginación**: Parámetros `limit` y `offset` para controlar resultados
- **Ordenamiento**: Resultados ordenados por número de Pokédex
- **Validación**: Pipes personalizados para validar IDs de MongoDB
- **Manejo de errores**: Respuestas HTTP apropiadas para cada caso

## Ejemplos de uso de la API

### Poblar la base de datos

```bash
GET http://localhost:3000/api/v2/seed
```

### Obtener todos los Pokémon (con paginación)

```bash
GET http://localhost:3000/api/v2/pokemon?limit=20&offset=0
```

### Buscar un Pokémon específico

```bash
# Por número de Pokédex
GET http://localhost:3000/api/v2/pokemon/1

# Por nombre
GET http://localhost:3000/api/v2/pokemon/bulbasaur

# Por ID de MongoDB
GET http://localhost:3000/api/v2/pokemon/507f1f77bcf86cd799439011
```

### Crear un nuevo Pokémon

```bash
POST http://localhost:3000/api/v2/pokemon
Content-Type: application/json

{
  "no": 1001,
  "name": "MiPokemon"
}
```

### Actualizar un Pokémon

```bash
PATCH http://localhost:3000/api/v2/pokemon/bulbasaur
Content-Type: application/json

{
  "name": "NuevoNombre"
}
```

### Eliminar un Pokémon

```bash
DELETE http://localhost:3000/api/v2/pokemon/507f1f77bcf86cd799439011
```

### 🏗️ Arquitectura Modular

- **Adaptadores HTTP**: Implementación de patrón adaptador para peticiones HTTP
- **Inyección de Dependencias**: Uso correcto de providers e imports entre módulos
- **Validación de DTOs**: Validación automática de datos con class-validator
- **Manejo de Errores**: Gestión centralizada de errores con excepciones personalizadas

## STACK

- MongoDB
- Nest
