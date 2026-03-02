# **Appi-common-data**
# **Manual Técnico y Documentación del API Common - Internal Catalogs**

## **1. Resumen Ejecutivo**
El sistema API Common - Internal Catalogs constituye un servicio de backend diseñado para centralizar la gestión y distribución de datos maestros transversales dentro de la organización. Su propósito fundamental es garantizar la consistencia, integridad y disponibilidad de catálogos de información común, tales como países, ciudades, géneros y datos geográficos, los cuales son consumidos por diversos aplicativos del ecosistema empresarial.

El presente documento detalla la arquitectura técnica, los procedimientos de despliegue, el modelo de datos subyacente y la especificación completa de los interfaces de programación (endpoints) expuestos.

## **2. Arquitectura del Sistema**

### **2.1. Descripción General**
La arquitectura del sistema se basa en un modelo de microservicio RESTful, construido sobre el framework NestJS. El diseño prioriza la modularidad, separando la lógica de negocio en módulos independientes (Countries, Cities, Genders, Geodata) que interactúan con una capa de persistencia relacional.

### **2.2. Stack Tecnológico**
El desarrollo e implementación del servicio se fundamentan en las siguientes tecnologías:

- **Runtime Environment:** Node.js (versión 18 o superior).
- **Framework de Backend:** NestJS (versión 11), estructurado bajo el patrón de diseño MVC y arquitectura modular.
- **Lenguaje de Programación:** TypeScript, proporcionando tipado estático y robustez al código.
- **Base de Datos:** PostgreSQL (versión 15), sistema de almacenamiento persistente de los catálogos.
- **ORM:** TypeORM, encargado del mapeo objeto-relacional.
- **Contenedorización:** Docker y Docker Compose.

### **2.3. Estructura del Proyecto**
El código fuente se organiza siguiendo las mejores prácticas de NestJS:

- **src/modules:** Lógica de negocio por dominio (países, ciudades, etc.).
- **src/shared:** Componentes transversales y reutilizables.
- **database:** Scripts de migración y seeds.
- **environments:** Archivos de configuración por entorno.

## **3. Configuración y Despliegue**

### **3.1. Requisitos Previos**
Se requiere tener instalados:

- Node.js v18+
- PostgreSQL v15+
- Docker (opcional pero recomendado)

### **3.2. Instalación y Ejecución**
El sistema se instala mediante NPM.

**Instalación de dependencias:**
```
npm install
```

**Configuración del entorno:** Crear archivo `.env` basado en `environments/.env.example`.

**Ejecución de la aplicación:**

- **Modo Desarrollo:**
```
npm run dev
```

- **Modo Producción:**
```
npm run prod
```
