# 🚀 Plataforma Apollo: Documentación del Modelo de Negocio

Este documento describe el modelo de negocio, los procesos operativos y la estructura funcional de la plataforma **Apollo**, diseñada para conectar a estudiantes con tutores expertos.

---

## 1. Resumen Ejecutivo
Apollo es una plataforma de **marketplace** de servicios educativos que facilita la conexión entre personas que buscan aprender (**Estudiantes**) y expertos dispuestos a enseñar (**Tutores**). El sistema gestiona todo el ciclo de vida de la tutoría: desde la búsqueda y agendamiento, hasta la realización de la video llamada y el procesamiento seguro de los pagos.

---

## 2. Modelo de Negocio
El modelo de negocio de Apollo se basa en la intermediación de servicios educativos con un esquema de comisiones por transacción.

### 2.1 Propuesta de Valor
*   **Para el Estudiante:** Acceso centralizado a una amplia red de tutores verificados en diversas áreas de conocimiento (Software, Idiomas, Ciencias, etc.), con herramientas integradas de agenda y video conferencia.
*   **Para el Tutor:** Una plataforma profesional para ofrecer sus servicios, gestionar su disponibilidad, automatizar el cobro y construir una reputación digital verificable.

### 2.2 Fuentes de Ingresos
1.  **Comisión por Transacción:** La plataforma retiene un porcentaje (configurado por defecto en el sistema al **10%**) del valor total de cada sesión pagada por el estudiante.
2.  **Gestión de Retiros:** Los tutores pueden solicitar retiros a sus cuentas bancarias, proceso que puede conllevar tarifas administrativas configurables.

---

## 3. Actores y Roles del Sistema


| Rol | Responsabilidad Principal |
| :--- | :--- |
| **Estudiante** | Usuario final que consume los servicios y califica a los tutores. |
| **Tutor** | Expertos que ofrecen servicios y gestionan su propia agenda/tarifas. |
| **Administrador** | Gestión técnica, financiera y operativa total de la plataforma. |
| **Moderador** | Verificación de perfiles, documentos y resolución de disputas. |

### Detalle de Capacidades
*   **Estudiante:** Búsqueda avanzada, reserva y pago de sesiones, acceso a historial y calificación de servicio.
*   **Tutor:** Onboarding riguroso (documentación y video), gestión de perfil profesional, creación de servicios específicos (ej. *“Clase de Java Avanzado”*) y panel financiero.

---

## 4. Procesos Core del Negocio

### 4.1 Ciclo de Vida de la Tutoría
1.  **Búsqueda:** Localización mediante filtros de especialidad.
2.  **Solicitud:** Selección de horario y solicitud de sesión.
3.  **Confirmación y Pago:** El pago se procesa por adelantado y queda en custodia (**escrow**).
4.  **Ejecución:** Conexión mediante la sala de video integrada.
5.  **Finalización:** Calificación del servicio y liberación de fondos a la billetera del tutor (menos la comisión).

### 4.2 Verificación de Confianza
*   Validación de identidad mediante documentos oficiales.
*   Verificación de antecedentes académicos.
*   Aprobación manual de perfiles antes de ser públicos.

### 4.3 Gestión Financiera
*   **Pasarelas de Pago:** Integración con PayPal, Tarjetas de Crédito, PSE/Nequi.
*   **Billetera Virtual:** Visualización de saldo en tiempo real y registro de cuentas bancarias para retiros.

---

## 5. Áreas de Conocimiento
La plataforma soporta categorías jerárquicas para una escalabilidad ilimitada:

*   **Temas (Topics):** Grandes áreas como *Desarrollo de Software, Matemáticas, Idiomas*.
*   **Subtemas (Subtopics):** Especialidades como *Frontend, Cálculo Diferencial, Inglés de Negocios*.
