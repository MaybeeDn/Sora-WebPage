# SORA Prisma Models v1.0

## Objetivo

Definir los modelos iniciales que posteriormente serán implementados en Prisma.

---

# Enums

## UserRole

```prisma
enum UserRole {
  STUDENT
  ADMIN
}
```

---

## SimulationType

```prisma
enum SimulationType {
  FULL
  AREA
}
```

---

## SimulationStatus

```prisma
enum SimulationStatus {
  IN_PROGRESS
  FINISHED
  ABANDONED
}
```

---

# Avatar

```prisma
model Avatar {
  id        String   @id @default(uuid())
  name      String
  imageUrl  String

  users     User[]

  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt
}
```

---

# User

```prisma
model User {
  id            String   @id @default(uuid())

  firstName     String
  lastName      String

  email         String   @unique
  passwordHash  String

  role          UserRole

  avatarId      String?
  avatar        Avatar? @relation(fields: [avatarId], references: [id])

  isActive      Boolean @default(true)

  attempts      SimulationAttempt[]

  createdAt     DateTime @default(now())
  updatedAt     DateTime @updatedAt
}
```

---

# Area

```prisma
model Area {
  id            String   @id @default(uuid())

  name          String   @unique
  description   String?

  topics        Topic[]
  competencies  Competency[]
  questions     Question[]

  createdAt     DateTime @default(now())
  updatedAt     DateTime @updatedAt
}
```

---

# Topic

```prisma
model Topic {
  id          String @id @default(uuid())

  name        String

  areaId      String
  area        Area @relation(fields: [areaId], references: [id])

  questions   Question[]

  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt
}
```

---

# Competency

```prisma
model Competency {
  id          String @id @default(uuid())

  name        String

  areaId      String
  area        Area @relation(fields: [areaId], references: [id])

  questions   Question[]

  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt
}
```

---

# Context

```prisma
model Context {
  id          String @id @default(uuid())

  title       String?
  content     String?
  imageUrl    String?

  questions   Question[]

  createdAt   DateTime @default(now())
  updatedAt   DateTime @updatedAt
}
```

---

# Question

```prisma
model Question {
  id              String @id @default(uuid())

  statement       String

  imageUrl        String?

  difficulty      Int @default(1)

  isActive        Boolean @default(true)

  contextId       String?
  context         Context? @relation(fields: [contextId], references: [id])

  areaId          String
  area            Area @relation(fields: [areaId], references: [id])

  topicId         String
  topic           Topic @relation(fields: [topicId], references: [id])

  competencyId    String
  competency      Competency @relation(fields: [competencyId], references: [id])

  options         Option[]

  simulationQuestions SimulationQuestion[]

  createdAt       DateTime @default(now())
  updatedAt       DateTime @updatedAt
}
```

---

# Option

```prisma
model Option {
  id            String @id @default(uuid())

  label         String

  content       String?

  imageUrl      String?

  isCorrect     Boolean @default(false)

  questionId    String
  question      Question @relation(fields: [questionId], references: [id])

  answers       Answer[]

  createdAt     DateTime @default(now())
  updatedAt     DateTime @updatedAt
}
```
