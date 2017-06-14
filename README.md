# ExamenPA
from tkinter import *
import random
import time
import turtle
from math import *

tk=Tk()
lap=turtle.Pen()
#Ejercicio3:métodos
class Gota:
    def __init__(self,canvas,color,n1,n2):
        self.canvas=canvas
        self.id=canvas.create_oval(10,5,20,20,fill=color)
        self.canvas.move(self.id,n1,n2)#posicion inicial
        starts=[1,2,3]
        random.shuffle(starts)
        self.y=starts[0]        
        self.x=0
        self.canvas_height=self.canvas.winfo_height()
        self.canvas_width=self.canvas.winfo_width()
             
    def draw(self):
        self.canvas.move(self.id,self.x,self.y)#dirección
        pos=self.canvas.coords(self.id)

def posaleatorx():
    arrpos=[25,50,100,150,200,250,300,350,400,450,500,550,600]
    random.shuffle(arrpos)
    x=arrpos[0]
    return x

def posaleatory():
    arrpos=[20,40,50,60,80,90,100,110,130,150,160,200]
    random.shuffle(arrpos)
    y=arrpos[0]
    return y

def lluvia():
    n1=Gota(canvas,'lightblue',posaleatorx(),posaleatory())
    n2=Gota(canvas,'lightblue',posaleatorx(),posaleatory())
    n3=Gota(canvas,'lightblue',posaleatorx(),posaleatory())
    n4=Gota(canvas,'lightblue',posaleatorx(),posaleatory())
    n5=Gota(canvas,'lightblue',posaleatorx(),posaleatory())
    n6=Gota(canvas,'lightblue',posaleatorx(),posaleatory())
    while 1:        
        n1.draw()        
        n2.draw()
        n3.draw()
        n4.draw()
        n5.draw()
        n6.draw()
        tk.update_idletasks()
        tk.update()
        time.sleep(0.01)
        
#Ejercicio2:método
def figura():    
    lap.reset()    
    lados=int(input("Ingrese el número de lados de la figura: "))
    if lados<=2:
        print("El número de lados debe ser mayor o igual que 3")        
    elif lados==3:
        l=int(input("Ingrese la longitud del lado del triángulo: "))
        h=(pow(3,1/2)*1)/2
        area=(l*h)/2
        per=3*l
        lap.forward(l)
        lap.left(135)
        lap.forward(l)
        lap.left(90)
        lap.forward(l)
        print("El área es: "+str(area))
        print("El perímetro es :"+str(per))
    elif lados==4:
        l=int(input("Ingrese la longitud del lado del cuadrado: "))        
        area=l*l
        per=4*l
        for i in range(0,4):
            lap.forward(l)
            lap.left(90)        
        print("El área es: "+str(area))
        print("El perímetro es :"+str(per))
    elif lados==5:
        l=int(input("Ingrese la longitud del lado del pentágono: "))
        for i in range(0,5):
            lap.forward(l)
            lap.left(180+180/l)
    else:
        print("Opción no válida")
        print("Intente de nuevo")
    print("Vuelva a presionar el botón para el cálculo de otra figura")
             
             
#Creacion de ventana
tk.title("Examen")
tk.resizable(0, 0)
tk.wm_attributes("-topmost", 1)
canvas = Canvas(tk, width=640, height=480, bd=0, highlightthickness=0)
canvas.pack()
tk.update()

bt=Button(tk,text="Figura Geométrica",command=figura).pack(side=LEFT)
bt=Button(tk,text="Animación de lluvia",command=lluvia).pack(side=RIGHT)

tk.mainloop()
