# **HU Apollo – Documentación de Historias de Usuario**

A continuación se presentan las Historias de Usuario (HU) para mejoras en el Dashboard, configuración regional, gestión de servicios, administración, perfil, agenda y notificaciones del sistema Apollo.

---

## **Dashboard y Visualización de Datos**

### **HU-01: Mejorar la visualización de la distribución por país**
**Como** Administrador de Apollo, **quiero** visualizar la distribución de usuarios por país mediante una gráfica optimizada en el dashboard, **para** interpretar rápidamente el alcance geográfico de la plataforma.

**Criterios de Aceptación:**
- **Dado** que el Administrador se encuentra en la pantalla principal del Dashboard,
- **Cuando** carga la sección "Distribución por País",
- **Entonces** el sistema debe mostrar un gráfico (mapa interactivo o barras) que agrupe tutores y estudiantes por país con etiquetas claras y legibles.

---

## **Configuración Regional y Moneda**

### **HU-02: Definición de moneda según ubicación del usuario**
**Como** Usuario (Estudiante o Tutor), **quiero** visualizar los precios en mi moneda local o en una moneda estándar, **para** entender el valor real sin cálculos manuales.

**Criterios de Aceptación:**
- **Dado** que el usuario ingresa desde un país específico,
- **Cuando** visualiza un servicio,
- **Entonces** el precio debe mostrarse en la moneda local si está soportada.

- **Dado** que no se puede detectar país o moneda no soportada,
- **Entonces** se debe mostrar el valor en **USD por defecto**.

---

## **Gestión de Servicios (Tutores)**

### **HU-03: Restricción de visibilidad para tutores no aprobados**
**Como** Tutor en proceso de registro, **quiero** que el sistema restrinja mi vista de servicios activos, **para** no confundirme con funcionalidades no disponibles.

**Criterios de Aceptación:**
- **Dado** un tutor con estado "Pendiente" o "Rechazado",
- **Cuando** intenta acceder a servicios ofertados,
- **Entonces** no debe mostrarse ningún registro ni permitir creación de servicios.

---

### **HU-04: Fijación de precios en Dólares (USD)**
**Como** Tutor aprobado, **quiero** establecer el valor de mis servicios en USD, **para** estandarizar mi tarifa internacionalmente.

**Criterios de Aceptación:**
- **Dado** que está en "Crear Servicio",
- **Cuando** ingresa el monto,
- **Entonces** el sistema debe guardarlo explícitamente como USD.

---

### **HU-05: Soporte para decimales en el valor del servicio**
**Como** Tutor, **quiero** ingresar decimales en el precio de mis servicios, **para** definir tarifas exactas.

**Criterios de Aceptación:**
- Debe aceptar valores como **15.00**, **120.5**, etc.
- Debe mostrarse la moneda por defecto.
- No es obligatorio mostrar dos decimales en valores enteros.

---

### **HU-06: Visualización de Categoría en listado de servicios**
**Como** Tutor, **quiero** ver la categoría de mis servicios en la tabla, **para** organizarlos fácilmente.

**Criterios de Aceptación:**
- La tabla "Mis Servicios" debe contener una columna **Categoría** visible.

---

## **Administración de Tutores**

### **HU-07 y HU-08: Inactivación segura de Tutores (Soft Delete)**
**Como** Administrador, **quiero** inactivar tutores en lugar de eliminarlos, **para** preservar historial y evitar errores.

**Criterios de Aceptación:**
- El modal debe mostrar el **Nombre del Tutor**.
- Al confirmar, el estado del tutor debe cambiar a **Inactivo**, sin borrar el registro.

---

## **Perfil y Documentación**

### **HU-09: Simplificación de UI al subir imagen de perfil**
**Como** Usuario, **quiero** una interfaz limpia al subir mi foto, **para** evitar confusión.

**Criterios de Aceptación:**
- Al abrir "Subir Imagen", solo deben aparecer **Seleccionar archivo / Subir** o **Cancelar**.

---

### **HU-10: Modal propio y corrección de carga de Cédula/Certificados**
**Como** Tutor, **quiero** subir mis documentos mediante un modal funcional, **para** completar mi validación.

**Criterios de Aceptación:**
- Al subir PDF, debe abrirse el selector de archivos inmediatamente.
- Si el archivo es válido, debe almacenarse y mostrarse sin errores.
- Solo debe mostrar error si existe fundamento (peso máx. 5 MB, extensión inválida, etc.).

---

## **HU-11: Integración de API de Países y Ciudades**
**Como** Usuario, **quiero** seleccionar mi ubicación desde listas estandarizadas, **para** asegurar precisión.

**Criterios de Aceptación:**
- Al seleccionar un país, el campo ciudad debe actualizarse con las ciudades correspondientes.

---

## **Agenda y Disponibilidad**

### **HU-12: Identificación visual de disponibilidad**
**Como** Estudiante, **quiero** ver resaltados los días disponibles, **para** agendar fácilmente.

**Criterios de Aceptación:**
- Los días con disponibilidad deben mostrarse con color distintivo.
- Debe permitir seleccionar la franja según duración del servicio.
- Considerar accesibilidad (usuarios de +35 años).

---

### **HU-13: Gestión dinámica de disponibilidad y corrección horaria**
**Como** Tutor/Sistema, **quiero** que la disponibilidad se gestione dinámicamente, **para** evitar errores.

**Criterios de Aceptación:**
- Si una reserva pendiente no se confirma en X horas → liberar horario.
- La hora registrada en DB debe coincidir exactamente con la seleccionada.

---

## **Notificaciones y UI General**

### **HU-14: Notificaciones por correo electrónico**
**Como** Usuario, **quiero** recibir correos sobre mis citas, **para** estar informado.

**Criterios de Aceptación:**
- Al crear, reprogramar o cancelar una cita → debe enviarse email con detalles.

---

### **HU-15: Estandarización de estilos en botones**
**Como** Usuario, **quiero** consistencia en los botones, **para** una experiencia profesional.

**Criterios de Aceptación:**
- Todos los botones deben seguir el UI Kit: color, tipografía, borde, hover.
- Ejemplo: El modal de "Cancelar / Guardar" debe usar estilos adecuados.

---
