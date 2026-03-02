# **Documentación Técnica del Sistema Apollo**

Este documento detalla la arquitectura, componentes y tecnologías utilizadas en el sistema Apollo, una plataforma de tutorías y asesorías académicas.

---

## **1. Visión General de la Arquitectura**
El sistema Apollo sigue una arquitectura de microservicios o servicios distribuidos, separando claramente la base de datos, el backend (API) y el frontend (App).

---

## **2. Componentes del Sistema**

### **2.1 Base de Datos (apollo-service-db)**
El sistema utiliza PostgreSQL como motor de base de datos relacional. Se utilizan extensiones avanzadas para funcionalidades específicas.

**Motor:** PostgreSQL

**Gestión de Migraciones:** Scripts personalizados en Node.js (`migrate.js`) y archivos SQL crudos.

**Extensiones Activas:**
- `uuid-ossp`: Para generación de identificadores únicos (UUID v4).
- `pgcrypto`: Para encriptación de datos sensibles.
- `pg_trgm`: Para búsquedas de texto eficientes.

### **Esquema de Base de Datos (Principales Tablas)**

#### **Usuarios y Autenticación:**
- `users`: Tabla central. Almacena credenciales, estados y tokens.
- `roles`: Definición de roles (user, tutor, admin, moderator).
- `user_roles`: Relación muchos a muchos.
- `profile`: Información extendida del usuario.

#### **Tutores y Servicios:**
- `tutor_profile`: Información específica de tutores.
- `tutor_services`: Servicios ofrecidos.
- `topics` / `subtopics`: Categorización de áreas de conocimiento.
- `availability`: Gestión de horarios disponibles.

#### **Sesiones y Pagos:**
- `sessions`: Registro de tutorías.
- `payments`: Registro transaccional.
- `invoices`: Facturas generadas.
- `withdrawals`: Solicitudes de retiro.

#### **Sistema:**
- `audit_log`: Trazabilidad.
- `notifications`: Notificaciones internas.
- `app_settings`: Configuración dinámica.

---

### **2.2 Backend API (apollo-service-api)**
API RESTful construida con Node.js y Express.

**Framework:** Express 4.18

**Lenguaje:** JavaScript (CommonJS)

### **Seguridad:**
- `helmet` (recomendado)
- `cors` para orígenes
- `jsonwebtoken` (JWT)
- `bcrypt` para hashing
- `passport` para Google OAuth

### **Patrón de Diseño:** Arquitectura en Capas
- **Controller:** Manejo de HTTP.
- **Service:** Lógica de negocio.
- **Repository:** Acceso a datos (con `pg`).
- **Routes:** Definición de endpoints.

### **Estructura de Directorios**
```
src/
├── core/               # Configuraciones, middlewares globales
├── modules/            # Módulos de negocio
│   └── users/          # Ejemplo
│       ├── users.controller.js
│       ├── users.service.js
│       ├── users.repository.js
│       └── users.routes.js
├── routes/             # Agrupador de rutas
├── shared/             # Utilidades comunes
├── app.js              # Configuración Express
└── server.js           # Entrypoint
```

### **Integraciones Externas Detectadas**
- **AWS S3**: Almacenamiento de archivos.
- **GetStream**: Chat y video.
- **PayPal**: Pagos.
- **Google OAuth**: Login social.

---

### **2.3 Frontend App (apollo-service-app)**
Aplicación SPA construida con Angular.

**Framework:** Angular

### **Estilos:**
- **TailwindCSS**
- **PrimeNG / PrimeFlex**

### **Estructura del Frontend:**
- `core`: Servicios singleton, interceptores.
- `shared`: Componentes reutilizables.
- `pages`: Vistas principales.
- `dashboard`: Módulo privado.

### **Routing:**
- **Rutas públicas:** Landing, Login, Registro.
- **Rutas privadas:** dashboard/* (AuthGuard)
- **Rutas especiales:** `video-call/:callId`

---

## **3. Infraestructura y Despliegue**
- **Docker:** Cada servicio posee Dockerfile.
- **Docker Compose:** Orquestación local.
- **Makefiles:** Automatización para build, run, logs.

---

## **4. Flujos Clave del Sistema**

### **Registro y Onboarding:**
1. Usuario se registra → API crea `users` + `profile`.
2. Si es tutor → completa `tutor_profile`, documentos, servicios.
3. Moderador valida documentos.

### **Agendamiento:**
- Estudiante busca tutor (topics, precio, rating).
- Consulta `availability`.
- Crea `session` en estado pending o confirmed.

### **Video Llamada:**
- Integración con GetStream o similar.
- Historial y duración quedan en `sessions`.

---
