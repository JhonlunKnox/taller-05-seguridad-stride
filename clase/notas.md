# 🗒️ Registro de Trabajo en Clase - Taller 5: Evaluación de Seguridad con STRIDE

## 📆 Fecha de la sesión

3 de septiembre de 2026 _(ajustar si la sesión fue en otra fecha)_

## 👥 Integrantes presentes

- Juan Pablo Luna Zuleta
- Alejandro Riveros
- Martín Ortega

## 🧠 Actividades realizadas en clase

Arrancamos revisando la guía paso a paso y las seis categorías de STRIDE. Lo primero que discutimos fue cuál flujo de EdukIT analizar. El ejemplo de la guía ya trabaja el acceso de estudiantes a cursos, así que decidimos tomar otro de los elementos sensibles del enunciado: **el procesamiento de pagos de suscripción con la pasarela externa**. Nos pareció el más interesante porque es el único flujo del caso base donde el límite de confianza se cruza hacia un tercero que no controlamos, y eso obliga a pensar amenazas que no aparecen en un flujo puramente interno.

Con eso definido dibujamos el DFD en el tablero y después lo pasamos a Mermaid para dejarlo en el repositorio. Identificamos dos procesos internos (módulo de suscripciones y servicio de conciliación), dos almacenes (base de suscripciones y medios de pago, y registro de transacciones), el actor externo estudiante y la pasarela como entidad externa fuera de la zona de confianza. Sobre esos elementos aplicamos las seis categorías una por una.

La discusión más larga fue con el webhook de confirmación de pago. Al principio lo habíamos clasificado como Tampering, porque estábamos pensando en que se modificaba el mensaje. Al revisarlo con el docente quedó claro que si el atacante genera el mensaje desde cero y el servidor no verifica el origen, la amenaza es de suplantación de la pasarela, o sea Spoofing. Esa distinción nos sirvió para las demás filas: Tampering es alterar algo que ya existe, Spoofing es hacerse pasar por alguien.

También nos costó no caer en el error de escribir amenazas genéricas. La primera versión de la fila de denegación de servicio decía "el sistema se puede caer", que no dice nada. La reescribimos apuntando al endpoint concreto y al momento del año en que el impacto es mayor.

**Herramientas usadas:** tablero, Mermaid para el DFD, Excel para la tabla, Docker para levantar Juice Shop en local.

## 🧪 Retos completados en OWASP Juice Shop

Levantamos la instancia con `docker run --rm -p 3000:3000 bkimminich/juice-shop` y alcanzamos a completar los cuatro retos, no solo el mínimo de uno:

| Reto | Categoría | Qué pasó | Fila de la tabla con la que se relaciona |
|---|---|---|---|
| 1 — Login bypass | Spoofing | Con `' OR 1=1--` en el campo de correo entramos como el primer usuario de la tabla, que resultó ser el administrador. La aplicación concatena el input en la consulta. | T7 |
| 2 — Precio manipulado | Tampering | Interceptamos la solicitud desde la pestaña Network y cambiamos el precio antes de confirmar. El servidor lo aceptó sin recalcular contra el catálogo. | T2 |
| 3 — Carrito ajeno | Information Disclosure | Cambiando el ID en `/rest/basket/6` a `/rest/basket/1` vimos el carrito de otro usuario. Es un IDOR clásico: hay autenticación pero no verificación de propiedad del recurso. | T4 |
| 4 — Panel de administración | Elevation of Privilege | Entramos a `/#/administration` como usuario normal. El rol solo se validaba en el frontend para ocultar el enlace del menú. | T6 |

Lo que más nos quedó del laboratorio es que en tres de los cuatro retos el problema no era la autenticación sino la **autorización**: el sistema sabía perfectamente quién éramos y de todas formas nos dejó hacer cosas que no nos correspondían. Eso cambió la forma en que redactamos las mitigaciones, que pasaron de "validar" a "revalidar en el servidor en cada solicitud".

## 🧩 Boceto inicial del modelo

DFD del flujo de pagos, tal como quedó después de la sesión:

```mermaid
flowchart LR
    estudiante(["🧑 Estudiante"])
    pasarela(["💳 Pasarela de Pagos (tercero)"])

    subgraph backend["Backend EdukIT (zona de confianza)"]
        auth["P0: Sistema de Autenticación"]
        subs["P1: Módulo de Suscripciones"]
        conc["P2: Servicio de Conciliación"]
        dbsub[("D1: BD de Suscripciones y Medios de Pago")]
        dblog[("D2: Registro de Transacciones")]
    end

    estudiante -->|"F0: credenciales"| auth
    estudiante -->|"F1: plan + monto"| subs
    subs -->|"F2: redirección de pago"| pasarela
    pasarela -->|"F3: webhook de confirmación"| subs
    subs -->|"F4: estado de la suscripción"| dbsub
    subs -->|"F5: evento de pago"| dblog
    subs -->|"F6: recibo"| estudiante
    conc -->|"F7: lectura para cuadre"| dblog
```

## 🔁 Tareas definidas para complementar el taller

| Tarea asignada | Responsable | Fecha estimada |
|---|---|---|
| Pasar la tabla de EdukIT al formato de la plantilla oficial y priorizar | Juan Pablo | 04/09 |
| DFD del proceso del cliente real y catálogo de elementos | Martín | 05/09 |
| Reconocimiento pasivo autorizado sobre el dominio institucional | Alejandro | 05/09 |
| Tabla STRIDE del cliente real (10 filas, las 6 categorías) | Los tres | 06/09 |
| Redacción del informe y referencias | Juan Pablo | 07/09 |

## ⚠️ Observaciones para la Parte 2

Quedó claro que no podemos repetir ninguna de las técnicas de Juice Shop contra el sistema del cliente. Para la columna de controles existentes vamos a usar reconocimiento pasivo sobre lo que ya es público, más lo que el cliente nos confirme directamente en reunión, y lo que no alcancemos a verificar lo dejamos marcado como pendiente en vez de inventarlo.

---

_Este documento resume el trabajo colaborativo realizado durante la sesión del Taller 5 en el curso AREM - Universidad de La Sabana._
