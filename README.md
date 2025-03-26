# calculador cientifica.

suma resta multiplica divide

def mostrar_menu():
    print("\nCalculadora Científica")
    print("1.  Suma")
    print("2.  Resta")
    print("3.  Multiplicación")
    print("4.  División")
    print("5.  Potencia")
    print("6.  Raíz Cuadrada")
    print("7.  Valor Absoluto")
    print("8.  Factorial")
    print("9.  Permutación (nPk)")
    print("10. Combinación (nCk)")
    print("11. Seno (radianes)")
    print("12. Coseno (radianes)")
    print("13. Tangente (radianes)")
    print("14. Arcoseno")
    print("15. Arcocoseno")
    print("16. Arcotangente")
    print("17. Seno Hiperbólico")
    print("18. Coseno Hiperbólico")
    print("19. Tangente Hiperbólica")
    print("20. Logaritmo Natural")
    print("21. Logaritmo Base 10")
    print("22. Constante Pi")
    print("23. Constante e")
    print("0.  Salir")

def obtener_numero(mensaje):
    while True:
        try:
            return float(input(mensaje))
        except ValueError:
            print("Entrada inválida. Introduce un número.")

def suma():
    a = obtener_numero("Primer número: ")
    b = obtener_numero("Segundo número: ")
    print(f"Resultado: {a + b}")

def resta():
    a = obtener_numero("Primer número: ")
    b = obtener_numero("Segundo número: ")
    print(f"Resultado: {a - b}")

def multiplicacion():
    a = obtener_numero("Primer número: ")
    b = obtener_numero("Segundo número: ")
    print(f"Resultado: {a * b}")

def division():
    a = obtener_numero("Numerador: ")
    while True:
        b = obtener_numero("Denominador: ")
        if b != 0:
            break
        print("Error: División por cero")
    print(f"Resultado: {a / b}")

def potencia():
    a = obtener_numero("Base: ")
    b = obtener_numero("Exponente: ")
    print(f"Resultado: {a ** b}")

def raiz_cuadrada():
    while True:
        num = obtener_numero("Número: ")
        if num >= 0:
            break
        print("Error: No se puede calcular raíz de número negativo")
    print(f"Resultado: {math.sqrt(num)}")

def valor_absoluto():
    num = obtener_numero("Número: ")
    print(f"Resultado: {abs(num)}")

def factorial():
    while True:
        num = int(obtener_numero("Número entero no negativo: "))
        if num >= 0:
            break
        print("Error: Factorial de número negativo")
    print(f"Resultado: {math.factorial(num)}")

def permutacion():
    while True:
        n = int(obtener_numero("n (total elementos): "))
        k = int(obtener_numero("k (elementos a elegir): "))
        if n >= k >= 0:
            break
        print("Error: n debe ser mayor o igual a k y ambos no negativos")
    print(f"Resultado: {math.perm(n, k)}")

def combinacion():
    while True:
        n = int(obtener_numero("n (total elementos): "))
        k = int(obtener_numero("k (elementos a elegir): "))
        if n >= k >= 0:
            break
        print("Error: n debe ser mayor o igual a k y ambos no negativos")
    print(f"Resultado: {math.comb(n, k)}")

def trigonometrica(func, nombre):
    while True:
        angulo = obtener_numero(f"{nombre} (radianes): ")
        try:
            resultado = func(angulo)
            print(f"Resultado: {resultado}")
            break
        except ValueError:
            print(f"Error: Valor inválido para {nombre.lower()}")

def inversa_trig(func, nombre):
    while True:
        valor = obtener_numero(f"Valor para {nombre}: ")
        try:
            resultado = func(valor)
            print(f"Resultado: {resultado} radianes")
            break
        except ValueError:
            print(f"Error: Valor fuera de rango para {nombre}")

funciones = {
    '1': suma,
    '2': resta,
    '3': multiplicacion,
    '4': division,
    '5': potencia,
    '6': raiz_cuadrada,
    '7': valor_absoluto,
    '8': factorial,
    '9': permutacion,
    '10': combinacion,
    '11': lambda: trigonometrica(math.sin, "Seno"),
    '12': lambda: trigonometrica(math.cos, "Coseno"),
    '13': lambda: trigonometrica(math.tan, "Tangente"),
    '14': lambda: inversa_trig(math.asin, "Arcoseno"),
    '15': lambda: inversa_trig(math.acos, "Arcocoseno"),
    '16': lambda: inversa_trig(math.atan, "Arcotangente"),
    '17': lambda: trigonometrica(math.sinh, "Seno Hiperbólico"),
    '18': lambda: trigonometrica(math.cosh, "Coseno Hiperbólico"),
    '19': lambda: trigonometrica(math.tanh, "Tangente Hiperbólica"),
    '20': lambda: logaritmo(math.log, "Natural"),
    '21': lambda: logaritmo(math.log10, "Base 10"),
    '22': lambda: print(f"Pi: {math.pi}"),
    '23': lambda: print(f"e: {math.e}")
}

def logaritmo(func, tipo):
    while True:
        num = obtener_numero(f"Número para logaritmo {tipo}: ")
        if num > 0:
            break
        print("Error: Logaritmo de número no positivo")
    print(f"Resultado: {func(num)}")

def main():
    while True:
        mostrar_menu()
        opcion = input("Selecciona una opción: ")
        
        if opcion == '0':
            print("¡Hasta luego!")
            break
            
        if opcion in funciones:
            try:
                funciones[opcion]()
            except Exception as e:
                print(f"Ocurrió un error: {str(e)}")
        else:
            print("Opción inválida. Inténtalo de nuevo.")

if __name__ == "__main__":
    main()
