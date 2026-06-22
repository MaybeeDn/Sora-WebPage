# SORA Database v1.0

## Objetivo

Definir la estructura inicial de la base de datos de SORA.

La base de datos está diseñada para soportar:

* Gestión de usuarios.
* Avatares.
* Banco de preguntas.
* Contextos compartidos.
* Simulacros tipo ICFES.
* Talleres.
* Resultados.
* Estadísticas.

---

# Convenciones

## Claves primarias

Todas las tablas utilizarán UUID.

## Timestamps

Todas las entidades principales incluirán:

* created_at
* updated_at

## Soft Delete

Los registros no serán eliminados físicamente.

Se utilizarán campos de estado para desactivar elementos cuando sea necesario.

---

# FASE 1 - Entidades Núcleo

## avatars

Descripción:
Almacena los avatares disponibles para los estudiantes.

Campos:

* id
* name
* image_url
* created_at
* updated_at

---

## users

Descripción:
Almacena estudiantes y administradores.

Campos:

* id
* first_name
* last_name
* email
* password_hash
* avatar_id
* role
* is_active
* created_at
* updated_at

Roles permitidos:

* STUDENT
* ADMIN

---

## areas

Descripción:
Áreas evaluadas por el ICFES.

Campos:

* id
* name
* description
* created_at
* updated_at

Datos iniciales:

* Lectura Crítica
* Matemáticas
* Sociales y Ciudadanas
* Ciencias Naturales
* Inglés

---

## topics

Descripción:
Temas específicos dentro de cada área.

Campos:

* id
* area_id
* name
* description
* created_at
* updated_at

---

## competencies

Descripción:
Competencias evaluadas por el ICFES.

Campos:

* id
* area_id
* name
* description
* created_at
* updated_at

---

# FASE 2 - Banco de Preguntas

## contexts

Descripción:
Textos, imágenes o recursos compartidos por varias preguntas.

Campos:

* id
* title
* content
* image_url
* source
* created_at
* updated_at

---

## questions

Descripción:
Preguntas individuales del banco.

Campos:

* id
* context_id
* area_id
* topic_id
* competency_id
* statement
* image_url
* difficulty
* is_active
* created_at
* updated_at

Dificultad:

* 1 = Fácil
* 2 = Media
* 3 = Difícil

---

## options

Descripción:
Opciones de respuesta.

Campos:

* id
* question_id
* option_label
* content
* image_url
* is_correct
* created_at
* updated_at

---

## question_imports

Descripción:
Registro de importaciones masivas provenientes de OCR.

Campos:

* id
* file_name
* imported_questions
* imported_at
* created_by

---

# FASE 3 - Simulacros

## simulation_attempts

Descripción:
Intentos de simulacro realizados por los estudiantes.

Campos:

* id
* user_id
* type
* area_id
* is_timed
* status
* started_at
* finished_at
* duration_seconds
* score
* created_at
* updated_at

Tipos:

* FULL
* AREA

Estados:

* IN_PROGRESS
* FINISHED
* ABANDONED

---

## simulation_questions

Descripción:
Preguntas asociadas a un intento específico.

Campos:

* id
* attempt_id
* question_id
* question_order
* created_at
* updated_at

---

## answers

Descripción:
Respuestas seleccionadas por los estudiantes.

Campos:

* id
* simulation_question_id
* selected_option_id
* is_correct
* answered_at
* created_at
* updated_at

---

# Relaciones Principales

avatars
└── users

areas
├── topics
├── competencies
└── questions

contexts
└── questions

questions
└── options

users
└── simulation_attempts

simulation_attempts
└── simulation_questions

simulation_questions
└── answers
