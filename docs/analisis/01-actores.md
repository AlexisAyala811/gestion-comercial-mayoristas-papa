# Actores del Sistema

## Aplicación móvil de gestión comercial de mayoristas de papa

La solución reconoce dos actores principales que interactúan directamente con la aplicación: el **Mayorista** y el **Encargado**.

| Actor | Necesidad principal | Responsabilidades en el sistema |
|---|---|---|
| Mayorista | Gestionar y supervisar integralmente el negocio. | Tiene acceso completo a todas las secciones y acciones del sistema: recepción y pesaje, compras, ventas, inventario, cuentas, caja, reportes, tendencias, patrones, pronósticos, configuración y administración de usuarios. |
| Encargado | Reemplazar operativamente al mayorista cuando este se encuentra ausente. | Durante la ausencia del mayorista, puede registrar el pesaje saco por saco e ingresar datos de compras y ventas. No accede a inventario, cuentas, caja, reportes, inteligencia artificial, configuración ni administración de usuarios. |

## Descripción de los actores

### Mayorista

Es el actor principal del sistema. Administra y supervisa las operaciones comerciales del negocio y dispone de acceso completo a los módulos de la aplicación.

### Encargado

Es el usuario que reemplaza temporalmente al mayorista cuando este se encuentra ausente. Su acceso está limitado al registro de pesaje, compras y ventas, mientras que los cálculos y efectos autorizados son procesados automáticamente por el sistema.