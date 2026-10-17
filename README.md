# ProyectoModulo2-Lenguaje-de-Interfaz

# Keygen Básico


#Descripción del proyecto

El objetivo de este proyecto es desarrollar un programa que solicite al usuario un nombre y genere una llave numérica a partir de la suma de los valores de sus caracteres.

## Funcionamiento del programa

El programa realiza las siguientes operaciones:

1. Obtiene el valor numérico de cada carácter leído.
2. Suma los valores de los caracteres mediante un acumulador.
3. Convierte la suma a una representación hexadecimal de 16 dígitos.
4. Muestra la llave generada en pantalla.

## Tabla de conversión hexadecimal

Se utilizo la siguiente instruccion, la cual es una tabla contiene los 16 símbolos que se utilizan para representar números hexadecimales: los dígitos del 0 al 9 y las letras de la A a la F.

```asm
hex_chars db '0123456789ABCDEF'
```
<img width="432" height="40" alt="image" src="https://github.com/user-attachments/assets/b417030e-8fc9-4587-862f-2962a912d31e" />

<img width="582" height="261" alt="image" src="https://github.com/user-attachments/assets/204feff8-bc94-46a3-b955-65d4af90497f" />


#Bloque de suma ASCII

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

<img width="1085" height="382" alt="image" src="https://github.com/user-attachments/assets/6d65c2c3-1e68-4caa-93db-613f44188411" />


#Conversión del resultado

El programa convierte el resultado a hexadecimal mediante operaciones de desplazamiento y extracción de cuatro bits.

El resultado se almacena en un búfer de 16 caracteres, rellenando con ceros a la izquierda cuando sea necesario. Esto permite mostrar llaves con un formato uniforme.

<img width="672" height="467" alt="image" src="https://github.com/user-attachments/assets/0235440d-a26b-48c8-bfb2-44e1f3430c72" />


#Compilación y ejecución

Para ensamblar el archivo se utiliza:

uasm64 -win64 keygen.asm


Después, se genera el ejecutable con GoLink:

GoLink.exe keygen.obj kernel32.dll /fo keygen.exe /console /entry main

<img width="848" height="287" alt="image" src="https://github.com/user-attachments/assets/ab0f5640-7e31-425f-a5a7-b47266a1965c" />

Finalmente, se ejecuta `keygen.exe` desde la consola de Windows.



# Resultados

# Prueba 1: Nombre `Ana`

Valores de los caracteres:

- A = 65
- n = 110
- a = 97

Suma total:

`65 + 110 + 97 = 272`

Resultado hexadecimal de 16 dígitos:

`0000000000000110`

<img width="1018" height="97" alt="image" src="https://github.com/user-attachments/assets/ddd9fc4d-ac30-4047-b37f-47b93dfe0f26" />

# Prueba 2: Nombre `Pedro`

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

<img width="1047" height="105" alt="image" src="https://github.com/user-attachments/assets/e5f0f34d-33cb-4c86-8abe-a5ae4a913825" />

#Prueba 3: Entrada vacía

Cuando el usuario no introduce un nombre válido, el programa muestra el mensaje de error correspondiente.

<img width="1027" height="101" alt="image" src="https://github.com/user-attachments/assets/73952154-e631-4ffc-b2a5-5ca6e0a49607" />


# Uso de inteligencia artificial

Se utilizó la herramienta de inteligencia artificial como apoyo para comprender las instrucciones del proyecto, específicamente el funcionamiento de la "tabla de conversión hexadecimal" y del "bloque de suma ASCII".

La herramienta ayudó a interpretar cómo se relacionan los valores numéricos de los caracteres con la suma acumulada, así como el procedimiento para convertir el resultado a hexadecimal.


# Link de la explicacion en video 

https://drive.google.com/drive/folders/1rMJllYyK2g00RaiRtwtvhqnh4RQnFxSG?usp=sharing
