# Block-de-nota-en-py
['hola.txt', 'main.py', 'Nota.py']
1 Para escribir,
2 Para borrar,
3 Para nueva nota
4 leer
5 Salir
Selecciona una opción:
# Es un block de nota hecho en python, es solo para pobrar conocimientos,pero los pueden modificar.
#codigo:


import os
import pyfiglet
from termcolor import colored

# Mensaje de bienvenida
bienvenida = "Block de notas"
bienvenida = pyfiglet.figlet_format(bienvenida)
print(colored(bienvenida, "blue"))
print(colored("Escribe tus notas aquí", "red"))

# Bucle principal
while True:
    lista_de_nota = os.listdir()
    print(colored(lista_de_nota,"red"))
    print(colored("1 Para escribir, \n2 Para borrar, \n3 Para nueva nota \n4 leer \n5 Salir", "yellow"))
    try:
        botones = int(input(colored("Selecciona una opción: ", "yellow")))

        if botones == 4:
            nombre_de_nota_a_leer = input("Nombre de la nota: ")
            with open(nombre_de_nota_a_leer, "r") as leer:
                leer =leer.read()
                lee = pyfiglet.figlet_format("Tu Nota")
                print(lee,"\n")
                print(f"Tu nota dice::::{leer}")


        if botones == 1:
            nota = input("Escribe tu nota: ")
            with open("Nota.txt", "a") as e:
                e.write(nota + '\n')  # Añadir nueva línea después de cada nota
            print(colored("Nota guardada con éxito.", "green"))

        elif botones == 2:
            w = input(colored("Nombre de la nota a borrar: ", "light_green"))
            # Verificar si el archivo existe antes de intentar abrirlo
            if os.path.exists(w):
                os.remove(w)  # Elimina el archivo
                print(colored("Nota borrada con éxito.", "green"))
            else:
                print(colored("El archivo no existe.", "red"))

        elif botones == 3:
            w = input(colored("Nombre de la nueva nota: ", "light_green"))
            nueva_nota = input("Escribe tu nueva nota: ")
            with open(w, "w") as nueva:
                nueva.write(nueva_nota + '\n')  # Añadir nueva línea después de la nota
            print(colored("Nueva nota guardada con éxito.", "green"))

        elif botones == 5:
            print(colored("Saliendo...", "red"))
            break  # Salir del bucle

        else:
            print(colored("Selecciona una opción válida", "red"))

    except ValueError:
        print(colored("Por favor, ingresa un número válido.", "red"))
