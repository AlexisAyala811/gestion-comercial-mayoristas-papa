# Modelo de Información del Sistema

## Aplicación móvil de gestión comercial de mayoristas de papa

El siguiente modelo representa las principales entidades de información que participan en la gestión comercial del mayorista y las relaciones existentes entre ellas.

El modelo contempla información del negocio, usuarios, proveedores, compradores, vehículos, recepción y pesaje, productos y lotes, operaciones comerciales y auditoría.

## Diagrama del Modelo de Información

```mermaid
flowchart LR

    %% =====================================================
    %% CONTEXTO DEL NEGOCIO
    %% =====================================================

    subgraph CONTEXTO["🏢 NEGOCIO Y ACCESO"]

        NEGOCIO["🏪 NEGOCIO
        ─────────────
        Identificación
        Sede
        Parámetros
        Estado"]

        USUARIO["👤 USUARIO
        ─────────────
        Identidad
        Rol
        Credenciales
        Estado"]

    end


    %% =====================================================
    %% RELACIONES COMERCIALES
    %% =====================================================

    subgraph RELACIONES["🤝 RELACIONES COMERCIALES"]

        PROVEEDOR["🚚 PROVEEDOR
        ─────────────
        Nombre
        Teléfono
        Procedencia
        Condiciones de pago"]

        COMPRADOR["🧑‍💼 COMPRADOR
        ─────────────
        Contacto
        Departamento
        Crédito
        Acuerdos"]

    end


    %% =====================================================
    %% TRANSPORTE
    %% =====================================================

    subgraph TRANSPORTE["🚛 TRANSPORTE"]

        VEHICULO["🚚 VEHÍCULO Y CONDUCTOR
        ─────────────
        Placa
        Conductor
        Origen
        Destino
        Llegada
        Salida"]

    end


    %% =====================================================
    %% RECEPCIÓN Y PESAJE
    %% =====================================================

    subgraph RECEPCION_PESAJE["⚖️ RECEPCIÓN Y PESAJE"]

        RECEPCION["📥 RECEPCIÓN Y PESAJE
        ─────────────
        Fecha
        Variedades
        Sacos
        Peso total
        Promedio
        Estado / cierre"]

        DETALLE["⚖️ DETALLE DE PESAJE
        ─────────────
        Secuencia
        Variedad
        Peso
        Fecha y hora
        Observación
        Estado"]

    end


    %% =====================================================
    %% PRODUCTOS E INVENTARIO
    %% =====================================================

    subgraph INVENTARIO["📦 PRODUCTOS E INVENTARIO"]

        PRODUCTO_LOTE["🥔 PRODUCTO Y LOTE
        ─────────────
        Variedad
        Calidad
        Procedencia
        Cantidad
        Costo
        Saldo"]

    end


    %% =====================================================
    %% OPERACIONES COMERCIALES
    %% =====================================================

    subgraph OPERACIONES["💰 OPERACIONES Y LIQUIDACIÓN"]

        OPERACION["💳 OPERACIÓN Y LIQUIDACIÓN
        ─────────────
        Compra / Venta
        Precio
        Flete
        Estiba
        Adelantos
        Cuotas
        Pagos
        Saldo"]

    end


    %% =====================================================
    %% TRAZABILIDAD
    %% =====================================================

    subgraph CONTROL["🛡️ CONTROL Y TRAZABILIDAD"]

        AUDITORIA["📋 AUDITORÍA
        ─────────────
        Usuario
        Fecha y hora
        Acción
        Cambio realizado
        Estado"]

    end


    %% =====================================================
    %% RELACIONES DEL NEGOCIO
    %% =====================================================

    NEGOCIO -->|"tiene"| USUARIO
    NEGOCIO -->|"registra"| PROVEEDOR
    NEGOCIO -->|"registra"| COMPRADOR
    NEGOCIO -->|"gestiona"| PRODUCTO_LOTE
    NEGOCIO -->|"controla"| OPERACION


    %% =====================================================
    %% RELACIONES DE RECEPCIÓN
    %% =====================================================

    PROVEEDOR -->|"entrega mercadería"| RECEPCION
    VEHICULO -->|"transporta"| RECEPCION
    USUARIO -->|"registra"| RECEPCION

    RECEPCION -->|"contiene"| DETALLE
    RECEPCION -->|"genera"| PRODUCTO_LOTE


    %% =====================================================
    %% OPERACIONES COMERCIALES
    %% =====================================================

    PRODUCTO_LOTE -->|"participa en"| OPERACION

    PROVEEDOR -->|"compra / pago"| OPERACION
    COMPRADOR -->|"venta / cobro"| OPERACION

    VEHICULO -->|"flete / despacho"| OPERACION

    USUARIO -->|"registra operación"| OPERACION


    %% =====================================================
    %% AUDITORÍA
    %% =====================================================

    USUARIO -->|"genera"| AUDITORIA
    OPERACION -.->|"cambios y anulaciones"| AUDITORIA
    RECEPCION -.->|"correcciones"| AUDITORIA


    %% =====================================================
    %% ESTILOS
    %% =====================================================

    classDef negocio fill:#E3F2FD,stroke:#1565C0,stroke-width:2px,color:#0D47A1;
    classDef usuario fill:#E8EAF6,stroke:#3949AB,stroke-width:2px,color:#1A237E;
    classDef comercial fill:#E8F5E9,stroke:#2E7D32,stroke-width:2px,color:#1B5E20;
    classDef transporte fill:#FFF3E0,stroke:#EF6C00,stroke-width:2px,color:#E65100;
    classDef recepcion fill:#FFF8E1,stroke:#F9A825,stroke-width:2px,color:#795548;
    classDef inventario fill:#F1F8E9,stroke:#558B2F,stroke-width:2px,color:#33691E;
    classDef operacion fill:#FCE4EC,stroke:#C2185B,stroke-width:2px,color:#880E4F;
    classDef auditoria fill:#ECEFF1,stroke:#455A64,stroke-width:2px,color:#263238;

    class NEGOCIO negocio;
    class USUARIO usuario;
    class PROVEEDOR,COMPRADOR comercial;
    class VEHICULO transporte;
    class RECEPCION,DETALLE recepcion;
    class PRODUCTO_LOTE inventario;
    class OPERACION operacion;
    class AUDITORIA auditoria;
```

## Descripción del modelo

El **Negocio** constituye el contexto principal de la información y permite asociar usuarios, proveedores, compradores, productos y operaciones comerciales.

El **Usuario** representa al mayorista o encargado que interactúa con la aplicación. Cada usuario dispone de un rol y permisos definidos, y sus acciones pueden ser registradas mediante mecanismos de auditoría.

El **Proveedor** participa principalmente en el proceso de recepción y compra de mercadería, mientras que el **Comprador** participa en las operaciones de venta, despacho, cobro y crédito.

La entidad **Vehículo y conductor** permite mantener información relacionada con el traslado de mercadería, tanto durante el ingreso de productos como durante los despachos.

La **Recepción y pesaje** representa el ingreso de mercadería al negocio. Una recepción contiene múltiples registros de **Detalle de pesaje**, donde se conserva individualmente el peso de cada saco.

Al finalizar la recepción, la información permite generar los **Productos y lotes** correspondientes, que posteriormente forman parte del inventario disponible.

La entidad **Operación y liquidación** representa las compras y ventas realizadas por el negocio y concentra información relacionada con precio, flete, estiba, adelantos, cuotas, pagos y saldos.

Finalmente, la **Auditoría** permite mantener trazabilidad sobre operaciones, modificaciones, correcciones y anulaciones realizadas por los usuarios.

## Flujo principal de información

El flujo general del modelo puede resumirse de la siguiente manera:

**Proveedor → Recepción → Detalle de pesaje → Producto/Lote → Operación comercial**

Para una compra:

**Proveedor → Recepción → Pesaje → Lote → Compra → Pago o saldo pendiente**

Para una venta:

**Producto/Lote → Venta → Comprador → Cobro o saldo pendiente**

Todas las operaciones relevantes quedan asociadas al usuario responsable y pueden generar registros de auditoría.