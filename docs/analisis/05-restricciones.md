# Restricciones del Proyecto

## Aplicación móvil de gestión comercial de mayoristas de papa

Las siguientes restricciones condicionan el diseño y la implementación de la solución, ya que establecen límites tecnológicos, operativos y funcionales que deben respetarse durante el desarrollo del sistema.

| Código | Restricción | Implicación arquitectónica |
|---|---|---|
| R01 | La primera versión operará en tablets Android y debe admitir conectividad irregular. | La aplicación debe utilizar una interfaz adaptable, almacenamiento local cifrado y sincronización diferida. |
| R02 | El registro de pesos se realizará manualmente durante el piloto. | El flujo de registro debe ser rápido, secuencial y permitir correcciones trazables antes del cierre del cargamento. |
| R03 | La base de datos central será la fuente oficial de operaciones y saldos. | La caché solo almacenará información temporal y podrá reconstruirse cuando sea necesario. |
| R04 | La capacidad de la inteligencia artificial dependerá de la cantidad, continuidad y calidad del historial disponible. | La IA operará por etapas: recolección y validación de datos, identificación de tendencias y patrones, y predicción con rango y confianza cuando exista evidencia suficiente. |
| R05 | Los datos de cada negocio deben permanecer aislados. | El sistema debe aplicar autorización por rol y por negocio en todos los servicios y consultas. |
| R06 | El MVP no incluirá facturación electrónica, GPS, pasarela de pagos ni balanzas integradas. | Se mantendrán interfaces versionadas que permitan incorporar estas integraciones en versiones futuras. |
| R07 | La solución debe ajustarse al presupuesto y a la capacidad operativa del proyecto. | Se priorizarán servicios administrados y un despliegue gradual, evitando complejidad innecesaria durante las primeras etapas. |