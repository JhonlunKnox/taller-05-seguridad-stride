# 📚 Referencias Bibliográficas del Taller

Este archivo contiene las fuentes consultadas para el desarrollo del taller, tanto para el componente técnico (marco STRIDE y laboratorio) como para la investigación complementaria sobre buenas prácticas de seguridad en el sector de educación superior.

## 🔖 Taller

_Taller 5 - Evaluación de Seguridad con STRIDE_

---

## 📚 Referencias utilizadas

### Marco STRIDE y modelado de amenazas

1. Shostack, A. *Threat Modeling: Designing for Security*. Wiley, 2014. Obra de referencia del marco STRIDE y de la metodología de modelado de amenazas sobre diagramas de flujo de datos.
2. Microsoft. "Microsoft Threat Modeling Tool threats — STRIDE model". Microsoft Learn. [https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats](https://learn.microsoft.com/en-us/azure/security/develop/threat-modeling-tool-threats). Fecha de consulta: 07/09/2026.
3. Vega F., C. A. *Guía Paso a Paso: Evaluación de Seguridad con STRIDE*. Curso Arquitectura Empresarial, Universidad de La Sabana, 2026. Material del taller.

### Laboratorio práctico

4. OWASP Foundation. "OWASP Juice Shop Project". [https://owasp.org/www-project-juice-shop/](https://owasp.org/www-project-juice-shop/). Fecha de consulta: 03/09/2026. Aplicación deliberadamente vulnerable usada para los cuatro retos de la Parte 1, ejecutada en instancia local con Docker.
5. OWASP Foundation. *OWASP Top 10:2025*. [https://owasp.org/Top10/2025/](https://owasp.org/Top10/2025/). Fecha de consulta: 07/09/2026. Versión vigente de la lista; se usó la categoría A01 (Broken Access Control) para clasificar los hallazgos de autorización de Juice Shop y su equivalente en el cliente.

### Normas y marcos de seguridad de la información

6. ISO/IEC. *ISO/IEC 27001:2022 — Information security, cybersecurity and privacy protection — Information security management systems — Requirements*. Organización Internacional de Normalización, 2022.
7. ISO/IEC. *ISO/IEC 27002:2022 — Information security controls*. Organización Internacional de Normalización, 2022. Controles de clasificación de la información, control de acceso, gestión de identidades y registro de eventos usados como vocabulario de las mitigaciones propuestas.
8. National Institute of Standards and Technology. *The NIST Cybersecurity Framework (CSF) 2.0*. NIST CSWP 29, febrero de 2024. [https://www.nist.gov/cyberframework](https://www.nist.gov/cyberframework). Fecha de consulta: 06/09/2026. Se utilizó la función *Govern* para argumentar que la brecha del cliente es de gobierno del dato y no de controles técnicos.

### Marco normativo colombiano y sector educación superior

9. Congreso de la República de Colombia. *Ley 1581 de 2012 — Por la cual se dictan disposiciones generales para la protección de datos personales*. [https://www.funcionpublica.gov.co/eva/gestornormativo/norma.php?i=49981](https://www.funcionpublica.gov.co/eva/gestornormativo/norma.php?i=49981). Fecha de consulta: 06/09/2026.
10. Presidencia de la República de Colombia. *Decreto 1377 de 2013*, hoy incorporado en el *Decreto Único Reglamentario 1074 de 2015*. Reglamentación parcial de la Ley 1581 de 2012.
11. Congreso de la República de Colombia. *Ley 1273 de 2009 — De la protección de la información y de los datos*. Marco de delitos informáticos que sustenta la restricción de no ejecutar pruebas activas contra sistemas reales sin autorización escrita.
12. Superintendencia de Industria y Comercio. *Guía sobre el tratamiento de datos personales en el contexto universitario*. Bogotá D.C., agosto de 2026. Disponible en la Sede Electrónica de la SIC: [https://sedeelectronica.sic.gov.co](https://sedeelectronica.sic.gov.co). Fecha de consulta: 07/09/2026. Fuente principal de la investigación complementaria por su especificidad para instituciones de educación superior.
13. El Observatorio de la Universidad Colombiana. "SIC presenta Guía para el tratamiento de datos personales en el contexto universitario". [https://www.universidad.edu.co/sic-presenta-guia-para-el-tratamiento-de-datos-personales-en-el-contexto-universitario/](https://www.universidad.edu.co/sic-presenta-guia-para-el-tratamiento-de-datos-personales-en-el-contexto-universitario/). 12 de agosto de 2026. Fecha de consulta: 07/09/2026. Consultada como resumen de prensa de la guía anterior.

### Plataforma del cliente (Microsoft 365)

14. Microsoft. "Learn about sensitivity labels — Microsoft Purview". Microsoft Learn. [https://learn.microsoft.com/en-us/purview/sensitivity-labels](https://learn.microsoft.com/en-us/purview/sensitivity-labels). Fecha de consulta: 06/09/2026. Base de la mitigación propuesta para C5.
15. Microsoft. "Data loss prevention policies — Microsoft Purview". Microsoft Learn. [https://learn.microsoft.com/en-us/purview/dlp-policy-reference](https://learn.microsoft.com/en-us/purview/dlp-policy-reference). Fecha de consulta: 06/09/2026.
16. Microsoft. "Data loss prevention policies for Microsoft Power Platform". Microsoft Learn. [https://learn.microsoft.com/en-us/power-platform/admin/wp-data-loss-prevention](https://learn.microsoft.com/en-us/power-platform/admin/wp-data-loss-prevention). Fecha de consulta: 06/09/2026. Base de la mitigación propuesta para C9.

### Insumos propios del proyecto

17. Riveros, A.; Luna Zuleta, J. P.; Ortega, M. *Caracterización del cliente y Visión de Arquitectura — Jefatura de Cultura de Innovación y Servicio*. Corte 1, curso AREM, Universidad de La Sabana, 2026. Fuente del catálogo de actores, del alcance y de las restricciones institucionales citadas en el informe.
18. Molina Rodríguez, J. A. Profesional de Experiencia y Servicio, Jefatura de Cultura de Innovación y Servicio, Universidad de La Sabana. Entrevistas y reuniones de seguimiento, 2026. Fuente primaria de la descripción del proceso de conciliación y del estado actual de los controles.

---

## 📌 Nota sobre el uso de herramientas

Fuente asistida por IA: Claude (Anthropic), septiembre de 2026. Se usó como apoyo para estructurar la tabla STRIDE y revisar la redacción del informe. El análisis del sistema del cliente, los supuestos y la priorización de riesgos son propios del equipo y se contrastaron con la información levantada directamente con la unidad.

---

_Este archivo forma parte de la entrega académica del curso AREM - Universidad de La Sabana._
