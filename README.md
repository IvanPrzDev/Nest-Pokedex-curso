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

5. Reconstruir la base de datos con la semilla (seed)

```
http://localhost:3000/api/v2/seed
```

## Funcionalidades Implementadas

### 📦 Seed de Pokémon

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
  - 🔄 **READ**: `GET /api/v2/pokemon` - Listar todos los Pokémon (pendiente)
  - 🔄 **READ**: `GET /api/v2/pokemon/:id` - Obtener Pokémon por ID (pendiente)
  - 🔄 **UPDATE**: `PATCH /api/v2/pokemon/:id` - Actualizar Pokémon (pendiente)
  - 🔄 **DELETE**: `DELETE /api/v2/pokemon/:id` - Eliminar Pokémon (pendiente)

### 🏗️ Arquitectura Modular

- **Adaptadores HTTP**: Implementación de patrón adaptador para peticiones HTTP
- **Inyección de Dependencias**: Uso correcto de providers e imports entre módulos
- **Validación de DTOs**: Validación automática de datos con class-validator
- **Manejo de Errores**: Gestión centralizada de errores con excepciones personalizadas

## STACK

- MongoDB
- Nest
