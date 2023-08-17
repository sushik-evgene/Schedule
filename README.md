# Schedule
from tkinter import *

root = Tk()
root.geometry("450x650+100+100")
root.resizable(False, False)
root.title('Schedule')

label = Label(root, text="Головне меню", font='Arial 16')
label.pack(pady=20)

# Кнопка "Меню" с закругленными углами
button1 = Button(root,
                 text='Меню ✅',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,                 # Увеличиваем borderwidth для создания закругленных углов
                 relief="ridge")                # Используем "ridge" relief для закругления углов
button1.pack(pady=10)

# Кнопка "Інше" с закругленными углами
button2 = Button(root,
                 text='Інше ⁉️',
                 width=25, height=2,
                 bg='white', fg='black',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge")
button2.pack(pady=10)

label.pack(anchor=CENTER)
button1.pack(anchor=CENTER)
button2.pack(anchor=CENTER)

root.mainloop()
