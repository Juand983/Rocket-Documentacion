\# Documentación del Sistema Apollo



Este documento describe el modelo de negocio, los procesos operativos y la estructura funcional de la plataforma Apollo, diseñada para conectar a estudiantes con tutores expertos.



\## 1. Resumen Ejecutivo

Apollo es una plataforma de “marketplace” de servicios educativos que facilita la conexión entre personas que buscan aprender (Estudiantes) y expertos dispuestos a enseñar (Tutores). El sistema gestiona todo el ciclo de vida de la tutoría: desde la búsqueda y agendamiento, hasta la realización de la video llamada y el procesamiento seguro de los pagos.



\## 2. Modelo de Negocio

El modelo de negocio de Apollo se basa en la intermediación de servicios educativos con un esquema de comisiones por transacción.



\### 2.1 Propuesta de Valor

\* \*\*Para el Estudiante:\*\* Acceso centralizado a una amplia red de tutores verificados en diversas áreas de conocimiento (Software, Idiomas, Ciencias, etc.), con herramientas integradas de agenda y video conferencia.

\* \*\*Para el Tutor:\*\* Una plataforma profesional para ofrecer sus servicios, gestionar su disponibilidad, automatizar el cobro y construir una reputación digital verificable.



\### 2.2 Fuentes de Ingresos

La principal fuente de ingresos es el cobro de comisiones por cada sesión de tutoría completada exitosamente.

\* \*\*Comisión por Transacción:\*\* La plataforma retiene un porcentaje (configurado por defecto en el sistema al 10%) del valor total de cada sesión pagada por el estudiante.

\* \*\*Gestión de Retiros:\*\* Los tutores acumulan saldo en la plataforma y pueden solicitar retiros a sus cuentas bancarias, proceso que también puede conllevar tarifas administrativas configurables.



\## 3. Actores y Roles del Sistema

El sistema identifica cuatro roles principales con permisos y responsabilidades diferenciadas:



\### 3.1 Estudiante (Usuario Regular)

Es el usuario final que consume los servicios.

Capacidades:

\* Búsqueda avanzada de tutores por tema, precio y calificación.

\* Visualización de perfiles detallados y disponibilidad.

\* Reserva y pago de sesiones.

\* Acceso a historial de sesiones y materiales compartidos.

\* Calificación y reseña del servicio recibido.



\### 3.2 Tutor

Expertos que ofrecen servicios educativos.

\* \*\*Onboarding:\*\* Proceso riguroso de registro que incluye carga de documentos de identidad, certificados profesionales y video de presentación.

Capacidades:

\* Gestión de perfil profesional (bio, experiencia, tarifa por hora).

\* Creación de servicios específicos (ej. “Clase de Java Avanzado”, “Asesoría de Tesis”).

\* Configuración de disponibilidad horaria flexible.

\* Gestión de solicitudes de sesión (aceptar/rechazar).

\* Panel financiero para ver ganancias y solicitar retiros.



\### 3.3 Administrador

Responsable de la gestión técnica y operativa total de la plataforma.



\### 3.4 Moderador

Rol enfocado en la calidad y seguridad de la comunidad.

Capacidades:

\* Verificación de documentos y perfiles de tutores nuevos.

\* Aprobación de videos de presentación.

\* Resolución de disputas básicas y moderación de contenido.



\## 4. Procesos Core del Negocio



\### 4.1 Ciclo de Vida de la Tutoría

1\. \*\*Búsqueda:\*\* El estudiante localiza un tutor mediante filtros de especialidad o subespecialidad.

2\. \*\*Solicitud:\*\* El estudiante selecciona un horario disponible y solicita la sesión.

3\. \*\*Confirmación y Pago:\*\* El pago se procesa por adelantado y queda en custodia (escrow) o en estado “pendiente”.

4\. \*\*Ejecución:\*\* En la fecha programada, ambos usuarios se conectan a través de la sala de video integrada en la plataforma.

5\. \*\*Finalización y Liberación:\*\* Al concluir la sesión, el estado cambia a completado. El estudiante califica al tutor y los fondos (menos la comisión) se liberan a la billetera virtual del tutor.



\### 4.2 Verificación de Confianza

\* Validación de identidad mediante documentos oficiales.

\* Verificación de antecedentes académicos o certificados cargados.

\* Aprobación manual de perfiles antes de que sean públicos en el buscador.



\### 4.3 Gestión Financiera

\* \*\*Pasarelas de Pago:\*\* Integración con múltiples proveedores (PayPal, Tarjetas de Crédito, PSE/Nequi).

\* \*\*Billetera del Tutor:\*\* Los tutores visualizan su saldo en tiempo real.

\* \*\*Retiros:\*\* Registro de cuentas bancarias para solicitar la transferencia de sus ganancias acumuladas.



\## 5. Áreas de Conocimiento

La plataforma está diseñada para ser multi-disciplinaria. Actualmente, su estructura soporta categorías jerárquicas:

\* \*\*Temas (Topics):\*\* Grandes áreas como Desarrollo de Software, Matemáticas, Idiomas.

\* \*\*Subtemas (Subtopics):\*\* Especialidades como Frontend, Cálculo Diferencial, Inglés de Negocios.



---



\## 🛠 Guía de Ejecución Local (Local Setup)

Esta documentación detalla los componentes del sistema Apollo, cómo ejecutarlo correctamente en un entorno local y la estructura de su base de datos.



Para levantar el sistema completo, se deben iniciar los servicios en el siguiente orden: \*\*Base de Datos -> API -> Frontend\*\*.



\### Requisitos Previos

\* Docker y Docker Compose

\* Make (opcional, pero recomendado)



\### 1. Base de Datos (apollo-service-db)

El servicio de base de datos PostgreSQL debe iniciarse primero ya que define la red compartida `apollo\_network`.



```bash

cd apollo-service-db

make upi       # Levanta el contenedor en segundo plano (detached)

make migrate   # Ejecuta las migraciones para crear las tablas



