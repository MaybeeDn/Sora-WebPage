# SORA Tech Stack v1.0

## Objetivo

Definir las tecnologías oficiales que serán utilizadas para el desarrollo inicial de la plataforma SORA.

Esta selección busca priorizar:

* Escalabilidad.
* Facilidad de mantenimiento.
* Rapidez de desarrollo.
* Bajo costo operativo.
* Compatibilidad con Docker.

---

# Arquitectura General

SORA estará compuesta por:

* Frontend Web
* Backend API
* Base de Datos
* Infraestructura Docker

---

# Frontend

## Framework

Next.js

## Lenguaje

TypeScript

## Estilos

Tailwind CSS

## Componentes UI

shadcn/ui

## Gestión de Estado

React Context + TanStack Query

## Formularios

React Hook Form

## Validación

Zod

---

# Backend

## Framework

NestJS

## Lenguaje

TypeScript

## Arquitectura

Modular Architecture

## Documentación API

Swagger

## Validación

class-validator

## Variables de Entorno

@nestjs/config

## Autenticación

JWT

## Hash de Contraseñas

bcrypt

---

# Base de Datos

## Motor

PostgreSQL

## ORM

Prisma

## Migraciones

Prisma Migrate

## Seeders

Prisma Seed

---

# Almacenamiento de Imágenes

## Versión Inicial

Cloudinary

Uso previsto:

* Avatares
* Imágenes de preguntas
* Imágenes de contextos
* Recursos de talleres

---

# OCR

## Objetivo

Extraer preguntas desde documentos PDF escaneados.

## Herramientas Iniciales

* OCRmyPDF
* Tesseract OCR

## Procesamiento

Scripts personalizados en Python.

---

# Infraestructura

## Contenedores

Docker

## Orquestación Local

Docker Compose

---

# Seguridad

## Autenticación

JWT

## Hashing

bcrypt

## Protección de Endpoints

NestJS Guards

## Validación

DTOs + class-validator

---

# Monitoreo

## Logs

NestJS Logger

## Futuro

Posible integración con:

* Grafana
* Prometheus

---

# Testing

## Backend

Jest

## Frontend

Vitest

## End to End

Playwright

---

# Control de Versiones

## Repositorio

GitHub

## Estrategia de Ramas

main

develop

feature/*

bugfix/*

---

# Convenciones

## Backend

snake_case en base de datos.

camelCase en TypeScript.

## Frontend

camelCase para variables y funciones.

PascalCase para componentes.

---

# Versiones Iniciales

Frontend:

* Next.js

Backend:

* NestJS

Base de Datos:

* PostgreSQL

ORM:

* Prisma

Contenedores:

* Docker

Lenguaje:

* TypeScript

---

# Futuras Integraciones

Posibles tecnologías a evaluar:

* Redis
* Elasticsearch
* IA para análisis académico
* Sistema de recomendaciones
* Aplicación móvil
* Notificaciones push

---

# Estado

Versión: 1.0

Estado: Aprobado para desarrollo inicial.
