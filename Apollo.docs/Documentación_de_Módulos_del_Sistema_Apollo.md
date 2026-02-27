Este documento presenta un desglose técnico y funcional de los módulos que componen la plataforma Apollo.
1. Módulos del Núcleo (Core)
Estos módulos son la base del funcionamiento del sistema y gestionan aspectos transversales.
1.1 Gestión de Usuarios y Autenticación
Encargado de la seguridad, registro y perfiles de los actores del sistema.
API Modules: auth, users, roles, profiles.
Database Tables: users, roles, user_roles, profile.
Frontend:
Páginas: login, register, forgot-password.
Dashboard: Perfil de usuario (en student y tutor).
Funcionalidades:
Login/Registro (Email y Google OAuth).
Recuperación de contraseña.
Gestión de roles (RBAC).
1.2 Configuración del Sistema
Gestión de variables globales y ajustes de la plataforma.
API Modules: app-settings.
Database Tables: app_settings.
Frontend: Dashboard de Admin (admin/settings - inferido).
Funcionalidades:
Control de comisiones.
Feature flags (activar/desactivar pasarelas).
Parámetros de negocio (precios mínimos, monedas).
2. Módulo de Tutores y Servicios
Corazón de la oferta de valor de Apollo. Gestiona la información de los expertos y lo que ofrecen.
2.1 Perfil Profesional
API Modules: tutors, topics, documents.
Database Tables: tutor_profile, topics, subtopics, tutor_documents, professional_topics.
Frontend:
Páginas: tutor-profile (público).
Dashboard: tutor/profile, tutor/services.
Funcionalidades:
Carga de video de presentación.
Gestión de áreas de conocimiento (Topics).
Verificación de documentos (Cédula, Diplomas).
2.2 Disponibilidad y Agenda
API Modules: availability.
Database Tables: availability, availability_status.
Frontend: tutor/availability (Calendario interactivo).
Funcionalidades:
Configuración de slots horarios disponibles.
Bloqueo de horarios (vacaciones, ocupado).
3. Módulo de Sesiones y Clases
Gestiona el ciclo de vida de la interacción educativa.
3.1 Gestión de Sesiones
API Modules: sessions, video-calls.
Database Tables: sessions, session_status, sessions_history.
Frontend:
Dashboard: student/sessions, tutor/sessions.
Página: video-call/:id.
Funcionalidades:
Solicitud y confirmación de clases.
Historial de estados (Pendiente -> Confirmada -> Completada).
Sala de video conferencia integrada.
3.2 Calificaciones
API Modules: ratings.
Database Tables: ratings.
Frontend: Componentes de valoración en perfil y post-sesión.
Funcionalidades:
Rating de 1 a 5 estrellas.
Reseñas escritas.
Cálculo de promedios para reputación del tutor.
4. Módulo Financiero
Gestiona el flujo de dinero entre estudiantes, plataforma y tutores.
4.1 Pagos y Facturación
API Modules: payments.
Database Tables: payments, invoices, payment_methods, payment_status.
Frontend: payment-success, payment-cancel, Dashboard Financiero.
Funcionalidades:
Procesamiento de pagos de estudiantes.
Generación de invoices/recibos.
Cálculo de comisiones de la plataforma.
4.2 Billetera y Retiros
API Modules: withdrawals.
Database Tables: withdrawals, tutor_bank_details.
Frontend: tutor/wallet (Billetera).
Funcionalidades:
Visualización de saldo acumulado.
Registro de cuentas bancarias.
Solicitud y aprobación de retiros.
5. Módulos Transversales
5.1 Búsqueda (Search)
API Modules: search.
Database Tables: Índices Full-Text Search en users y topics.
Frontend: Página search (Buscador principal).
Funcionalidades:
Filtros avanzados (precio, valoración, tema).
Búsqueda por palabras clave.
5.2 Notificaciones
API Modules: notifications.
Database Tables: notifications.
Frontend: Componente de campana de notificaciones en el Header.
Funcionalidades:
Avisos en tiempo real (Socket.io / GetStream).
Emails transaccionales (confirmación de cita, pago exitoso).
