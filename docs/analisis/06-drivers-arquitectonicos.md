# Drivers Arquitectónicos

## Aplicación móvil de gestión comercial de mayoristas de papa

Los drivers arquitectónicos representan las necesidades de negocio, atributos de calidad y restricciones que influyen directamente en las decisiones de arquitectura de la solución.

| Código | Driver y origen | Decisión e influencia arquitectónica |
|---|---|---|
| DA01 | Continuidad — RF21, AC02, R01 | Se utilizará persistencia local y una cola de sincronización para garantizar que la captura de pesos y otras operaciones autorizadas continúen aun cuando falle la conexión a Internet. |
| DA02 | Integridad — RF06, RF06B, RF08, AC03 | Se utilizarán identificadores únicos, transacciones e idempotencia para evitar registros duplicados y asegurar que una misma operación no modifique más de una vez el inventario o los saldos. |
| DA03 | Aislamiento — RF01, RF22, AC04, R05 | La autenticación, autorización por negocio y auditoría se aplicarán en el backend. La interfaz móvil no será el único mecanismo de control de acceso. |
| DA04 | Crecimiento — AC01, AC06, R07 | El backend se diseñará sin estado para permitir escalamiento horizontal. Se podrá utilizar balanceo de carga y caché para catálogos y consultas frecuentes, sin convertir la caché en fuente oficial de saldos. |
| DA05 | IA progresiva — RF19, R04 | El proceso analítico estará separado de las transacciones principales. Primero se acumularán y validarán datos, luego se identificarán tendencias y patrones, y las predicciones se habilitarán cuando exista información suficiente y de calidad. |
| DA06 | Evolución — AC07, R06 | Se utilizará inicialmente un monolito modular con API versionada y adaptadores de integración, de manera que futuras integraciones no accedan directamente a la base de datos. |
| DA07 | Recuperación — AC08, R03 | Se implementarán respaldos automáticos y procedimientos de restauración probados. Una réplica o caché no reemplazará las copias de seguridad de la base de datos central. |