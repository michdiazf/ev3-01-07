import os
import random
import csv
import statistics

sueldos=[]
trabajadores =["Juan Pérez","María García","Carlos López","Ana Martínez","Pedro Rodríguez","Laura Hernández","Miguel Sánchez","Isabel Gómez","Francisco Díaz","Elena Fernández"] 
#15 espacios
#10 trabajadores

menu="""
Menu principal
1.- Asignar sueldos aleatorios
2.- Clasificar sueldos
3.- Ver estadisticas
4.- Reporte de sueldos
5.- Salir del programa

Opcion: """

def generarArchivo():
    with open ("lista.txt", "w", encoding = "utf-8") as archivo:
        archivo.write(reporte())

def asignarSueldos(): #opcion 1
    for i in range(len(trabajadores)):
        sueldos.append(random.randint(300000,25000000))
    print(sueldos)
    print("Sueldos creados")
    input("Presione ENTER para volver al menu ")
    return

def clasificar(): #opcion 2
    for i in range(len(sueldos)):
        if i<800000:
            reporte=generarArchivo(i<800000)
            s+=1
            print(f"""
            Sueldos menores a $800.000 TOTAL: {s}
            Nombre empleado | Sueldo  """)
            with open (reporte) as archivo:
                archivo.write(reporte)
        elif 800000<=i>=2000000:
            reporte=generarArchivo(800000<=i>=2000000)
            t+=1
            print(f"""
            Sueldos entre $800.000 y $2.000.000  TOTAL: {t}
            Nombre empleado | Sueldo  """) 
            with open (reporte) as archivo:
                archivo.write(reporte)
        elif i>2000000:
            reporte=generarArchivo(i>2000000)
            u+=1
            print(f"""
            Sueldos superiores a $2.000.000  TOTAL: {u}
            Nombre empleado | Sueldo  """)
            with open (reporte) as archivo:
                archivo.write(reporte)
    input(f"TOTAL SUELDOS: ${sum(sueldos)}")
    input("Presione ENTER para volver al menu ")
    return
  

def estadisticas(): #opcion 3
    med=statistics.geometric_mean(sueldos)
    minimo=min(sueldos)
    maximo=max(sueldos)
    prom=(sum(sueldos)/10)
    print(f"Sueldo mas bajo: ${minimo}")
    print(f"Sueldo mas alto: ${maximo}")
    print(f"Promedio de sueldos: ${prom}")
    print(f"Media geometrica: {med}")
    input("Presione ENTER para volver al menu ")
    return

def reporte(): #opcion 4
    for row in range(len(trabajadores)):
        dSalud= (sueldos)*0.07
        dAFP= (sueldos)*0.12
        totalDesc=(dSalud-dAFP)
        sueldoLiq=(sueldos-totalDesc)
    print("""
| Nombre empleado  | Sueldo base($) | Descuento salud($) | Descuento AFP($) | Sueldo liquido($) | 
|                  |                |                    |                  |                   |
""")  
    texto += f"{trabajadores[row][0]:18d}"
    texto += f"{trabajadores[row][1]:16d}{sueldos}"
    texto += f"{trabajadores[row][2]:20d}{dSalud}"
    texto += f"{trabajadores[row][3]:18d}{dAFP}"
    texto += f"{trabajadores[row][4]:19d}{sueldoLiq}"
    input("Presione ENTER para volver al menu ")
    return

def salir(): #opcion 5 
    input("""
Finalizando programa...
Desarrollado por Michelle Diaz
RUT 19.430.905-8""")
    

while True:
    try:
        os.system("cls")
        opc=int(input(menu))
        if opc==1:
            asignarSueldos()
        elif opc==2:
            clasificar()
        elif opc==3:
            estadisticas()
        elif opc==4:
            reporte()
        elif opc==5:
            salir()
            break
        else:
            input("Error, vuelva a ingresar")
    except:
        input("Excepción")




