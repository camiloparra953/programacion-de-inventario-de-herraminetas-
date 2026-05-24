# ================================
# SISTEMA DE INVENTARIO (HERRAMIENTAS)
# ================================

# Función para calcular la cantidad a pedir
def calcular_pedido(stock_actual, stock_minimo):
    return max(0, stock_minimo - stock_actual)


# Función para mostrar pedidos
def generar_lista_pedidos(inventario):
    print("\n LISTA DE PEDIDOS:\n")
    
    hay_pedidos = False

    for codigo, nombre, stock_actual, stock_minimo in inventario:
        cantidad = calcular_pedido(stock_actual, stock_minimo)
        
        if cantidad > 0:
            print(f" Código: {codigo}")
            print(f"   Herramienta: {nombre}")
            print(f"   Stock actual: {stock_actual}")
            print(f"   Stock mínimo: {stock_minimo}")
            print(f"    Cantidad a pedir: {cantidad}\n")
            hay_pedidos = True

    if not hay_pedidos:
        print(" No se necesitan pedidos. Todo el inventario está completo.")


# Inventario de herramientas
inventario = [
    ["H001", "Martillo", 8, 15],
    ["H002", "Destornillador", 20, 10],
    ["H003", "Taladro", 3, 7],
    ["H004", "Llave inglesa", 12, 12],
    ["H005", "Sierra", 2, 6]
]

# Ejecutar sistema
print(" SISTEMA DE CONTROL DE HERRAMIENTAS")
generar_lista_pedidos(inventario)
