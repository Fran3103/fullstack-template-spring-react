# Fullstack Template (Spring Boot + React + MySQL)

Template base para proyectos fullstack con **Java + Spring Boot**, **React** y **MySQL**, pensado para reutilizarlo como punto de partida en distintos proyectos (e-commerce, gym, restaurante, etc.).

## Stack

**Backend**

* Java 17+ (o 21)
* Spring Boot
* Spring Security + JWT
* JPA / Hibernate
* Flyway (migraciones)
* MySQL

**Frontend**

* React (Vite)
* (Opcional) TypeScript
* React Router

**Infra**

* Docker + Docker Compose

---

## Requisitos

Instalado en tu máquina:

* **Git**
* **Java** 17+ (o 21)
* **Maven** (si no usás wrapper)
* **Node.js** 18+ (recomendado)
* **Docker Desktop** (para levantar MySQL con compose)

---

## Estructura del repositorio

* `backend/` → API REST (Spring Boot)
* `frontend/` → UI (React)

---

## Variables de entorno

Copiá los ejemplos y ajustá valores según tu setup:

* `backend/.env.example` → copiar a `backend/.env`
* `frontend/.env.example` → copiar a `frontend/.env`

> Nota: si corrés con Docker Compose, parte de estas variables se toman desde `docker-compose.yml`.

---

## Levantar con Docker (recomendado)

Desde la raíz del repo:

1. Crear archivos `.env` a partir de los ejemplos (si aplica).
2. Ejecutar:

* `docker compose up --build`

Esto levanta:

* MySQL
* Backend

Luego levantás el frontend en modo dev (ver sección Frontend).

---

## Levantar Backend (sin Docker)

1. Asegurate de tener MySQL corriendo localmente.
2. Configurá `backend/.env` o `backend/src/main/resources/application-dev.yml`.
3. Ejecutá desde `backend/`:

* `mvn spring-boot:run`

Backend por defecto:

* URL: `http://localhost:8080`
* Swagger: `http://localhost:8080/swagger-ui/index.html`

---

## Levantar Frontend

Desde `frontend/`:

1. Instalar dependencias:

* `npm install`

2. Ejecutar en modo desarrollo:

* `npm run dev`

Frontend por defecto:

* URL: `http://localhost:5173`

---

## Endpoints base (Foundation)

* `POST /auth/login`
* `POST /auth/register` (si está habilitado)
* `GET /users/me` (requiere JWT)

---

## Roadmap del template (Sprint 0 / Foundation)

### Backend

* [ ] Crear proyecto Spring Boot con dependencias base (Web, Validation, Security, JPA, Flyway, MySQL, OpenAPI)
* [ ] Configurar perfiles `dev` y `prod` (yml separados)
* [ ] Configurar conexión a MySQL por variables de entorno
* [ ] Agregar Flyway y crear migraciones iniciales:

  * [ ] `users`
  * [ ] `roles` (o enum) y relación con usuarios si aplica
* [ ] Implementar autenticación JWT:

  * [ ] `POST /auth/login`
  * [ ] `POST /auth/register` (opcional, o dejar preparado para invitaciones)
* [ ] Implementar endpoint de usuario actual:

  * [ ] `GET /users/me`
* [ ] Implementar RBAC base:

  * [ ] Roles `ADMIN` y `USER`
  * [ ] Ejemplo de endpoint solo admin (para probar 403)
* [ ] Manejo estándar de errores (handler global):

  * [ ] 400 validación
  * [ ] 401 no autenticado
  * [ ] 403 sin permisos
  * [ ] 404 no encontrado
  * [ ] 409 conflicto
  * [ ] 500 inesperado
* [ ] Documentar endpoints y auth en Swagger
* [ ] Docker compose para MySQL + Backend (con variables)
* [ ] (Opcional) Tests de ejemplo:

  * [ ] Login OK
  * [ ] Endpoint protegido sin token → 401
  * [ ] Rol insuficiente → 403

### Frontend

* [ ] Crear proyecto React (Vite)
* [ ] Configurar estructura feature-first:

  * [ ] `features/auth`
  * [ ] `shared` (ui, hooks, utils)
  * [ ] `app` (router/providers)
* [ ] Implementar login page
* [ ] Implementar Auth provider (token + user + roles)
* [ ] Implementar cliente HTTP con interceptor de JWT
* [ ] Implementar rutas protegidas (ProtectedRoute) + pantalla Unauthorized
* [ ] Layout base (navbar/sidebar placeholders)
* [ ] Estados UI compartidos:

  * [ ] Loader
  * [ ] Empty state
  * [ ] Error state
* [ ] (Opcional) Test mínimo de routing o auth

### Documentación

* [ ] Completar `README.md` (root) con:

  * [ ] requisitos
  * [ ] cómo levantar con Docker
  * [ ] cómo levantar manual
  * [ ] variables de entorno
* [ ] Agregar `.env.example` para backend y frontend
* [ ] Agregar colección Postman base (auth + me)

---

## Credenciales demo

> Pendiente: definir usuario demo cuando exista seed/migración inicial.

---

## Licencia

Uso libre para proyectos personales y portfolio.
