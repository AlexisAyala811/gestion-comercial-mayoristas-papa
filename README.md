# Gestión Comercial de Mayoristas de Papa

## Descripción

Proyecto académico orientado al desarrollo de una aplicación móvil para mejorar la gestión comercial de los comerciantes mayoristas de papa.

La solución busca reemplazar progresivamente el uso de cuadernos y registros dispersos mediante una plataforma que centralice las principales operaciones comerciales del negocio.

## Problema

Actualmente, parte de la información relacionada con recepción de mercadería, pesaje, compras, ventas, fletes, estiba, inventario, pagos, cobranzas y saldos puede registrarse manualmente.

Esta forma de trabajo dificulta conocer de manera rápida y precisa:

- Stock disponible.
- Costos de compra.
- Saldos pendientes.
- Pagos realizados.
- Cobranzas.
- Resultados de las operaciones.
- Historial de precios.

## Objetivo general

Desarrollar una aplicación móvil/tablet que mejore la gestión comercial de los comerciantes mayoristas de papa mediante la digitalización, automatización y análisis inteligente de sus principales procesos de negocio.

## Funcionalidades principales

- Gestión de usuarios y roles.
- Gestión de clientes y proveedores.
- Registro de recepción de mercadería.
- Pesaje saco por saco.
- Gestión de productos y variedades.
- Registro de compras.
- Cálculo de fletes y costos.
- Gestión de adelantos.
- Control de inventario.
- Registro de ventas y despachos.
- Gestión de cuentas por pagar.
- Gestión de cuentas por cobrar.
- Registro de pagos y cobranzas.
- Control de caja.
- Alertas y notificaciones.
- Reportes comerciales.
- Auditoría de operaciones.
- Operación temporal sin conexión.
- Sincronización posterior con la plataforma central.
- Analítica e inteligencia artificial.

## Actores principales

### Mayorista

Tiene acceso completo a las funcionalidades del sistema y puede gestionar y supervisar integralmente las operaciones comerciales.

### Encargado

Puede reemplazar temporalmente al mayorista y registrar operaciones autorizadas relacionadas principalmente con pesaje, compras y ventas.

## Arquitectura

La solución utiliza una arquitectura organizada en capas:

1. Presentación.
2. Lógica de negocio.
3. Datos.

La aplicación móvil se comunica con el backend mediante una API REST.

La aplicación no accede directamente a la base de datos central.

## Tecnologías

### Aplicación móvil

- React Native.
- Expo.
- TypeScript.
- Expo Router.

### Backend

- NestJS 12.
- TypeScript.
- API REST versionada bajo `/api/v1`.

### Base de datos

- PostgreSQL 17.
- TypeORM.

### Analítica e inteligencia artificial

El componente analítico utilizará progresivamente el historial de operaciones para:

- Analizar la evolución de precios.
- Identificar tendencias.
- Detectar patrones.
- Analizar variedad, calidad, procedencia y volumen.
- Generar estimaciones de precios cuando exista información suficiente.
- Mostrar rangos y niveles de confianza.

## Estructura del proyecto

```text
gestion-comercial-mayoristas-papa/
│
├── analytics/
│
├── backend/
│
├── docs/
│   ├── analisis/
│   │   ├── 01-actores.md
│   │   ├── 02-historias-de-usuario.md
│   │   ├── 03-requisitos-funcionales.md
│   │   ├── 04-atributos-de-calidad.md
│   │   ├── 05-restricciones.md
│   │   └── 06-drivers-arquitectonicos.md
│   │
│   ├── arquitectura/
│   │   ├── arquitectura-inicial.md
│   │   ├── despliegue.md
│   │   └── sincronizacion.md
│   │
│   └── modelo-datos/
│       └── modelo-informacion.md
│
├── mobile/
│
├── .gitignore
└── README.md