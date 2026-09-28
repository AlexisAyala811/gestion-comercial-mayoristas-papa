````md
# Estilo arquitectónico

Se seleccionó una arquitectura de tipo monolito modular, apoyada en principios de Clean Architecture, con el objetivo de mantener una sola aplicación desplegable, pero organizada en módulos funcionales claramente definidos. Esta decisión mejora la mantenibilidad, facilita la evolución del negocio y permite escalar de forma controlada sin romper la cohesión general del sistema.

## Resumen ejecutivo

- Un único sistema desplegable, pero modular por dominio.
- Separación clara entre reglas de negocio, casos de uso y tecnología.
- Módulos independientes para catálogo, ventas, pagos y usuarios.
- Bajo acoplamiento con proveedores externos mediante interfaces y adaptadores.
- Base sólida para crecimiento gradual sin migración completa de arquitectura.

## Diagrama de arquitectura

```mermaid
flowchart LR
    %% Capas
    subgraph CL["Capa de clientes"]
        U1[Cliente]
        U2[Vendedor]
        U3[Administrador]
    end

    subgraph UI["Capa de presentación"]
        FE[Portal Web / Frontend]
    end

    subgraph APP["Capa de aplicación y negocio"]
        API[API / Backend]
        M1[Catálogo]
        M2[Carrito]
        M3[Pedidos]
        M4[Pagos]
        M5[Usuarios]
    end

    subgraph DATA["Capa de persistencia e infraestructura"]
        DB[(Base de datos)]
        MQ[(Servicios auxiliares)]
    end

    subgraph EXT["Integraciones externas"]
        PAY[Pasarela de pagos]
        SMS[Notificaciones]
    end

    %% Flujo principal
    U1 --> FE
    U2 --> FE
    U3 --> FE

    FE --> API
    API --> M1
    API --> M2
    API --> M3
    API --> M4
    API --> M5

    M1 --> DB
    M2 --> DB
    M3 --> DB
    M4 --> DB
    M5 --> DB

    M4 --> PAY
    M3 --> SMS

    %% Estilos
    classDef user fill:#E3F2FD,stroke:#1565C0,stroke-width:1.5px,color:#0D47A1;
    classDef ui fill:#E8F5E9,stroke:#2E7D32,stroke-width:1.5px,color:#1B5E20;
    classDef app fill:#FFF3E0,stroke:#EF6C00,stroke-width:1.5px,color:#E65100;
    classDef data fill:#F3E5F5,stroke:#6A1B9A,stroke-width:1.5px,color:#4A148C;
    classDef ext fill:#FCE4EC,stroke:#C2185B,stroke-width:1.5px,color:#880E4F;

    class U1,U2,U3 user;
    class FE ui;
    class API,M1,M2,M3,M4,M5 app;
    class DB,MQ data;
    class PAY,SMS ext;
```

## Principales componentes

- Cliente: consulta productos, realiza compras y gestiona su orden.
- Vendedor: administra ventas, stock y catálogo.
- Administrador: supervisa operaciones, usuarios y configuración del sistema.
- Frontend: interfaz web para la interacción con los usuarios.
- API / Backend: coordina la lógica de negocio y la comunicación entre módulos.
- Módulos:
  - Catálogo
  - Carrito
  - Pedidos
  - Pagos
  - Usuarios
- Base de datos: persistencia central de información.
- Pasarela de pagos: servicio externo para procesamiento financiero.
- Notificaciones: integración para alertas y confirmaciones.

## Principios de diseño aplicados

- Monolito modular: una sola aplicación desplegable con dominios funcionales separados.
- Clean Architecture: independencia entre reglas de negocio y detalles técnicos.
- Bajo acoplamiento: cada módulo interactúa mediante contratos definidos.
- Escalabilidad controlada: posibilidad de crecer por funcionalidad sin afectar la base del sistema.
- Mantenibilidad: cambios del negocio o tecnología se gestionan de forma más segura.

Este estilo arquitectónico ofrece un equilibrio adecuado entre simplicidad operativa y capacidad de evolución, siendo una opción sólida para un sistema comercial de mayoristas con crecimiento progresivo.
````