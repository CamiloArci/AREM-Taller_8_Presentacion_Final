# 📄 Resumen Ejecutivo del Proyecto Arquitectónico

## 🏢 Nombre del Cliente
Ataraxia Parkour — Gimnasio especializado en parkour, Bogotá, Colombia.

## 🎯 Objetivo General del Proyecto
El proyecto buscó analizar y documentar la arquitectura empresarial de Ataraxia Parkour, un gimnasio de parkour que opera con herramientas digitales mínimas (Excel Online y WhatsApp Business) y sin ningún sistema de información formal. El reto arquitectónico central fue identificar cómo una organización pequeña puede modernizar su operación de forma incremental, sin incurrir en costos elevados ni en cambios disruptivos. El valor aportado consiste en una propuesta de solución concreta, costeada y viable, que automatiza los procesos manuales críticos del negocio manteniendo las herramientas que el equipo ya conoce.

## 🧱 Vistas Arquitectónicas Cubiertas

| Vista                  | Alcance de la Solución                                                                 |
|------------------------|----------------------------------------------------------------------------------------|
| Procesos de Negocio    | Modelado de los tres macroprocesos: pago de clases, registro de sesiones y control de asistencia |
| Información / Datos    | Identificación de entidades: Estudiante, Paquete de clases y Asistencia; análisis de brechas en el manejo de datos sensibles |
| Aplicaciones / Sistemas| Mapeo de las dos únicas herramientas actuales (Excel Online y WhatsApp Business) y propuesta de nuevas aplicaciones (bot, app móvil, n8n) |
| Infraestructura        | Diagnóstico de dependencia total en nube de terceros (Microsoft 365 y Meta); propuesta de VPS propio con n8n |
| Seguridad              | Identificación de cuatro brechas críticas: sin RBAC, sin auditoría, sin backup formal y datos médicos sin cifrado |
| Cumplimiento Normativo | Señalamiento de riesgo por almacenamiento de datos de salud de estudiantes sin protección adicional, relevante bajo la Ley 1581 de Colombia |

## 🧩 Hallazgos Clave

- ❗ Toda la operación del gimnasio recae en un único archivo de Excel Online sin control de versiones ni roles diferenciados, convirtiéndolo en un punto único de falla.
- 🔄 No existe integración entre las herramientas actuales: el flujo de datos entre Excel y WhatsApp es completamente manual, generando riesgo permanente de errores y pérdida de información.
- 📌 Los datos médicos y de condición física de los estudiantes se almacenan sin cifrado ni protección adicional, lo que representa una brecha de seguridad y un riesgo de cumplimiento normativo.
- 📌 La arquitectura no tiene mecanismo de auditoría: es imposible saber quién modificó qué dato y cuándo dentro del Excel.
- 📌 No existen copias de seguridad propias del gimnasio; la continuidad del negocio depende completamente de la disponibilidad de Microsoft 365.

## 🚀 Recomendaciones Principales

- Implementar un **bot de WhatsApp Business** como canal de comunicación y validación de pagos con los estudiantes (~$10.000 COP/mes).
- Desplegar **n8n en un VPS** para automatizar el flujo de datos entre el bot, la base de datos y el Excel, eliminando el registro manual (~$25.000–$80.000 COP/mes).
- Desarrollar una **aplicación móvil privada** para que los profesores registren clases y descuenten saldo directamente, con base de datos en Firebase (~$2.100.000 COP, pago único).
- Migrar los datos históricos del Excel a la nueva arquitectura como parte de la implementación inicial (~$1.700.000 COP, pago único por automatización e implementación).
- Implementar roles de acceso diferenciados (RBAC) para separar los permisos del administrador de los de los profesores.
- Establecer una política de backup periódico de los datos fuera de la dependencia de Microsoft 365.

## 💡 Reflexión Final

Este ejercicio permitió al equipo aplicar de forma práctica los conceptos de arquitectura empresarial en un cliente real con restricciones concretas de presupuesto y capacidad técnica. El caso de Ataraxia Parkour demuestra que incluso organizaciones muy pequeñas enfrentan retos arquitectónicos significativos, y que las soluciones más valiosas no siempre son las más complejas: una arquitectura bien diseñada con herramientas de bajo costo puede transformar la operación de un negocio de forma sostenible. El equipo desarrolló habilidades de análisis estructurado, identificación de brechas, modelado de vistas y comunicación ejecutiva de soluciones tecnológicas adaptadas al contexto del cliente.

---

_Este resumen ejecutivo forma parte de la entrega final del curso AREM - Arquitectura Empresarial - Universidad de La Sabana._
