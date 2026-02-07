# Proyecto-AFA-con-Python
Este proyecto fue hecho para representar los datos principales de un torneo de futbol AFA. pidiendo al usuario que cargue datos como nombre del DT, nombre del equipo, victorias, empates, derrotas. Dentro de el mismo se puede eleguir una formacion tactica e incluso los jugadores que ocupan dichas posiciones. 
[Proyecto AFA.py](https://github.com/user-attachments/files/25154651/Proyecto.AFA.py)
#area de funiones (usando TAD)
class Equipo (object):
    def __init__ (self, nombre = "", dt = ""):
        self.nombre = nombre
        self.dt = dt

class Datos (object):    
    def __init__ (self, victoria = 0, empate = 0, derrota = 0):
        self.victoria = victoria
        self.empate = empate
        self.derrota = derrota
        self.informacion = []

#op 1
def agregar_equipo (equip, info):
    equip.nombre=input("Ingrese el nombre del equipo: ").capitalize()
    while equip.nombre != "999":
        equip.dt = input("Ingrese el nombre del DT: ").capitalize()
        info.victoria = int(input("Ingrese la cantidad de partidos ganados: "))
        info.empate = int(input("Ingrese la cantidad de partidos empatados: "))
        info.derrota = int(input("Ingrese la cantidad de partidos perdidos: "))
        equip.nombre=input("Ingrese el nombre del equipo o ingrese '999': ").capitalize()

        lista=[equip.nombre, equip.dt, info.victoria, info.empate, info.derrota]
        info.informacion.append(lista)
    return info.informacion

#op 2
def campeon (info):
    max_puntos = 0
    equipo_campeon = ""

    for x in info.informacion:
        puntos = x[2]*3 + x[3]*1
        if puntos > max_puntos:
            max_puntos = puntos
            equipo_campeon = x[0]
            print("El equipo campeon es: ", equipo_campeon, "con ", max_puntos, "puntos")
    return equipo_campeon

#op 3
def peor_equipo (info):
    equipo_perdedor = ""
    min_puntos = 999
    for x in info.informacion:
        puntos = x[2]*3 + x[3]*1
        if puntos < min_puntos:
            min_puntos = puntos
            equipo_perdedor = x[0]
            print("El peor equipo es: ", equipo_perdedor, "con", min_puntos, "puntos")
    return equipo_perdedor

#op 4 y 5 
def promedios (info):
    partidos = 15
    nom = input("Ingrese el nombre del equipo para sacar promedios: ").capitalize()
    for x in info.informacion:
        if x[0] == nom:
            prom_victorias = x[2] / partidos
            prom=puntos = x[2]*3 + x[3]*1 / partidos
            print("El promedio de victorias es: ", prom_victorias, "con un promedio de puntos de: ", prom)
            return prom_victorias, prom

#op 5
def equipo_armado (info):
    formacion=[]
    nom = input("Ingrese el nombre del equipo para armar la formacion: ").capitalize()
    dream = """
    1. 4-3-3
    2. 4-4-2
    """
    print(dream)
    opcion = int(input("Ingrese la formacion que desea: "))
    if opcion == 1:
        pt1 = input("Ingrese el nombre del portero: ").capitalize()
        ld1 = input("Ingrese el nombre del lateral derecho 1: ").capitalize()
        dfc1 = input("Ingrese el nombre del defensa 1: ").capitalize()  
        dfc2 = input("Ingrese el nombre del defensa 2: ").capitalize()
        li1 = input("Ingrese el nombre del lateral izquierdo 1: ").capitalize()
        mc1 = input("Ingrese el nombre del mediocampista central 1: ").capitalize()
        mco1 = input("Ingrese el nombre del mediocampista ofensivo 1: ").capitalize()
        mco2 = input("Ingrese el nombre del mediocampista ofensivo 2: ").capitalize()
        md1 = input("Ingrese el nombre del mediocampista derecho 1: ").capitalize()
        mi1 = input("Ingrese el nombre del mediocampista izquierdo 1: ").capitalize()
        dc1 = input("Ingrese el nombre del delantero centro 1: ").capitalize()

        formacion = [pt1, ld1, dfc1, dfc2, li1, mc1, mco1, mco2, md1, mi1, dc1]

    elif opcion == 2:
        pt2 = input("Ingrese el nombre del portero: ").capitalize()
        ld2 = input("Ingrese el nombre del lateral derecho 2: ").capitalize()
        dfc3 = input("Ingrese el nombre del defensa 1: ").capitalize()  
        dfc4 = input("Ingrese el nombre del defensa 2: ").capitalize()
        li2 = input("Ingrese el nombre del lateral izquierdo 2: ").capitalize()
        mc2 = input("Ingrese el nombre del mediocampista central 2: ").capitalize()
        mc3 = input("Ingrese el nombre del mediocampista central 3: ").capitalize()
        md2 = input("Ingrese el nombre del mediocampista derecho 2: ").capitalize()
        mi2 = input("Ingrese el nombre del mediocampista izquierdo 2: ").capitalize()
        dc2 = input("Ingrese el nombre del delantero centro 2: ").capitalize()
        dc3 = input("Ingrese el nombre del delantero centro 3: ").capitalize()

        formacion = [pt2, ld2, dfc3, dfc4, li2, mc2, mc3, md2, mi2, dc2, dc3]

    return formacion

#programa principal
menu = """
1.Agregar un equipo
2.Mostrar el equipo campeon
3.Mostrar el peor equipo
4.Sacar promedio de victorias y puntos
5.Armar equipo
6.Salir
"""

print(menu)
equip = Equipo()
datos = Datos()
op = 0
while op != 6:
    try:
        op = int(input("Ingrese una opcion: "))
    except ValueError:
        print("Opcion invalida")
        continue

    if op == 1:
        x = agregar_equipo (equip, datos)

    elif op == 2:
        campeon (datos)

    elif op == 3:
        peor_equipo (datos)
    
    elif op == 4:
        promedios (datos)

    elif op == 5:
        team = equipo_armado(Datos())

    else:
        print("Opcion incorrecta, ingrese nuevamente: ")
        
    op = int(input("Ingrese una opcion correcta: "))
