from tkinter import *
from tkinter import ttk

def show_menu_tab():                       # Вкладка  Головне меню
    notebook.select(menu_tab)

def show_submenu_tab():                    # Вкладка Меню
    notebook.select(submenu_tab)

def show_other_tab():                      # Вкладка Інше
    notebook.select(other_tab)

def show_versions_tab():                   # Вкладка Верії та оновлення
    notebook.select(versions_tab)

def show_autor_tab():                      # В кладка Автори
    notebook.select(autor_tab)

def show_support_tab():                    # Вкладка Техпідтримка
    notebook.select(support_tab)

def show_week_schedule_tab():              # Вкладка Розклад по дням тиждня
    notebook.select(week_schedule_tab)

def show_all_schedule_tab():               # Вкладка Весь розкла
    notebook.select(all_schedule_tab)

def show_list_teachers_tab():              # Вкладка Список викладачів
    notebook.select(list_teachers_tab)

def show_items_tab():                      # Вкладка Предмети
    notebook.select(items_tab)

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
versions_tab = Frame(notebook)
autor_tab = Frame(notebook)
support_tab = Frame(notebook)
week_schedule_tab = Frame(notebook)
all_schedule_tab = Frame(notebook)
list_teachers_tab = Frame(notebook)
items_tab  = Frame(notebook)

notebook.add(menu_tab, text="Меню")
notebook.add(other_tab, text="Інше")
notebook.add(submenu_tab, text="Підменю")
notebook.add(versions_tab, text="Версії та оновлення")
notebook.add(autor_tab, text="Автори")
notebook.add(support_tab, text="Техпідтримка")
notebook.add(week_schedule_tab, text="Розклад по дням тиждня")
notebook.add(all_schedule_tab, text="Весь розкла")
notebook.add(list_teachers_tab, text="Список викладачів")
notebook.add(items_tab, text="Предмети")


label = Label(menu_tab, text="Головне меню", font='Arial 16')
label.pack(pady=10)
label = Label(menu_tab, text="ㅤ", font='Arial 16')
label.pack(pady=60)

frame_buttons = Frame(menu_tab)
frame_buttons.pack()

button1 = Button(frame_buttons,
                 text='Меню ✅',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge",
                 command=show_submenu_tab)
button1.pack(side=TOP, fill=X, padx=5, pady=10)

button2 = Button(frame_buttons,
                 text='Інше ⁉️',
                 width=15, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge",
                 command=show_other_tab)
button2.pack(side=TOP, fill=X, padx=5, pady=10)

label_other = Label(other_tab, text="Iнше", font='Arial 16')
label_other.pack(pady=10)

frame_back_other = Frame(other_tab)
frame_back_other.pack(anchor='nw', padx=5, pady=5)

def back_to_menu_from_other():
    notebook.select(menu_tab)

button_back_other = Button(frame_back_other, text="← Назад", command=back_to_menu_from_other)
button_back_other.pack(side=LEFT)

label = Label(other_tab, text="ㅤ", font='Arial 16')
label.pack(pady=30)

button3 = Button(other_tab,
                 text='Версії та оновлення',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge",
                 command=show_versions_tab)
button3.pack(pady=10)

label = Label(versions_tab, text="Версії та оновлення", font='Arial 16')
label.pack(pady=10)

frame_back_versions = Frame(versions_tab)
frame_back_versions.pack(anchor='nw', padx=5, pady=5)

def back_to_other_from_versions():
    notebook.select(other_tab)

button_back_versions = Button(frame_back_versions, text="← Назад", command=back_to_other_from_versions)
button_back_versions.pack(side=LEFT)

button4 = Button(other_tab,
                 text='Автори',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge",
                 command=show_autor_tab)
button4.pack(pady=10)

label_autor = Label(autor_tab, text="Автори", font='Arial 16')
label_autor.pack(pady=10)

frame_back_autor = Frame(autor_tab)
frame_back_autor.pack(anchor='nw', padx=5, pady=5)

def back_to_other_from_autor():
    notebook.select(other_tab)

button_back_autor = Button(frame_back_autor, text="← Назад", command=back_to_other_from_autor)
button_back_autor.pack(side=LEFT)

button5 = Button(other_tab,
                 text='Техпідтримка',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge",
                 command=show_support_tab)
button5.pack(pady=10)

label_support = Label(support_tab, text="Техпідтримка", font='Arial 16')
label_support.pack(pady=10)

frame_back_support = Frame(support_tab)
frame_back_support.pack(anchor='nw', padx=5, pady=5)

def back_to_other_from_support():
    notebook.select(other_tab)

button_back_support = Button(frame_back_support, text="← Назад", command=back_to_other_from_versions)
button_back_support.pack(side=LEFT)

label_support1 = Label(support_tab, text='''Тел. +380 99 205 ** **  ㅤㅤㅤㅤㅤㅤㅤㅤㅤ
Пошта. sushikev****@gmail.comㅤㅤㅤㅤㅤ''', font='Arial 16')
label_support1.pack(pady=10)

# То же самое для вкладки "Підменю"
label_submenu = Label(submenu_tab, text="Меню", font='Arial 16')
label_submenu.pack(pady=10)

frame_back_submenu = Frame(submenu_tab)
frame_back_submenu.pack(anchor='nw', padx=5, pady=5)

def back_to_menu_from_submenu():
    notebook.select(menu_tab)

button_back_submenu = Button(frame_back_submenu, text="← Назад", command=back_to_menu_from_submenu)
button_back_submenu.pack(side=LEFT)

label = Label(submenu_tab, text="ㅤ", font='Arial 16')
label.pack(pady=20)

button6 = Button(submenu_tab,
                 text='Розклад по дням тиждня',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge",
                 command=show_week_schedule_tab)
button6.pack(pady=10)

label = Label(week_schedule_tab, text="Розклад по дням тиждня", font='Arial 16')
label.pack(pady=10)

frame_back_week_schedule = Frame(week_schedule_tab)
frame_back_week_schedule.pack(anchor='nw', padx=5, pady=5)

def back_to_submenu_from_week_schedule():
    notebook.select(submenu_tab)

button_back_week_schedule = Button(frame_back_week_schedule, text="← Назад", command=back_to_submenu_from_week_schedule)
button_back_week_schedule.pack(side=LEFT)

button7 = Button(submenu_tab,
                 text='Весь розклад',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge",
                 command=show_all_schedule_tab)
button7.pack(pady=10)

label = Label(all_schedule_tab, text="Весь розклад", font='Arial 16')
label.pack(pady=10)

frame_back_all_schedule = Frame(all_schedule_tab)
frame_back_all_schedule.pack(anchor='nw', padx=5, pady=5)

def back_to_submenu_from_all_schedule():
    notebook.select(submenu_tab)

button_back_all_schedule = Button(frame_back_all_schedule, text="← Назад", command=back_to_submenu_from_all_schedule)
button_back_all_schedule.pack(side=LEFT)

button8 = Button(submenu_tab,
                 text='Список викладачів',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge",
                 command=show_list_teachers_tab)
button8.pack(pady=10)

button9 = Button(submenu_tab,
                 text='Предмети',
                 width=25, height=2,
                 bg='black', fg='white',
                 font='Arial 16',
                 borderwidth=5,
                 relief="ridge",
                 command=show_items_tab)
button9.pack(pady=10)

root.mainloop()

