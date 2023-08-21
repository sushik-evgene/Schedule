from tkinter import *                      # Подключаем модули
from tkinter import ttk                    # |
from PIL import Image, ImageTk             # |

def show_menu_tab():                       # Вкладка  Головне меню
    notebook.select(menu_tab)
def show_submenu_tab():                    # Вкладка Меню
    notebook.select(submenu_tab)
def show_other_tab():                      # Вкладка Інше
    notebook.select(other_tab)
def show_week_schedule_tab():              # Вкладка Розклад по дням тиждня
    notebook.select(week_schedule_tab)
def show_all_schedule_tab():               # Вкладка Весь розкла
    notebook.select(all_schedule_tab)
def show_list_teachers_tab():              # Вкладка Список викладачів
    notebook.select(list_teachers_tab)
def show_items_tab():                      # Вкладка Предмети
    notebook.select(items_tab)
def show_versions_tab():                   # Вкладка Верії та оновлення
    notebook.select(versions_tab)
def show_versions1_tab():                  # Вкладка версія
    notebook.select(versions1_tab)
def show_versions2_tab():                  # Вкладка версія
    notebook.select(versions2_tab)
def show_versions3_tab():                  # Вкладка версія
    notebook.select(versions3_tab)
def show_versions4_tab():                  # Вкладка версія
    notebook.select(versions4_tab)
def show_versions5_tab():                  # Вкладка версія
    notebook.select(versions5_tab)

def show_autor_tab():                      # В кладка Автори
    notebook.select(autor_tab)
def show_support_tab():                    # Вкладка Техпідтримка
    notebook.select(support_tab)

def set_tab_background(tab, image):
    tab_label = Label(tab, image=image)
    tab_label.place(x=0, y=0, relwidth=1, relheight=1)

root = Tk()                                # Создаем окно
root.geometry("450x650+100+100")           # Задаем размеры (Ширина)-(Высота) Место появления окна
root.resizable(False, False)               # Блокируем возможность изменения окна (Ширина)-(Высота)
root.title('Schedule')                     # Даем название окну

background_image = PhotoImage(file="C:/IT-Schedule/img/1.gif")       # Импортируем фото (Фон)
image_it_college = Image.open("C:/IT-Schedule/img/it-college.jpg")   # | Надпись (ІТ-КОЛЕДЖ ХАІ)
image_back = Image.open("C:/IT-Schedule/img/back.jpg")               # | Стрелка назад

hex_color = "#005d92"                      # Цвет фона в формате "#RRGGBB"
root.configure(background=hex_color)       # Устанавливаем цвет фона для окна

style = ttk.Style()                        # Создаем стиль для скрытия фона и заголовка верхней панели
style.layout("TNotebook.Tab", [])          # Пустой layout убирает заголовок

notebook = ttk.Notebook(root)              # Какая-то херня я не разобрался...
notebook.pack(fill="both", expand=True)    # |

menu_tab = Frame(notebook)                 # Создаем вкладки (Головна)
submenu_tab = Frame(notebook)              # | Меню
other_tab = Frame(notebook)                # | Інше
week_schedule_tab = Frame(notebook)        # | Розклад по дням тиждня
all_schedule_tab = Frame(notebook)         # | Весь розклад
list_teachers_tab = Frame(notebook)        # | Список викадачів
items_tab = Frame(notebook)                # | Предмети
versions_tab = Frame(notebook)             # | Версії та оновлення
versions1_tab = Frame(notebook)
versions2_tab = Frame(notebook)
versions3_tab = Frame(notebook)
versions4_tab = Frame(notebook)
versions5_tab = Frame(notebook)
autor_tab = Frame(notebook)                # | Автори
support_tab = Frame(notebook)              # | Техпідтримка







set_tab_background(menu_tab, background_image)                   # Задаем фон (Фото)--Головна
set_tab_background(submenu_tab, background_image)                # | Меню
set_tab_background(other_tab, background_image)                  # | Інше
set_tab_background(week_schedule_tab, background_image)          # | Розклад по дням тиждня
set_tab_background(all_schedule_tab, background_image)           # | Весь розклад
set_tab_background(list_teachers_tab, background_image)          # | Список викадачів
set_tab_background(items_tab, background_image)                  # | Предмети
set_tab_background(versions_tab, background_image)               # | Версії та оновлення
set_tab_background(autor_tab, background_image)                  # | Автори
set_tab_background(support_tab, background_image)                # | Техпідтримка

for tab in [menu_tab, submenu_tab, other_tab, versions_tab, autor_tab,support_tab,
week_schedule_tab, all_schedule_tab,list_teachers_tab, items_tab]:
    tab.configure(background=hex_color)

notebook.add(menu_tab)                     # Создаем вкладки (Головна)
notebook.add(submenu_tab)                  # | Меню
notebook.add(other_tab)                    # | Інше
notebook.add(week_schedule_tab)            # | Розклад по дням тиждня
notebook.add(all_schedule_tab)             # | Весь розклад
notebook.add(list_teachers_tab)            # | Список викадачів
notebook.add(versions_tab)                 # | Версії та оновлення
notebook.add(versions1_tab)
notebook.add(versions2_tab)
notebook.add(versions3_tab)
notebook.add(versions4_tab)
notebook.add(versions5_tab)


notebook.add(autor_tab, text="Автори")                           # | Автори
notebook.add(support_tab, text="Техпідтримка")                   # | Техпідтримка

new_size = (300, 30)                                             # Новый размер для фото (ширина, высота)--
image_it_college = image_it_college.resize(new_size)             # | -- Надпись (ІТ-КОЛЕДЖ ХАІ)

photo_it_college = ImageTk.PhotoImage(image_it_college)

background_label = Label(root, image=photo_it_college, borderwidth=0)
background_label.place(x=70, y=15, anchor='nw')

label = Label(menu_tab, text="ㅤ", font='Arial 16', background=hex_color)
label.pack(pady=10)

transparent_label = Label(menu_tab, text="Головна", bg=hex_color, fg="white",
                          highlightbackground=hex_color, highlightcolor=hex_color, font='Arial 16')
transparent_label.pack(pady=2)

label = Label(menu_tab, text="ㅤ", font='Arial 16', background=hex_color)
label.pack(pady=60)

button_menu = Button(menu_tab,
                 text='Меню ✅',
                 width=18, height=1,
                 bg='white', fg='#005d92',
                 font='Arial 20',
                 borderwidth=2,
                 relief="ridge",
                 activeforeground="#005d92",
                 command=show_submenu_tab)
button_menu.pack(pady=10)

label = Label(submenu_tab, text="ㅤ", font='Arial 16', background=hex_color)
label.pack(pady=10)

transparent_label = Label(submenu_tab, text="Меню", bg=hex_color, fg="white",
                          highlightbackground=hex_color, highlightcolor=hex_color, font='Arial 16')
transparent_label.pack(pady=2)

frame_back_submenu = Frame(submenu_tab)
frame_back_submenu.pack(anchor='nw', padx=10, pady=5)

def back_to_menu_from_submenu():
    notebook.select(menu_tab)

new_size_back = (30, 30)                      # Новый размер (ширина, высота)
image_back = image_back.resize(new_size_back)

photo_back = ImageTk.PhotoImage(image_back)

button_back_submenu = Button(frame_back_submenu, image=photo_back, borderwidth=-4,
activebackground="#005d92", activeforeground="#005d92", command=back_to_menu_from_submenu)
button_back_submenu.pack(side=LEFT)

label = Label(submenu_tab, text="ㅤ", font='Arial 16', background=hex_color)
label.pack(pady=10)

button2 = Button(menu_tab,
                 text='Інше',
                 width=18, height=1,
                 bg='white', fg='#005d92',
                 font='Arial 20',
                 borderwidth=2,
                 relief="ridge",
                 activeforeground="#005d92",
                 command=show_other_tab)
button2.pack(pady=10)

transparent_label = Label(other_tab, text="Iнше", bg=hex_color, fg="white",
                          highlightbackground=hex_color, highlightcolor=hex_color, font='Arial 16')
transparent_label.pack(pady=10)

frame_back_other = Frame(other_tab)
frame_back_other.pack(anchor='nw', padx=5, pady=5)

def back_to_menu_from_other():
    notebook.select(menu_tab)

button_back_other = Button(frame_back_other, text="← Назад", command=back_to_menu_from_other)
button_back_other.pack(side=LEFT)

label = Label(other_tab, text="ㅤ", font='Arial 16', background=hex_color)
label.pack(pady=30)

button3 = Button(other_tab,
                 text='Версії та оновлення',
                 width=18, height=1,
                 bg='white', fg='#005d92',
                 font='Arial 19',
                 borderwidth=2,
                 relief="ridge",
                 activeforeground="#005d92",
                 command=show_versions_tab)
button3.pack(pady=10)

label = Label(versions_tab, text="ㅤ", font='Arial 16', background=hex_color)
label.pack(pady=10)

transparent_label = Label(versions_tab, text="Версії та оновлення", bg=hex_color, fg="white",
                          highlightbackground=hex_color, highlightcolor=hex_color, font='Arial 16')
transparent_label.pack(pady=10)

frame_back_versions = Frame(versions_tab)
frame_back_versions.pack(anchor='nw', padx=5, pady=5)

def back_to_other_from_versions():
    notebook.select(other_tab)

button_back_versions = Button(frame_back_versions, text="← Назад", command=back_to_other_from_versions)
button_back_versions.pack(side=LEFT)

button_versions1 = Button(versions_tab,
                 text='V. Beta.1 ⚡',
                 width=12, height=1,
                 bg='white', fg='#005d92',
                 font='Arial 16',
                 borderwidth=2,
                 relief="ridge",
                 command=show_versions1_tab)
button_versions1.pack(pady=10)

button_versions2 = Button(versions_tab,
                 text='V. Beta.2 ⚡',
                 width=12, height=1,
                 bg='white', fg='#005d92',
                 font='Arial 16',
                 borderwidth=2,
                 relief="ridge",
                 command=show_versions2_tab)
button_versions2.pack(pady=10)

button_versions3 = Button(versions_tab,
                 text='V. Beta.1.1 ⚡',
                 width=12, height=1,
                 bg='white', fg='#005d92',
                 font='Arial 16',
                 borderwidth=2,
                 relief="ridge",
                 command=show_versions3_tab)
button_versions3.pack(pady=10)

button_versions4 = Button(versions_tab,
                 text='V. Beta.1.2 ⚡',
                 width=12, height=1,
                 bg='white', fg='#005d92',
                 font='Arial 16',
                 borderwidth=2,
                 relief="ridge",
                 command=show_versions4_tab)
button_versions4.pack(pady=10)

button_versions5 = Button(versions_tab,
                 text='Release V.1.0',
                 width=18, height=1,
                 bg='white', fg='#005d92',
                 font='Arial 16',
                 borderwidth=2,
                 relief="ridge",
                 command=show_versions5_tab)
button_versions5.pack(pady=10)






button_autor = Button(other_tab,
                 text='Автори',
                 width=18, height=1,
                 bg='white', fg='#005d92',
                 font='Arial 19',
                 borderwidth=2,
                 relief="ridge",
                 command=show_autor_tab)
button_autor.pack(pady=10)

transparent_label = Label(autor_tab, text="Автори", bg=hex_color, fg="white",
                          highlightbackground=hex_color, highlightcolor=hex_color, font='Arial 16')
transparent_label.pack(pady=10)

frame_back_autor = Frame(autor_tab)
frame_back_autor.pack(anchor='nw', padx=5, pady=5)

def back_to_other_from_autor():
    notebook.select(other_tab)

button_back_autor = Button(frame_back_autor, text="← Назад", command=back_to_other_from_autor)
button_back_autor.pack(side=LEFT)

button_support = Button(other_tab,
                 text='Техпідтримка',
                 width=18, height=1,
                 bg='white', fg='#005d92',
                 font='Arial 19',
                 borderwidth=2,
                 relief="ridge",
                 command=show_support_tab)
button_support.pack(pady=10)

transparent_label = Label(support_tab, text="Техпідтримка", bg=hex_color, fg="white",
                          highlightbackground=hex_color, highlightcolor=hex_color, font='Arial 16')
transparent_label.pack(pady=10)

frame_back_support = Frame(support_tab)
frame_back_support.pack(anchor='nw', padx=5, pady=5)

def back_to_other_from_support():
    notebook.select(other_tab)

button_back_support = Button(frame_back_support, text="← Назад", command=back_to_other_from_versions)
button_back_support.pack(side=LEFT)

transparent_label = Label(support_tab, text='''Тел. +380 99 205 ** **  ㅤㅤㅤㅤㅤㅤㅤㅤㅤ
Пошта. sushikev****@gmail.comㅤㅤㅤㅤㅤ''', bg=hex_color, fg="white",
                          highlightbackground=hex_color, highlightcolor=hex_color, font='Arial 16')
transparent_label.pack(pady=10)

button_week_schedule = Button(submenu_tab,
                 text='Розклад по дням тиждня',
                 width=25, height=2,
                 bg='white', fg='#005d92',
                 font='Arial 16',
                 borderwidth=2,
                 relief="ridge",
                 command=show_week_schedule_tab)
button_week_schedule.pack(pady=10)

transparent_label = Label(week_schedule_tab, text="Розклад по дням тиждня", bg=hex_color, fg="white",
                          highlightbackground=hex_color, highlightcolor=hex_color, font='Arial 16')
transparent_label.pack(pady=10)

def back_to_submenu_from_week_schedule():
    notebook.select(submenu_tab)

frame_back_week_schedule = Frame(week_schedule_tab)
frame_back_week_schedule.pack(anchor='nw', padx=5, pady=5)

def back_to_submenu_from_week_schedule():
    notebook.select(submenu_tab)

button_back_week_schedule = Button(frame_back_week_schedule, text="← Назад", command=back_to_submenu_from_week_schedule)
button_back_week_schedule.pack(side=LEFT)

button_all_schedule = Button(submenu_tab,
                 text='Весь розклад',
                 width=25, height=2,
                 bg='white', fg='#005d92',
                 font='Arial 16',
                 borderwidth=2,
                 relief="ridge",
                 command=show_all_schedule_tab)
button_all_schedule.pack(pady=10)

transparent_label = Label(all_schedule_tab, text="Весь розклад", bg=hex_color, fg="white",
                          highlightbackground=hex_color, highlightcolor=hex_color, font='Arial 16')
transparent_label.pack(pady=10)

frame_back_all_schedule = Frame(all_schedule_tab)
frame_back_all_schedule.pack(anchor='nw', padx=5, pady=5)

def back_to_submenu_from_all_schedule():
    notebook.select(submenu_tab)

button_back_all_schedule = Button(frame_back_all_schedule, text="← Назад", command=back_to_submenu_from_all_schedule)
button_back_all_schedule.pack(side=LEFT)

button_list_teachers = Button(submenu_tab,
                 text='Список викладачів',
                 width=25, height=2,
                 bg='white', fg='#005d92',
                 font='Arial 16',
                 borderwidth=2,
                 relief="ridge",
                 command=show_list_teachers_tab)
button_list_teachers.pack(pady=10)

transparent_label = Label(list_teachers_tab, text="Список викладачів", bg=hex_color, fg="white",
                          highlightbackground=hex_color, highlightcolor=hex_color, font='Arial 16')
transparent_label.pack(pady=10)

frame_back_list_teachers = Frame(list_teachers_tab)
frame_back_list_teachers.pack(anchor='nw', padx=5, pady=5)

def back_to_submenu_from_list_teachers():
    notebook.select(submenu_tab)

button_back_list_teachers = Button(frame_back_list_teachers, text="← Назад", command=back_to_submenu_from_list_teachers)
button_back_list_teachers.pack(side=LEFT)

button_items = Button(submenu_tab,
                 text='Предмети',
                 width=25, height=2,
                 bg='white', fg='#005d92',
                 font='Arial 16',
                 borderwidth=2,
                 relief="ridge",
                 command=show_items_tab)
button_items.pack(pady=10)

transparent_label = Label(items_tab, text="Предмети", bg=hex_color, fg="white",
                          highlightbackground=hex_color, highlightcolor=hex_color, font='Arial 16')
transparent_label.pack(pady=10)

frame_back_items = Frame(items_tab)
frame_back_items.pack(anchor='nw', padx=5, pady=5)

def back_to_submenu_from_items():
    notebook.select(submenu_tab)

button_back_items = Button(frame_back_items, text="← Назад", command=back_to_submenu_from_items)
button_back_items.pack(side=LEFT)

root.mainloop()

