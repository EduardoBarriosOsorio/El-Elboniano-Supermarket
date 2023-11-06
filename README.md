# Python El-Elboniano-Supermarket
Problema Contable de caja registradora 
La caja registradora entrega mal el vuelto al cliente. Por lo tanto se procedió a realizar un programa en Python para solucionar esto:
1.-Ingresar productos, cantidad y valor unitario hasta el simbolo "#"
2.-Mencionar el total de la compra
3.-Ingresar metodo de pago
4.-Entregar el monto entregado por el cliente en efectivo y calcular el vuelto, mostrando billetes y monedas minimizando la cantidad de monedas y billetes a entregar

#Pseudocódigo
hasta que se ingrese el simbolo "#"
  Ingrese el producto que desea comprar, la cantidad y valor unitario
  guardar datos ingresados

mostrar la suma de los los costos de los productos

ingresar método de pago y monto (suponemos tarjeta y efectivo)

mostrar vuelto: monto entregado - costo

determinar cuantos billetes de 20 caben en vuelto
actualizar valor de vuelto
determinar cuantos billetes de 10 caben en vuelto
actualizar valor de vuelto
determinar...

mostrar por pantalla la cantidad de billetes y monedas a devolver.


boleta = []
while(True):
  datos = input("Ingrese el producto que desea comprar, la cantidad y valor unitario:")
  if datos == "#":
    break
  datos = datos.split(",")
  boleta.append(datos)

 monto_final = 0
for i in range(0,len(boleta)):
  cantidad = int(boleta[i][1])
  precio = int(boleta[i][2])
  monto_final = monto_final + (cantidad * precio)
print(f"Total de la compra {monto_final}")

monto_final = 0
for producto in boleta:
  cantidad = int(producto[1])
  precio = int(producto[2])
  monto_final = monto_final + (cantidad * precio)
print(f"Total de la compra {monto_final}")

forma_pagar = input("Ingrese medio de pago y monto entregado:")
forma_pagar = forma_pagar.split(",")
#forma_pagar = [efectivo,<monto>] [efectivo, 20000]
if forma_pagar[0] == "Tarjeta":
  print("no hay vuelto")

elif forma_pagar[0] == "Efectivo":
  vuelto = int(forma_pagar[1]) - int(monto_final)
  print(f"Monto vuelto:{vuelto}")
  # a saber: x%y devuelve el resto entre la division entre "x" e "y" (10%3)=1
  
  

  #cuantos billetes de 20.000 caben en el vuelto
  #guardar la cantidad de billetes
  #actualizar el valor de vuelto

  billetes_20 = int(vuelto/20000)
  vuelto = vuelto%20000     #vuelto=42.000     42000%20000=2000
  #vuelto = vuelto-(billetes_20*20000)
  
  billetes_10 = int(vuelto/10000)
  vuelto = vuelto%10000

  billetes_5 = int(vuelto/5000)
  vuelto = vuelto%5000

  billetes_2 = int(vuelto/2000)
  vuelto = vuelto%2000

  billetes_1 = int(vuelto/1000)
  vuelto = vuelto%1000

  monedas_500 = int(vuelto/500)
  vuelto = vuelto%500

  monedas_100 = int(vuelto/100)
  vuelto = vuelto%100

  monedas_50 = int(vuelto/50)
  vuelto = vuelto%50

  monedas_10 = int(vuelto/10)
  vuelto = vuelto%10
  
  monedas_5 = int(vuelto/5)
  vuelto = vuelto%5

  monedas_1 = int(vuelto/1)
  vuelto = vuelto%1
  
  vuelto_unidades =[billetes_20, billetes_10,billetes_5, billetes_2, billetes_1, monedas_500, monedas_100, monedas_50, monedas_10, monedas_5, monedas_1]
  definicion_unidades = ["billetes de 20 mil", "billetes de 10 mil", "billetes de 5 mil", "billetes de 2 mil", "billete de 1 mil", "monedas de 500", "monedas de 100", "monedas de 50", "monedas de 10", "monedas de 5", "monedas de 1"]

print("Entregar", end=" ")
for i in range(0,len(vuelto_unidades)):
  if vuelto_unidades[i]!=0:
    print(f"{vuelto_unidades[i]} {definicion_unidades[i]}", end=", ")
    
