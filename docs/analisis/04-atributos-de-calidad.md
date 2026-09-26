# Atributos de Calidad

## Aplicación móvil de gestión comercial de mayoristas de papa

Los atributos de calidad definen cómo debe comportarse el sistema, además de las funcionalidades que ofrece. Estos atributos orientan las decisiones de arquitectura y permiten evaluar aspectos como rendimiento, disponibilidad, seguridad, integridad y mantenibilidad.

| Código | Atributo | Escenario de calidad |
|---|---|---|
| AC01 | Rendimiento | Durante la descarga, el sistema debe guardar cada peso localmente en menos de 1 segundo. Las consultas centrales deben responder en menos de 3 segundos para el 95 % de las solicitudes con 20 usuarios concurrentes durante el piloto. |
| AC02 | Disponibilidad | Ante una interrupción de Internet de hasta 2 horas, la aplicación debe continuar registrando pesos localmente. El servicio central debe alcanzar una disponibilidad mensual objetivo de 99,5 %. |
| AC03 | Integridad | Si una operación se reintenta hasta cinco veces, el sistema debe conservar un único registro confirmado y aplicar una sola vez los efectos sobre inventario y saldos. |
| AC04 | Seguridad | Cuando un usuario intente consultar información perteneciente a otro negocio, el sistema debe denegar el acceso y registrar el intento. El aislamiento debe verificarse en todos los endpoints protegidos. |
| AC05 | Usabilidad | Después de una capacitación breve, al menos el 90 % de los usuarios piloto debe poder registrar y cerrar un cargamento sin asistencia y sin pérdida de pesos. |
| AC06 | Escalabilidad | Al duplicarse la concurrencia de 20 a 40 usuarios, el sistema debe permitir agregar una nueva instancia del backend y conservar el objetivo de respuesta establecido en AC01. |
| AC07 | Mantenibilidad | Cuando se modifique una regla de estiba, el cambio debe realizarse en el módulo de costos sin afectar la interfaz de pesaje ni las reglas de cuentas, verificando el comportamiento mediante pruebas de regresión. |
| AC08 | Recuperación | Ante la pérdida de la base de datos central, el sistema debe poder restaurarse con un objetivo RPO de 24 horas y RTO de 4 horas. Los pesos aún no sincronizados dependerán del almacenamiento local de la tablet. |