from tkinter import *
from tkinter import ttk

def show_menu_tab():
    notebook.select(menu_tab)

def show_other_tab():
    notebook.select(other_tab)

def show_submenu_tab():
    notebook.select(submenu_tab)

root = Tk()
root.geometry("450x650+100+100")
root.resizable(False, False)
root.title('Schedule')

# Создаем стиль для скрытия фона и заголовка верхней панели
style = ttk.Style()
style.layout("TNotebook.Tab", [])  # Пустой layout убирает заголовок

notebook = ttk.Notebook(root)
notebook.pack(fill="both", expand=True)

menu_tab = Frame(notebook)
other_tab = Frame(notebook)
submenu_tab = Frame(notebook)

notebook.add(menu_tab, text="Меню")
notebook.add(other_tab, text="Інше")
notebook.add(submenu_tab, text="Підменю")

label = Label(menu_tab, text="Головне меню", font='Arial 16')
label.pack(pady=65)

button1 = Button(menu_tab,
                 text='Меню ✅',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge",
                 command=show_submenu_tab)
button1.pack(pady=10)

button2 = Button(menu_tab,
                 text='Інше ⁉️',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge",
                 command=show_other_tab)
button2.pack(pady=10)

label_other = Label(other_tab, text="Iнше", font='Arial 16')
label_other.pack(pady=20)

def back_to_menu_from_other():
    notebook.select(menu_tab)

button_back_other = Button(other_tab, text="← Назад", command=back_to_menu_from_other)
button_back_other.pack(anchor='nw', padx=10, pady=10)  # Верхний левый угол

button3 = Button(other_tab,
                 text='Версії та оновлення',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge")
button3.pack(pady=10)

# То же самое для вкладки "Підменю"
label_submenu = Label(submenu_tab, text="Підменю", font='Arial 16')
label_submenu.pack(pady=20)

def back_to_menu_from_submenu():
    notebook.select(menu_tab)

button_back_submenu = Button(submenu_tab, text="← Назад", command=back_to_menu_from_submenu)
button_back_submenu.pack(anchor='nw', padx=10, pady=10)  # Верхний левый угол

button6 = Button(submenu_tab,
                 text='Кнопка 1 підменю',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge")
button6.pack(pady=10)

button7 = Button(submenu_tab,
                 text='Кнопка 2 підменю',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge")
button7.pack(pady=10)

button8 = Button(submenu_tab,
                 text='Кнопка 3 підменю',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge")
button8.pack(pady=10)

button9 = Button(submenu_tab,
                 text='Кнопка 4 підменю',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge")
button9.pack(pady=10)

root.mainloop()
