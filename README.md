# ProyectoModulo2-Lenguaje-de-Interfaz

# Keygen Básico


#Descripción del proyecto

El objetivo de este proyecto es desarrollar un programa que solicite al usuario un nombre y genere una llave numérica a partir de la suma de los valores de sus caracteres.

## 2. Funcionamiento del programa

El programa realiza las siguientes operaciones:

1. Muestra un mensaje solicitando el nombre de usuario.
2. Lee el nombre introducido por el usuario.
3. Comprueba que la entrada no esté vacía.
4. Obtiene el valor numérico de cada carácter leído.
5. Suma los valores de los caracteres mediante un acumulador.
6. Convierte la suma a una representación hexadecimal de 16 dígitos.
7. Muestra la llave generada en pantalla.

## 3. Tabla de conversión hexadecimal

Se agregó la siguiente tabla de caracteres:

```asm
hex_chars db '0123456789ABCDEF'
```

Esta tabla contiene los 16 símbolos que se utilizan para representar números hexadecimales: los dígitos del 0 al 9 y las letras de la A a la F.

Durante la conversión, el programa obtiene cada grupo de cuatro bits del resultado mediante operaciones binarias y utiliza ese valor como índice para localizar el carácter hexadecimal correspondiente.

**Captura 1. Tabla de conversión hexadecimal**

> Insertar aquí una captura del código donde aparece la declaración `hex_chars` y, si es posible, el bloque `hex_loop` que utiliza la tabla.

## 4. Bloque de suma ASCII

Se agregó un bloque que recorre los caracteres introducidos por el usuario y suma sus valores numéricos.

Las instrucciones principales son:

```asm
movzx rdx, byte ptr [rsi]
add rax, rdx
inc rsi
loop suma_loop
```

La instrucción `movzx` obtiene el valor numérico de un carácter y lo coloca en el registro `RDX`. La instrucción `add` acumula ese valor en `RAX`. Después, `inc` avanza a la siguiente posición del búfer y `loop` repite el proceso mientras queden caracteres por procesar.

Al terminar, el resultado se almacena en la variable `suma` para utilizarlo durante la conversión hexadecimal.

**Captura 2. Bloque de suma ASCII**

> Insertar aquí una captura del código que incluya la etiqueta `suma_loop`, las instrucciones de suma y el almacenamiento del resultado en la variable `suma`.

## 5. Conversión del resultado

Una vez obtenida la suma, el programa convierte el resultado a hexadecimal mediante operaciones de desplazamiento y extracción de cuatro bits.

El resultado se almacena en un búfer de 16 caracteres, rellenando con ceros a la izquierda cuando sea necesario. Esto permite mostrar llaves con un formato uniforme.

**Captura 3. Bloque de conversión hexadecimal**

> Insertar aquí una captura del código donde aparezcan `hex_loop`, la operación `and`, el desplazamiento `shr` y el almacenamiento de los caracteres en `hex_buffer`.

## 6. Compilación y ejecución

Para ensamblar el archivo se utiliza:

```bat
uasm64 -win64 keygen.asm
```

Después, se genera el ejecutable con GoLink:

```bat
GoLink.exe keygen.obj kernel32.dll /fo keygen.exe /console /entry main
```

Finalmente, se ejecuta `keygen.exe` desde la consola de Windows.

**Captura 4. Compilación del programa**

> Insertar aquí una captura del CMD donde se observe la compilación y la generación del ejecutable, si ambas operaciones se completaron correctamente.

## 7. Pruebas y resultados

### Prueba 1: Nombre `Ana`

Valores de los caracteres:

- A = 65
- n = 110
- a = 97

Suma total:

`65 + 110 + 97 = 272`

Resultado hexadecimal de 16 dígitos:

`0000000000000110`

**Captura 5. Ejecución con el nombre Ana**

> Insertar aquí una captura de la consola donde se vea el nombre introducido y la llave generada.

### Prueba 2: Nombre `Pedro`

Valores de los caracteres:

- P = 80
- e = 101
- d = 100
- r = 114
- o = 111

Suma total:

`80 + 101 + 100 + 114 + 111 = 506`

Resultado hexadecimal de 16 dígitos:

`00000000000001FA`

**Captura 6. Ejecución con el nombre Pedro**

> Insertar aquí una captura de la consola donde se vea el nombre introducido y la llave generada.

### Prueba 3: Entrada vacía

Cuando el usuario no introduce un nombre válido, el programa muestra el mensaje de error correspondiente.

**Captura 7. Validación de entrada vacía**

> Insertar aquí una captura de la consola que muestre el mensaje de error.

## 8. Uso de inteligencia artificial

Se utilizó una herramienta de inteligencia artificial como apoyo para comprender las instrucciones del proyecto, específicamente el significado y funcionamiento de la **tabla de conversión hexadecimal** y del **bloque de suma ASCII**.

La herramienta ayudó a interpretar cómo se relacionan los valores numéricos de los caracteres con la suma acumulada, así como el procedimiento para convertir el resultado a hexadecimal. También se utilizó como apoyo para comprender las instrucciones de ensamblador involucradas.

El código fue revisado y probado durante el desarrollo del proyecto. La inteligencia artificial se utilizó como recurso de consulta y aprendizaje para comprender mejor la lógica implementada.

## 9. Conclusión

Este proyecto permitió comprender cómo trabajar con entrada y salida de consola en Windows x64, recorrer caracteres almacenados en memoria, sumar sus valores numéricos y convertir el resultado a hexadecimal.

La implementación de la tabla de conversión y del bloque de suma ASCII permitió complementar el funcionamiento del programa y entender cómo se procesa una entrada de texto para producir una llave numérica.

