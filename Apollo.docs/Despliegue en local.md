Despliegue en local
Esta documentación detalla los componentes del sistema Apollo, cómo ejecutarlo correctamente en un entorno local y la estructura de su base de datos.
Guía de Ejecución Local (Local Setup)
Para levantar el sistema completo, se deben iniciar los servicios en el siguiente orden: Base de Datos -> API -> Frontend.
Requisitos Previos
Docker y Docker Compose
Make (opcional, pero recomendado)

1. Base de Datos (apollo-service-db)
El servicio de base de datos PostgreSQL debe iniciarse primero ya que define la red compartida apollo_network.

```
cd apollo-service-db
make upi      # Levanta el contenedor en segundo plano (detached)
make migrate  # Ejecuta las migraciones para crear las tablas
```

Verificación:
- El contenedor apollo-db debe estar corriendo (puerto 5432).
- Debe existir la red apollo_network.

2. Backend API (apollo-service-api)

Configuración Previa (.env): Asegúrate de que el archivo .env apunte al nombre del contenedor de la base de datos y no a una IP remota.

```
DB_HOST=apollo-db
DB_NAME=apollo_db
POSTGRES_DB=apollo_db
```

Api Service (apollo-service-api)
Configuración Previa (src/app.js):

```js
const allowedOrigins = [
  'http://localhost:4200',
  'http://localhost:3000',
  'http://localhost:4001', //agregar puerto 4001
  'https://apolloasesorias.com',
  'https://www.apolloasesorias.com',
  'https://qa.apolloasesorias.com',
  'https://www.qa.apolloasesorias.com',
  'https://api.apolloasesorias.com',
  'https://api-qa.apolloasesorias.com'
];
```

Configuración Previa ultimas lineas de docker-compose.yml para agregar en la misma red docker:

```yaml
networks:
  dokploy-network
  apollo_network

networks:
  dokploy-network:
    external: true
  apollo_network:
    external: true
```

Ejecución: Es crítico usar docker compose up --build.

```
cd apollo-service-api
docker-compose up -d --build
```

Notas Importantes:
- La API corre en el puerto 4000.
- Logs importantes:

```
docker logs -f apollo-api
```

3. Frontend Web App (apollo-service-app)

Configuración Previa (src/environments/environment.ts):

```ts
export const environment = {
  production: false,
  apiUrl: "http://localhost:4000/api", // Asegurar este valor
};
```

Ejecución:

```
cd apollo-service-app
docker compose up -d --build
```

Acceso:
http://localhost:4001

Estructura de Base de Datos
El sistema utiliza PostgreSQL. A continuación se listan las tablas principales del esquema public:
Usuarios y Perfiles
users
roles
user_roles
profile
tutor_profile
user_status

Sesiones y Tutorías
sessions
session_status
sessions_history
availability

Académico
topics
subtopics
tutor_services
tutor_service_subtopics

Pagos y Facturación
payments
invoices
payment_methods
withdrawals
tutor_bank_details

Sistema y Configuración
app_settings
notifications
audit_log / deletion_audit_log
schema_migrations

Credenciales de Acceso (Entorno Local)
Administrador
Email: admin@apollo.com
Contraseña: 123456

Usuario Estudiante
Email: user@apollo.com
Contraseña: 123456

Tutor
Email: tutor@apollo.com
Contraseña: 123456

Error de migración que impide el inicio de sesión:
Al intentar ingresar al sistema con las credenciales, aparece un error de contraseña incorrecta. Esto se debe a un problema en la migración actual del sistema. Para probar el sistema, dirígete a , donde el sistema valida correctamente la contraseña.
