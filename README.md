# Georreferenciacion-de-Sismos-
#SE IMPORTAN LAS BIBLIOTECAS QUE SE OCUPARAN PARA REALIZAR EL PROYECTO
import numpy as np
from numpy.random import rand
import csv
import math
import matplotlib.pyplot as plt
import pandas as pd

#SE DEFINE CADA COLUMNA QUE SE QUE VENDRA EN EL ARCHIVO CSV:V,X,Y(VERTICE,COORDENADAS X,Y,AL IGUAL QUE BANDERA Y CANTIDAD PARA PODER HACER OTRAS OPERACIONES 
FECHA=[]
HORA=[]
MAGNITUD=[]
LATITUD=[]
LONGITUD=[]
LOCALIZACION=[]
cantidad= 0

#se habre el archivo csv y saca cada uno de los datos
print('Â¿COMO SE LLAMA EL ARCHIVO CSV EN LA QUE SE VA A TRABAJAR?')
nombre= input()
nombre=nombre+'.csv'
#LEE EL ARCHIVO Y LO MUESTRA EN LA PANTALLA
with open (nombre) as f:
    reader=csv.reader(f)
    print('LOS DATOS DENTRO DEL ARCHIVO CSV SE MOSTRARAN AL SIGUIENTE:')
    print('                                   ')
    for row in reader:
        print(row)
    print('                                   ')
#HABRE EL ARCHIVO CSV DE DATOS
with open (nombre) as csvfile:
    reader = csv.DictReader(csvfile)
    for row in reader:
        MAGNITUD.append(float(row['MAGNITUD']))
        LATITUD.append(float(row['LATITUD']))

#LEE LOS DATOS DE LATITUDES Y LONGITUDES
data=pd.read_csv('scol.txt',header=1,delim_whitespace=True)
#DEFINE LAS FILAS QUE SE VAN A LEER YA QUE SON EL 3 Y EL 4 DE LATITU Y LONGITUD, RECUERDE QUE PYTHON LEE LA PRIMERA FILA COMO 0.
x=data.iloc[:,3]    
y=data.iloc[:,4]
print("Estas son los datos de  Latitudes de sismos del Estado de Colima")
print (x)
print ("Estas son los datos de  longitudes de Sismos del Estado de Colima")
print(y)
#PLOTEA LOS DATOS QUE SE ENCUENTRAN
plt.plot(x,y,'ro')
plt.xlabel('Latitudes')
plt.ylabel('Longitud')
plt.show()
