from tkinter import *                          # Подключаем модули
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
def show_question_tab():
    notebook.select(question_tab)


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
background_question_image = PhotoImage(file="C:/IT-Schedule/img1/background_question_answer.gif")
background_list_teachers_image = PhotoImage(file="C:/IT-Schedule/img1/background_list_teachers.gif")


image_back_all_schedule = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_week_schedule = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_question = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_list_teachers = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")


button_week_schedule_image = Image.open("C:/IT-Schedule/img1/button_week_schedule.jpg")
button_all_schedule_image = Image.open("C:/IT-Schedule/img1/button_all_schedule.jpg")
button_monday_image = Image.open("C:/IT-Schedule/img1/button_monday.jpg")
button_tuesday_image = Image.open("C:/IT-Schedule/img1/button_tuesday.jpg")
button_wednesday_image = Image.open("C:/IT-Schedule/img1/button_wednesday.jpg")
button_thursday_image = Image.open("C:/IT-Schedule/img1/button_thursday.jpg")
button_friday_image = Image.open("C:/IT-Schedule/img1/button_friday.jpg")

button_functions_image = Image.open("C:/IT-Schedule/img1/button_functions.jpg")
button_question_image = Image.open("C:/IT-Schedule/img1/button_question_answer.jpg")
button_support_image = Image.open("C:/IT-Schedule/img1/button_support.jpg")
button_settings_image = Image.open("C:/IT-Schedule/img1/button_settings.jpg")
button_tell_image = Image.open("C:/IT-Schedule/img1/button_tell.jpg")
button_about_us_image = Image.open("C:/IT-Schedule/img1/button_about_us.jpg")



button_list_teachers_image = Image.open("C:/IT-Schedule/img1/button_list_teachers.jpg")
button_items_image = Image.open("C:/IT-Schedule/img1/button_items.jpg")

'''button_schedule_tab_image = Image.open("C:/IT-Schedule/img1/schedule_tab.jpg")'''


button_schedule_tab_image2 = Image.open("C:/IT-Schedule/img1/schedule_tab1.jpg")
button_schedule_tab_image3 = Image.open("C:/IT-Schedule/img1/schedule_tab1.jpg")

button_other_tab_image1 = Image.open("C:/IT-Schedule/img1/other_tab.jpg")
button_other_tab_image3 = Image.open("C:/IT-Schedule/img1/other_tab1.jpg")

button_menu_tab_image1 = Image.open("C:/IT-Schedule/img1/menu_tab.jpg")
button_menu_tab_image2 = Image.open("C:/IT-Schedule/img1/menu_tab1.jpg")




style = ttk.Style()                        # Создаем стиль для скрытия фона и заголовка верхней панели
style.layout("TNotebook.Tab", [])          # Пустой layout убирает заголовок

notebook = ttk.Notebook(root)              # Какая-то херня я не разобрался...
notebook.pack(fill="both", expand=True)    # |

submenu_tab = Frame(notebook)              # | Меню
menu_tab = Frame(notebook)                 # | Меню
other_tab = Frame(notebook)                # | Інше
week_schedule_tab = Frame(notebook)        # | Розклад по дням тиждня
all_schedule_tab = Frame(notebook)         # | Весь розклад
question_tab = Frame(notebook)
list_teachers_tab = Frame(notebook)

set_tab_background(submenu_tab, background_submenu_image)
set_tab_background(other_tab, background_other_image)
set_tab_background(menu_tab, background_menu_image)
set_tab_background(week_schedule_tab, background_week_schedule_image)
set_tab_background(all_schedule_tab, background_all_schedule_image)
set_tab_background(question_tab, background_question_image)
set_tab_background(list_teachers_tab, background_list_teachers_image)


notebook.add(submenu_tab)                  # | Головна
notebook.add(other_tab)                    # | Розклад по дням тиждня
notebook.add(menu_tab)                     # | Меню
notebook.add(week_schedule_tab)            # | Розклад по дням тиждня
notebook.add(all_schedule_tab)             # | Весь розклад
notebook.add(question_tab)
notebook.add(list_teachers_tab)


# ВСЯ ВКЛАДКА РОЗКЛАД
label = Label(submenu_tab, text="ㅤ", font='e-Ukraine 16', background="#fee698")
label.pack(pady=70)

new_size_button_week_schedule = (380, 150)                      # Новый размер (ширина, высота)
button_week_schedule_image = button_week_schedule_image.resize(new_size_button_week_schedule)

photo_button_week_schedule = ImageTk.PhotoImage(button_week_schedule_image)

button_week_schedule = Button(submenu_tab,
                      image=photo_button_week_schedule,
                      borderwidth=0,
                      activebackground="#fee698",
                      activeforeground="#fee698",
                      relief="flat", highlightthickness=0,
                      command=show_week_schedule_tab)
button_week_schedule.pack(pady=0)


new_size_button_all_schedule = (380, 150)                      # Новый размер (ширина, высота)
button_all_schedule_image = button_all_schedule_image.resize(new_size_button_all_schedule)

photo_button_all_schedule = ImageTk.PhotoImage(button_all_schedule_image)

button_all_schedule = Button(submenu_tab,
                      image=photo_button_all_schedule,
                      borderwidth=0,
                      activebackground="#fee698",
                      activeforeground="#fee698",
                      relief="flat", highlightthickness=0,
                      command=show_all_schedule_tab)
button_all_schedule.pack(anchor='nw', padx=33, pady=3)


label = Label(submenu_tab, text="ㅤ", font='Arial 20', background="#fee698")
label.pack(pady=28)

new_size_button_menu_tab1 = (68, 60)                      # Новый размер (ширина, высота)
button_menu_tab_image1 = button_menu_tab_image1.resize(new_size_button_menu_tab1)

photo_button_menu_tab1 = ImageTk.PhotoImage(button_menu_tab_image1)

button_menu_tab1 = Button(submenu_tab,
                      image=photo_button_menu_tab1,
                      borderwidth=0,
                      activebackground="#fee698",
                      activeforeground="#fee698",
                      relief="flat", highlightthickness=0,
                      command=show_menu_tab)


new_size_button_other_tab1 = (68, 60)                      # Новый размер (ширина, высота)
button_other_tab_image1 = button_other_tab_image1.resize(new_size_button_other_tab1)

photo_button_other_tab1 = ImageTk.PhotoImage(button_other_tab_image1)

button_other_tab1 = Button(submenu_tab,
                      image=photo_button_other_tab1,
                      borderwidth=0,
                      activebackground="#fee698",
                      activeforeground="#fee698",
                      relief="flat", highlightthickness=0,
                      command=show_other_tab)


button_menu_tab1.pack(side="right", padx=37)
button_other_tab1.pack(side="right", padx=47)



# ВКЛАДКА РОЗКЛАД ПО ДНЯМ ТИЖНЯ
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



# ВКЛАДКА ВЕСЬ РОЗКЛАД
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







# ВСЯ ВКЛАДКА ІНШЕ
label = Label(other_tab, text="ㅤ", font='e-Ukraine 16', background="#f6f4f0")
label.pack(pady=70)

new_size_button_list_teachers = (380, 150)                      # Новый размер (ширина, высота)
button_list_teachers_image = button_list_teachers_image.resize(new_size_button_list_teachers)

photo_button_list_teachers = ImageTk.PhotoImage(button_list_teachers_image)

button_list_teachers = Button(other_tab,
                      image=photo_button_list_teachers,
                      borderwidth=0,
                      activebackground="#f6f4f0",
                      activeforeground="#f6f4f0",
                      relief="flat", highlightthickness=0,
                      command=show_list_teachers_tab)
button_list_teachers.pack(pady=0)


new_size_button_items = (380, 150)                      # Новый размер (ширина, высота)
button_items_image = button_items_image.resize(new_size_button_items)

photo_button_items = ImageTk.PhotoImage(button_items_image)

button_items = Button(other_tab,
                      image=photo_button_items,
                      borderwidth=0,
                      activebackground="#f6f4f0",
                      activeforeground="#f6f4f0",
                      relief="flat", highlightthickness=0,
                      command=show_items_tab)
button_items.pack(anchor='nw', padx=33, pady=3)

label = Label(other_tab, text="ㅤ", font='Arial 20', background="#f6f4f0")
label.pack(pady=28)









new_size_button_menu_tab2 = (68, 60)                      # Новый размер (ширина, высота)
button_menu_tab_image2 = button_menu_tab_image2.resize(new_size_button_menu_tab2)

photo_button_menu_tab2 = ImageTk.PhotoImage(button_menu_tab_image2)

button_menu_tab2 = Button(other_tab,
                      image=photo_button_menu_tab2,
                      borderwidth=0,
                      activebackground="white",
                      activeforeground="white",
                      relief="flat", highlightthickness=0,
                      command=show_menu_tab)




button_schedule_tab2 = Button(other_tab, text="Розклад", command=show_submenu_tab)

new_size_button_schedule_tab2 = (68, 60)                      # Новый размер (ширина, высота)
button_schedule_tab_image2 = button_schedule_tab_image2.resize(new_size_button_schedule_tab2)

photo_button_schedule_tab2 = ImageTk.PhotoImage(button_schedule_tab_image2)

button_schedule_tab2 = Button(other_tab,
                      image=photo_button_schedule_tab2,
                      borderwidth=0,
                      activebackground="white",
                      activeforeground="white",
                      relief="flat", highlightthickness=0,
                      command=show_submenu_tab)



button_menu_tab2.pack(side="right", padx=37)
button_schedule_tab2.pack(side="left", padx=38)


# ВКЛАДКА СПИСОК ВИКЛАДАЧІВ
frame_back_list_teachers = Frame(list_teachers_tab)
frame_back_list_teachers.pack(anchor='nw', padx=25, pady=22)

def back_to_submenu_from_list_teachers():
    notebook.select(other_tab)

new_size_back_list_teachers = (18, 25)                      # Новый размер (ширина, высота)
image_back_list_teachers = image_back_list_teachers.resize(new_size_back_list_teachers)

photo_back_list_teachers = ImageTk.PhotoImage(image_back_list_teachers)

button_back_list_teachers = Button(frame_back_list_teachers, image=photo_back_list_teachers, borderwidth=-4,
activebackground="#f6f4f0", activeforeground="#f6f4f0", relief="flat", highlightthickness=0, command=back_to_submenu_from_list_teachers)
button_back_list_teachers.pack(side=LEFT)


# ВСЯ ВКЛАДКА МЕНЮ

label = Label(menu_tab, text="ㅤ", font='e-Ukraine 1', background="#c6d9e8")
label.pack(pady=35)


new_size_button_functions = (450, 68)                      # Новый размер (ширина, высота)
button_functions_image = button_functions_image.resize(new_size_button_functions)

photo_button_functions = ImageTk.PhotoImage(button_functions_image)

button_functions = Button(menu_tab,
                      image=photo_button_functions,
                      borderwidth=0,
                      activebackground="#e3edf5",
                      activeforeground="#e3edf5",
                      relief="flat", highlightthickness=0)
button_functions.pack(pady=0)



new_size_button_question = (450, 66)                      # Новый размер (ширина, высота)
button_question_image = button_question_image.resize(new_size_button_question)

photo_button_question = ImageTk.PhotoImage(button_question_image)

button_question = Button(menu_tab,
                      image=photo_button_question,
                      borderwidth=0,
                      activebackground="#e3edf5",
                      activeforeground="#e3edf5",
                      relief="flat", highlightthickness=0,
                      command=show_question_tab)
button_question.pack(pady=0)



new_size_button_support = (450, 52)                      # Новый размер (ширина, высота)
button_support_image = button_support_image.resize(new_size_button_support)

photo_button_support = ImageTk.PhotoImage(button_support_image)

button_support = Button(menu_tab,
                      image=photo_button_support,
                      borderwidth=0,
                      activebackground="#e3edf5",
                      activeforeground="#e3edf5",
                      relief="flat", highlightthickness=0)
button_support.pack(pady=0)



new_size_button_settings = (450, 38)                      # Новый размер (ширина, высота)
button_settings_image = button_settings_image.resize(new_size_button_settings)

photo_button_settings = ImageTk.PhotoImage(button_settings_image)

button_settings = Button(menu_tab,
                      image=photo_button_settings,
                      borderwidth=0,
                      activebackground="#e3edf5",
                      activeforeground="#e3edf5",
                      relief="flat", highlightthickness=0)
button_settings.pack(anchor='nw', padx=5,pady=32)



new_size_button_tell = (450, 52)                      # Новый размер (ширина, высота)
button_tell_image = button_tell_image.resize(new_size_button_tell)

photo_button_tell = ImageTk.PhotoImage(button_tell_image)

button_tell = Button(menu_tab,
                      image=photo_button_tell,
                      borderwidth=0,
                      activebackground="#e3edf5",
                      activeforeground="#e3edf5",
                      relief="flat", highlightthickness=0)
button_tell.pack(pady=5)



def open_new_window():
    new_window = Toplevel(root)  # Создаем новое окно
    new_window.geometry("1325x725+90+30")  # Задаем размеры (Ширина)-(Высота) Место появления окна
    new_window.resizable(False, False)
    new_window.title("Про НАс")

    label5 = Label(new_window, text='''
    Это новое окно 
    
    Тут я захерачу красивое оформление и все о проекте ''', font='e-Ukraine 20')
    label5.pack()


new_size_button_about_us = (450, 50)                      # Новый размер (ширина, высота)
button_about_us_image = button_about_us_image.resize(new_size_button_about_us)

photo_button_about_us = ImageTk.PhotoImage(button_about_us_image)

button_about_us = Button(menu_tab,
                         image=photo_button_about_us,
                         borderwidth=0,
                         activebackground="#e3edf5",
                         activeforeground="#e3edf5",
                         relief="flat", highlightthickness=0,
                         command=open_new_window)  # Правильное местоположение скобок
button_about_us.pack(pady=0)




label = Label(menu_tab, text="ㅤ", font='Arial 12', background="#e3edf5")
label.pack(pady=30)

button14 = Button(menu_tab, text="Розклад", command=show_submenu_tab)
button24 = Button(menu_tab, text="Інше", command=show_other_tab)
button34 = Button(menu_tab, text="Кнопка" )


button14.pack(side="left", padx=52)
button24.pack(side="left", padx=12)
button34.pack(side="left", padx=45)



# ВКЛАДКА ПИТАННЯ ТА ВЫДПОВІ
frame_back_question = Frame(question_tab)
frame_back_question.pack(anchor='nw', padx=25, pady=22)

def back_to_submenu_from_question():
    notebook.select(menu_tab)

new_size_back_question = (18, 25)                      # Новый размер (ширина, высота)
image_back_question = image_back_question.resize(new_size_back_question)

photo_back_question = ImageTk.PhotoImage(image_back_question)

button_back_question = Button(frame_back_question, image=photo_back_question, borderwidth=-4,
activebackground="#dfe7f2", activeforeground="#dfe7f2", relief="flat", highlightthickness=0, command=back_to_submenu_from_question)
button_back_question.pack(side=LEFT)


root.mainloop()


# В ближайших обновлениях добавить возможность подания всего расписания по недельно по месячно или весь
