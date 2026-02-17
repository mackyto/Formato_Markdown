```mermaid
classDiagram
    direction TB

    %% Definición de la Superclase
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

    %% Relación de Herencia: Cliente y Pedido EXTIENDEN de ID
    ID <|-- Cliente
    ID <|-- Pedido

    %% Relaciones de Agregación y Composición
    Cliente "1" o-- "0..*" Pedido : tiene/mantiene
    Pedido "1" *-- "1..*" LineaPedido : compuesto por
    LineaPedido "0..*" --> "1" Producto : referencia a
