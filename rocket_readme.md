# **Rocket Readme**
# **Lineamientos formales para Desarrollo de Software**

## **1. Sobre la planificación e implementación**
Rocket organiza el trabajo en quarters (Q1, Q2, Q3, Q4). Cada quarter contiene un conjunto de features y hallazgos (errores, defectos, fallos) debidamente priorizado(a)s, que representan capacidades, actualizaciones y/o mejoras del producto.

Cada feature se identifica como:
**F{número_de_quarter}.{número_de_feature}**
Ejemplo: **F4.1**

## **2. Sobre las definiciónes de negocio**
**LAS EPICAS DEBEN ESTAR DEFINIDAS EN ESTE FORMATO ANTES DE COMENZAR DESARROLLO**

Cada feature debe incluir:
- **Código** (código interno según nomenclatura)
- **Título de la Épica**
- **Descripción general**
- **Objetivo de negocio** (el porqué es necesaria, o el valor agregado)
- **Flujo(s) de usuario(s)** (paso a paso funcional en detalle)
- **Requerimientos funcionales y no funcionales** (opcional)
- **Criterios de aceptación (definidos con BDD)**
- **Supuestos, dependencias y restricciones** (opcional)

## **3. Sobre la metodología BDD y criterios de aceptación (AC)**
La definición es responsabilidad del equipo de negocio, con apoyo de líderes de tecnología.

### **Consideraciones para definir y desarrollar AC**
Los criterios se redactan estrictamente bajo el formato:
- **Dado** (contexto inicial)
- **Cuando** (acción o evento)
- **Entonces** (resultado esperado)

Los criterios de aceptación deben:
- Ser verificables y medibles.
- Cubrir todos los caminos funcionales relevantes.
- Ser acordados por negocio, QA y líderes de tecnología.

💡 *Los desarrolladores implementarán exclusivamente lo especificado en los criterios de aceptación.*

💡 *El tablero de trabajo se organiza en tareas derivadas de dichos criterios.*

💡 *Cada criterio de aceptación debe convertirse en una (preferido) o varias tareas.*

### **Evidencias de cumplimiento de ACs**
Al completar un criterio, el desarrollador debe subir evidencia obligatoria:
- Video de validación, o documento paso a paso con capturas claras.

Las evidencias deben demostrar que el criterio se cumple en ambiente de desarrollo.

### **Validación de ACs**
**QA valida primero:**
- Confirma cumplimiento del AC.
- Realiza pruebas funcionales.
- Documenta cualquier error con evidencia detallada.

**Negocio valida segundo:**
- Asegura que el comportamiento cumple los objetivos funcionales.

## **4. Sobre la calidad en los productos desarrollados**
Se contemplan los hallazgos estándar de un SDLC genérico (error, defecto, fallo o actualización).

### **Hallazgo:** 
Una observación documentada que indica una desviación, anomalía, riesgo o situación relevante que requiere análisis.

### **Defecto:**
Imperfección en un artefacto de software que puede causar un fallo durante la ejecución.

### **Error:**
Acción humana incorrecta que produce un defecto o interpretación incorrecta de requisitos.

### **Fallo:**
Manifestación de un defecto cuando el sistema no cumple con el comportamiento esperado.

### **Actualizaciones:**
Modificaciones controladas para corregir defectos, mejorar funcionalidades o prevenir problemas futuros.

## **5. Marco de clasificación de hallazgos QA para el Sprint Backlog**
QA no clasifica por intuición, sino por **evidencia observable y trazabilidad**.

Un hallazgo primero es hallazgo, luego se clasifica objetivamente como error, defecto, fallo o actualización.

### **Normalización de hallazgos**
Todo hallazgo QA debe contener:
- ¿Qué se observó? (comportamiento real)
- ¿Qué se esperaba? (según requisito, AC o contrato)
- ¿Dónde ocurre? (entorno, versión)
- ¿Cómo reproducirlo? (paso a paso)
- Evidencia (screenshots, video, trazas)
- Prioridad
- Riesgo
- Impacto

Para clasificar un hallazgo, siga el diagrama de flujo.

## **Fuentes**
ISO 19011:2018 – Guidelines for auditing management systems.
ISO/IEC/IEEE 24765:2017 – Systems and Software Engineering Vocabulary.
IEEE Std 610.12-1990 – Standard Glossary of Software Engineering Testing.
ISTQB (2023). Glossary of Testing Terms.
ISO/IEC 25010:2011 – Systems and Software Quality Models.
IEEE Std 1219-1998 – Software Maintenance.
ISO/IEC 14764:2006 – Software Life Cycle Processes – Maintenance.
Reason, J. (1990). *Human Error*. Cambridge University Press.
Sommerville, I. (2016). *Software Engineering* (10th ed.). Pearson.
Laprie, J.-C. (1992). *Dependability: Basic Concepts and Terminology*. Springer.
Galin, D. (2018). *Software Quality Assurance: From Theory to Implementation*. Pearson.
Pressman, R. S., & Maxim, B. R. (2020). *Software Engineering: A Practitioner’s Approach*. McGraw-Hill.

## **About the team**
- @MartinDelg (CEO)
- @Rocket (CTO)
- @Jose Eduardo Tirado Verbel (Dev)
- @Hernan Marzola (Dev)
- @María Paula P. (QA)

## **Fundamentación**
- Agile (Agile Software Development)
- Scrumban (Scrum y Kanban)
- BDD (Behavior-Driven Development)

## **Resources**
- GitHub
