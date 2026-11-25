# 📋 Sistema de Gestión de Proyectos | Angular + NestJS

Aplicación web full stack para gestionar **clientes, proyectos y tareas**. Tiene usuarios con roles, panel de estadísticas con gráficos, historial de cambios y reportes en PDF.

Es el **Trabajo Final Integrador de Desarrollo de Aplicaciones Web** (2026) de la Tecnicatura Universitaria en Desarrollo Web (UNER). Lo desarrollé **en equipo** con otros tres compañeros.

> 📌 Esta es una copia en mi cuenta personal del repositorio original del grupo: [DAW-AL/grupo-AL](https://github.com/DAW-AL/grupo-AL). El historial de commits completo está incluido.

---

## 🛠️ Tecnologías

![Angular](https://img.shields.io/badge/Angular_21-DD0031?style=flat&logo=angular&logoColor=white)
![NestJS](https://img.shields.io/badge/NestJS_11-E0234E?style=flat&logo=nestjs&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat&logo=typescript&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![TypeORM](https://img.shields.io/badge/TypeORM-FE0803?style=flat&logo=typeorm&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger-85EA2D?style=flat&logo=swagger&logoColor=black)

**Frontend**
- **Angular 21** con componentes standalone, guards e interceptores HTTP
- **PrimeNG** y PrimeIcons para la interfaz
- **Chart.js** (ng2-charts) para los gráficos del panel de estadísticas

**Backend**
- **NestJS 11** con arquitectura modular: módulos `auth`, `gestion` e `historial`
- **TypeORM + PostgreSQL**
- **JWT** para la autenticación, **bcrypt** para cifrar contraseñas y **guards de roles**
- **class-validator** para validar los datos de entrada mediante DTOs
- **Swagger** para documentar la API, **Helmet** para seguridad y **PDFKit** para los reportes
- **Compodoc** para la documentación técnica del código

**Deploy**
- **PM2** para el backend y **Nginx** para servir el frontend

## ✨ Funcionalidades

- **Login con JWT** y dos roles: **administrador** y **usuario**.
- **ABM de clientes, proyectos y tareas**, con estados (activo, finalizado, pendiente, baja), borrado lógico y reactivación.
- **Gestión de usuarios** (solo administrador) y módulo de **perfil**.
- **Panel de inicio** con tarjetas de estadísticas y gráficos.
- **Historial de cambios**: registra quién modificó qué y cuándo.
- **Reportes en PDF** de clientes y proyectos.
- **API versionada** (`/api/v1/...`) y documentada con Swagger.

## 🙋‍♂️ Mi aporte

Participé en todo el proyecto. Me encargué principalmente de:

- La **inicialización del proyecto** y su estructura base.
- El **módulo de clientes** completo: entidad, DTOs, servicio y controlador en el backend, y la **pantalla de clientes en Angular**.
- La **documentación Swagger** del módulo de usuarios.
- La **configuración del proyecto** (`.gitignore`, variables de entorno y deploy) y la actualización de clientes desde la vista de proyectos.

## 👥 Equipo

- **Andrés Labra**
- **Demian Diak**
- **Ezequiel Sánchez**: [GitHub](https://github.com/zequisanchez) · [LinkedIn](https://www.linkedin.com/in/ezequieleduardosanchez)
- **Micaela Ortiz**

---

## 📁 Estructura

```
├── backend/     # API REST en NestJS
│   └── src/modules/
│       ├── auth/        # login, usuarios, JWT, roles
│       ├── gestion/     # clientes, proyectos, tareas, estadísticas, PDF
│       └── historial/   # registro de cambios
├── frontend/    # Aplicación Angular
│   └── src/app/         # inicio, proyectos, clientes, tareas, usuarios, historial, perfil
└── script/      # Script SQL para crear la base de datos
```

## 📋 Instalación

### Requisitos
- Node.js 20 o superior
- PostgreSQL

### 1. Base de datos
Crear una base de datos en PostgreSQL y ejecutar el script `script/scriptSQL.txt`.

### 2. Backend
```bash
cd backend
npm install
```
Copiar `.env.example` como `.env` dentro de `backend/` y completar los datos:
```env
PORT=3000
DB_HOST=localhost
DB_PORT=5432
DB_USERNAME=postgres
DB_PASSWORD=tu_password
DB_NAME=nombre_de_tu_base
DB_LOGGING=true
SWAGGER_HABILITADO=true
JWT_SECRET=una_clave_secreta_larga
```
Después iniciar el servidor:
```bash
npm run start:dev
```
La API queda en `http://localhost:3000/api` y, con `SWAGGER_HABILITADO=true`, la documentación Swagger se ve en esa misma dirección.

### 3. Frontend
```bash
cd frontend
npm install
npm start
```
La aplicación queda en `http://localhost:4200`. Las peticiones a `/api` se redirigen al backend con `proxy.conf.json`.
