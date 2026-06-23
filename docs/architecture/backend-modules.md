# SORA Backend Modules v1.0

## Objetivo

Definir la arquitectura modular del backend de SORA utilizando NestJS.

La aplicación se organizará por módulos independientes para facilitar:

* Escalabilidad.
* Mantenimiento.
* Desarrollo colaborativo.
* Pruebas.
* Futuras expansiones.

---

# Arquitectura General

```text
src/

├── auth/
├── users/
├── avatars/
├── questions/
├── contexts/
├── workshops/
├── simulations/
├── results/
├── statistics/
├── admin/
├── common/
└── database/
```

---

# Auth Module

## Responsabilidad

Gestionar la autenticación y autorización.

## Funciones

* Login.
* Logout.
* Recuperación de contraseña.
* Restablecimiento de contraseña.
* Gestión de JWT.

## Endpoints

POST /auth/login

POST /auth/logout

POST /auth/forgot-password

POST /auth/reset-password

---

# Users Module

## Responsabilidad

Gestionar la información de los usuarios.

## Funciones

* Perfil de usuario.
* Actualización de datos.
* Consulta de información personal.

## Endpoints

GET /users/me

PATCH /users/me

PATCH /users/avatar

---

# Avatars Module

## Responsabilidad

Gestionar los avatares disponibles.

## Funciones

* Consultar catálogo de avatares.

## Endpoints

GET /avatars

---

# Questions Module

## Responsabilidad

Gestionar el banco de preguntas.

## Funciones

* Crear preguntas.
* Editar preguntas.
* Desactivar preguntas.
* Consultar preguntas.

## Endpoints

GET /questions

GET /questions/:id

POST /questions

PATCH /questions/:id

DELETE /questions/:id

---

# Contexts Module

## Responsabilidad

Gestionar contextos compartidos.

## Funciones

* Crear contextos.
* Editar contextos.
* Asociar preguntas.

## Endpoints

GET /contexts

GET /contexts/:id

POST /contexts

PATCH /contexts/:id

DELETE /contexts/:id

---

# Workshops Module

## Responsabilidad

Gestionar talleres académicos.

## Funciones

* Consultar talleres.
* Resolver talleres.
* Calificar talleres.

## Endpoints

GET /workshops

GET /workshops/:id

POST /workshops/:id/submit

---

# Simulations Module

## Responsabilidad

Gestionar simulacros.

## Funciones

* Generar simulacros.
* Reanudar simulacros.
* Guardar respuestas.
* Finalizar simulacros.

## Endpoints

POST /simulations/generate

GET /simulations/:id

POST /simulations/:id/answer

POST /simulations/:id/finish

---

# Results Module

## Responsabilidad

Gestionar resultados obtenidos.

## Funciones

* Consultar resultados.
* Consultar detalle de resultados.

## Endpoints

GET /results

GET /results/:id

---

# Statistics Module

## Responsabilidad

Gestionar estadísticas académicas.

## Funciones

* Evolución histórica.
* Rendimiento por área.
* Rendimiento por tema.
* Rendimiento por competencia.

## Endpoints

GET /statistics

GET /statistics/progress

GET /statistics/areas

GET /statistics/topics

GET /statistics/competencies

---

# Admin Module

## Responsabilidad

Gestionar operaciones administrativas.

## Funciones

* Gestión de usuarios.
* Gestión de importaciones OCR.
* Gestión de configuraciones.

## Endpoints

GET /admin/users

POST /admin/users

PATCH /admin/users/:id

GET /admin/imports

---

# Common Module

## Responsabilidad

Compartir utilidades comunes.

## Contendrá

* Guards.
* Decorators.
* Helpers.
* Constants.
* Exceptions.

---

# Database Module

## Responsabilidad

Gestionar la conexión con PostgreSQL.

## Contendrá

* Entidades.
* Repositorios.
* Migraciones.
* Seeders.

---

# Tecnologías Base

Backend:

* NestJS

Base de Datos:

* PostgreSQL

ORM:

* Prisma (propuesto)

Autenticación:

* JWT

Contenedores:

* Docker

Documentación API:

* Swagger

Validación:

* class-validator

Variables de entorno:

* @nestjs/config

```
```
