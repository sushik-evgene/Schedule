from tkinter import *                           # Подключаем модули
from tkinter import ttk                         # |
from PIL import Image, ImageTk                  # |
from tkinter.scrolledtext import ScrolledText

def show_week_schedule_tab():                  # Вкладка Розклад по дням тиждня
    notebook.select(week_schedule_tab)
def show_all_schedule_tab():                   # Вкладка Весь розкла
    notebook.select(all_schedule_tab)
def show_submenu_tab():                        # Вкладка Меню
    notebook.select(submenu_tab)
def show_other_tab():                          # Вкладка Інше
    notebook.select(other_tab)
def show_menu_tab():                           # Вкладка  Головне меню
    notebook.select(menu_tab)
def show_list_teachers_tab():
    notebook.select(list_teachers_tab)
def show_items_tab():
    notebook.select(items_tab)


def set_tab_background(tab, image):
    tab_label = Label(tab, image=image)
    tab_label.place(x=0, y=0, relwidth=1, relheight=1)

root = Tk()                                    # Создаем окно
root.geometry("450x650+100+100")               # Задаем размеры (Ширина)-(Высота) Место появления окна
root.resizable(False, False)                   # Блокируем возможность изменения окна (Ширина)-(Высота)
root.title('IT - Schedule')                   # Даем название окну

background_submenu_image = PhotoImage(file="C:/IT-Schedule/img1/background_submenu.gif")
background_other_image = PhotoImage(file="C:/IT-Schedule/img1/background_other.gif")
background_menu_image = PhotoImage(file="C:/IT-Schedule/img1/background_menu.gif")
background_week_schedule_image = PhotoImage(file="C:/IT-Schedule/img1/background_week_schedule.gif")
background_all_schedule_image = PhotoImage(file="C:/IT-Schedule/img1/background_schedule_all.gif")

image_back_menu = Image.open("C:/IT-Schedule/img1/back_submenu.jpg")                         # | С трелка назад
image_back_all_schedule = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_week_schedule = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_other = Image.open("C:/IT-Schedule/img1/back_submenu.jpg")

button_week_schedule_image = Image.open("C:/IT-Schedule/img1/button_week_schedule.jpg")
button_all_schedule_image = Image.open("C:/IT-Schedule/img1/button_all_schedule.jpg")
button_monday_image = Image.open("C:/IT-Schedule/img1/button_monday.jpg")
button_tuesday_image = Image.open("C:/IT-Schedule/img1/button_tuesday.jpg")
button_wednesday_image = Image.open("C:/IT-Schedule/img1/button_wednesday.jpg")
button_thursday_image = Image.open("C:/IT-Schedule/img1/button_thursday.jpg")
button_friday_image = Image.open("C:/IT-Schedule/img1/button_friday.jpg")

button_list_teachers_image = Image.open("C:/IT-Schedule/img1/button_list_teachers.jpg")
button_items_image = Image.open("C:/IT-Schedule/img1/button_items.jpg")

'''button_schedule_tab_image = Image.open("C:/IT-Schedule/img1/schedule_tab.jpg")'''


button_other_tab_image = Image.open("C:/IT-Schedule/img1/other_tab.jpg")
button_menu_tab_image = Image.open("C:/IT-Schedule/img1/menu_tab.jpg")

style = ttk.Style()                        # Создаем стиль для скрытия фона и заголовка верхней панели
style.layout("TNotebook.Tab", [])          # Пустой layout убирает заголовок

notebook = ttk.Notebook(root)              # Какая-то херня я не разобрался...
notebook.pack(fill="both", expand=True)    # |

submenu_tab = Frame(notebook)              # | Меню
menu_tab = Frame(notebook)                 # | Меню
other_tab = Frame(notebook)                # | Інше
week_schedule_tab = Frame(notebook)        # | Розклад по дням тиждня
all_schedule_tab = Frame(notebook)         # | Весь розклад


set_tab_background(submenu_tab, background_submenu_image)
set_tab_background(other_tab, background_other_image)
set_tab_background(menu_tab, background_menu_image)
set_tab_background(week_schedule_tab, background_week_schedule_image)
set_tab_background(all_schedule_tab, background_all_schedule_image)



notebook.add(submenu_tab)                  # | Головна
notebook.add(other_tab)                    # | Розклад по дням тиждня
notebook.add(menu_tab)                     # | Меню
notebook.add(week_schedule_tab)            # | Розклад по дням тиждня
notebook.add(all_schedule_tab)             # | Весь розклад



label = Label(submenu_tab, text="ㅤ", font='e-Ukraine 16', background="#c6d4cb")
label.pack(pady=55)

new_size_button_week_schedule = (380, 150)                      # Новый размер (ширина, высота)
button_week_schedule_image = button_week_schedule_image.resize(new_size_button_week_schedule)

photo_button_week_schedule = ImageTk.PhotoImage(button_week_schedule_image)

button_week_schedule = Button(submenu_tab,
                      image=photo_button_week_schedule,
                      borderwidth=0,
                      activebackground="#c6d4cb",
                      activeforeground="#c6d4cb",
                      relief="flat", highlightthickness=0,
                      command=show_week_schedule_tab)
button_week_schedule.pack(pady=0)


frame_back_week_schedule = Frame(week_schedule_tab)
frame_back_week_schedule.pack(anchor='nw', padx=25, pady=28)

def back_to_submenu_from_week_schedule():
    notebook.select(submenu_tab)

new_size_back_week_schedule = (25, 22)                      # Новый размер (ширина, высота)
image_back_week_schedule = image_back_week_schedule.resize(new_size_back_week_schedule)

photo_back_week_schedule = ImageTk.PhotoImage(image_back_week_schedule)

button_back_week_schedule = Button(frame_back_week_schedule, image=photo_back_week_schedule, borderwidth=-4,
activebackground="#dfe7f2", activeforeground="#dfe7f2", relief="flat", highlightthickness=0, command=back_to_submenu_from_week_schedule)
button_back_week_schedule.pack(side=LEFT)


label = Label(week_schedule_tab, text="ㅤ", font='Arial 1', background="#dfe7f2")
label.pack(padx=1, pady=0)


new_size_button_monday = (370, 100)                      # Новый размер (ширина, высота)
button_monday_image = button_monday_image.resize(new_size_button_monday)

photo_button_monday = ImageTk.PhotoImage(button_monday_image)

button_monday = Button(week_schedule_tab,
                      image=photo_button_monday,
                      borderwidth=0,
                      activebackground="#dfe7f2",
                      activeforeground="#dfe7f2",
                      relief="flat", highlightthickness=0)
button_monday.pack(pady=1)



new_size_button_tuesday = (370, 100)                      # Новый размер (ширина, высота)
button_tuesday_image = button_tuesday_image.resize(new_size_button_tuesday)

photo_button_tuesday = ImageTk.PhotoImage(button_tuesday_image)

button_tuesday = Button(week_schedule_tab,
                      image=photo_button_tuesday,
                      borderwidth=0,
                      activebackground="#dfe7f2",
                      activeforeground="#dfe7f2",
                      relief="flat", highlightthickness=0)
button_tuesday.pack(pady=1)



new_size_button_wednesday = (370, 100)                      # Новый размер (ширина, высота)
button_wednesday_image = button_wednesday_image.resize(new_size_button_wednesday)

photo_button_wednesday = ImageTk.PhotoImage(button_wednesday_image)

button_wednesday = Button(week_schedule_tab,
                      image=photo_button_wednesday,
                      borderwidth=0,
                      activebackground="#dfe7f2",
                      activeforeground="#dfe7f2",
                      relief="flat", highlightthickness=0)
button_wednesday.pack(pady=1)



new_size_button_thursday = (370, 100)                      # Новый размер (ширина, высота)
button_thursday_image = button_thursday_image.resize(new_size_button_thursday)

photo_button_thursday = ImageTk.PhotoImage(button_thursday_image)

button_thursday = Button(week_schedule_tab,
                      image=photo_button_thursday,
                      borderwidth=0,
                      activebackground="#dfe7f2",
                      activeforeground="#dfe7f2",
                      relief="flat", highlightthickness=0)
button_thursday.pack(pady=1)



new_size_button_friday = (370, 100)                      # Новый размер (ширина, высота)
button_friday_image = button_friday_image.resize(new_size_button_friday)

photo_button_friday = ImageTk.PhotoImage(button_friday_image)

button_friday = Button(week_schedule_tab,
                      image=photo_button_friday,
                      borderwidth=0,
                      activebackground="#dfe7f2",
                      activeforeground="#dfe7f2",
                      relief="flat", highlightthickness=0)
button_friday.pack(pady=1)


new_size_button_all_schedule = (380, 170)                      # Новый размер (ширина, высота)
button_all_schedule_image = button_all_schedule_image.resize(new_size_button_all_schedule)

photo_button_all_schedule = ImageTk.PhotoImage(button_all_schedule_image)

button_all_schedule = Button(submenu_tab,
                      image=photo_button_all_schedule,
                      borderwidth=0,
                      activebackground="#c6d4cb",
                      activeforeground="#c6d4cb",
                      relief="flat", highlightthickness=0,
                      command=show_all_schedule_tab)
button_all_schedule.pack(anchor='nw', padx=33, pady=3)



frame_back_all_schedule = Frame(all_schedule_tab)
frame_back_all_schedule.pack(anchor='nw', padx=25, pady=28)


def back_to_submenu_from_all_schedule():
    notebook.select(submenu_tab)

new_size_back_all_schedule = (25, 22)                      # Новый размер (ширина, высота)
image_back_all_schedule = image_back_all_schedule.resize(new_size_back_all_schedule)

photo_back_all_schedule = ImageTk.PhotoImage(image_back_all_schedule)

button_back_all_schedule = Button(frame_back_all_schedule, image=photo_back_all_schedule, borderwidth=-4,
activebackground="#dfe7f2", activeforeground="#dfe7f2", relief="flat", highlightthickness=0, command=back_to_submenu_from_all_schedule)
button_back_all_schedule.pack(side=LEFT)


# ВЕСЬ РАЗДЕЛ РАСПИСАНИЕ
label = Label(submenu_tab, text="ㅤ", font='Arial 12', background="#c6d4cb")
label.pack(pady=38)

new_size_button_menu_tab = (50, 60)                      # Новый размер (ширина, высота)
button_menu_tab_image = button_menu_tab_image.resize(new_size_button_menu_tab)

photo_button_menu_tab = ImageTk.PhotoImage(button_menu_tab_image)

button_menu_tab1 = Button(submenu_tab,
                      image=photo_button_menu_tab,
                      borderwidth=0,
                      activebackground="#c6d4cb",
                      activeforeground="#c6d4cb",
                      relief="flat", highlightthickness=0,
                      command=show_menu_tab)


new_size_button_other_tab = (38, 53)                      # Новый размер (ширина, высота)
button_other_tab_image = button_other_tab_image.resize(new_size_button_other_tab)

photo_button_other_tab = ImageTk.PhotoImage(button_other_tab_image)

button_other_tab1 = Button(submenu_tab,
                      image=photo_button_other_tab,
                      borderwidth=0,
                      activebackground="#c6d4cb",
                      activeforeground="#c6d4cb",
                      relief="flat", highlightthickness=0,
                      command=show_other_tab)



button2 = Button(submenu_tab, text="Кнопка 1")

button_menu_tab1.pack(side="right", padx=30)
button2.pack(side="right", padx=30)
button_other_tab1.pack(side="right", padx=25)



# ВСЯ ВКЛАДКА ІНШЕ
label = Label(other_tab, text="ㅤ", font='e-Ukraine 1', background="#c6d9e8")
label.pack(pady=67)

new_size_button_list_teachers = (380, 150)                      # Новый размер (ширина, высота)
button_list_teachers_image = button_list_teachers_image.resize(new_size_button_list_teachers)

photo_button_list_teachers = ImageTk.PhotoImage(button_list_teachers_image)

button_list_teachers = Button(other_tab,
                      image=photo_button_list_teachers,
                      borderwidth=0,
                      activebackground="#e3edf5",
                      activeforeground="#e3edf5",
                      relief="flat", highlightthickness=0,
                      command=show_list_teachers_tab)
button_list_teachers.pack(pady=0)


new_size_button_items = (380, 170)                      # Новый размер (ширина, высота)
button_items_image = button_items_image.resize(new_size_button_items)

photo_button_items = ImageTk.PhotoImage(button_items_image)

button_items = Button(other_tab,
                      image=photo_button_items,
                      borderwidth=0,
                      activebackground="#e3edf5",
                      activeforeground="#e3edf5",
                      relief="flat", highlightthickness=0,
                      command=show_items_tab)
button_items.pack(anchor='nw', padx=33, pady=0)

label = Label(other_tab, text="ㅤ", font='Arial 12', background="#e3edf5")
label.pack(pady=38)

button3 = Button(other_tab, text="Меню", command=show_menu_tab)
button21 = Button(other_tab, text="Кнопка 2")
button1 = Button(other_tab, text="Розклад", command=show_submenu_tab)

button3.pack(side="right", padx=26)
button21.pack(side="right", padx=22)
button1.pack(side="left", padx=40)



# ВСЯ ВКЛАДКА МЕНЮ





root.mainloop()


# В ближайших обновлениях добавить возможность подания всего расписания по недельно по месячно или весь
#
#
#
#
#
#
