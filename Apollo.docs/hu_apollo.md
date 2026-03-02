# **HU Apollo – Historias de Usuario**

A continuación se documentan todas las Historias de Usuario tal como fueron enviadas, **sin eliminar contenido**, pero con **mejoras en títulos, estructura y negrillas** para mayor legibilidad.

---

# **Dashboard y Visualización de Datos**

## **HU-01: Mejorar la visualización de la distribución por país**
**Como** Administrador de Apollo, **quiero** visualizar la distribución de usuarios por país mediante una gráfica optimizada en el dashboard, **para** interpretar rápidamente el alcance geográfico de la plataforma.

### **Criterios de Aceptación:**
- **Dado** que el Administrador se encuentra en la pantalla principal del Dashboard,
- **Cuando** carga la sección **"Distribución por País"**, 
- **Entonces** el sistema debe mostrar un gráfico (mapa interactivo o barras) que agrupe a tutores y estudiantes por país con etiquetas claras y legibles.

---

# **Configuración Regional y Moneda**

## **HU-02: Definición de moneda según ubicación del usuario**
**Como** Usuario (Estudiante o Tutor), **quiero** visualizar los precios en mi moneda local o en una moneda estándar, **para** entender el valor real de los servicios sin hacer cálculos manuales.

### **Criterios de Aceptación:**
- **Dado** que un usuario ingresa a la plataforma desde un país específico (detectado por IP o perfil), **cuando** visualiza un servicio o consultoría, **entonces** el precio se muestra en la moneda local si está soportada.
- **Dado** que el sistema no puede detectar el país o la moneda no está soportada, **cuando** se muestra el precio, **entonces** el sistema debe mostrar el valor en **USD (por defecto)**.

---

# **Gestión de Servicios (Tutores)**

## **HU-03: Restricción de visibilidad para tutores no aprobados**
**Como** Tutor en proceso de registro, **quiero** que el sistema restrinja mi vista de servicios activos, **para** no confundirme con funcionalidades que aún no puedo operar.

### **Criterios de Aceptación:**
- **Dado** un tutor con estado **"Pendiente"** o **"Rechazado"**, **cuando** intenta acceder a la lista de servicios ofertados, **entonces** el sistema no debe mostrar ningún registro ni permitir la creación de nuevos servicios.

*(Ver imagen: Martin Delgado está rechazado y aparece)*

---

## **HU-04: Fijación de precios en Dólares (USD)**
**Como** Tutor aprobado, **quiero** establecer el valor de mis servicios en USD, **para** estandarizar mi tarifa internacional.

### **Criterios de Aceptación:**
- **Dado** que el tutor está en el formulario **"Crear Servicio"**, **cuando** ingresa el monto en **"Valor"**, **entonces** el sistema debe guardar dicho monto explícitamente como **USD**.

---

## **HU-05: Soporte para decimales en el valor del servicio**
**Como** Tutor, **quiero** poder ingresar valores decimales, **para** definir tarifas exactas (ej: 15.00 USD).

### **Criterios de Aceptación:**
- El sistema debe permitir valores como `15.00` sin errores.
- Debe mostrar la moneda por defecto.
- Nota: si se usa USD por defecto, no es necesario mostrar dos decimales en precios enteros (ej: 15 USD, 120 USD).

---

## **HU-06: Visualización de Categoría en listado de servicios**
**Como** Tutor, **quiero** ver la categoría asignada a mis servicios, **para** organizar y distinguir mis ofertas.

### **Criterios de Aceptación:**
- La tabla "Mis Servicios" debe incluir una columna visible llamada **"Categoría"**.

---

# **Administración de Tutores**

## **HU-07 y HU-08: Inactivación segura de Tutores (Soft Delete)**
**Como** Administrador, **quiero** inactivar tutores en lugar de eliminarlos, **para** preservar historial y evitar errores.

### **Criterios de Aceptación:**
- El modal debe mostrar explícitamente el **Nombre del Tutor**.
- Al confirmar, el tutor pasa a estado **"Inactivo"**, sin eliminar el registro.

---

# **Perfil y Documentación**

## **HU-09: Simplificación de UI al subir imagen de perfil**
**Como** Usuario, **quiero** una interfaz limpia al subir mi foto, **para** saber claramente qué hacer.

### **Criterios de Aceptación:**
- Al abrir "Subir Imagen", solo deben mostrarse **Seleccionar archivo / Subir** o **Cancelar**, eliminando botones heredados como "Guardar Cambios".

*(Esto ya fue implementado, pero la HU debe documentarse)*

---

## **HU-10: Modal propio y corrección de carga de Cédula/Certificados**
**Como** Tutor, **quiero** subir mis documentos mediante una ventana emergente funcional, **para** completar mi validación.

### **Criterios de Aceptación:**
- Al intentar subir PDF, debe abrirse directamente el buscador de archivos.
- Si el archivo es válido, debe cargarse y visualizarse correctamente.
- No debe mostrar "Error al subir PDF" sin justificación.
- Errores válidos pueden incluir: archivo > **5 MB**, extensión incorrecta, etc.

---

# **HU-11: Integración de API de Países y Ciudades**
**Como** Usuario, **quiero** seleccionar país y ciudad desde listas estandarizadas, **para** asegurar la exactitud de mi ubicación.

### **Criterios de Aceptación:**
- Al seleccionar un país, el campo ciudad debe actualizarse automáticamente con las ciudades correspondientes.
- Aplica para **todos los roles**.

*(Ver imagen)*

---

# **Agenda y Disponibilidad**

## **HU-12: Identificación visual de disponibilidad**
**Como** Estudiante buscando tutor, **quiero** ver resaltados los días disponibles, **para** identificar cuándo puedo agendar.

### **Criterios de Aceptación:**
- Los días con disponibilidad deben tener un color llamativo.
- Debe diferenciarse el día seleccionado del resto.
- Considerar accesibilidad: usuarios mayores de 35 años.
- Aunque el servicio dura 10 minutos, los intervalos visibles son de 30 minutos.

---

## **HU-13: Gestión dinámica de disponibilidad y corrección horaria**
**Como** Tutor y Sistema, **quiero** que la disponibilidad se actualice automáticamente, **para** evitar bloqueos innecesarios.

### **Criterios de Aceptación:**
- Si una reserva pendiente no se confirma en X horas, el horario debe liberarse.
- La hora registrada debe coincidir **exactamente** con la hora seleccionada (sin desfase horario).

---

# **Notificaciones y UI General**

## **HU-14: Notificaciones por correo electrónico**
**Como** Usuario, **quiero** recibir notificaciones por correo, **para** estar informado sin entrar a la plataforma.

### **Criterios de Aceptación:**
- Cuando se crea, reprograma o cancela una consultoría, el sistema debe enviar correo a Tutor y Estudiante.

---

## **HU-15: Estandarización de estilos en botones**
**Como** Usuario, **quiero** que los botones tengan apariencia consistente, **para** una experiencia más profesional.

### **Criterios de Aceptación:**
- Todos los botones deben cumplir el UI Kit: color, borde, tipografía, hover.
- Ejemplo: el modal de "Cancelar / Guardar" debe usar estilos correctos.

---
