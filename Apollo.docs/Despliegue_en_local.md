Esta documentación detalla los componentes del sistema Apollo, cómo ejecutarlo correctamente en un entorno local y la estructura de su base de datos.
Guía de Ejecución Local (Local Setup)
Para levantar el sistema completo, se deben iniciar los servicios en el siguiente orden: Base de Datos -> API -> Frontend.
Requisitos Previos
Docker y Docker Compose
Make (opcional, pero recomendado)

1. Base de Datos (apollo-service-db)
   El servicio de base de datos PostgreSQL debe iniciarse primero ya que define la red compartida apollo_network.
   cd apollo-service-db
   make upi       # Levanta el contenedor en segundo plano (detached)
   make migrate   # Ejecuta las migraciones para crear las tablas
   Verificación:
   El contenedor apollo-db debe estar corriendo (puerto 5432).
   Debe existir la red apollo_network.
2. Backend API (apollo-service-api)
   Configuración Previa (.env): Asegúrate de que el archivo .env apunte al nombre del contenedor de la base de datos y no a una IP remota.
   DB_HOST=apollo-db
   DB_NAME=apollo_db
   POSTGRES_DB=apollo_db
   Api Service (apollo-service-api)
   Configuración Previa (src/app.js):
   // Configuraciones de la app
   const allowedOrigins = [
   'http://localhost:4200',
   'http://localhost:3000',
   'http://localhost:4001',  //agregar puerto 4001
   'https://apolloasesorias.com',
   'https://www.apolloasesorias.com',
   'https://qa.apolloasesorias.com',
   'https://www.qa.apolloasesorias.com',
   'https://api.apolloasesorias.com',
   'https://api-qa.apolloasesorias.com'
   ];

Configuración Previa ultimas lineas de docker-compose.yml para agregar en la misma red docke (pegar desde la linea 60).
networks:
dokploy-network
apollo_network #Se añade esta linea para agregar a network docker
networks:
dokploy-network:
external: true
apollo_network: #Se añade esta linea para agregar a network docker
external: true #Se añade esta linea para agregar a network docker
Ejecución: Es crítico usar docker compose up --build para asegurar que la API se conecte a la red correcta (apollo_network) y tenga los orígenes CORS actualizados.
cd apollo-service-api

# Asegura que el docker-compose.yml tenga 'networks: - apollo_network'

docker-compose up -d --build
Notas Importantes:
La API corre en el puerto 4000.
Logs importantes: docker logs -f apollo-api 3. Frontend Web App (apollo-service-app)
Configuración Previa (src/environments/environment.ts): El frontend debe apuntar a la API local, no a QA.
**export** **const** environment = {
production: **false**,
apiUrl: "http://localhost:4000/api", _// Asegurar este valor_
_// ..._
};
Ejecución:
cd apollo-service-app
docker compose up -d --build
Acceso:
La aplicación estará disponible en http://localhost:4001.
Estructura de Base de Datos
El sistema utiliza PostgreSQL. A continuación se listan las tablas principales del esquema public:
Usuarios y Perfiles
users: Tabla central de autenticación (ID, email, password hash).
roles: Roles del sistema (admin, tutor, user).
user_roles: Relación N:M entre usuarios y roles.
profile: Información básica del perfil (nombre, ciudad, biografía).
tutor_profile: Información específica para tutores (tarifa, experiencia).
user_status: Estados de cuenta (active, suspended, etc.).
Sesiones y Tutorías
sessions: Registro de clases/sesiones agendadas.
session_status: Estados de una sesión (scheduled, completed, cancelled).
sessions_history: Histórico de cambios en sesiones.
availability: Horarios disponibles de los tutores.
Académico
topics: Materias principales/Áreas de conocimiento.
subtopics: Sub-materias específicas.
tutor_services: Servicios ofrecidos por el tutor.
tutor_service_subtopics: Relación de servicios con temas específicos.
Pagos y Facturación
payments: Registro de transacciones.
invoices: Facturas generadas.
payment_methods: Métodos de pago guardados.
withdrawals: Solicitudes de retiro de dinero (para tutores).
tutor_bank_details: Datos bancarios de tutores.
Sistema y Configuración
app_settings: Configuraciones globales.
notifications: Notificaciones para usuarios.
audit_log / deletion_audit_log: Logs de auditoría y seguridad.
schema_migrations: Control de versiones de migraciones.
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
