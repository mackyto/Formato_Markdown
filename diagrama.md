```mermaid
classDiagram
    direction TB

    class ID {
        <<abstract>>
        - int id
        + getId() int
    }

    class Cliente {
        - String nombre
        - List~Pedido~ historial
        + realizarPedido(Pedido p)
    }

    class Pedido {
        - Date fecha
        - String estado
        - List~LineaPedido~ lineas
        + calcularTotal() double
    }

    class LineaPedido {
        - int cantidad
        - Producto producto
        + calcularSubtotal() double
    }

    class Producto {
        - String nombre
        - double precio
    }

    %% Relación de Herencia (Especialización)
    ID <|-- Cliente
    ID <|-- Pedido

    %% Otras Relaciones
    Cliente "1" o-- "0..*" Pedido : Agregación
    Pedido "1" *-- "1..*" LineaPedido : Composición
    LineaPedido "0..*" --> "1" Producto : Asociación
