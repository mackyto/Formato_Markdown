```mermaid
classDiagram
    direction TB

    class Cliente {
        - int id
        - String nombre
        - List~Pedido~ historial
        + realizarPedido(Pedido p) void
    }

    class Pedido {
        - int id
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

    %% Relaciones basadas en la lógica de negocio
    Cliente "1" o-- "0..*" Pedido : Agregación (el pedido sobrevive al cliente)
    Pedido "1" *-- "1..*" LineaPedido : Composición (las líneas mueren con el pedido)
    LineaPedido "0..*" --> "1" Producto : Asociación (referencia de catálogo)
