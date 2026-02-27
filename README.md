Lineamientos formales para Desarrollo de Software
1. Sobre la planificación e implementación
Rocket organiza el trabajo en quarters (Q1, Q2, Q3, Q4). Cada quarter contiene un conjunto de features y hallazgos (errores, defectos, fallos) debidamente priorizado(a)s, que representan capacidades, actualizaciones y/o mejoras del producto.
Cada feature se identifica como:
F{número_de_quarter}.{número_de_feature} 
Ejemplo: F4.1
2. Sobre las definiciónes de negocio 
LAS EPICAS DEBEN ESTAR DEFINIDAS EN ESTE FORMATO ANTES DE COMENZAR DESARROLLO
Cada feature debe incluir:
Codigo (código interno según nomenclatura)
Titulo de la Epica
Descripción general
Objetivo de negocio (el porque es necesaria, o en su defecto el valor agregado)
Flujo(s) de usuario(s) (paso a paso funcional en detalle)
Requerimientos funcionales y no funcionales (opcional)
Criterios de aceptación (definidos con BDD)
Supuestos, dependencias y restricciones (opcional)
3. Sobre la métodología “Desarrollo basado en comportamientos (BDD) y criterios de aceptación (AC)”
La definición es responsabilidad del equipo de negocio, con apoyo de líderes de tecnología.
Consideraciones para definir y desarrollar AC
Los criterios se redactan estrictamente bajo el formato
**Dado** (contexto inicial)
**Cuando** (acción o evento)
**Entonces** (resultado esperado)
Los criterios de aceptación deben:
Ser verificables y medibles.
Cubrir todos los caminos funcionales relevantes.
Ser acordados por negocio, QA y líderes de tecnología.

💡Los desarrolladores implementarán exclusivamente lo especificado en los criterios de aceptación.

💡El tablero de trabajo se organiza en tareas derivadas de dichos criterios.

💡Cada criterio de aceptación debe convertirse en una (preferido) o varias tareas.

Evidencias de cumplimiento de ACs
Al completar un criterio, el desarrollador debe subir evidencia obligatoria:
Video de validación, o documento paso a paso con capturas claras.
Las evidencias deben demostrar que el criterio se cumple en ambiente de desarrollo.
Validación de ACs
QA valida primero:
Confirma cumplimiento del AC.
Realiza pruebas funcionales.
Documenta cualquier error con evidencia detallada (video o capturas).
Negocio valida segundo:
Asegura que el comportamiento cumple los objetivos funcionales.
4. Sobre la calidad en los productos desarrollados
Se contemplan los hallazgos estandares de un SDLC generico (error, defecto, fallo o actualización).
Hallazgo: Un hallazgo es una observación documentada identificada durante actividades de revisión, auditoría, pruebas o monitoreo, que indica una desviación, anomalía, riesgo o situación relevante que requiere análisis, pero que aún no ha sido clasificada como defecto o mejora.
Defecto:  Un defecto es una imperfección o anomalía en un artefacto de software (código, diseño, requisitos o documentación) que puede causar un fallo durante la ejecución del sistema.
Error:  Un error es una acción humana incorrecta que produce un resultado erróneo, como un defecto en el software o una interpretación incorrecta de los requisitos.
Fallo: Un fallo es la manifestación observable de un defecto durante la ejecución del software, cuando el sistema no cumple con su comportamiento esperado.
Actualizaciones: Las actualizaciones son modificaciones controladas aplicadas a un sistema de software con el objetivo de corregir defectos, mejorar funcionalidades, prevenir problemas futuros o adaptar el sistema a cambios del entorno.
5. Marco de clasificación de hallazgos QA para construcción del Sprint Backlog
QA no clasifica por intuición, clasifica por evidencia observable y trazabilidad.
Un hallazgo, no nace siendo error, defecto, fallo o actualización. Primero es un hallazgo, y luego se clasifica según criterios objetivos.
Normalización de hallazgos
Todo hallazgo QA debe contener mínimamente:
¿Qué se observó? (comportamiento real)
¿Qué se esperaba? (según requisito, criterio de aceptación, ó contrato)
¿Dónde ocurre?(entorno, versión)
¿Cómo reproducirlo? (pasos a paso)
Evidencia (screenshots, video, traces, logs)
Prioridad
Riesgo
Impacto
Para clasificar un hallazgo, siga el siguiente diagrama de flujo
!Normalización de hallazgos

Fuentes
ISO 19011:2018 – Guidelines for auditing management systems.
ISO/IEC/IEEE 24765:2017 – Systems and Software Engineering Vocabulary.
IEEE Std 610.12-1990 – Standard Glossary of Software Engineering Testing.
ISTQB (2023). Glossary of Testing Terms.
ISO/IEC 25010:2011 – Systems and Software Quality Models.
IEEE Std 1219-1998 – Software Maintenance.
ISO/IEC 14764:2006 – Software Life Cycle Processes – Maintenance.
Reason, J. (1990). Human Error. Cambridge University Press.
Sommerville, I. (2016). Software Engineering (10th ed.). Pearson.
Laprie, J.-C. (1992). Dependability: Basic Concepts and Terminology. Springer.
Galin, D. (2018). Software Quality Assurance: From Theory to Implementation. Pearson.
Pressman, R. S., & Maxim, B. R. (2020). Software Engineering: A Practitioner’s Approach. McGraw-Hill.
About the team
@MartinDelg (CEO)
@Rocket  (CTO)
@Jose Eduardo Tirado Verbel (Dev)
@Hernan Marzola (Dev)
@María Paula P. (QA)
Fundamentación
Agile (Agile Software Development)
Scrumban (Scrum y Kanban)
BDD (Behavior-Driven Development)
Resources
Github
