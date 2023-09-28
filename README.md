from tkinter import *
from tkinter import ttk
from tkinter import messagebox
from PIL import Image, ImageTk
from tkinter.scrolledtext import ScrolledText
import tkinter as tk
import webbrowser
import pyperclip
from datetime import datetime, timedelta
from plyer import notification
from tkinter import Tk, Label, font
import openpyxl
import schedule

# Открываем Excel-файл
excel_file_path = "C:/IT-Schedule/table.xlsx"
workbook = openpyxl.load_workbook(excel_file_path)

# Указываем имя страницы, с которой нужно загрузить данные
initial_sheet_name = "1"
target_sheet_name = "2"

# Получаем объект страницы
sheet = workbook[initial_sheet_name]

# Получаем значение из клетки J1 (предполагается, что это дата)
date_in_cell = sheet["J1"].value

# Проверяем, если значение из клетки J1 - это дата
if isinstance(date_in_cell, datetime):
    # Получаем текущую дату
    current_date = datetime.now().date()

    # Сравниваем текущую дату с датой из клетки J1
    if current_date > date_in_cell.date():
        # Переключаемся на целевую страницу Excel
        sheet = workbook[target_sheet_name]

def show_week_schedule_tab():
    notebook.select(week_schedule_tab)
def show_all_schedule_tab():
    notebook.select(all_schedule_tab)
def show_submenu_tab():  # Вкладка Меню
    notebook.select(submenu_tab)
def show_other_tab():
    notebook.select(other_tab)
def show_menu_tab():  # Вкладка  Головне меню
    notebook.select(menu_tab)
def show_list_teachers_tab():
    notebook.select(list_teachers_tab)
def show_items_tab():
    notebook.select(items_tab)
def show_question_tab():
    notebook.select(question_tab)
def show_support_tab():
    notebook.select(support_tab)
def show_tell_tab():
    notebook.select(tell_tab)
def show_settings_tab():
    notebook.select(settings_tab)
def show_functions1_tab():
    notebook.select(functions1_tab)
def show_functions2_tab():
    notebook.select(functions2_tab)
def show_functions3_tab():
    notebook.select(functions3_tab)
def show_functions4_tab():
    notebook.select(functions4_tab)

def show_ukrainian_language_tab1():
    notebook.select(ukrainian_language_tab1)
def show_ukrainian_literature_tab1():
    notebook.select(ukrainian_literature_tab1)
def show_english_tab1():
    notebook.select(english_tab1)
def show_history_tab1():
    notebook.select(history_tab1)
def show_economy_tab1():
    notebook.select(economy_tab1)
def show_mathematics_tab1():
    notebook.select(mathematics_tab1)
def show_physics_tab1():
    notebook.select(physics_tab1)
def show_astronomy_tab1():
    notebook.select(astronomy_tab1)
def show_biology_tab1():
    notebook.select(biology_tab1)
def show_pt_tab1():
    notebook.select(pt_tab1)
def show_it_tab1():
    notebook.select(it_tab1)
def show_programming_tab1():
    notebook.select(programming_tab1)
def show_amo_tab1():
    notebook.select(amo_tab1)
def show_ls_tab1():
    notebook.select(ls_tab1)




def show_monday_tab():
    notebook.select(monday_tab)
def show_tuesday_tab():
    notebook.select(tuesday_tab)
def show_wednesday_tab():
    notebook.select(wednesday_tab)
def show_thursday_tab():
    notebook.select(thursday_tab)
def show_friday_tab():
    notebook.select(friday_tab)

def show_ukrainian_language_tab():
    notebook.select(ukrainian_language_tab)
def show_ukrainian_literature_tab():
    notebook.select(ukrainian_literature_tab)
def show_english_tab():
    notebook.select(english_tab)
def show_history_tab():
    notebook.select(history_tab)
def show_economy_tab():
    notebook.select(economy_tab)
def show_mathematics_tab():
    notebook.select(mathematics_tab)
def show_physics_tab():
    notebook.select(physics_tab)
def show_astronomy_tab():
    notebook.select(astronomy_tab)
def show_biology_tab():
    notebook.select(biology_tab)
def show_pt_tab():
    notebook.select(pt_tab)
def show_it_tab():
    notebook.select(it_tab)
def show_programming_tab():
    notebook.select(programming_tab)
def show_amo_tab():
    notebook.select(amo_tab)
def show_ls_tab():
    notebook.select(ls_tab)



def set_tab_background(tab, image):
    tab_label = Label(tab, image=image)
    tab_label.place(x=0, y=0, relwidth=1, relheight=1)


# Время начала пар
class_times = ["08:25", "09:55", "11:25", "13:05"]

# Переменная для отслеживания состояния уведомлений
notifications_enabled = True


# Функция для проверки, есть ли пара через 5 минут
def check_class():
    current_time = datetime.now().strftime("%H:%M")
    current_day = datetime.now().weekday()  # Получаем текущий день недели (0 - понедельник, 6 - воскресенье)

    # Проверяем, что сегодня не суббота (5) и не воскресенье (6)
    if current_day != 5 and current_day != 6 and notifications_enabled:
        if current_time in class_times:
            notification_title = "Попередження"
            notification_text = f"За 5 хвилин почнеться пара!"
            notification.notify(
                title=notification_title,
                message=notification_text,
                timeout=10  # Время отображения уведомления (в секундах)
            )
    root.after(30000, check_class)  # Проверка каждую минуту


def toggle_notifications():
    global notifications_enabled
    notifications_enabled = not notifications_enabled
    if notifications_enabled:
        toggle_button.config(image=button_enable_image,
                             width=smaller_button_width,
                             height=smaller_button_height,
                             borderwidth=0,
                             activebackground="#f6f4f0",
                             activeforeground="#f6f4f0",
                             relief="flat", highlightthickness=0)
    else:
        toggle_button.config(image=button_disable_image,
                             width=smaller_button_width,
                             height=smaller_button_height,
                             borderwidth=0,
                             activebackground="#f6f4f0",
                             activeforeground="#f6f4f0",
                             relief="flat", highlightthickness=0)


# Функция для обновления вида кнопки на основе состояния
def update_button():
    if confirm_exit.get():
        confirm_button.config(image=button_enable_image, compound="left")
    else:
        confirm_button.config(image=button_disable_image, compound="left")


root = Tk()  # Создаем окно
root.geometry("450x650+100+100")  # Задаем размеры (Ширина)-(Высота) Место появления окна
root.resizable(False, False)  # Блокируем возможность изменения окна (Ширина)-(Высота)
root.title('#IT - Schedule')

background_submenu_image = PhotoImage(file="C:/IT-Schedule/img1/background_submenu.gif")
background_other_image = PhotoImage(file="C:/IT-Schedule/img1/background_other.gif")
background_menu_image = PhotoImage(file="C:/IT-Schedule/img1/background_menu.gif")
background_week_schedule_image = PhotoImage(file="C:/IT-Schedule/img1/background_week_schedule.gif")
background_all_schedule_image = PhotoImage(file="C:/IT-Schedule/img1/background_schedule_all.gif")
background_question_image = PhotoImage(file="C:/IT-Schedule/img1/background_question_answer.gif")
background_list_teachers_image = PhotoImage(file="C:/IT-Schedule/img1/background_list_teachers.gif")
background_support_image = PhotoImage(file="C:/IT-Schedule/img1/background_support.gif")
background_tell_image = PhotoImage(file="C:/IT-Schedule/img1/background_tell.gif")
background_items_image = PhotoImage(file="C:/IT-Schedule/img1/background_items.gif")
background_settings_image = PhotoImage(file="C:/IT-Schedule/img1/background_settings.gif")

background_functions1_image = PhotoImage(file="C:/IT-Schedule/img1/background_functions1.gif")
background_functions2_image = PhotoImage(file="C:/IT-Schedule/img1/background_functions2.gif")
background_functions3_image = PhotoImage(file="C:/IT-Schedule/img1/background_functions3.gif")
background_functions4_image = PhotoImage(file="C:/IT-Schedule/img1/background_functions4.gif")

background_ukrainian_language_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_ukrainian_language.gif")
background_ukrainian_literature_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_ukrainian_literature.gif")
background_english_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_english.gif")
background_history_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_history.gif")
background_economy_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_economy.gif")
background_mathematics_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_mathematics.gif")
background_physics_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_physics.gif")
background_astronomy_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_astronomy.gif")
background_biology_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_biology.gif")
background_pt_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_pt.gif")
background_it_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_it.gif")
background_programming_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_programming.gif")
background_amo_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_amo.gif")
background_ls_image1 = PhotoImage(file="C:/IT-Schedule/img1/background_ls.gif")

background_ukrainian_language_image = PhotoImage(file="C:/IT-Schedule/img1/background_ukrainian_language.gif")
background_ukrainian_literature_image = PhotoImage(file="C:/IT-Schedule/img1/background_ukrainian_literature.gif")
background_english_image = PhotoImage(file="C:/IT-Schedule/img1/background_english.gif")
background_history_image = PhotoImage(file="C:/IT-Schedule/img1/background_history.gif")
background_economy_image = PhotoImage(file="C:/IT-Schedule/img1/background_economy.gif")
background_mathematics_image = PhotoImage(file="C:/IT-Schedule/img1/background_mathematics.gif")
background_physics_image = PhotoImage(file="C:/IT-Schedule/img1/background_physics.gif")
background_astronomy_image = PhotoImage(file="C:/IT-Schedule/img1/background_astronomy.gif")
background_biology_image = PhotoImage(file="C:/IT-Schedule/img1/background_biology.gif")
background_pt_image = PhotoImage(file="C:/IT-Schedule/img1/background_pt.gif")
background_it_image = PhotoImage(file="C:/IT-Schedule/img1/background_it.gif")
background_programming_image = PhotoImage(file="C:/IT-Schedule/img1/background_programming.gif")
background_amo_image = PhotoImage(file="C:/IT-Schedule/img1/background_amo.gif")
background_ls_image = PhotoImage(file="C:/IT-Schedule/img1/background_ls.gif")


background_monday_image = PhotoImage(file="C:/IT-Schedule/img1/background_monday.gif")
background_tuesday_image = PhotoImage(file="C:/IT-Schedule/img1/background_tuesday.gif")
background_wednesday_image = PhotoImage(file="C:/IT-Schedule/img1/background_wednesday.gif")
background_thursday_image = PhotoImage(file="C:/IT-Schedule/img1/background_thursday.gif")
background_friday_image = PhotoImage(file="C:/IT-Schedule/img1/background_friday.gif")



image_back_all_schedule = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_week_schedule = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_question = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_list_teachers = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_support = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_items = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_settings = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_tell = Image.open("C:/IT-Schedule/img1/back_tell.jpg")

image_back_monday = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_tuesday = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_wednesday = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_thursday = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")
image_back_friday = Image.open("C:/IT-Schedule/img1/back_schedule_all.jpg")

button_list_teachers_image = Image.open("C:/IT-Schedule/img1/button_list_teachers.jpg")
button_items_image = Image.open("C:/IT-Schedule/img1/button_items.jpg")
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
button_share_image = Image.open("C:/IT-Schedule/img1/button_tell1.jpg")
button_about_us_image = Image.open("C:/IT-Schedule/img1/button_about_us.jpg")

button_go_support1_image = Image.open("C:/IT-Schedule/img1/button_go1.jpg")
button_go_support2_image = Image.open("C:/IT-Schedule/img1/button_go2.jpg")
button_go_support3_image = Image.open("C:/IT-Schedule/img1/button_go3.jpg")

button_schedule_tab_image2 = Image.open("C:/IT-Schedule/img1/schedule_tab1.jpg")
button_schedule_tab_image3 = Image.open("C:/IT-Schedule/img1/schedule_tab1.jpg")
button_other_tab_image1 = Image.open("C:/IT-Schedule/img1/other_tab.jpg")
button_other_tab_image3 = Image.open("C:/IT-Schedule/img1/other_tab1.jpg")
button_menu_tab_image1 = Image.open("C:/IT-Schedule/img1/menu_tab.jpg")
button_menu_tab_image2 = Image.open("C:/IT-Schedule/img1/menu_tab1.jpg")

button_functions1_close_image = Image.open("C:/IT-Schedule/img1/button_functions_close.jpg")
button_functions2_close_image = Image.open("C:/IT-Schedule/img1/button_functions_close.jpg")
button_functions3_close_image = Image.open("C:/IT-Schedule/img1/button_functions_close.jpg")

button_functions1_further_image = Image.open("C:/IT-Schedule/img1/button_functions_further.jpg")
button_functions2_further_image = Image.open("C:/IT-Schedule/img1/button_functions_further.jpg")
button_functions3_further_image = Image.open("C:/IT-Schedule/img1/button_functions_further.jpg")
button_functions4_further_image = Image.open("C:/IT-Schedule/img1/button_functions_further1.jpg")

button_items_ukrainian_language_image = Image.open("C:/IT-Schedule/img1/button_items_ukrainian_language.jpg")
button_items_ukrainian_literature_image = Image.open("C:/IT-Schedule/img1/button_items_ukrainian_literature.jpg")
button_items_english_image = Image.open("C:/IT-Schedule/img1/button_items_english.jpg")
button_items_history_image = Image.open("C:/IT-Schedule/img1/button_items_history.jpg")
button_items_economy_image = Image.open("C:/IT-Schedule/img1/button_items_economy.jpg")
button_items_mathematics_image = Image.open("C:/IT-Schedule/img1/button_items_mathematics.jpg")
button_items_physics_image = Image.open("C:/IT-Schedule/img1/button_items_physics.jpg")
button_items_astronomy_image = Image.open("C:/IT-Schedule/img1/button_items_astronomy.jpg")
button_items_biology_image = Image.open("C:/IT-Schedule/img1/button_items_biology.jpg")
button_items_pt_image = Image.open("C:/IT-Schedule/img1/button_items_pt.jpg")
button_items_it_image = Image.open("C:/IT-Schedule/img1/button_items_it.jpg")
button_items_programming_image = Image.open("C:/IT-Schedule/img1/button_items_programming.jpg")
button_items_amo_image = Image.open("C:/IT-Schedule/img1/button_items_amo.jpg")
button_items_ls_image = Image.open("C:/IT-Schedule/img1/button_items_ls.jpg")


button_back_items1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items2 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items3 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items4 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items5 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items6 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items7 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items8 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items9 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items10 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items11 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items12 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items13 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items14 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items15 = Image.open("C:/IT-Schedule/img1/back_items.jpg")

button_back_items1_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items2_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items3_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items4_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items5_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items6_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items7_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items8_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items9_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items10_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items11_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items12_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items13_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items14_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")
button_back_items15_1 = Image.open("C:/IT-Schedule/img1/back_items.jpg")





button_come1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come2 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come3 = Image.open("C:/IT-Schedule/img1/button_come1.jpg")
button_come4 = Image.open("C:/IT-Schedule/img1/button_come2.jpg")
button_come5 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come6 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come7 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come8 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come9 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come10 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come11 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come12 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come13 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come14 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come15 = Image.open("C:/IT-Schedule/img1/button_come.jpg")


button_come1_1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come2_1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come3_1 = Image.open("C:/IT-Schedule/img1/button_come1.jpg")
button_come4_1 = Image.open("C:/IT-Schedule/img1/button_come2.jpg")
button_come5_1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come6_1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come7_1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come8_1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come9_1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come10_1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come11_1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come12_1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come13_1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come14_1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")
button_come15_1 = Image.open("C:/IT-Schedule/img1/button_come.jpg")

button_ukr_mova_image1 = Image.open("C:/IT-Schedule/img1/button_ukr_mova.jpg")
button_ukr_mova_image2 = Image.open("C:/IT-Schedule/img1/button_ukr_mova.jpg")
button_ukr_mova_image3 = Image.open("C:/IT-Schedule/img1/button_ukr_mova.jpg")
button_ukr_mova_image4 = Image.open("C:/IT-Schedule/img1/button_ukr_mova.jpg")
button_ukr_mova_image5 = Image.open("C:/IT-Schedule/img1/button_ukr_mova.jpg")

button_ukr_lit_image1 = Image.open("C:/IT-Schedule/img1/button_ukr_lit.jpg")
button_ukr_lit_image2 = Image.open("C:/IT-Schedule/img1/button_ukr_lit.jpg")
button_ukr_lit_image3 = Image.open("C:/IT-Schedule/img1/button_ukr_lit.jpg")
button_ukr_lit_image4 = Image.open("C:/IT-Schedule/img1/button_ukr_lit.jpg")
button_ukr_lit_image5 = Image.open("C:/IT-Schedule/img1/button_ukr_lit.jpg")

button_english_image1 = Image.open("C:/IT-Schedule/img1/button_english.jpg")
button_english_image2 = Image.open("C:/IT-Schedule/img1/button_english.jpg")
button_english_image3 = Image.open("C:/IT-Schedule/img1/button_english.jpg")
button_english_image4 = Image.open("C:/IT-Schedule/img1/button_english.jpg")
button_english_image5 = Image.open("C:/IT-Schedule/img1/button_english.jpg")

button_history_image1 = Image.open("C:/IT-Schedule/img1/button_history.jpg")
button_history_image2 = Image.open("C:/IT-Schedule/img1/button_history.jpg")
button_history_image3 = Image.open("C:/IT-Schedule/img1/button_history.jpg")
button_history_image4 = Image.open("C:/IT-Schedule/img1/button_history.jpg")
button_history_image5 = Image.open("C:/IT-Schedule/img1/button_history.jpg")

button_economy_image1 = Image.open("C:/IT-Schedule/img1/button_economy.jpg")
button_economy_image2 = Image.open("C:/IT-Schedule/img1/button_economy.jpg")
button_economy_image3 = Image.open("C:/IT-Schedule/img1/button_economy.jpg")
button_economy_image4 = Image.open("C:/IT-Schedule/img1/button_economy.jpg")
button_economy_image5 = Image.open("C:/IT-Schedule/img1/button_economy.jpg")

button_math_image1 = Image.open("C:/IT-Schedule/img1/button_math.jpg")
button_math_image2 = Image.open("C:/IT-Schedule/img1/button_math.jpg")
button_math_image3 = Image.open("C:/IT-Schedule/img1/button_math.jpg")
button_math_image4 = Image.open("C:/IT-Schedule/img1/button_math.jpg")
button_math_image5 = Image.open("C:/IT-Schedule/img1/button_math.jpg")

button_physics_image1 = Image.open("C:/IT-Schedule/img1/button_physics.jpg")
button_physics_image2 = Image.open("C:/IT-Schedule/img1/button_physics.jpg")
button_physics_image3 = Image.open("C:/IT-Schedule/img1/button_physics.jpg")
button_physics_image4 = Image.open("C:/IT-Schedule/img1/button_physics.jpg")
button_physics_image5 = Image.open("C:/IT-Schedule/img1/button_physics.jpg")

button_astronomy_image1 = Image.open("C:/IT-Schedule/img1/button_astronomy.jpg")
button_astronomy_image2 = Image.open("C:/IT-Schedule/img1/button_astronomy.jpg")
button_astronomy_image3 = Image.open("C:/IT-Schedule/img1/button_astronomy.jpg")
button_astronomy_image4 = Image.open("C:/IT-Schedule/img1/button_astronomy.jpg")
button_astronomy_image5 = Image.open("C:/IT-Schedule/img1/button_astronomy.jpg")

button_biology_image1 = Image.open("C:/IT-Schedule/img1/button_biology.jpg")
button_biology_image2 = Image.open("C:/IT-Schedule/img1/button_biology.jpg")
button_biology_image3 = Image.open("C:/IT-Schedule/img1/button_biology.jpg")
button_biology_image4 = Image.open("C:/IT-Schedule/img1/button_biology.jpg")
button_biology_image5 = Image.open("C:/IT-Schedule/img1/button_biology.jpg")

button_PKZ_image1 = Image.open("C:/IT-Schedule/img1/button_PKZ.jpg")
button_PKZ_image2 = Image.open("C:/IT-Schedule/img1/button_PKZ.jpg")
button_PKZ_image3 = Image.open("C:/IT-Schedule/img1/button_PKZ.jpg")
button_PKZ_image4 = Image.open("C:/IT-Schedule/img1/button_PKZ.jpg")
button_PKZ_image5 = Image.open("C:/IT-Schedule/img1/button_PKZ.jpg")

button_IT_image1 = Image.open("C:/IT-Schedule/img1/button_IT.jpg")
button_IT_image2 = Image.open("C:/IT-Schedule/img1/button_IT.jpg")
button_IT_image3 = Image.open("C:/IT-Schedule/img1/button_IT.jpg")
button_IT_image4 = Image.open("C:/IT-Schedule/img1/button_IT.jpg")
button_IT_image5 = Image.open("C:/IT-Schedule/img1/button_IT.jpg")

button_program_image1 = Image.open("C:/IT-Schedule/img1/button_program.jpg")
button_program_image2 = Image.open("C:/IT-Schedule/img1/button_program.jpg")
button_program_image3 = Image.open("C:/IT-Schedule/img1/button_program.jpg")
button_program_image4 = Image.open("C:/IT-Schedule/img1/button_program.jpg")
button_program_image5 = Image.open("C:/IT-Schedule/img1/button_program.jpg")

button_AMO_image1 = Image.open("C:/IT-Schedule/img1/button_AMO.jpg")
button_AMO_image2 = Image.open("C:/IT-Schedule/img1/button_AMO.jpg")
button_AMO_image3 = Image.open("C:/IT-Schedule/img1/button_AMO.jpg")
button_AMO_image4 = Image.open("C:/IT-Schedule/img1/button_AMO.jpg")
button_AMO_image5 = Image.open("C:/IT-Schedule/img1/button_AMO.jpg")

button_BZHD_image1 = Image.open("C:/IT-Schedule/img1/button_BZHD.jpg")
button_BZHD_image2 = Image.open("C:/IT-Schedule/img1/button_BZHD.jpg")
button_BZHD_image3 = Image.open("C:/IT-Schedule/img1/button_BZHD.jpg")
button_BZHD_image4 = Image.open("C:/IT-Schedule/img1/button_BZHD.jpg")
button_BZHD_image5 = Image.open("C:/IT-Schedule/img1/button_BZHD.jpg")



icon = PhotoImage(file="C:/IT-Schedule/img1/logo_icon.png")
root.iconphoto(True, icon)

style = ttk.Style()  # Создаем стиль для скрытия фона и заголовка верхней панели
style.layout("TNotebook.Tab", [])  # Пустой layout убирает заголовок

notebook = ttk.Notebook(root)
notebook.pack(fill="both", expand=True)

submenu_tab = Frame(notebook)
menu_tab = Frame(notebook)
other_tab = Frame(notebook)
week_schedule_tab = Frame(notebook)
all_schedule_tab = Frame(notebook)
question_tab = Frame(notebook)
list_teachers_tab = Frame(notebook)
support_tab = Frame(notebook)
items_tab = Frame(notebook)
tell_tab = Frame(notebook)
settings_tab = Frame(notebook)
functions1_tab = Frame(notebook)
functions2_tab = Frame(notebook)
functions3_tab = Frame(notebook)
functions4_tab = Frame(notebook)

monday_tab = Frame(notebook)
tuesday_tab = Frame(notebook)
wednesday_tab = Frame(notebook)
thursday_tab = Frame(notebook)
friday_tab = Frame(notebook)

ukrainian_language_tab = Frame(notebook)
ukrainian_literature_tab = Frame(notebook)
english_tab = Frame(notebook)
history_tab = Frame(notebook)
economy_tab = Frame(notebook)
mathematics_tab = Frame(notebook)
physics_tab = Frame(notebook)
astronomy_tab = Frame(notebook)
biology_tab = Frame(notebook)
pt_tab = Frame(notebook)
it_tab = Frame(notebook)
programming_tab = Frame(notebook)
amo_tab = Frame(notebook)
ls_tab = Frame(notebook)


ukrainian_language_tab1 = Frame(notebook)
ukrainian_literature_tab1 = Frame(notebook)
english_tab1 = Frame(notebook)
history_tab1 = Frame(notebook)
economy_tab1 = Frame(notebook)
mathematics_tab1 = Frame(notebook)
physics_tab1 = Frame(notebook)
astronomy_tab1 = Frame(notebook)
biology_tab1 = Frame(notebook)
pt_tab1 = Frame(notebook)
it_tab1 = Frame(notebook)
programming_tab1 = Frame(notebook)
amo_tab1 = Frame(notebook)
ls_tab1 = Frame(notebook)

set_tab_background(submenu_tab, background_submenu_image)
set_tab_background(other_tab, background_other_image)
set_tab_background(menu_tab, background_menu_image)
set_tab_background(week_schedule_tab, background_week_schedule_image)
set_tab_background(all_schedule_tab, background_all_schedule_image)
set_tab_background(question_tab, background_question_image)
set_tab_background(list_teachers_tab, background_list_teachers_image)
set_tab_background(support_tab, background_support_image)
set_tab_background(items_tab, background_items_image)
set_tab_background(tell_tab, background_tell_image)
set_tab_background(settings_tab, background_settings_image)

set_tab_background(functions1_tab, background_functions1_image)
set_tab_background(functions2_tab, background_functions2_image)
set_tab_background(functions3_tab, background_functions3_image)
set_tab_background(functions4_tab, background_functions4_image)

set_tab_background(ukrainian_language_tab1, background_ukrainian_language_image1)
set_tab_background(ukrainian_literature_tab1, background_ukrainian_literature_image1)
set_tab_background(english_tab1, background_english_image1)
set_tab_background(history_tab1, background_history_image1)
set_tab_background(economy_tab1, background_economy_image1)
set_tab_background(mathematics_tab1, background_mathematics_image1)
set_tab_background(physics_tab1, background_physics_image1)
set_tab_background(astronomy_tab1, background_astronomy_image1)
set_tab_background(biology_tab1, background_biology_image1)
set_tab_background(pt_tab1, background_pt_image1)
set_tab_background(it_tab1, background_it_image1)
set_tab_background(programming_tab1, background_programming_image1)
set_tab_background(amo_tab1, background_amo_image1)
set_tab_background(ls_tab1, background_ls_image1)

set_tab_background(ukrainian_language_tab, background_ukrainian_language_image)
set_tab_background(ukrainian_literature_tab, background_ukrainian_literature_image)
set_tab_background(english_tab, background_english_image)
set_tab_background(history_tab, background_history_image)
set_tab_background(economy_tab, background_economy_image)
set_tab_background(mathematics_tab, background_mathematics_image)
set_tab_background(physics_tab, background_physics_image)
set_tab_background(astronomy_tab, background_astronomy_image)
set_tab_background(biology_tab, background_biology_image)
set_tab_background(pt_tab, background_pt_image)
set_tab_background(it_tab, background_it_image)
set_tab_background(programming_tab, background_programming_image)
set_tab_background(amo_tab, background_amo_image)
set_tab_background(ls_tab, background_ls_image)


set_tab_background(monday_tab, background_monday_image)
set_tab_background(tuesday_tab, background_tuesday_image)
set_tab_background(wednesday_tab, background_wednesday_image)
set_tab_background(thursday_tab, background_thursday_image)
set_tab_background(friday_tab, background_friday_image)




notebook.add(submenu_tab)
notebook.add(other_tab)
notebook.add(menu_tab)
notebook.add(week_schedule_tab)
notebook.add(all_schedule_tab)
notebook.add(question_tab)
notebook.add(list_teachers_tab)
notebook.add(support_tab)
notebook.add(items_tab)
notebook.add(tell_tab)
notebook.add(settings_tab)

notebook.add(monday_tab)
notebook.add(tuesday_tab)
notebook.add(wednesday_tab)
notebook.add(thursday_tab)
notebook.add(friday_tab)

notebook.add(functions1_tab)
notebook.add(functions2_tab)
notebook.add(functions3_tab)
notebook.add(functions4_tab)

notebook.add(ukrainian_language_tab1)
notebook.add(ukrainian_literature_tab1)
notebook.add(english_tab1)
notebook.add(history_tab1)
notebook.add(economy_tab1)
notebook.add(mathematics_tab1)
notebook.add(physics_tab1)
notebook.add(astronomy_tab1)
notebook.add(biology_tab1)
notebook.add(pt_tab1)
notebook.add(it_tab1)
notebook.add(programming_tab1)
notebook.add(amo_tab1)
notebook.add(ls_tab1)

notebook.add(ukrainian_language_tab)
notebook.add(ukrainian_literature_tab)
notebook.add(english_tab)
notebook.add(history_tab)
notebook.add(economy_tab)
notebook.add(mathematics_tab)
notebook.add(physics_tab)
notebook.add(astronomy_tab)
notebook.add(biology_tab)
notebook.add(pt_tab)
notebook.add(it_tab)
notebook.add(programming_tab)
notebook.add(amo_tab)
notebook.add(ls_tab)


smaller_button_width = 100
smaller_button_height = 30

button_enable_image = ImageTk.PhotoImage(
    Image.open("C:/IT-Schedule/img1/button_enable.jpg").resize((smaller_button_width, smaller_button_height)))
button_disable_image = ImageTk.PhotoImage(
    Image.open("C:/IT-Schedule/img1/button_disable.jpg").resize((smaller_button_width, smaller_button_height)))

toggle_button = Button(settings_tab, image=button_enable_image, command=toggle_notifications,
                       width=smaller_button_width, height=smaller_button_height,
                       borderwidth=0, activebackground="#f6f4f0",
                       activeforeground="#f6f4f0", relief="flat", highlightthickness=0)
toggle_button.pack(anchor='nw', side='right', padx=35, pady=92)

# ВСЯ ВКЛАДКА РОЗКЛАД
label = Label(submenu_tab, text="ㅤ", font='Arial 16', background="#fee698")
label.pack(pady=70)

new_size_button_week_schedule = (380, 150)  # Новый размер (ширина, высота)
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

new_size_button_all_schedule = (380, 150)  # Новый размер (ширина, высота)
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

new_size_button_menu_tab1 = (68, 60)  # Новый размер (ширина, высота)
button_menu_tab_image1 = button_menu_tab_image1.resize(new_size_button_menu_tab1)

photo_button_menu_tab1 = ImageTk.PhotoImage(button_menu_tab_image1)

button_menu_tab1 = Button(submenu_tab,
                          image=photo_button_menu_tab1,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat", highlightthickness=0,
                          command=show_menu_tab)

new_size_button_other_tab1 = (68, 60)  # Новый размер (ширина, высота)
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
frame_back_week_schedule.pack(anchor='nw', padx=25, pady=22)


def back_to_submenu_from_week_schedule():
    notebook.select(submenu_tab)


new_size_back_week_schedule = (18, 25)  # Новый размер (ширина, высота)
image_back_week_schedule = image_back_week_schedule.resize(new_size_back_week_schedule)

photo_back_week_schedule = ImageTk.PhotoImage(image_back_week_schedule)

button_back_week_schedule = Button(frame_back_week_schedule, image=photo_back_week_schedule, borderwidth=-4,
                                   activebackground="#f6f4f0", activeforeground="#f6f4f0", relief="flat",
                                   highlightthickness=0, command=back_to_submenu_from_week_schedule)
button_back_week_schedule.pack(side=LEFT)

label = Label(week_schedule_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(padx=1, pady=0)

new_size_button_monday = (370, 90)  # Новый размер (ширина, высота)
button_monday_image = button_monday_image.resize(new_size_button_monday)

photo_button_monday = ImageTk.PhotoImage(button_monday_image)

button_monday = Button(week_schedule_tab,
                       image=photo_button_monday,
                       borderwidth=0,
                       activebackground="#f6f4f0",
                       activeforeground="#f6f4f0",
                       relief="flat", highlightthickness=0,
                       command=show_monday_tab)
button_monday.pack(pady=5)


new_size_button_tuesday = (370, 90)  # Новый размер (ширина, высота)
button_tuesday_image = button_tuesday_image.resize(new_size_button_tuesday)

photo_button_tuesday = ImageTk.PhotoImage(button_tuesday_image)

button_tuesday = Button(week_schedule_tab,
                        image=photo_button_tuesday,
                        borderwidth=0,
                        activebackground="#f6f4f0",
                        activeforeground="#f6f4f0",
                        relief="flat", highlightthickness=0,
                        command=show_tuesday_tab)
button_tuesday.pack(pady=5)

new_size_button_wednesday = (370, 90)  # Новый размер (ширина, высота)
button_wednesday_image = button_wednesday_image.resize(new_size_button_wednesday)

photo_button_wednesday = ImageTk.PhotoImage(button_wednesday_image)

button_wednesday = Button(week_schedule_tab,
                          image=photo_button_wednesday,
                          borderwidth=0,
                          activebackground="#f6f4f0",
                          activeforeground="#f6f4f0",
                          relief="flat", highlightthickness=0,
                          command=show_wednesday_tab)
button_wednesday.pack(pady=5)

new_size_button_thursday = (370, 90)  # Новый размер (ширина, высота)
button_thursday_image = button_thursday_image.resize(new_size_button_thursday)

photo_button_thursday = ImageTk.PhotoImage(button_thursday_image)

button_thursday = Button(week_schedule_tab,
                         image=photo_button_thursday,
                         borderwidth=0,
                         activebackground="#f6f4f0",
                         activeforeground="#f6f4f0",
                         relief="flat", highlightthickness=0,
                         command=show_thursday_tab)
button_thursday.pack(pady=5)

new_size_button_friday = (370, 90)  # Новый размер (ширина, высота)
button_friday_image = button_friday_image.resize(new_size_button_friday)

photo_button_friday = ImageTk.PhotoImage(button_friday_image)

button_friday = Button(week_schedule_tab,
                       image=photo_button_friday,
                       borderwidth=0,
                       activebackground="#f6f4f0",
                       activeforeground="#f6f4f0",
                       relief="flat", highlightthickness=0,
                       command=show_friday_tab)
button_friday.pack(pady=5)

# ВКЛАДКА ВЕСЬ РОЗКЛАД
frame_back_all_schedule = Frame(all_schedule_tab)
frame_back_all_schedule.pack(anchor='nw', padx=25, pady=22)


def back_to_submenu_from_all_schedule():
    notebook.select(submenu_tab)


new_size_back_all_schedule = (18, 25)  # Новый размер (ширина, высота)
image_back_all_schedule = image_back_all_schedule.resize(new_size_back_all_schedule)

photo_back_all_schedule = ImageTk.PhotoImage(image_back_all_schedule)

button_back_all_schedule = Button(frame_back_all_schedule, image=photo_back_all_schedule, borderwidth=-4,
                                  activebackground="#f6f4f0", activeforeground="#f6f4f0", relief="flat",
                                  highlightthickness=0, command=back_to_submenu_from_all_schedule)
button_back_all_schedule.pack(side=LEFT)

label = Label(all_schedule_tab, text=" ", font='Mariupol 18', background="#f6f4f0")
label.pack(pady=20)
label = Label(all_schedule_tab, text="404", font='Consolas 80', background="#f6f4f0")
label.pack(pady=5)
label = Label(all_schedule_tab, text="На даний момент весь", font='Mariupol 18', background="#f6f4f0")
label.pack(pady=0)
label = Label(all_schedule_tab, text=" розклад не надано", font='Mariupol 18', background="#f6f4f0")
label.pack(pady=0)
label = Label(all_schedule_tab, text=" ", font='Mariupol 18', background="#f6f4f0")
label.pack(pady=121)
frame_all_schedule = tk.Frame(all_schedule_tab)
frame_all_schedule.pack()
label = tk.Label(frame_all_schedule, text="Стосовно розкладу:", font='Mariupol 12', background="#f6f4f0")
label.pack(side=tk.LEFT)  # Размещаем первый лейбл слева


def open_link(event):
    webbrowser.open("https://it-college.kh.ua/")


label1 = tk.Label(frame_all_schedule, text="https://it-college.kh.ua                          ", fg="blue",
                  cursor="hand2", font='Mariupol 12', background="#f6f4f0")
label1.pack(side=tk.LEFT)  # Размещаем второй лейбл слева
label1.bind("<Button-1>", open_link)

# ВКЛАДКА ДРУГОЕ
label = Label(other_tab, text="ㅤ", font='Arial 16', background="#f6f4f0")
label.pack(pady=70)

new_size_button_list_teachers = (380, 150)  # Новый размер (ширина, высота)
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

new_size_button_items = (380, 150)  # Новый размер (ширина, высота)
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

new_size_button_menu_tab2 = (68, 60)
button_menu_tab_image2 = button_menu_tab_image2.resize(new_size_button_menu_tab2)

photo_button_menu_tab2 = ImageTk.PhotoImage(button_menu_tab_image2)

button_menu_tab2 = Button(other_tab,
                          image=photo_button_menu_tab2,
                          borderwidth=0,
                          activebackground="white",
                          activeforeground="white",
                          relief="flat", highlightthickness=0,
                          command=show_menu_tab)

new_size_button_schedule_tab2 = (68, 60)
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

# ВКЛАДКА СПИСОК ПРЕПОДАВАТЕЛЕЙ
frame_back_list_teachers = Frame(list_teachers_tab)
frame_back_list_teachers.pack(anchor='nw', padx=25, pady=22)


def back_to_submenu_from_list_teachers():
    notebook.select(other_tab)


new_size_back_list_teachers = (18, 25)  # Новый размер (ширина, высота)
image_back_list_teachers = image_back_list_teachers.resize(new_size_back_list_teachers)

photo_back_list_teachers = ImageTk.PhotoImage(image_back_list_teachers)

button_back_list_teachers = Button(frame_back_list_teachers, image=photo_back_list_teachers, borderwidth=-4,
                                   activebackground="#f6f4f0", activeforeground="#f6f4f0", relief="flat",
                                   highlightthickness=0, command=back_to_submenu_from_list_teachers)
button_back_list_teachers.pack(side=LEFT)

# ВСЯ ВКЛАДКА ПРЕДМЕТИ
frame_back_items = Frame(items_tab)
frame_back_items.pack(anchor='nw', padx=25, pady=22)


def back_to_submenu_from_items():
    notebook.select(other_tab)


new_size_back_items = (18, 25)  # Новый размер (ширина, высота)
image_back_items = image_back_items.resize(new_size_back_items)

photo_back_items = ImageTk.PhotoImage(image_back_items)

button_back_items = Button(frame_back_items, image=photo_back_items, borderwidth=-4,
                           activebackground="#f1f0f1", activeforeground="#f1f0f1", relief="flat", highlightthickness=0,
                           command=back_to_submenu_from_items)
button_back_items.pack(side=LEFT)

label = Label(items_tab, text="ㅤ", font='Arial 1', background="#f1f0f1")
label.pack(pady=2)

frame_items1 = tk.Frame(items_tab)
frame_items1.pack()
frame_items2 = tk.Frame(items_tab)
frame_items2.pack()
frame_items3 = tk.Frame(items_tab)
frame_items3.pack()
frame_items4 = tk.Frame(items_tab)
frame_items4.pack()
frame_items5 = tk.Frame(items_tab)
frame_items5.pack()
frame_items6 = tk.Frame(items_tab)
frame_items6.pack()
frame_items7 = tk.Frame(items_tab)
frame_items7.pack()

new_size_button_items_ukrainian_language = (200, 60)  # Новый размер (ширина, высота)
button_items_ukrainian_language_image = button_items_ukrainian_language_image.resize(
    new_size_button_items_ukrainian_language)

photo_button_items_ukrainian_language = ImageTk.PhotoImage(button_items_ukrainian_language_image)

button_items_ukrainian_language = Button(frame_items1,
                                         image=photo_button_items_ukrainian_language,
                                         borderwidth=0,
                                         activebackground="#f1f0f1",
                                         activeforeground="#f1f0f1",
                                         relief="flat", highlightthickness=0,
                                         command=show_ukrainian_language_tab1)
button_items_ukrainian_language.pack(side=tk.LEFT, padx=5, pady=6)

new_size_button_items_ukrainian_literature = (200, 60)  # Новый размер (ширина, высота)
button_items_ukrainian_literature_image = button_items_ukrainian_literature_image.resize(
    new_size_button_items_ukrainian_literature)

photo_button_items_ukrainian_literature = ImageTk.PhotoImage(button_items_ukrainian_literature_image)

button_items_ukrainian_literature = Button(frame_items1,
                                           image=photo_button_items_ukrainian_literature,
                                           borderwidth=0,
                                           activebackground="#f1f0f1",
                                           activeforeground="#f1f0f1",
                                           relief="flat", highlightthickness=0,
                                           command=show_ukrainian_language_tab1)
button_items_ukrainian_literature.pack(side=tk.LEFT, padx=5, pady=6)

new_size_button_items_english = (200, 60)  # Новый размер (ширина, высота)
button_items_english_image = button_items_english_image.resize(
    new_size_button_items_english)

photo_button_items_english = ImageTk.PhotoImage(button_items_english_image)

button_items_english = Button(frame_items2,
                              image=photo_button_items_english,
                              borderwidth=0,
                              activebackground="#f1f0f1",
                              activeforeground="#f1f0f1",
                              relief="flat", highlightthickness=0,
                              command=show_english_tab1)
button_items_english.pack(side=tk.LEFT, padx=5, pady=6)

new_size_button_items_history = (200, 60)  # Новый размер (ширина, высота)
button_items_history_image = button_items_history_image.resize(new_size_button_items_history)

photo_button_items_history = ImageTk.PhotoImage(button_items_history_image)

button_items_history = Button(frame_items2,
                              image=photo_button_items_history,
                              borderwidth=0,
                              activebackground="#f1f0f1",
                              activeforeground="#f1f0f1",
                              relief="flat", highlightthickness=0,
                              command=show_history_tab1)
button_items_history.pack(side=tk.LEFT, padx=5, pady=6)

new_size_button_items_economy = (200, 60)  # Новый размер (ширина, высота)
button_items_economy_image = button_items_economy_image.resize(new_size_button_items_economy)

photo_button_items_economy = ImageTk.PhotoImage(button_items_economy_image)

button_items_economy = Button(frame_items3,
                              image=photo_button_items_economy,
                              borderwidth=0,
                              activebackground="#f1f0f1",
                              activeforeground="#f1f0f1",
                              relief="flat", highlightthickness=0,
                              command=show_economy_tab1)
button_items_economy.pack(side=tk.LEFT, padx=5, pady=6)

new_size_button_items_mathematics = (200, 60)  # Новый размер (ширина, высота)
button_items_mathematics_image = button_items_mathematics_image.resize(new_size_button_items_mathematics)

photo_button_items_mathematics = ImageTk.PhotoImage(button_items_mathematics_image)

button_items_mathematics = Button(frame_items3,
                                  image=photo_button_items_mathematics,
                                  borderwidth=0,
                                  activebackground="#f1f0f1",
                                  activeforeground="#f1f0f1",
                                  relief="flat", highlightthickness=0,
                                  command=show_mathematics_tab1)
button_items_mathematics.pack(side=tk.LEFT, padx=5, pady=6)

new_size_button_items_physics = (200, 60)  # Новый размер (ширина, высота)
button_items_physics_image = button_items_physics_image.resize(new_size_button_items_physics)

photo_button_items_physics = ImageTk.PhotoImage(button_items_physics_image)

button_items_physics = Button(frame_items4,
                              image=photo_button_items_physics,
                              borderwidth=0,
                              activebackground="#f1f0f1",
                              activeforeground="#f1f0f1",
                              relief="flat", highlightthickness=0,
                              command=show_physics_tab1)
button_items_physics.pack(side=tk.LEFT, padx=5, pady=6)

new_size_button_items_astronomy = (200, 60)  # Новый размер (ширина, высота)
button_items_astronomy_image = button_items_astronomy_image.resize(new_size_button_items_astronomy)

photo_button_items_astronomy = ImageTk.PhotoImage(button_items_astronomy_image)

button_items_astronomy = Button(frame_items4,
                                image=photo_button_items_astronomy,
                                borderwidth=0,
                                activebackground="#f1f0f1",
                                activeforeground="#f1f0f1",
                                relief="flat", highlightthickness=0,
                                command=show_astronomy_tab1)
button_items_astronomy.pack(side=tk.LEFT, padx=5, pady=6)

new_size_button_items_pt = (200, 60)  # Новый размер (ширина, высота)
button_items_pt_image = button_items_pt_image.resize(new_size_button_items_pt)

photo_button_items_pt = ImageTk.PhotoImage(button_items_pt_image)

button_items_pt = Button(frame_items5,
                         image=photo_button_items_pt,
                         borderwidth=0,
                         activebackground="#f1f0f1",
                         activeforeground="#f1f0f1",
                         relief="flat", highlightthickness=0,
                         command=show_pt_tab1)
button_items_pt.pack(side=tk.LEFT, padx=5, pady=6)

new_size_button_items_it = (200, 60)  # Новый размер (ширина, высота)
button_items_it_image = button_items_it_image.resize(new_size_button_items_it)

photo_button_items_it = ImageTk.PhotoImage(button_items_it_image)

button_items_it = Button(frame_items5,
                         image=photo_button_items_it,
                         borderwidth=0,
                         activebackground="#f1f0f1",
                         activeforeground="#f1f0f1",
                         relief="flat", highlightthickness=0,
                         command=show_it_tab1)
button_items_it.pack(side=tk.LEFT, padx=5, pady=6)

new_size_button_items_biology = (200, 60)  # Новый размер (ширина, высота)
button_items_biology_image = button_items_biology_image.resize(new_size_button_items_biology)

photo_button_items_biology = ImageTk.PhotoImage(button_items_biology_image)

button_items_biology = Button(frame_items6,
                              image=photo_button_items_biology,
                              borderwidth=0,
                              activebackground="#f1f0f1",
                              activeforeground="#f1f0f1",
                              relief="flat", highlightthickness=0,
                              command=show_biology_tab1)
button_items_biology.pack(side=tk.LEFT, padx=5, pady=6)

new_size_button_items_programming = (200, 60)  # Новый размер (ширина, высота)
button_items_programming_image = button_items_programming_image.resize(new_size_button_items_programming)

photo_button_items_programming = ImageTk.PhotoImage(button_items_programming_image)

button_items_programming = Button(frame_items6,
                                  image=photo_button_items_programming,
                                  borderwidth=0,
                                  activebackground="#f1f0f1",
                                  activeforeground="#f1f0f1",
                                  relief="flat", highlightthickness=0,
                                  command=show_programming_tab1)
button_items_programming.pack(side=tk.LEFT, padx=5, pady=6)

new_size_button_items_amo = (200, 60)  # Новый размер (ширина, высота)
button_items_amo_image = button_items_amo_image.resize(new_size_button_items_amo)

photo_button_items_amo = ImageTk.PhotoImage(button_items_amo_image)

button_items_amo = Button(frame_items7,
                          image=photo_button_items_amo,
                          borderwidth=0,
                          activebackground="#f1f0f1",
                          activeforeground="#f1f0f1",
                          relief="flat", highlightthickness=0,
                          command=show_amo_tab1)
button_items_amo.pack(side=tk.LEFT, padx=5, pady=6)

new_size_button_items_ls = (200, 60)  # Новый размер (ширина, высота)
button_items_ls_image = button_items_ls_image.resize(new_size_button_items_ls)

photo_button_items_ls = ImageTk.PhotoImage(button_items_ls_image)

button_items_ls = Button(frame_items7,
                         image=photo_button_items_ls,
                         borderwidth=0,
                         activebackground="#f1f0f1",
                         activeforeground="#f1f0f1",
                         relief="flat", highlightthickness=0,
                         command=show_ls_tab1)
button_items_ls.pack(side=tk.LEFT, padx=5, pady=6)

# ВСЯ ВКЛАДКА МЕНЮ
label = Label(menu_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=35, padx=10)

new_size_button_functions = (450, 51)  # Новый размер (ширина, высота)
button_functions_image = button_functions_image.resize(new_size_button_functions)

photo_button_functions = ImageTk.PhotoImage(button_functions_image)

button_functions = Button(menu_tab,
                          image=photo_button_functions,
                          borderwidth=0,
                          activebackground="#f6f4f0",
                          activeforeground="#f6f4f0",
                          relief="flat", highlightthickness=0,
                          command=show_functions1_tab)
button_functions.pack(pady=0)

new_size_button_question = (450, 51)  # Новый размер (ширина, высота)
button_question_image = button_question_image.resize(new_size_button_question)

photo_button_question = ImageTk.PhotoImage(button_question_image)

button_question = Button(menu_tab,
                         image=photo_button_question,
                         borderwidth=0,
                         activebackground="#f6f4f0",
                         activeforeground="#f6f4f0",
                         relief="flat", highlightthickness=0,
                         command=show_question_tab)
button_question.pack(pady=0)

new_size_button_support = (450, 51)
button_support_image = button_support_image.resize(new_size_button_support)

photo_button_support = ImageTk.PhotoImage(button_support_image)

button_support = Button(menu_tab,
                        image=photo_button_support,
                        borderwidth=0,
                        activebackground="#f6f4f0",
                        activeforeground="#f6f4f0",
                        relief="flat", highlightthickness=0,
                        command=show_support_tab)
button_support.pack(pady=1)

new_size_button_settings = (450, 51)  # Новый размер (ширина, высота)
button_settings_image = button_settings_image.resize(new_size_button_settings)

photo_button_settings = ImageTk.PhotoImage(button_settings_image)

button_settings = Button(menu_tab,
                         image=photo_button_settings,
                         borderwidth=0,
                         activebackground="#f6f4f0",
                         activeforeground="#f6f4f0",
                         relief="flat", highlightthickness=0,
                         command=show_settings_tab)
button_settings.pack(pady=20)

new_size_button_tell = (450, 51)  # Новый размер (ширина, высота)
button_tell_image = button_tell_image.resize(new_size_button_tell)

photo_button_tell = ImageTk.PhotoImage(button_tell_image)

button_tell = Button(menu_tab,
                     image=photo_button_tell,
                     borderwidth=0,
                     activebackground="#f6f4f0",
                     activeforeground="#f6f4f0",
                     relief="flat", highlightthickness=0,
                     command=show_tell_tab)
button_tell.pack(pady=0)


def open_new_window():
    new_window = Toplevel(root)  # Создаем новое окно
    new_window.geometry("1325x725+90+30")  # Задаем размеры (Ширина)-(Высота) Место появления окна
    new_window.resizable(False, False)
    new_window.title("Про НАс")

    image = Image.open(
        "C:/IT-Schedule/img1/background_about_us.png")  # Замените "your_image_file.png" на путь к вашему изображению
    photo = ImageTk.PhotoImage(image)

    # Создание Label с изображением
    image_label = tk.Label(new_window, image=photo)
    image_label.photo = photo  # Обязательно храните ссылку на изображение, чтобы избежать удаления из памяти
    image_label.pack()


new_size_button_about_us = (450, 51)  # Новый размер (ширина, высота)
button_about_us_image = button_about_us_image.resize(new_size_button_about_us)

photo_button_about_us = ImageTk.PhotoImage(button_about_us_image)

button_about_us = Button(menu_tab,
                         image=photo_button_about_us,
                         borderwidth=0,
                         activebackground="#f6f4f0",
                         activeforeground="#f6f4f0",
                         relief="flat", highlightthickness=0,
                         command=open_new_window)  # Правильное местоположение скобок
button_about_us.pack(pady=0)

label = Label(menu_tab, text="ㅤ", font='Arial 11', background="#f6f4f0")
label.pack(pady=62)

new_size_button_schedule_tab3 = (68, 60)  # Новый размер (ширина, высота)
button_schedule_tab_image3 = button_schedule_tab_image3.resize(new_size_button_schedule_tab3)

photo_button_schedule_tab3 = ImageTk.PhotoImage(button_schedule_tab_image3)

button_schedule_tab3 = Button(menu_tab,
                              image=photo_button_schedule_tab3,
                              borderwidth=0,
                              activebackground="white",
                              activeforeground="white",
                              relief="flat", highlightthickness=0,
                              command=show_submenu_tab)

new_size_button_other_tab3 = (68, 60)  # Новый размер (ширина, высота)
button_other_tab_image3 = button_other_tab_image3.resize(new_size_button_other_tab3)

photo_button_other_tab3 = ImageTk.PhotoImage(button_other_tab_image3)

button_other_tab3 = Button(menu_tab,
                           image=photo_button_other_tab3,
                           borderwidth=0,
                           activebackground="white",
                           activeforeground="white",
                           relief="flat", highlightthickness=0,
                           command=show_other_tab)

button_schedule_tab3.pack(side="left", padx=38)
button_other_tab3.pack(side="left", padx=45)

# ВКЛАДКА ВОПРОСЫ ОТВЕТЫ
frame_back_question = Frame(question_tab)
frame_back_question.pack(anchor='nw', padx=25, pady=22)


def back_to_submenu_from_question():
    notebook.select(menu_tab)


new_size_back_question = (18, 25)  # Новый размер (ширина, высота)
image_back_question = image_back_question.resize(new_size_back_question)

photo_back_question = ImageTk.PhotoImage(image_back_question)

button_back_question = Button(frame_back_question, image=photo_back_question, borderwidth=-4,
                              activebackground="#f6f4f0", activeforeground="#f6f4f0", relief="flat",
                              highlightthickness=0, command=back_to_submenu_from_question)
button_back_question.pack(side=LEFT)

# ВКЛАДКА ПОДЕЛИТСЯ
label = Label(tell_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=229, padx=7)

frame_back_tell = Frame(tell_tab)
frame_back_tell.pack(anchor='nw', padx=16, pady=10)


def back_to_submenu_from_tell():
    notebook.select(menu_tab)


new_size_back_tell = (17, 17)  # Новый размер (ширина, высота)
image_back_tell = image_back_tell.resize(new_size_back_tell)

photo_back_tell = ImageTk.PhotoImage(image_back_tell)

button_back_tell = Button(frame_back_tell, image=photo_back_tell, borderwidth=-4,
                          activebackground="#dfe7f2", activeforeground="#dfe7f2", relief="flat", highlightthickness=0,
                          command=back_to_submenu_from_tell)
button_back_tell.pack(side=LEFT)

new_size_button_share_button = (205, 60)  # Новый размер (ширина, высота)
button_share_image = button_share_image.resize(new_size_button_share_button)

photo_button_share = ImageTk.PhotoImage(button_share_image)

app_combobox = None  # Define app_combobox as a global variable


def share_with_friends():
    global app_combobox  # Use the global variable
    selected_app = app_combobox.get()
    message = '''IT Schedule - це твій вірний супутник в організації навчального процесу! У ньому ти знайдеш розклад занять із переліком викладачів та корисними інструментами для успішного навчання. Не втрачай нагоди спростити своє навчання! Успіх у навчанні стає ближчим з IT Schedule! 📚👨‍🏫 Завантажуй IT Schedule прямо зараз: http://surl.li/lljty'''

    app_urls = {
        "WhatsApp": "https://api.whatsapp.com/send?text=" + message,
        "Facebook": "https://www.facebook.com/sharer/sharer.php?u=" + message,
        "Telegram": "https://t.me/share/url?url=" + message,
        "Viber": "viber://forward?text=" + message,
        "Messenger": "fb-messenger://share/?link=" + message,
        "Instagram": "https://www.instagram.com/?hl=en" + message
    }

    if selected_app in app_urls:
        app_url = app_urls[selected_app]
        webbrowser.open(app_url)  # Открыть ссылку в браузере

    # Выпадающий список соцсетей


apps = ["WhatsApp", "Facebook", "Telegram", "Viber", "Messenger", "Instagram"]
app_combobox = ttk.Combobox(tell_tab, values=apps, font=("Mariupol", 14), width=16)
app_combobox.set(apps[2])  # значение по умолчанию
app_combobox.pack(padx=18, pady=20)

# Создание кнопки рассказать друзьям
share_button = tk.Button(tell_tab,
                         image=photo_button_share,
                         borderwidth=0, activebackground="white",
                         activeforeground="white", relief="flat",
                         highlightthickness=0, command=lambda: (share_with_friends(), show_menu_tab()))
share_button.pack(padx=18, pady=0)

# ВКЛАДКА ТЕХПОТДЕРЖКА
frame_back_support = Frame(support_tab)
frame_back_support.pack(anchor='nw', padx=25, pady=22)


def back_to_submenu_from_support():
    notebook.select(menu_tab)


new_size_back_support = (18, 25)  # Новый размер (ширина, высота)
image_back_support = image_back_support.resize(new_size_back_support)

photo_back_support = ImageTk.PhotoImage(image_back_all_schedule)

button_back_support = Button(frame_back_support, image=photo_back_support, borderwidth=-4,
                             activebackground="#f6f4f0", activeforeground="#f6f4f0", relief="flat",
                             highlightthickness=0, command=back_to_submenu_from_support)
button_back_support.pack(side=LEFT)

label = Label(support_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(pady=18)


# КНОПКИ ДЛЯ ДИСКОРДА

def open_link_discord():
    hyperlink_d = "https://discord.gg/C3Rmq53u"
    webbrowser.open(hyperlink_d)


new_size_button_go_support1 = (375, 65)  # Новый размер (ширина, высота)
button_go_support1_image = button_go_support1_image.resize(new_size_button_go_support1)

photo_button_go_support1 = ImageTk.PhotoImage(button_go_support1_image)

button_go_support1 = Button(support_tab,
                            image=photo_button_go_support1,
                            borderwidth=0,
                            activebackground="#f6f4f0",
                            activeforeground="#f6f4f0",
                            relief="flat", highlightthickness=0,
                            command=open_link_discord)
button_go_support1.pack(pady=5)


# КНОПКИ ДЛЯ ТЕЛЕГРАМ
def open_link_telegram():
    hyperlink_t = "https://t.me/it_schedule_khai"
    webbrowser.open(hyperlink_t)


new_size_button_go_support2 = (375, 65)  # Новый размер (ширина, высота)
button_go_support2_image = button_go_support2_image.resize(new_size_button_go_support2)

photo_button_go_support2 = ImageTk.PhotoImage(button_go_support2_image)

button_go_support2 = Button(support_tab,
                            image=photo_button_go_support2,
                            borderwidth=0,
                            activebackground="#f6f4f0",
                            activeforeground="#f6f4f0",
                            relief="flat", highlightthickness=0,
                            command=open_link_telegram)

button_go_support2.pack(pady=5)


# КНОПКИ ДЛЯ ПОЧТА
def open_link_gmail():
    hyperlink_t = "https://it.schedule1@gmail.com"
    webbrowser.open(hyperlink_t)


new_size_button_go_support3 = (375, 65)  # Новый размер (ширина, высота)
button_go_support3_image = button_go_support3_image.resize(new_size_button_go_support3)

photo_button_go_support3 = ImageTk.PhotoImage(button_go_support3_image)

button_go_support3 = Button(support_tab,
                            image=photo_button_go_support3,
                            borderwidth=0,
                            activebackground="#f6f4f0",
                            activeforeground="#f6f4f0",
                            relief="flat", highlightthickness=0,
                            command=open_link_gmail)

button_go_support3.pack(pady=5)

# КНОПКИ ДЛЯ НАСТРОЙКИ
frame_back_settings = Frame(settings_tab)
frame_back_settings.pack(anchor='nw', padx=25, pady=22)


def back_to_submenu_from_settings():
    notebook.select(menu_tab)


new_size_back_settings = (18, 25)  # Новый размер (ширина, высота)
image_back_settings = image_back_settings.resize(new_size_back_settings)

photo_back_settings = ImageTk.PhotoImage(image_back_settings)

button_back_settings = Button(frame_back_settings, image=photo_back_settings, borderwidth=-4,
                              activebackground="#f6f4f0", activeforeground="#f6f4f0", relief="flat",
                              highlightthickness=0, command=back_to_submenu_from_settings)
button_back_settings.pack(side=LEFT)

# КНОПКИ ФУНКЦИИ И ПОДСКАЗКИ
frame_button_functions1_close = Frame(functions1_tab)
frame_button_functions1_close.pack(anchor='nw', padx=25, pady=92)

new_size_button_functions1_close = (25, 25)  # Новый размер (ширина, высота)
button_functions1_close_image = button_functions1_close_image.resize(new_size_button_functions1_close)

photo_button_functions1_close = ImageTk.PhotoImage(button_functions1_close_image)

button_functions1_close = Button(frame_button_functions1_close,
                                 image=photo_button_functions1_close,
                                 borderwidth=0,
                                 activebackground="#fee698",
                                 activeforeground="#fee698",
                                 relief="flat", highlightthickness=0,
                                 command=show_submenu_tab)
button_functions1_close.pack(side=LEFT)

new_size_functions1_further = (18, 28)
button_functions1_further_image = button_functions1_further_image.resize(new_size_functions1_further)

photo_button_functions1_further = ImageTk.PhotoImage(button_functions1_further_image)

button_functions1_further = Button(functions1_tab,
                                   image=photo_button_functions1_further,
                                   borderwidth=0,
                                   activebackground="#f6f4f0",
                                   activeforeground="#f6f4f0",
                                   relief="flat", highlightthickness=0,
                                   command=show_functions2_tab)
button_functions1_further.pack(anchor='nw', side='right', padx=48, pady=30)

frame_button_functions2_close = Frame(functions2_tab)
frame_button_functions2_close.pack(anchor='nw', padx=25, pady=92)

new_size_button_functions2_close = (25, 25)  # Новый размер (ширина, высота)
button_functions2_close_image = button_functions2_close_image.resize(new_size_button_functions2_close)

photo_button_functions2_close = ImageTk.PhotoImage(button_functions2_close_image)

button_functions2_close = Button(frame_button_functions2_close,
                                 image=photo_button_functions2_close,
                                 borderwidth=0,
                                 activebackground="#fee698",
                                 activeforeground="#fee698",
                                 relief="flat", highlightthickness=0,
                                 command=show_submenu_tab)
button_functions2_close.pack(side=LEFT)

new_size_functions2_further = (18, 28)
button_functions2_further_image = button_functions2_further_image.resize(new_size_functions2_further)

photo_button_functions2_further = ImageTk.PhotoImage(button_functions2_further_image)

button_functions2_further = Button(functions2_tab,
                                   image=photo_button_functions2_further,
                                   borderwidth=0,
                                   activebackground="#f6f4f0",
                                   activeforeground="#f6f4f0",
                                   relief="flat", highlightthickness=0,
                                   command=show_functions3_tab)
button_functions2_further.pack(anchor='nw', side='right', padx=48, pady=30)

frame_button_functions3_close = Frame(functions3_tab)
frame_button_functions3_close.pack(anchor='nw', padx=25, pady=92)

new_size_button_functions3_close = (25, 25)  # Новый размер (ширина, высота)
button_functions3_close_image = button_functions3_close_image.resize(new_size_button_functions3_close)

photo_button_functions3_close = ImageTk.PhotoImage(button_functions3_close_image)

button_functions3_close = Button(frame_button_functions3_close,
                                 image=photo_button_functions3_close,
                                 borderwidth=0,
                                 activebackground="#fee698",
                                 activeforeground="#fee698",
                                 relief="flat", highlightthickness=0,
                                 command=show_submenu_tab)
button_functions3_close.pack(side=LEFT)

new_size_functions3_further = (18, 28)
button_functions3_further_image = button_functions3_further_image.resize(new_size_functions3_further)

photo_button_functions3_further = ImageTk.PhotoImage(button_functions3_further_image)

button_functions3_further = Button(functions3_tab,
                                   image=photo_button_functions3_further,
                                   borderwidth=0,
                                   activebackground="#f6f4f0",
                                   activeforeground="#f6f4f0",
                                   relief="flat", highlightthickness=0,
                                   command=show_functions4_tab)
button_functions3_further.pack(anchor='nw', side='right', padx=48, pady=30)

label = Label(functions4_tab, text="ㅤ", font='Arial 1', background="#fee698")
label.pack(anchor='nw', pady=170, padx=7)

new_size_functions4_further = (175, 42)
button_functions4_further_image = button_functions4_further_image.resize(new_size_functions4_further)

photo_button_functions4_further = ImageTk.PhotoImage(button_functions4_further_image)

button_functions4_further = Button(functions4_tab,
                                   image=photo_button_functions4_further,
                                   borderwidth=0,
                                   activebackground="#f6f4f0",
                                   activeforeground="#f6f4f0",
                                   relief="flat", highlightthickness=0,
                                   command=show_submenu_tab)
button_functions4_further.pack(pady=5)



# ВКЛАДКА УКПАИНСКИЙ ЯЗЫК
new_size_back_items1 = (17, 17)
button_back_items1 = button_back_items1.resize(new_size_back_items1)

photo_button_back_items1 = ImageTk.PhotoImage(button_back_items1)

button_back_items1 = Button(ukrainian_language_tab1,
                                   image=photo_button_back_items1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_items_tab)
button_back_items1.pack(anchor='nw', padx=62, pady=134)

label = Label(ukrainian_language_tab1, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items1():
    url = "https://us02web.zoom.us/j/3657204853?pwd=bU1WK1FnbndkempsL1VCK2VPZ2lTQT09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items1 = (305, 58)
button_come1 = button_come1.resize(new_size_come_items1)

photo_button_come_items1 = ImageTk.PhotoImage(button_come1)

button_come_items1 = Button(ukrainian_language_tab1,
                                   image=photo_button_come_items1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items1)
button_come_items1.pack(anchor='nw', padx=72, pady=0)

#УКРАИНСКАЯ ЛИТЕРАТУРА
new_size_back_items2 = (17, 17)
button_back_items2 = button_back_items2.resize(new_size_back_items2)

photo_button_back_items2 = ImageTk.PhotoImage(button_back_items2)

button_back_items2 = Button(ukrainian_literature_tab1,
                                   image=photo_button_back_items2,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_items_tab)
button_back_items2.pack(anchor='nw', padx=62, pady=134)

label = Label(ukrainian_language_tab1, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items2():
    url = "https://us02web.zoom.us/j/3657204853?pwd=bU1WK1FnbndkempsL1VCK2VPZ2lTQT09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items2 = (305, 58)
button_come2 = button_come2.resize(new_size_come_items1)

photo_button_come_items2 = ImageTk.PhotoImage(button_come2)

button_come_items2 = Button(ukrainian_literature_tab1,
                                   image=photo_button_come_items2,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items2)
button_come_items2.pack(anchor='nw', padx=72, pady=0)

#АНГЛИЙСКИЙ ЯЗЫК

#ИСТОРИЯ
new_size_back_items5 = (17, 17)
button_back_items5 = button_back_items5.resize(new_size_back_items5)

photo_button_back_items5 = ImageTk.PhotoImage(button_back_items5)

button_back_items5 = Button(history_tab1,
                                   image=photo_button_back_items5,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_items_tab)
button_back_items5.pack(anchor='nw', padx=62, pady=134)

label = Label(history_tab1, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items5():
    url = "https://us02web.zoom.us/j/6173922396?pwd=NkJhQi9nTkg5SUs2NkZxZmE1N2gwdz09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items5 = (305, 58)
button_come5 = button_come5.resize(new_size_come_items5)

photo_button_come_items5 = ImageTk.PhotoImage(button_come5)

button_come_items5 = Button(history_tab1,
                                   image=photo_button_come_items5,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items5)
button_come_items5.pack(anchor='nw', padx=72, pady=0)


#ЕКОНОМИКА
new_size_back_items6 = (17, 17)
button_back_items6 = button_back_items6.resize(new_size_back_items6)

photo_button_back_items6 = ImageTk.PhotoImage(button_back_items6)

button_back_items6 = Button(economy_tab1,
                                   image=photo_button_back_items6,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_items_tab)
button_back_items6.pack(anchor='nw', padx=62, pady=134)

label = Label(economy_tab1, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items6():
    url = "https://us05web.zoom.us/j/9184322138?pwd=eDhYQkhuOTZwdGt4dnVYUkZWYXRQdz09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items6 = (305, 58)
button_come6 = button_come6.resize(new_size_come_items6)

photo_button_come_items6 = ImageTk.PhotoImage(button_come6)

button_come_items6 = Button(economy_tab1,
                                   image=photo_button_come_items6,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items6)
button_come_items6.pack(anchor='nw', padx=72, pady=0)


#МАТЕМАТИЕА
new_size_back_items7 = (17, 17)
button_back_items7 = button_back_items7.resize(new_size_back_items7)

photo_button_back_items7 = ImageTk.PhotoImage(button_back_items7)

button_back_items7 = Button(mathematics_tab1,
                                   image=photo_button_back_items7,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_items_tab)
button_back_items7.pack(anchor='nw', padx=62, pady=134)

label = Label(mathematics_tab1, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items7():
    url = "https://us05web.zoom.us/j/5252402130?pwd=M3pUYWNIbjNIbHU1ZXFkbHNoSnMwUT09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items7 = (305, 58)
button_come7 = button_come7.resize(new_size_come_items7)

photo_button_come_items7 = ImageTk.PhotoImage(button_come7)

button_come_items7 = Button(mathematics_tab1,
                                   image=photo_button_come_items7,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items7)
button_come_items7.pack(anchor='nw', padx=72, pady=0)

#ФИЗИКА
new_size_back_items8 = (17, 17)
button_back_items8 = button_back_items8.resize(new_size_back_items8)

photo_button_back_items8 = ImageTk.PhotoImage(button_back_items8)

button_back_items8 = Button(physics_tab1,
                                   image=photo_button_back_items8,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_items_tab)
button_back_items8.pack(anchor='nw', padx=62, pady=134)

label = Label(physics_tab1, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items8():
    url = "https://us02web.zoom.us/j/7649687132?pwd=Z0g2dFdtRzhabm1JRFBrNEpmVWF1dz09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items8 = (305, 58)
button_come8 = button_come8.resize(new_size_come_items8)

photo_button_come_items8 = ImageTk.PhotoImage(button_come8)

button_come_items8 = Button(physics_tab1,
                                   image=photo_button_come_items8,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items8)
button_come_items8.pack(anchor='nw', padx=72, pady=0)

#АСТРОНОМИЯ
new_size_back_items9 = (17, 17)
button_back_items9 = button_back_items9.resize(new_size_back_items9)

photo_button_back_items9 = ImageTk.PhotoImage(button_back_items9)

button_back_items9 = Button(astronomy_tab1,
                                   image=photo_button_back_items9,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_items_tab)
button_back_items9.pack(anchor='nw', padx=62, pady=134)

label = Label(astronomy_tab1, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items9():
    url = "https://us05web.zoom.us/j/5252402130?pwd=M3pUYWNIbjNIbHU1ZXFkbHNoSnMwUT09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items9 = (305, 58)
button_come9 = button_come9.resize(new_size_come_items9)

photo_button_come_items9 = ImageTk.PhotoImage(button_come9)

button_come_items9 = Button(astronomy_tab1,
                                   image=photo_button_come_items9,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items9)
button_come_items9.pack(anchor='nw', padx=72, pady=0)


#ФКЗ
new_size_back_items10 = (17, 17)
button_back_items10 = button_back_items10.resize(new_size_back_items10)

photo_button_back_items10 = ImageTk.PhotoImage(button_back_items10)

button_back_items10 = Button(pt_tab1,
                                   image=photo_button_back_items10,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_items_tab)
button_back_items10.pack(anchor='nw', padx=62, pady=134)

label = Label(pt_tab1, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items10():
    url = "https://us02web.zoom.us/j/5089407939?pwd=QTlhZW83T2ZDSXdRU3UxRFlqZ2dsUT09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items10 = (305, 58)
button_come10 = button_come10.resize(new_size_come_items10)

photo_button_come_items10 = ImageTk.PhotoImage(button_come10)

button_come_items10 = Button(pt_tab1,
                                   image=photo_button_come_items10,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items10)
button_come_items10.pack(anchor='nw', padx=72, pady=0)

#ИНФОРМАЦИОННЫЕ ТЕХНОЛОГИИ
new_size_back_items11 = (17, 17)
button_back_items11 = button_back_items11.resize(new_size_back_items11)

photo_button_back_items11 = ImageTk.PhotoImage(button_back_items11)

button_back_items11 = Button(it_tab1,
                                   image=photo_button_back_items11,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_items_tab)
button_back_items11.pack(anchor='nw', padx=62, pady=134)

label = Label(it_tab1, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items11():
    url = "https://us02web.zoom.us/j/5742475269?pwd=cjhtajBlUmhJQ2NxU1V6ak5ydmtqZz09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items11 = (305, 58)
button_come11 = button_come11.resize(new_size_come_items11)

photo_button_come_items11 = ImageTk.PhotoImage(button_come11)

button_come_items11 = Button(it_tab1,
                                   image=photo_button_come_items11,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items11)
button_come_items11.pack(anchor='nw', padx=72, pady=0)

#БИОЛОГИЯ
new_size_back_items12 = (17, 17)
button_back_items12 = button_back_items12.resize(new_size_back_items12)

photo_button_back_items12 = ImageTk.PhotoImage(button_back_items12)

button_back_items12 = Button(biology_tab1,
                                   image=photo_button_back_items12,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_items_tab)
button_back_items12.pack(anchor='nw', padx=62, pady=134)

label = Label(biology_tab1, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items12():
    url = "https://us04web.zoom.us/j/5698912902?pwd=Ia6IrL0bfl0JP1PxidpDWdD4YKrRUO.1"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items12 = (305, 58)
button_come12 = button_come12.resize(new_size_come_items12)

photo_button_come_items12 = ImageTk.PhotoImage(button_come12)

button_come_items12 = Button(biology_tab1,
                                   image=photo_button_come_items12,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items12)
button_come_items12.pack(anchor='nw', padx=72, pady=0)


#ПРОГРАМИРОВАННИЕ
new_size_back_items13 = (17, 17)
button_back_items13 = button_back_items13.resize(new_size_back_items13)

photo_button_back_items13 = ImageTk.PhotoImage(button_back_items13)

button_back_items13 = Button(programming_tab1,
                                   image=photo_button_back_items13,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_items_tab)
button_back_items13.pack(anchor='nw', padx=62, pady=134)

label = Label(programming_tab1, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items13():
    url = "https://us06web.zoom.us/j/86016246672?pwd=rc3X1BavqTXvV5igkkXSCQ76zZkF8U.1"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items13 = (305, 58)
button_come13 = button_come13.resize(new_size_come_items13)

photo_button_come_items13 = ImageTk.PhotoImage(button_come13)

button_come_items13 = Button(programming_tab1,
                                   image=photo_button_come_items13,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items13)
button_come_items13.pack(anchor='nw', padx=72, pady=0)


#АМО
new_size_back_items14 = (17, 17)
button_back_items14 = button_back_items14.resize(new_size_back_items14)

photo_button_back_items14 = ImageTk.PhotoImage(button_back_items14)

button_back_items14 = Button(amo_tab1,
                                   image=photo_button_back_items14,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_items_tab)
button_back_items14.pack(anchor='nw', padx=62, pady=134)

label = Label(amo_tab1, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items14():
    url = "https://meet.google.com/sud-bvdp-gch-"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items14 = (305, 58)
button_come14 = button_come14.resize(new_size_come_items14)

photo_button_come_items14 = ImageTk.PhotoImage(button_come14)

button_come_items14 = Button(amo_tab1,
                                   image=photo_button_come_items14,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items14)
button_come_items14.pack(anchor='nw', padx=72, pady=0)


#БЖД
new_size_back_items15 = (17, 17)
button_back_items15 = button_back_items15.resize(new_size_back_items15)

photo_button_back_items15 = ImageTk.PhotoImage(button_back_items15)

button_back_items15 = Button(ls_tab1,
                                   image=photo_button_back_items15,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_items_tab)
button_back_items15.pack(anchor='nw', padx=62, pady=134)

label = Label(ls_tab1, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items15():
    url = "https://meet.google.com/ogw-qguh-tyu"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items15 = (305, 58)
button_come15 = button_come15.resize(new_size_come_items15)

photo_button_come_items15 = ImageTk.PhotoImage(button_come15)

button_come_items15 = Button(ls_tab1,
                                   image=photo_button_come_items15,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items15)
button_come_items15.pack(anchor='nw', padx=72, pady=0)




















new_size_back_items1_1 = (17, 17)
button_back_items1_1 = button_back_items1_1.resize(new_size_back_items1_1)

photo_button_back_items1_1 = ImageTk.PhotoImage(button_back_items1_1)

button_back_items1_1 = Button(ukrainian_language_tab,
                                   image=photo_button_back_items1_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_week_schedule_tab)
button_back_items1_1.pack(anchor='nw', padx=62, pady=134)

label = Label(ukrainian_language_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items1_1():
    url = "https://us02web.zoom.us/j/3657204853?pwd=bU1WK1FnbndkempsL1VCK2VPZ2lTQT09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items1_1 = (305, 58)
button_come1_1 = button_come1_1.resize(new_size_come_items1_1)

photo_button_come_items1_1= ImageTk.PhotoImage(button_come1_1)

button_come_items1_1 = Button(ukrainian_language_tab,
                                   image=photo_button_come_items1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items1)
button_come_items1_1.pack(anchor='nw', padx=72, pady=0)

#УКРАИНСКАЯ ЛИТЕРАТУРА
new_size_back_items2_1 = (17, 17)
button_back_items2_1 = button_back_items2_1.resize(new_size_back_items2_1)

photo_button_back_items2_1 = ImageTk.PhotoImage(button_back_items2_1)

button_back_items2_1 = Button(ukrainian_literature_tab,
                                   image=photo_button_back_items2_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_week_schedule_tab)
button_back_items2_1.pack(anchor='nw', padx=62, pady=134)

label = Label(ukrainian_language_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items2_1():
    url = "https://us02web.zoom.us/j/3657204853?pwd=bU1WK1FnbndkempsL1VCK2VPZ2lTQT09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items2_1 = (305, 58)
button_come2_1 = button_come2_1.resize(new_size_come_items2_1)

photo_button_come_items2_1 = ImageTk.PhotoImage(button_come2_1)

button_come_items2_1 = Button(ukrainian_literature_tab,
                                   image=photo_button_come_items2_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items2_1)
button_come_items2_1.pack(anchor='nw', padx=72, pady=0)

#АНГЛИЙСКИЙ ЯЗЫК

#ИСТОРИЯ
new_size_back_items5_1 = (17, 17)
button_back_items5_1 = button_back_items5_1.resize(new_size_back_items5_1)

photo_button_back_items5_1 = ImageTk.PhotoImage(button_back_items5_1)

button_back_items5_1 = Button(history_tab,
                                   image=photo_button_back_items5_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_week_schedule_tab)
button_back_items5_1.pack(anchor='nw', padx=62, pady=134)

label = Label(history_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items5_1():
    url = "https://us02web.zoom.us/j/6173922396?pwd=NkJhQi9nTkg5SUs2NkZxZmE1N2gwdz09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items5_1 = (305, 58)
button_come5_1 = button_come5_1.resize(new_size_come_items5_1)

photo_button_come_items5_1 = ImageTk.PhotoImage(button_come5_1)

button_come_items5_1 = Button(history_tab,
                                   image=photo_button_come_items5_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items5_1)
button_come_items5_1.pack(anchor='nw', padx=72, pady=0)


#ЕКОНОМИКА
new_size_back_items6_1 = (17, 17)
button_back_items6_1 = button_back_items6_1.resize(new_size_back_items6_1)

photo_button_back_items6_1 = ImageTk.PhotoImage(button_back_items6_1)

button_back_items6_1 = Button(economy_tab,
                                   image=photo_button_back_items6_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_week_schedule_tab)
button_back_items6_1.pack(anchor='nw', padx=62, pady=134)

label = Label(economy_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items6_1():
    url = "https://us05web.zoom.us/j/9184322138?pwd=eDhYQkhuOTZwdGt4dnVYUkZWYXRQdz09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items6_1 = (305, 58)
button_come6_1 = button_come6_1.resize(new_size_come_items6_1)

photo_button_come_items6_1 = ImageTk.PhotoImage(button_come6_1)

button_come_items6_1 = Button(economy_tab,
                                   image=photo_button_come_items6_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items6_1)
button_come_items6_1.pack(anchor='nw', padx=72, pady=0)


#МАТЕМАТИЕА
new_size_back_items7_1 = (17, 17)
button_back_items7_1 = button_back_items7_1.resize(new_size_back_items7_1)

photo_button_back_items7_1 = ImageTk.PhotoImage(button_back_items7_1)

button_back_items7_1 = Button(mathematics_tab,
                                   image=photo_button_back_items7_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_week_schedule_tab)
button_back_items7_1.pack(anchor='nw', padx=62, pady=134)

label = Label(mathematics_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7_1)


def open_link_items7_1():
    url = "https://us05web.zoom.us/j/5252402130?pwd=M3pUYWNIbjNIbHU1ZXFkbHNoSnMwUT09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items7_1 = (305, 58)
button_come7_1 = button_come7_1.resize(new_size_come_items7_1)

photo_button_come_items7_1 = ImageTk.PhotoImage(button_come7_1)

button_come_items7_1 = Button(mathematics_tab,
                                   image=photo_button_come_items7_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items7_1)
button_come_items7_1.pack(anchor='nw', padx=72, pady=0)

#ФИЗИКА
new_size_back_items8_1 = (17, 17)
button_back_items8_1 = button_back_items8_1.resize(new_size_back_items8_1 )

photo_button_back_items8_1 = ImageTk.PhotoImage(button_back_items8_1)

button_back_items8_1 = Button(physics_tab,
                                   image=photo_button_back_items8_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_week_schedule_tab)
button_back_items8_1.pack(anchor='nw', padx=62, pady=134)

label = Label(physics_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items8_1():
    url = "https://us02web.zoom.us/j/7649687132?pwd=Z0g2dFdtRzhabm1JRFBrNEpmVWF1dz09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items8_1 = (305, 58)
button_come8_1 = button_come8_1.resize(new_size_come_items8)

photo_button_come_items8_1 = ImageTk.PhotoImage(button_come8)

button_come_items8_1 = Button(physics_tab,
                                   image=photo_button_come_items8_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items8_1)
button_come_items8_1.pack(anchor='nw', padx=72, pady=0)

#АСТРОНОМИЯ
new_size_back_items9_1 = (17, 17)
button_back_items9_1 = button_back_items9_1.resize(new_size_back_items9_1)

photo_button_back_items9_1 = ImageTk.PhotoImage(button_back_items9_1)

button_back_items9_1 = Button(astronomy_tab,
                                   image=photo_button_back_items9_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_week_schedule_tab)
button_back_items9_1.pack(anchor='nw', padx=62, pady=134)

label = Label(astronomy_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items9_1():
    url = "https://us05web.zoom.us/j/5252402130?pwd=M3pUYWNIbjNIbHU1ZXFkbHNoSnMwUT09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items9_1 = (305, 58)
button_come9_1 = button_come9_1.resize(new_size_come_items9_1)

photo_button_come_items9_1 = ImageTk.PhotoImage(button_come9_1)

button_come_items9_1 = Button(astronomy_tab,
                                   image=photo_button_come_items9_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items9_1)
button_come_items9_1.pack(anchor='nw', padx=72, pady=0)


#ФКЗ
new_size_back_items10_1 = (17, 17)
button_back_items10_1 = button_back_items10_1.resize(new_size_back_items10_1)

photo_button_back_items10_1 = ImageTk.PhotoImage(button_back_items10_1)

button_back_items10_1 = Button(pt_tab,
                                   image=photo_button_back_items10_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_week_schedule_tab)
button_back_items10_1.pack(anchor='nw', padx=62, pady=134)

label = Label(pt_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items10_1():
    url = "https://us02web.zoom.us/j/5089407939?pwd=QTlhZW83T2ZDSXdRU3UxRFlqZ2dsUT09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items10_1 = (305, 58)
button_come10_1 = button_come10_1.resize(new_size_come_items10_1)

photo_button_come_items10_1 = ImageTk.PhotoImage(button_come10_1)

button_come_items10_1 = Button(pt_tab,
                                   image=photo_button_come_items10_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items10_1)
button_come_items10_1.pack(anchor='nw', padx=72, pady=0)

#ИНФОРМАЦИОННЫЕ ТЕХНОЛОГИИ
new_size_back_items11_1 = (17, 17)
button_back_items11_1 = button_back_items11_1.resize(new_size_back_items11_1)

photo_button_back_items11_1 = ImageTk.PhotoImage(button_back_items11_1)

button_back_items11_1 = Button(it_tab,
                                   image=photo_button_back_items11_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_week_schedule_tab)
button_back_items11_1.pack(anchor='nw', padx=62, pady=134)

label = Label(it_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items11_1():
    url = "https://us02web.zoom.us/j/5742475269?pwd=cjhtajBlUmhJQ2NxU1V6ak5ydmtqZz09"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items11_1 = (305, 58)
button_come11_1 = button_come11_1.resize(new_size_come_items11_1)

photo_button_come_items11_1 = ImageTk.PhotoImage(button_come11_1)

button_come_items11_1 = Button(it_tab,
                                   image=photo_button_come_items11_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items11_1)
button_come_items11_1.pack(anchor='nw', padx=72, pady=0)

#БИОЛОГИЯ
new_size_back_items12_1 = (17, 17)
button_back_items12_1 = button_back_items12_1.resize(new_size_back_items12_1)

photo_button_back_items12_1 = ImageTk.PhotoImage(button_back_items12_1)

button_back_items12_1 = Button(biology_tab,
                                   image=photo_button_back_items12_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_week_schedule_tab)
button_back_items12_1.pack(anchor='nw', padx=62, pady=134)

label = Label(biology_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items12_1():
    url = "https://us04web.zoom.us/j/5698912902?pwd=Ia6IrL0bfl0JP1PxidpDWdD4YKrRUO.1"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items12_1 = (305, 58)
button_come12_1 = button_come12_1.resize(new_size_come_items12_1)

photo_button_come_items12_1 = ImageTk.PhotoImage(button_come12_1)

button_come_items12_1 = Button(biology_tab,
                                   image=photo_button_come_items12_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items12_1)
button_come_items12_1.pack(anchor='nw', padx=72, pady=0)


#ПРОГРАМИРОВАННИЕ
new_size_back_items13_1 = (17, 17)
button_back_items13_1 = button_back_items13_1.resize(new_size_back_items13_1)

photo_button_back_items13_1 = ImageTk.PhotoImage(button_back_items13_1)

button_back_items13_1 = Button(programming_tab,
                                   image=photo_button_back_items13_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_week_schedule_tab)
button_back_items13_1.pack(anchor='nw', padx=62, pady=134)

label = Label(programming_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items13_1():
    url = "https://us06web.zoom.us/j/86016246672?pwd=rc3X1BavqTXvV5igkkXSCQ76zZkF8U.1"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items13_1 = (305, 58)
button_come13_1 = button_come13_1.resize(new_size_come_items13_1)

photo_button_come_items13_1 = ImageTk.PhotoImage(button_come13_1)

button_come_items13_1 = Button(programming_tab,
                                   image=photo_button_come_items13_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items13_1)
button_come_items13_1.pack(anchor='nw', padx=72, pady=0)


#АМО
new_size_back_items14_1 = (17, 17)
button_back_items14_1 = button_back_items14_1.resize(new_size_back_items14_1)

photo_button_back_items14_1 = ImageTk.PhotoImage(button_back_items14_1)

button_back_items14_1 = Button(amo_tab,
                                   image=photo_button_back_items14_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_week_schedule_tab)
button_back_items14_1.pack(anchor='nw', padx=62, pady=134)

label = Label(amo_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items14_1():
    url = "https://meet.google.com/sud-bvdp-gch-"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items14_1 = (305, 58)
button_come14_1 = button_come14_1.resize(new_size_come_items14_1)

photo_button_come_items14_1 = ImageTk.PhotoImage(button_come14_1)

button_come_items14_1 = Button(amo_tab,
                                   image=photo_button_come_items14_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items14_1)
button_come_items14_1.pack(anchor='nw', padx=72, pady=0)


#БЖД
new_size_back_items15_1 = (17, 17)
button_back_items15_1 = button_back_items15_1.resize(new_size_back_items15_1)

photo_button_back_items15_1 = ImageTk.PhotoImage(button_back_items15_1)

button_back_items15_1= Button(ls_tab,
                                   image=photo_button_back_items15_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=show_week_schedule_tab)
button_back_items15_1.pack(anchor='nw', padx=62, pady=134)

label = Label(ls_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=79, padx=7)


def open_link_items15_1():
    url = "https://meet.google.com/ogw-qguh-tyu"  # Замените ссылку на нужную вам
    webbrowser.open(url)

new_size_come_items15_1 = (305, 58)
button_come15_1 = button_come15_1.resize(new_size_come_items15_1)

photo_button_come_items15_1 = ImageTk.PhotoImage(button_come15_1)

button_come_items15_1 = Button(ls_tab,
                                   image=photo_button_come_items15_1,
                                   borderwidth=0,
                                   activebackground="white",
                                   activeforeground="white",
                                   relief="flat", highlightthickness=0,
                                   command=open_link_items15_1)
button_come_items15_1.pack(anchor='nw', padx=72, pady=0)





















#ПОНЕДЕЛЬНИК
frame_back_monday = Frame(monday_tab)
frame_back_monday.pack(anchor='nw', padx=25, pady=22)


def back_to_submenu_from_monday():
    notebook.select(week_schedule_tab)


new_size_back_monday = (18, 25)  # Новый размер (ширина, высота)
image_back_monday = image_back_monday.resize(new_size_back_monday)

photo_back_monday = ImageTk.PhotoImage(image_back_monday)

button_back_monday = Button(frame_back_monday, image=photo_back_monday, borderwidth=-4,
                              activebackground="#f6f4f0", activeforeground="#f6f4f0", relief="flat",
                              highlightthickness=0, command=back_to_submenu_from_monday)
button_back_monday.pack(side=LEFT)

label = Label(monday_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=5)

# ВТОРНИК
frame_back_tuesday = Frame(tuesday_tab)
frame_back_tuesday.pack(anchor='nw', padx=25, pady=22)


def back_to_submenu_from_tuesday():
    notebook.select(week_schedule_tab)


new_size_back_tuesday = (18, 25)  # Новый размер (ширина, высота)
image_back_tuesday = image_back_tuesday.resize(new_size_back_tuesday)

photo_back_tuesday = ImageTk.PhotoImage(image_back_tuesday)

button_back_tuesday = Button(frame_back_tuesday, image=photo_back_tuesday, borderwidth=-4,
                              activebackground="#f6f4f0", activeforeground="#f6f4f0", relief="flat",
                              highlightthickness=0, command=back_to_submenu_from_tuesday)
button_back_tuesday.pack(side=LEFT)

label = Label(tuesday_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=5)

#СРЕДА
frame_back_wednesday = Frame(wednesday_tab)
frame_back_wednesday.pack(anchor='nw', padx=25, pady=22)


def back_to_submenu_from_wednesday():
    notebook.select(week_schedule_tab)


new_size_back_wednesday = (18, 25)  # Новый размер (ширина, высота)
image_back_wednesday = image_back_wednesday.resize(new_size_back_wednesday)

photo_back_wednesday = ImageTk.PhotoImage(image_back_wednesday)

button_back_wednesday = Button(frame_back_wednesday, image=photo_back_wednesday, borderwidth=-4,
                              activebackground="#f6f4f0", activeforeground="#f6f4f0", relief="flat",
                              highlightthickness=0, command=back_to_submenu_from_wednesday)
button_back_wednesday.pack(side=LEFT)

label = Label(wednesday_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=5)



#ЧЕТВЕРГ
frame_back_thursday = Frame(thursday_tab)
frame_back_thursday.pack(anchor='nw', padx=25, pady=22)


def back_to_submenu_from_thursday():
    notebook.select(week_schedule_tab)


new_size_back_thursday = (18, 25)  # Новый размер (ширина, высота)
image_back_thursday = image_back_thursday.resize(new_size_back_thursday)

photo_back_thursday = ImageTk.PhotoImage(image_back_thursday)

button_back_thursday = Button(frame_back_thursday, image=photo_back_thursday, borderwidth=-4,
                              activebackground="#f6f4f0", activeforeground="#f6f4f0", relief="flat",
                              highlightthickness=0, command=back_to_submenu_from_thursday)
button_back_thursday.pack(side=LEFT)

label = Label(thursday_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=5)



#ПЯТНИЦА
frame_back_friday = Frame(friday_tab)
frame_back_friday.pack(anchor='nw', padx=25, pady=22)


def back_to_submenu_from_friday():
    notebook.select(week_schedule_tab)


new_size_back_friday = (18, 25)  # Новый размер (ширина, высота)
image_back_friday = image_back_friday.resize(new_size_back_friday)

photo_back_friday = ImageTk.PhotoImage(image_back_friday)

button_back_friday = Button(frame_back_friday, image=photo_back_friday, borderwidth=-4,
                              activebackground="#f6f4f0", activeforeground="#f6f4f0", relief="flat",
                              highlightthickness=0, command=back_to_submenu_from_friday)
button_back_friday.pack(side=LEFT)

label = Label(friday_tab, text="ㅤ", font='Arial 1', background="#f6f4f0")
label.pack(anchor='nw', pady=5)





new_size_all_items_by_day_week_image = (380, 106)

# НАЧАЛО 1 ПАРЫ ПОНЕДЕЛЬНИКА
if sheet['B2'].value == 'Укр Мова':
    button_ukr_mova_image1 = button_ukr_mova_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_ukr_mova1 = ImageTk.PhotoImage(button_ukr_mova_image1)

    button_ukr_mova1 = Button(monday_tab,
                              image=photo_button_ukr_mova1,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova1.pack(pady=15)
elif sheet['B2'].value == 'Укр Літ':
    button_ukr_lit_image1 = button_ukr_lit_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_ukr_lit1 = ImageTk.PhotoImage(button_ukr_lit_image1)

    button_ukr_lit1 = Button(monday_tab,
                             image=photo_button_ukr_lit1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit1.pack(pady=15)
elif sheet['B2'].value == 'Англійська':
    button_english_image1 = button_english_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_english1 = ImageTk.PhotoImage(button_english_image1)

    button_english1 = Button(monday_tab,
                             image=photo_button_english1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english1.pack(pady=15)
elif sheet['B2'].value == 'Історія':
    button_history_image1 = button_history_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_history1 = ImageTk.PhotoImage(button_history_image1)

    button_history1 = Button(monday_tab,
                             image=photo_button_history1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history1.pack(pady=15)
elif sheet['B2'].value == 'Економіка':
    button_economy_image1 = button_economy_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_economy1 = ImageTk.PhotoImage(button_economy_image1)

    button_economy1 = Button(monday_tab,
                             image=photo_button_economy1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy1.pack(pady=15)
elif sheet['B2'].value == 'Математика':
    button_math_image1 = button_math_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_math1 = ImageTk.PhotoImage(button_math_image1)

    button_math1 = Button(monday_tab,
                          image=photo_button_math1,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                             command=show_mathematics_tab)
    button_math1.pack(pady=15)
elif sheet['B2'].value == 'Фізика':
    button_physics_image1 = button_physics_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_physics1 = ImageTk.PhotoImage(button_physics_image1)

    button_physics1 = Button(monday_tab,
                             image=photo_button_physics1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics1.pack(pady=15)
elif sheet['B2'].value == 'Астрономія':
    button_astronomy_image1 = button_astronomy_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_astronomy1 = ImageTk.PhotoImage(button_astronomy_image1)

    button_astronomy1 = Button(monday_tab,
                               image=photo_button_astronomy1,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy1.pack(pady=15)
elif sheet['B2'].value == 'Біологія':
    button_biology_image1 = button_biology_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_biology1 = ImageTk.PhotoImage(button_biology_image1)

    button_biology1 = Button(monday_tab,
                             image=photo_button_biology1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology1.pack(pady=15)
elif sheet['B2'].value == 'ФКЗ':
    button_PKZ_image1 = button_PKZ_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_PKZ1 = ImageTk.PhotoImage(button_PKZ_image1)

    button_PKZ1 = Button(monday_tab,
                         image=photo_button_PKZ1,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ1.pack(pady=15)
elif sheet['B2'].value == 'IT':
    button_IT_image1 = button_IT_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_IT1 = ImageTk.PhotoImage(button_IT_image1)

    button_IT1 = Button(monday_tab,
                        image=photo_button_IT1,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT1.pack(pady=15)
elif sheet['B2'].value == 'Програмування':
    button_program_image1 = button_program_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_program1 = ImageTk.PhotoImage(button_program_image1)

    button_program1 = Button(monday_tab,
                             image=photo_button_program1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program1.pack(pady=15)
elif sheet['B2'].value == 'АМО':
    button_AMO_image1 = button_AMO_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_AMO1 = ImageTk.PhotoImage(button_AMO_image1)

    button_AMO1 = Button(monday_tab,
                         image=photo_button_AMO1,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO1.pack(pady=15)
elif sheet['B2'].value == 'БЖД':
    button_BZHD_image1 = button_BZHD_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_BZHD1 = ImageTk.PhotoImage(button_BZHD_image1)

    button_BZHD1 = Button(monday_tab,
                          image=photo_button_BZHD1,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD1.pack(pady=15)
# КОНЕЦ 1 ПАРЫ ПОНЕДЕЛЬНИКА

# НАЧАЛО 2 ПАРЫ ПОНЕДЕЛЬНИКА
new_size_button_secmonday_image1 = (380, 106)
if sheet['B3'].value == 'Укр Мова':
    button_ukr_mova_image1 = button_ukr_mova_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_ukr_mova1 = ImageTk.PhotoImage(button_ukr_mova_image1)

    button_ukr_mova1 = Button(monday_tab,
                              image=photo_button_ukr_mova1,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova1.pack(pady=0)
elif sheet['B3'].value == 'Укр Літ':
    button_ukr_lit_image = button_ukr_lit_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_ukr_lit1 = ImageTk.PhotoImage(button_ukr_lit_image)

    button_ukr_lit1 = Button(monday_tab,
                             image=photo_button_ukr_lit1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit1.pack(pady=0)
elif sheet['B3'].value == 'Англійська':
    button_english_image1 = button_english_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_english1 = ImageTk.PhotoImage(button_english_image1)

    button_english1 = Button(monday_tab,
                             image=photo_button_english1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english1.pack(pady=0)
elif sheet['B3'].value == 'Історія':
    button_history_image1 = button_history_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_history1 = ImageTk.PhotoImage(button_history_image1)

    button_history1 = Button(monday_tab,
                             image=photo_button_history1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history1.pack(pady=0)
elif sheet['B3'].value == 'Економіка':
    button_economy_image1 = button_economy_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_economy1 = ImageTk.PhotoImage(button_economy_image1)

    button_economy1 = Button(monday_tab,
                             image=photo_button_economy1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy1.pack(pady=0)
elif sheet['B3'].value == 'Математика':
    button_math_image1 = button_math_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_math1 = ImageTk.PhotoImage(button_math_image1)

    button_math1 = Button(monday_tab,
                          image=photo_button_math1,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                             command=show_mathematics_tab)
    button_math1.pack(pady=0)
elif sheet['B3'].value == 'Фізика':
    button_physics_image1 = button_physics_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_physics1 = ImageTk.PhotoImage(button_physics_image1)

    button_physics1 = Button(monday_tab,
                             image=photo_button_physics1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics1.pack(pady=0)
elif sheet['B3'].value == 'Астрономія':
    button_astronomy_image1 = button_astronomy_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_astronomy1 = ImageTk.PhotoImage(button_astronomy_image1)

    button_astronomy1 = Button(monday_tab,
                               image=photo_button_astronomy1,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy1.pack(pady=0)
elif sheet['B3'].value == 'Біологія':
    button_biology_image1 = button_biology_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_biology1 = ImageTk.PhotoImage(button_biology_image1)

    button_biology1 = Button(monday_tab,
                             image=photo_button_biology1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology1.pack(pady=0)
elif sheet['B3'].value == 'ФКЗ':
    button_PKZ_image1 = button_PKZ_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_PKZ1 = ImageTk.PhotoImage(button_PKZ_image1)

    button_PKZ1 = Button(monday_tab,
                         image=photo_button_PKZ1,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ1.pack(pady=0)
elif sheet['B3'].value == 'IT':
    button_IT_image1 = button_IT_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_IT1 = ImageTk.PhotoImage(button_IT_image1)

    button_IT1 = Button(monday_tab,
                        image=photo_button_IT1,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT1.pack(pady=0)
elif sheet['B3'].value == 'Програмування':
    button_program_image1 = button_program_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_program1 = ImageTk.PhotoImage(button_program_image1)

    button_program1 = Button(monday_tab,
                             image=photo_button_program1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program1.pack(pady=0)
elif sheet['B3'].value == 'АМО':
    button_AMO_image1 = button_AMO_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_AMO1 = ImageTk.PhotoImage(button_AMO_image1)

    button_AMO1 = Button(monday_tab,
                         image=photo_button_AMO1,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO1.pack(pady=0)
elif sheet['B3'].value == 'БЖД':
    button_BZHD_image1 = button_BZHD_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_BZHD1 = ImageTk.PhotoImage(button_BZHD_image1)

    button_BZHD1 = Button(monday_tab,
                          image=photo_button_BZHD1,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD1.pack(pady=0)
# КОНЕЦ 2 ПАРЫ ПОНЕДЕЛЬНИКА

# НАЧАЛО 3 ПАРЫ ПОНЕДЕЛЬНИКА
new_size_button_thmonday_image = (380, 106)
if sheet['B4'].value == 'Укр Мова':
    button_ukr_mova_image1 = button_ukr_mova_image1.resize(new_size_button_thmonday_image)

    photo_button_ukr_mova1 = ImageTk.PhotoImage(button_ukr_mova_image1)

    button_ukr_mova1 = Button(monday_tab,
                              image=photo_button_ukr_mova1,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova1.pack(pady=15)
elif sheet['B4'].value == 'Укр Літ':
    button_ukr_lit_image1 = button_ukr_lit_image1.resize(new_size_button_thmonday_image)

    photo_button_ukr_lit1 = ImageTk.PhotoImage(button_ukr_lit_image1)

    button_ukr_lit1 = Button(monday_tab,
                             image=photo_button_ukr_lit1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                              command=show_ukrainian_literature_tab)
    button_ukr_lit1.pack(pady=15)
elif sheet['B4'].value == 'Англійська':
    button_english_image = button_english_image1.resize(new_size_button_thmonday_image)

    photo_button_english1 = ImageTk.PhotoImage(button_english_image1)

    button_english1 = Button(monday_tab,
                             image=photo_button_english1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english1.pack(pady=15)
elif sheet['B4'].value == 'Історія':
    button_history_image1 = button_history_image1.resize(new_size_button_thmonday_image)

    photo_button_history1 = ImageTk.PhotoImage(button_history_image1)

    button_history1 = Button(monday_tab,
                             image=photo_button_history1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history1.pack(pady=15)
elif sheet['B4'].value == 'Економіка':
    button_economy_image1 = button_economy_image1.resize(new_size_button_thmonday_image)

    photo_button_economy1 = ImageTk.PhotoImage(button_economy_image1)

    button_economy1 = Button(monday_tab,
                             image=photo_button_economy1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy1.pack(pady=15)
elif sheet['B4'].value == 'Математика':
    button_math_image1 = button_math_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_math1 = ImageTk.PhotoImage(button_math_image1)

    button_math1 = Button(monday_tab,
                          image=photo_button_math1,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math1.pack(pady=15)
elif sheet['B4'].value == 'Фізика':
    button_physics_image1 = button_physics_image1.resize(new_size_button_thmonday_image)

    photo_button_physics1 = ImageTk.PhotoImage(button_physics_image1)

    button_physics1 = Button(monday_tab,
                             image=photo_button_physics1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics1.pack(pady=15)
elif sheet['B4'].value == 'Астрономія':
    button_astronomy_image1 = button_astronomy_image1.resize(new_size_button_thmonday_image)

    photo_button_astronomy1 = ImageTk.PhotoImage(button_astronomy_image1)

    button_astronomy1 = Button(monday_tab,
                               image=photo_button_astronomy1,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy1.pack(pady=15)
elif sheet['B4'].value == 'Біологія':
    button_biology_image1 = button_biology_image1.resize(new_size_button_thmonday_image)

    photo_button_biology1 = ImageTk.PhotoImage(button_biology_image1)

    button_biology1 = Button(monday_tab,
                             image=photo_button_biology1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology1.pack(pady=15)
elif sheet['B4'].value == 'ФКЗ':
    button_PKZ_image1 = button_PKZ_image1.resize(new_size_button_thmonday_image)

    photo_button_PKZ1 = ImageTk.PhotoImage(button_PKZ_image1)

    button_PKZ1 = Button(monday_tab,
                         image=photo_button_PKZ1,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ1.pack(pady=15)
elif sheet['B4'].value == 'IT':
    button_IT_image1 = button_IT_image1.resize(new_size_button_thmonday_image)

    photo_button_IT1 = ImageTk.PhotoImage(button_IT_image1)

    button_IT1 = Button(monday_tab,
                        image=photo_button_IT1,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT1.pack(pady=15)
elif sheet['B4'].value == 'Програмування':
    button_program_image1 = button_program_image1.resize(new_size_button_thmonday_image)

    photo_button_program1 = ImageTk.PhotoImage(button_program_image1)

    button_program1 = Button(monday_tab,
                             image=photo_button_program1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program1.pack(pady=15)
elif sheet['B4'].value == 'АМО':
    button_AMO_image1 = button_AMO_image1.resize(new_size_button_thmonday_image)

    photo_button_AMO1 = ImageTk.PhotoImage(button_AMO_image1)

    button_AMO1 = Button(monday_tab,
                         image=photo_button_AMO1,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO1.pack(pady=15)
elif sheet['B4'].value == 'БЖД':
    button_BZHD_image1 = button_BZHD_image1.resize(new_size_button_thmonday_image)

    photo_button_BZHD1 = ImageTk.PhotoImage(button_BZHD_image1)

    button_BZHD1 = Button(monday_tab,
                          image=photo_button_BZHD1,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD1.pack(pady=15)
# КОНЕЦ 3 ПАРЫ ПОНЕДЕЛЬНИКА

# НАЧАЛО 4 ПАРЫ ПОНЕДЕЛЬНИКА
new_size_button_fmonday_image = (380, 106)
if sheet['B5'].value == 'Укр Мова':
    button_ukr_mova_image1 = button_ukr_mova_image1.resize(new_size_button_fmonday_image)

    photo_button_ukr_mova1 = ImageTk.PhotoImage(button_ukr_mova_image1)

    button_ukr_mova1 = Button(monday_tab,
                              image=photo_button_ukr_mova1,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova1.pack(pady=0)
elif sheet['B5'].value == 'Укр Літ':
    button_ukr_lit_image1 = button_ukr_lit_image1.resize(new_size_button_fmonday_image)

    photo_button_ukr_lit1 = ImageTk.PhotoImage(button_ukr_lit_image1)

    button_ukr_lit1 = Button(monday_tab,
                             image=photo_button_ukr_lit1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit1.pack(pady=0)
elif sheet['B5'].value == 'Англійська':
    button_english_image1 = button_english_image1.resize(new_size_button_fmonday_image)

    photo_button_english1 = ImageTk.PhotoImage(button_english_image1)

    button_english1 = Button(monday_tab,
                             image=photo_button_english1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english1.pack(pady=0)
elif sheet['B5'].value == 'Історія':
    button_history_image1 = button_history_image1.resize(new_size_button_fmonday_image)

    photo_button_history1 = ImageTk.PhotoImage(button_history_image1)

    button_history1 = Button(monday_tab,
                             image=photo_button_history1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history1.pack(pady=0)
elif sheet['B5'].value == 'Економіка':
    button_economy_image1 = button_economy_image1.resize(new_size_button_fmonday_image)

    photo_button_economy1 = ImageTk.PhotoImage(button_economy_image1)

    button_economy1 = Button(monday_tab,
                             image=photo_button_economy1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy1.pack(pady=0)
elif sheet['B5'].value == 'Математика':
    button_math_image1 = button_math_image1.resize(new_size_button_fmonday_image)

    photo_button_math1 = ImageTk.PhotoImage(button_math_image1)

    button_math1 = Button(monday_tab,
                          image=photo_button_math1,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math1.pack(pady=0)
elif sheet['B5'].value == 'Фізика':
    button_physics_image1 = button_physics_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_physics1 = ImageTk.PhotoImage(button_physics_image1)

    button_physics1 = Button(monday_tab,
                             image=photo_button_physics1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics1.pack(pady=0)
elif sheet['B5'].value == 'Астрономія':
    button_astronomy_image1 = button_astronomy_image1.resize(new_size_button_fmonday_image)

    photo_button_astronomy1 = ImageTk.PhotoImage(button_astronomy_image1)

    button_astronomy1 = Button(monday_tab,
                               image=photo_button_astronomy1,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy1.pack(pady=0)
elif sheet['B5'].value == 'Біологія':
    button_biology_image1 = button_biology_image1.resize(new_size_button_fmonday_image)

    photo_button_biology1 = ImageTk.PhotoImage(button_biology_image1)

    button_biology1 = Button(monday_tab,
                             image=photo_button_biology1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology1.pack(pady=0)
elif sheet['B5'].value == 'ФКЗ':
    button_PKZ_image1 = button_PKZ_image1.resize(new_size_all_items_by_day_week_image)

    photo_button_PKZ1 = ImageTk.PhotoImage(button_PKZ_image1)

    button_PKZ1 = Button(monday_tab,
                         image=photo_button_PKZ1,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ1.pack(pady=0)
elif sheet['B5'].value == 'IT':
    button_IT_image1 = button_IT_image1.resize(new_size_button_fmonday_image)

    photo_button_IT1 = ImageTk.PhotoImage(button_IT_image1)

    button_IT1 = Button(monday_tab,
                        image=photo_button_IT1,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT1.pack(pady=0)
elif sheet['B5'].value == 'Програмування':
    button_program_image1 = button_program_image1.resize(new_size_button_fmonday_image)

    photo_button_program1 = ImageTk.PhotoImage(button_program_image1)

    button_program1 = Button(monday_tab,
                             image=photo_button_program1,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program1.pack(pady=0)
elif sheet['B5'].value == 'АМО':
    button_AMO_image1 = button_AMO_image1.resize(new_size_button_fmonday_image)

    photo_button_AMO1 = ImageTk.PhotoImage(button_AMO_image1)

    button_AMO1 = Button(monday_tab,
                         image=photo_button_AMO1,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO1.pack(pady=0)
elif sheet['B5'].value == 'БЖД':
    button_BZHD_image1 = button_BZHD_image1.resize(new_size_button_fmonday_image)

    photo_button_BZHD1 = ImageTk.PhotoImage(button_BZHD_image1)

    button_BZHD1 = Button(monday_tab,
                          image=photo_button_BZHD1,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD1.pack(pady=0)
# КОНЕЦ 4 ПАРЫ ПОНЕДЕЛЬНИКА


# НАЧАЛО 1 ПАРЫ ВТОРНИКА
new_size_button_tuesday_image = (380, 106)
if sheet['D2'].value == 'Укр Мова':
    button_ukr_mova_image2 = button_ukr_mova_image2.resize(new_size_button_tuesday_image)

    photo_button_ukr_mova2 = ImageTk.PhotoImage(button_ukr_mova_image2)

    button_ukr_mova2 = Button(tuesday_tab,
                              image=photo_button_ukr_mova2,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova2.pack(pady=15)
elif sheet['D2'].value == 'Укр Літ':
    button_ukr_lit_image2 = button_ukr_lit_image2.resize(new_size_button_tuesday_image)

    photo_button_ukr_lit2 = ImageTk.PhotoImage(button_ukr_lit_image2)

    button_ukr_lit2 = Button(tuesday_tab,
                             image=photo_button_ukr_lit2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit2.pack(pady=15)
elif sheet['D2'].value == 'Англійська':
    button_english_image2 = button_english_image2.resize(new_size_button_tuesday_image)

    photo_button_english2 = ImageTk.PhotoImage(button_english_image2)

    button_english2 = Button(tuesday_tab,
                             image=photo_button_english2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english2.pack(pady=15)
elif sheet['D2'].value == 'Історія':
    button_history_image2 = button_history_image2.resize(new_size_button_tuesday_image)

    photo_button_history2 = ImageTk.PhotoImage(button_history_image2)

    button_history2 = Button(tuesday_tab,
                             image=photo_button_history2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history2.pack(pady=15)
elif sheet['D2'].value == 'Економіка':
    button_economy_image2 = button_economy_image2.resize(new_size_button_tuesday_image)

    photo_button_economy2 = ImageTk.PhotoImage(button_economy_image2)

    button_economy2 = Button(tuesday_tab,
                             image=photo_button_economy2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy2.pack(pady=15)
elif sheet['D2'].value == 'Математика':
    button_math_image = button_math_image2.resize(new_size_button_tuesday_image)

    photo_button_math2 = ImageTk.PhotoImage(button_math_image2)

    button_math2 = Button(tuesday_tab,
                          image=photo_button_math2,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math2.pack(pady=15)
elif sheet['D2'].value == 'Фізика':
    button_physics_image2 = button_physics_image2.resize(new_size_button_tuesday_image)

    photo_button_physics2 = ImageTk.PhotoImage(button_physics_image2)

    button_physics2 = Button(tuesday_tab,
                             image=photo_button_physics2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics2.pack(pady=15)
elif sheet['D2'].value == 'Астрономія':
    button_astronomy_image2 = button_astronomy_image2.resize(new_size_button_tuesday_image)

    photo_button_astronomy2 = ImageTk.PhotoImage(button_astronomy_image2)

    button_astronomy2 = Button(tuesday_tab,
                               image=photo_button_astronomy2,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy2.pack(pady=15)
elif sheet['D2'].value == 'Біологія':
    button_biology_image2 = button_biology_image2.resize(new_size_button_tuesday_image)

    photo_button_biology2 = ImageTk.PhotoImage(button_biology_image2)

    button_biology2 = Button(tuesday_tab,
                             image=photo_button_biology2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology2.pack(pady=15)
elif sheet['D2'].value == 'ФКЗ':
    button_PKZ_image2 = button_PKZ_image2.resize(new_size_button_tuesday_image)

    photo_button_PKZ2 = ImageTk.PhotoImage(button_PKZ_image2)

    button_PKZ2 = Button(tuesday_tab,
                         image=photo_button_PKZ2,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ2.pack(pady=15)
elif sheet['D2'].value == 'IT':
    button_IT_image2 = button_IT_image2.resize(new_size_button_tuesday_image)

    photo_button_IT2 = ImageTk.PhotoImage(button_IT_image2)

    button_IT2 = Button(tuesday_tab,
                        image=photo_button_IT2,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT2.pack(pady=15)
elif sheet['D2'].value == 'Програмування':
    button_program_image2 = button_program_image2.resize(new_size_button_tuesday_image)

    photo_button_program2 = ImageTk.PhotoImage(button_program_image2)

    button_program2 = Button(tuesday_tab,
                             image=photo_button_program2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program2.pack(pady=15)
elif sheet['D2'].value == 'АМО':
    button_AMO_image2 = button_AMO_image2.resize(new_size_button_tuesday_image)

    photo_button_AMO2 = ImageTk.PhotoImage(button_AMO_image2)

    button_AMO2 = Button(tuesday_tab,
                         image=photo_button_AMO2,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO2.pack(pady=15)
elif sheet['D2'].value == 'БЖД':
    button_BZHD2_image = button_BZHD_image2.resize(new_size_button_tuesday_image)

    photo_button_BZHD2 = ImageTk.PhotoImage(button_BZHD_image2)

    button_BZHD2 = Button(tuesday_tab,
                          image=photo_button_BZHD2,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD2.pack(pady=15)
# КОНЕЦ 1 ПАРЫ ВТОРНИКА

# НАЧАЛО 2 ПАРЫ ВТОРНИКА
if sheet['D3'].value == 'Укр Мова':
    button_ukr_mova_image2 = button_ukr_mova_image2.resize(new_size_button_tuesday_image)

    photo_button_ukr_mova2 = ImageTk.PhotoImage(button_ukr_mova_image2)

    button_ukr_mova2 = Button(tuesday_tab,
                              image=photo_button_ukr_mova2,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova2.pack(pady=0)
elif sheet['D3'].value == 'Укр Літ':
    button_ukr_lit_image2 = button_ukr_lit_image2.resize(new_size_button_tuesday_image)

    photo_button_ukr_lit2 = ImageTk.PhotoImage(button_ukr_lit_image2)

    button_ukr_lit2 = Button(tuesday_tab,
                             image=photo_button_ukr_lit2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit2.pack(pady=0)
elif sheet['D3'].value == 'Англійська':
    button_english_image2 = button_english_image2.resize(new_size_button_tuesday_image)

    photo_button_english2 = ImageTk.PhotoImage(button_english_image2)

    button_english2 = Button(tuesday_tab,
                             image=photo_button_english2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english2.pack(pady=0)
elif sheet['D3'].value == 'Історія':
    button_history_image2 = button_history_image2.resize(new_size_button_tuesday_image)

    photo_button_history2 = ImageTk.PhotoImage(button_history_image2)

    button_history2 = Button(tuesday_tab,
                             image=photo_button_history2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history2.pack(pady=0)
elif sheet['D3'].value == 'Економіка':
    button_economy_image2 = button_economy_image2.resize(new_size_button_tuesday_image)

    photo_button_economy2 = ImageTk.PhotoImage(button_economy_image2)

    button_economy2 = Button(tuesday_tab,
                             image=photo_button_economy2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy2.pack(pady=0)
elif sheet['D3'].value == 'Математика':
    button_math_image2 = button_math_image2.resize(new_size_button_tuesday_image)

    photo_button_math2 = ImageTk.PhotoImage(button_math_image2)

    button_math2 = Button(tuesday_tab,
                          image=photo_button_math2,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math2.pack(pady=0)
elif sheet['D3'].value == 'Фізика':
    button_physics_image2 = button_physics_image2.resize(new_size_button_tuesday_image)

    photo_button_physics2 = ImageTk.PhotoImage(button_physics_image2)

    button_physics2 = Button(tuesday_tab,
                             image=photo_button_physics2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics2.pack(pady=0)
elif sheet['D3'].value == 'Астрономія':
    button_astronomy_image2 = button_astronomy_image2.resize(new_size_button_tuesday_image)

    photo_button_astronomy2 = ImageTk.PhotoImage(button_astronomy_image2)

    button_astronomy2 = Button(tuesday_tab,
                               image=photo_button_astronomy2,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy2.pack(pady=0)
elif sheet['D3'].value == 'Біологія':
    button_biology_image2 = button_biology_image2.resize(new_size_button_tuesday_image)

    photo_button_biology2 = ImageTk.PhotoImage(button_biology_image2)

    button_biology2 = Button(tuesday_tab,
                             image=photo_button_biology2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology2.pack(pady=0)
elif sheet['D3'].value == 'ФКЗ':
    button_PKZ_image2 = button_PKZ_image2.resize(new_size_button_tuesday_image)

    photo_button_PKZ2 = ImageTk.PhotoImage(button_PKZ_image2)

    button_PKZ2 = Button(tuesday_tab,
                         image=photo_button_PKZ2,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ2.pack(pady=0)
elif sheet['D3'].value == 'IT':
    button_IT_image2 = button_IT_image2.resize(new_size_button_tuesday_image)

    photo_button_IT2 = ImageTk.PhotoImage(button_IT_image2)

    button_IT2 = Button(tuesday_tab,
                        image=photo_button_IT2,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT2.pack(pady=0)
elif sheet['D3'].value == 'Програмування':
    button_program_image2 = button_program_image2.resize(new_size_button_tuesday_image)

    photo_button_program2 = ImageTk.PhotoImage(button_program_image2)

    button_program2 = Button(tuesday_tab,
                             image=photo_button_program2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program2.pack(pady=0)
elif sheet['D3'].value == 'АМО':
    button_AMO_image2 = button_AMO_image2.resize(new_size_button_tuesday_image)

    photo_button_AMO2 = ImageTk.PhotoImage(button_AMO_image2)

    button_AMO2 = Button(tuesday_tab,
                         image=photo_button_AMO2,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO2.pack(pady=0)
elif sheet['D3'].value == 'БЖД':
    button_BZHD_image2 = button_BZHD_image2.resize(new_size_button_tuesday_image)

    photo_button_BZHD2 = ImageTk.PhotoImage(button_BZHD_image2)

    button_BZHD2 = Button(tuesday_tab,
                          image=photo_button_BZHD2,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD2.pack(pady=0)
# КОНЕЦ 2 ПАРЫ ВТОРНИКА


# НАЧАЛО 3 ПАРЫ ВТОРНИКА
if sheet['D4'].value == 'Укр Мова':
    button_ukr_mova_image2 = button_ukr_mova_image2.resize(new_size_button_tuesday_image)

    photo_button_ukr_mova2 = ImageTk.PhotoImage(button_ukr_mova_image2)

    button_ukr_mova2 = Button(tuesday_tab,
                              image=photo_button_ukr_mova2,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,command=show_ukrainian_language_tab)
    button_ukr_mova2.pack(pady=15)
elif sheet['D4'].value == 'Укр Літ':
    button_ukr_lit_image2 = button_ukr_lit_image2.resize(new_size_button_tuesday_image)

    photo_button_ukr_lit2 = ImageTk.PhotoImage(button_ukr_lit_image2)

    button_ukr_lit2 = Button(tuesday_tab,
                             image=photo_button_ukr_lit2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit2.pack(pady=15)
elif sheet['D4'].value == 'Англійська':
    button_english_image2 = button_english_image2.resize(new_size_button_tuesday_image)

    photo_button_english2 = ImageTk.PhotoImage(button_english_image2)

    button_english2 = Button(tuesday_tab,
                             image=photo_button_english2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english2.pack(pady=15)
elif sheet['D4'].value == 'Історія':
    button_history_image2 = button_history_image2.resize(new_size_button_tuesday_image)

    photo_button_history2 = ImageTk.PhotoImage(button_history_image2)

    button_history2 = Button(tuesday_tab,
                             image=photo_button_history2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history2.pack(pady=15)
elif sheet['D4'].value == 'Економіка':
    button_economy_image2 = button_economy_image2.resize(new_size_button_tuesday_image)

    photo_button_economy2 = ImageTk.PhotoImage(button_economy_image2)

    button_economy2 = Button(tuesday_tab,
                             image=photo_button_economy2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy2.pack(pady=15)
elif sheet['D4'].value == 'Математика':
    button_math_image2 = button_math_image2.resize(new_size_button_tuesday_image)

    photo_button_math2 = ImageTk.PhotoImage(button_math_image2)

    button_math2 = Button(tuesday_tab,
                          image=photo_button_math2,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math2.pack(pady=15)
elif sheet['D4'].value == 'Фізика':
    button_physics_image2 = button_physics_image2.resize(new_size_button_tuesday_image)

    photo_button_physics2 = ImageTk.PhotoImage(button_physics_image2)

    button_physics2 = Button(tuesday_tab,
                             image=photo_button_physics2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics2.pack(pady=15)
elif sheet['D4'].value == 'Астрономія':
    button_astronomy_image2 = button_astronomy_image2.resize(new_size_button_tuesday_image)

    photo_button_astronomy2 = ImageTk.PhotoImage(button_astronomy_image2)

    button_astronomy2 = Button(tuesday_tab,
                               image=photo_button_astronomy2,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy2.pack(pady=15)
elif sheet['D4'].value == 'Біологія':
    button_biology_image2 = button_biology_image2.resize(new_size_button_tuesday_image)

    photo_button_biology2 = ImageTk.PhotoImage(button_biology_image2)

    button_biology2 = Button(tuesday_tab,
                             image=photo_button_biology2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology2.pack(pady=15)
elif sheet['D4'].value == 'ФКЗ':
    button_PKZ_image2 = button_PKZ_image2.resize(new_size_button_tuesday_image)

    photo_button_PKZ2 = ImageTk.PhotoImage(button_PKZ_image2)

    button_PKZ2 = Button(tuesday_tab,
                         image=photo_button_PKZ2,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ2.pack(pady=15)
elif sheet['D4'].value == 'IT':
    button_IT_image2 = button_IT_image2.resize(new_size_button_tuesday_image)

    photo_button_IT2 = ImageTk.PhotoImage(button_IT_image2)

    button_IT2 = Button(tuesday_tab,
                        image=photo_button_IT2,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT2.pack(pady=15)
elif sheet['D4'].value == 'Програмування':
    button_program_image2 = button_program_image2.resize(new_size_button_tuesday_image)

    photo_button_program2 = ImageTk.PhotoImage(button_program_image2)

    button_program2 = Button(tuesday_tab,
                             image=photo_button_program2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program2.pack(pady=15)
elif sheet['D4'].value == 'АМО':
    button_AMO_image2 = button_AMO_image2.resize(new_size_button_tuesday_image)

    photo_button_AMO2 = ImageTk.PhotoImage(button_AMO_image2)

    button_AMO2 = Button(tuesday_tab,
                         image=photo_button_AMO2,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO2.pack(pady=15)
elif sheet['D4'].value == 'БЖД':
    button_BZHD_image2 = button_BZHD_image2.resize(new_size_button_tuesday_image)

    photo_button_BZHD2 = ImageTk.PhotoImage(button_BZHD_image2)

    button_BZHD2 = Button(tuesday_tab,
                          image=photo_button_BZHD2,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD2.pack(pady=15)
# КОНЕЦ 3 ПАРЫ ВТОРНИКА

# НАЧАЛО 4 ПАРЫ ВТОРНИКА
if sheet['D5'].value == 'Укр Мова':
    button_ukr_mova_image2 = button_ukr_mova_image2.resize(new_size_button_fmonday_image)

    photo_button_ukr_mova2 = ImageTk.PhotoImage(button_ukr_mova_image2)

    button_ukr_mova2 = Button(tuesday_tab,
                              image=photo_button_ukr_mova2,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova2.pack(pady=0)
elif sheet['D5'].value == 'Укр Літ':
    button_ukr_lit_image2 = button_ukr_lit_image2.resize(new_size_button_fmonday_image)

    photo_button_ukr_lit2 = ImageTk.PhotoImage(button_ukr_lit_image2)

    button_ukr_lit2 = Button(tuesday_tab,
                             image=photo_button_ukr_lit2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit2.pack(pady=0)
elif sheet['D5'].value == 'Англійська':
    button_english_image2 = button_english_image2.resize(new_size_button_fmonday_image)

    photo_button_english2 = ImageTk.PhotoImage(button_english_image2)

    button_english2 = Button(tuesday_tab,
                             image=photo_button_english2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english2.pack(pady=0)
elif sheet['D5'].value == 'Історія':
    button_history_image2 = button_history_image2.resize(new_size_button_fmonday_image)

    photo_button_history2 = ImageTk.PhotoImage(button_history_image2)

    button_history2 = Button(tuesday_tab,
                             image=photo_button_history2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history2.pack(pady=0)
elif sheet['D5'].value == 'Економіка':
    button_economy_image2 = button_economy_image2.resize(new_size_button_fmonday_image)

    photo_button_economy2 = ImageTk.PhotoImage(button_economy_image2)

    button_economy2 = Button(tuesday_tab,
                             image=photo_button_economy2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy2.pack(pady=0)
elif sheet['D5'].value == 'Математика':
    button_math_image2 = button_math_image2.resize(new_size_button_fmonday_image)

    photo_button_math2 = ImageTk.PhotoImage(button_math_image2)

    button_math2 = Button(tuesday_tab,
                          image=photo_button_math2,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math2.pack(pady=0)
elif sheet['D5'].value == 'Фізика':
    button_physics_image2 = button_physics_image2.resize(new_size_button_fmonday_image)

    photo_button_physics2 = ImageTk.PhotoImage(button_physics_image2)

    button_physics2 = Button(tuesday_tab,
                             image=photo_button_physics2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics2.pack(pady=0)
elif sheet['D5'].value == 'Астрономія':
    button_astronomy_image2 = button_astronomy_image2.resize(new_size_button_fmonday_image)

    photo_button_astronomy2 = ImageTk.PhotoImage(button_astronomy_image2)

    button_astronomy2 = Button(tuesday_tab,
                               image=photo_button_astronomy2,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy2.pack(pady=0)
elif sheet['D5'].value == 'Біологія':
    button_biology_image2 = button_biology_image2.resize(new_size_button_fmonday_image)

    photo_button_biology2 = ImageTk.PhotoImage(button_biology_image2)

    button_biology2 = Button(tuesday_tab,
                             image=photo_button_biology2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology2.pack(pady=0)
elif sheet['D5'].value == 'ФКЗ':
    button_PKZ_image2 = button_PKZ_image2.resize(new_size_button_fmonday_image)

    photo_button_PKZ2 = ImageTk.PhotoImage(button_PKZ_image2)

    button_PKZ2 = Button(tuesday_tab,
                         image=photo_button_PKZ2,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ2.pack(pady=0)
elif sheet['D5'].value == 'IT':
    button_IT_image2 = button_IT_image2.resize(new_size_button_fmonday_image)

    photo_button_IT2 = ImageTk.PhotoImage(button_IT_image2)

    button_IT2 = Button(tuesday_tab,
                        image=photo_button_IT2,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT2.pack(pady=0)
elif sheet['D5'].value == 'Програмування':
    button_program_image2 = button_program_image2.resize(new_size_button_fmonday_image)

    photo_button_program2 = ImageTk.PhotoImage(button_program_image2)

    button_program2 = Button(tuesday_tab,
                             image=photo_button_program2,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program2.pack(pady=0)
elif sheet['D5'].value == 'АМО':
    button_AMO_image2 = button_AMO_image2.resize(new_size_button_fmonday_image)

    photo_button_AMO2 = ImageTk.PhotoImage(button_AMO_image2)

    button_AMO2 = Button(tuesday_tab,
                         image=photo_button_AMO2,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO2.pack(pady=0)
elif sheet['D5'].value == 'БЖД':
    button_BZHD_image2 = button_BZHD_image2.resize(new_size_button_fmonday_image)

    photo_button_BZHD2 = ImageTk.PhotoImage(button_BZHD_image2)

    button_BZHD2 = Button(tuesday_tab,
                          image=photo_button_BZHD2,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD2.pack(pady=0)
# КОНЕЦ 4 ПАРЫ ВТОРНИКА


# НАЧАЛО 1 ПАРЫ СРЕДЫ
new_size_button_wednesday_image = (380, 106)
if sheet['F2'].value == 'Укр Мова':
    button_ukr_mova_image4 = button_ukr_mova_image4.resize(new_size_button_wednesday_image)

    photo_button_ukr_mova4 = ImageTk.PhotoImage(button_ukr_mova_image4)

    button_ukr_mova4 = Button(wednesday_tab,
                              image=photo_button_ukr_mova4,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova4.pack(pady=15)
elif sheet['F2'].value == 'Укр Літ':
    button_ukr_lit_image4 = button_ukr_lit_image4.resize(new_size_button_wednesday_image)

    photo_button_ukr_lit4 = ImageTk.PhotoImage(button_ukr_lit_image4)

    button_ukr_lit4 = Button(wednesday_tab,
                             image=photo_button_ukr_lit4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit4.pack(pady=15)
elif sheet['F2'].value == 'Англійська':
    button_english_image4 = button_english_image4.resize(new_size_button_wednesday_image)

    photo_button_english4 = ImageTk.PhotoImage(button_english_image4)

    button_english4 = Button(wednesday_tab,
                             image=photo_button_english4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english4.pack(pady=15)
elif sheet['F2'].value == 'Історія':
    button_history_image4 = button_history_image4.resize(new_size_button_wednesday_image)

    photo_button_history4 = ImageTk.PhotoImage(button_history_image4)

    button_history4 = Button(wednesday_tab,
                             image=photo_button_history4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history4.pack(pady=15)
elif sheet['F2'].value == 'Економіка':
    button_economy_image4 = button_economy_image3.resize(new_size_button_wednesday_image)

    photo_button_economy4 = ImageTk.PhotoImage(button_economy_image4)

    button_economy4 = Button(wednesday_tab,
                             image=photo_button_economy4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy4.pack(pady=15)
elif sheet['F2'].value == 'Математика':
    button_math_image4 = button_math_image3.resize(new_size_button_wednesday_image)

    photo_button_math4 = ImageTk.PhotoImage(button_math_image4)

    button_math4 = Button(wednesday_tab,
                          image=photo_button_math4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math4.pack(pady=15)
elif sheet['F2'].value == 'Фізика':
    button_physics_image4 = button_physics_image4.resize(new_size_button_wednesday_image)

    photo_button_physics4 = ImageTk.PhotoImage(button_physics_image4)

    button_physics4 = Button(wednesday_tab,
                             image=photo_button_physics4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics4.pack(pady=15)
elif sheet['F2'].value == 'Астрономія':
    button_astronomy_image4 = button_astronomy_image4.resize(new_size_button_wednesday_image)

    photo_button_astronomy4 = ImageTk.PhotoImage(button_astronomy_image4)

    button_astronomy4 = Button(wednesday_tab,
                               image=photo_button_astronomy4,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy4.pack(pady=15)
elif sheet['F2'].value == 'Біологія':
    button_biology_image4 = button_biology_image4.resize(new_size_button_wednesday_image)

    photo_button_biology4 = ImageTk.PhotoImage(button_biology_image4)

    button_biology4 = Button(wednesday_tab,
                             image=photo_button_biology4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology4.pack(pady=15)
elif sheet['F2'].value == 'ФКЗ':
    button_PKZ_image4 = button_PKZ_image4.resize(new_size_button_wednesday_image)

    photo_button_PKZ4 = ImageTk.PhotoImage(button_PKZ_image4)

    button_PKZ4 = Button(wednesday_tab,
                         image=photo_button_PKZ4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ4.pack(pady=15)
elif sheet['F2'].value == 'IT':
    button_IT_image4 = button_IT_image4.resize(new_size_button_wednesday_image)

    photo_button_IT4 = ImageTk.PhotoImage(button_IT_image4)

    button_IT4 = Button(wednesday_tab,
                        image=photo_button_IT4,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT4.pack(pady=15)
elif sheet['F2'].value == 'Програмування':
    button_program_image4 = button_program_image4.resize(new_size_button_wednesday_image)

    photo_button_program4 = ImageTk.PhotoImage(button_program_image4)

    button_program4 = Button(wednesday_tab,
                             image=photo_button_program4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program4.pack(pady=15)
elif sheet['F2'].value == 'АМО':
    button_AMO_image4 = button_AMO_image4.resize(new_size_button_wednesday_image)

    photo_button_AMO4 = ImageTk.PhotoImage(button_AMO_image4)

    button_AMO4 = Button(wednesday_tab,
                         image=photo_button_AMO4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO4.pack(pady=15)
elif sheet['F2'].value == 'БЖД':
    button_BZHD_image4 = button_BZHD_image4.resize(new_size_button_wednesday_image)

    photo_button_BZHD4 = ImageTk.PhotoImage(button_BZHD_image4)

    button_BZHD4 = Button(wednesday_tab,
                          image=photo_button_BZHD4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD4.pack(pady=15)
# КОНЕЦ 1 ПАРЫ СРЕДЫ

# НАЧАЛО 2 ПАРЫ СРЕДЫ
if sheet['F3'].value == 'Укр Мова':
    button_ukr_mova_image4 = button_ukr_mova_image4.resize(new_size_button_wednesday_image)

    photo_button_ukr_mova4 = ImageTk.PhotoImage(button_ukr_mova_image4)

    button_ukr_mova4 = Button(wednesday_tab,
                              image=photo_button_ukr_mova4,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova4.pack(pady=0)
elif sheet['F3'].value == 'Укр Літ':
    button_ukr_lit_image4 = button_ukr_lit_image4.resize(new_size_button_wednesday_image)

    photo_button_ukr_lit4 = ImageTk.PhotoImage(button_ukr_lit_image4)

    button_ukr_lit4 = Button(wednesday_tab,
                             image=photo_button_ukr_lit4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit4.pack(pady=0)
elif sheet['F3'].value == 'Англійська':
    button_english_image3 = button_english_image3.resize(new_size_button_wednesday_image)

    photo_button_english4 = ImageTk.PhotoImage(button_english_image4)

    button_english4 = Button(wednesday_tab,
                             image=photo_button_english4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english4.pack(pady=0)
elif sheet['F3'].value == 'Історія':
    button_history_image4 = button_history_image3.resize(new_size_button_wednesday_image)

    photo_button_history4 = ImageTk.PhotoImage(button_history_image4)

    button_history4 = Button(wednesday_tab,
                             image=photo_button_history4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history4.pack(pady=0)
elif sheet['F3'].value == 'Економіка':
    button_economy_image4 = button_economy_image3.resize(new_size_button_wednesday_image)

    photo_button_economy4 = ImageTk.PhotoImage(button_economy_image4)

    button_economy4 = Button(wednesday_tab,
                             image=photo_button_economy4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy4.pack(pady=0)
elif sheet['F3'].value == 'Математика':
    button_math_image4 = button_math_image3.resize(new_size_button_wednesday_image)

    photo_button_math4 = ImageTk.PhotoImage(button_math_image4)

    button_math4 = Button(wednesday_tab,
                          image=photo_button_math4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math4.pack(pady=0)
elif sheet['F3'].value == 'Фізика':
    button_physics_image4 = button_physics_image3.resize(new_size_button_wednesday_image)

    photo_button_physics4 = ImageTk.PhotoImage(button_physics_image4)

    button_physics4 = Button(wednesday_tab,
                             image=photo_button_physics4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics4.pack(pady=0)
elif sheet['F3'].value == 'Астрономія':
    button_astronomy_image4 = button_astronomy_image4.resize(new_size_button_wednesday_image)

    photo_button_astronomy4 = ImageTk.PhotoImage(button_astronomy_image4)

    button_astronomy4 = Button(wednesday_tab,
                               image=photo_button_astronomy4,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy4.pack(pady=0)
elif sheet['F3'].value == 'Біологія':
    button_biology_image4 = button_biology_image3.resize(new_size_button_wednesday_image)

    photo_button_biology4 = ImageTk.PhotoImage(button_biology_image4)

    button_biology4 = Button(wednesday_tab,
                             image=photo_button_biology4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology4.pack(pady=0)
elif sheet['F3'].value == 'ФКЗ':
    button_PKZ_image4 = button_PKZ_image3.resize(new_size_button_wednesday_image)

    photo_button_PKZ4 = ImageTk.PhotoImage(button_PKZ_image4)

    button_PKZ4 = Button(wednesday_tab,
                         image=photo_button_PKZ4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ4.pack(pady=0)
elif sheet['F3'].value == 'IT':
    button_IT_image4 = button_IT_image3.resize(new_size_button_wednesday_image)

    photo_button_IT4 = ImageTk.PhotoImage(button_IT_image4)

    button_IT4 = Button(wednesday_tab,
                        image=photo_button_IT4,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT4.pack(pady=0)
elif sheet['F3'].value == 'Програмування':
    button_program_image4 = button_program_image3.resize(new_size_button_wednesday_image)

    photo_button_program4 = ImageTk.PhotoImage(button_program_image4)

    button_program4 = Button(wednesday_tab,
                             image=photo_button_program4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program4.pack(pady=0)
elif sheet['F3'].value == 'АМО':
    button_AMO_image4 = button_AMO_image3.resize(new_size_button_wednesday_image)

    photo_button_AMO4 = ImageTk.PhotoImage(button_AMO_image4)

    button_AMO4 = Button(wednesday_tab,
                         image=photo_button_AMO4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO4.pack(pady=0)
elif sheet['F3'].value == 'БЖД':
    button_BZHD_image4 = button_BZHD_image4.resize(new_size_button_wednesday_image)

    photo_button_BZHD4 = ImageTk.PhotoImage(button_BZHD_image4)

    button_BZHD4 = Button(wednesday_tab,
                          image=photo_button_BZHD4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD4.pack(pady=0)
# КОНЕЦ 2 ПАРЫ СРЕДЫ

# НАЧАЛО 3 ПАРЫ СРЕДЫ
if sheet['F4'].value == 'Укр Мова':
    button_ukr_mova_image4 = button_ukr_mova_image3.resize(new_size_button_wednesday_image)

    photo_button_ukr_mova4 = ImageTk.PhotoImage(button_ukr_mova_image4)

    button_ukr_mova4 = Button(wednesday_tab,
                              image=photo_button_ukr_mova4,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova4.pack(pady=15)
elif sheet['F4'].value == 'Укр Літ':
    button_ukr_lit_image4 = button_ukr_lit_image4.resize(new_size_button_wednesday_image)

    photo_button_ukr_lit4 = ImageTk.PhotoImage(button_ukr_lit_image4)

    button_ukr_lit4 = Button(wednesday_tab,
                             image=photo_button_ukr_lit4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit4.pack(pady=15)
elif sheet['F4'].value == 'Англійська':
    button_english_image4 = button_english_image3.resize(new_size_button_wednesday_image)

    photo_button_english4 = ImageTk.PhotoImage(button_english_image4)

    button_english4 = Button(wednesday_tab,
                             image=photo_button_english4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english4.pack(pady=15)
elif sheet['F4'].value == 'Історія':
    button_history_image4 = button_history_image4.resize(new_size_button_wednesday_image)

    photo_button_history4 = ImageTk.PhotoImage(button_history_image4)

    button_history4 = Button(wednesday_tab,
                             image=photo_button_history4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history4.pack(pady=15)
elif sheet['F4'].value == 'Економіка':
    button_economy_image4 = button_economy_image4.resize(new_size_button_wednesday_image)

    photo_button_economy4 = ImageTk.PhotoImage(button_economy_image4)

    button_economy4 = Button(wednesday_tab,
                             image=photo_button_economy4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy4.pack(pady=15)
elif sheet['F4'].value == 'Математика':
    button_math_image4 = button_math_image4.resize(new_size_button_wednesday_image)

    photo_button_math4 = ImageTk.PhotoImage(button_math_image4)

    button_math4 = Button(wednesday_tab,
                          image=photo_button_math4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math4.pack(pady=15)
elif sheet['F4'].value == 'Фізика':
    button_physics_image4 = button_physics_image4.resize(new_size_button_wednesday_image)

    photo_button_physics4 = ImageTk.PhotoImage(button_physics_image4)

    button_physics4 = Button(wednesday_tab,
                             image=photo_button_physics4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics4.pack(pady=15)
elif sheet['F4'].value == 'Астрономія':
    button_astronomy_image = button_astronomy_image3.resize(new_size_button_wednesday_image)

    photo_button_astronomy4 = ImageTk.PhotoImage(button_astronomy_image4)

    button_astronomy4 = Button(wednesday_tab,
                               image=photo_button_astronomy4,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy4.pack(pady=15)
elif sheet['F4'].value == 'Біологія':
    button_biology_image4 = button_biology_image4.resize(new_size_button_wednesday_image)

    photo_button_biology4 = ImageTk.PhotoImage(button_biology_image4)

    button_biology4 = Button(wednesday_tab,
                             image=photo_button_biology4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology4.pack(pady=15)
elif sheet['F4'].value == 'ФКЗ':
    button_PKZ_image4 = button_PKZ_image3.resize(new_size_button_wednesday_image)

    photo_button_PKZ4 = ImageTk.PhotoImage(button_PKZ_image4)

    button_PKZ4 = Button(wednesday_tab,
                         image=photo_button_PKZ4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ4.pack(pady=15)
elif sheet['F4'].value == 'IT':
    button_IT_image4 = button_IT_image4.resize(new_size_button_wednesday_image)

    photo_button_IT4 = ImageTk.PhotoImage(button_IT_image4)

    button_IT4 = Button(wednesday_tab,
                        image=photo_button_IT4,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT4.pack(pady=15)
elif sheet['F4'].value == 'Програмування':
    button_program_image4 = button_program_image4.resize(new_size_button_wednesday_image)

    photo_button_program4 = ImageTk.PhotoImage(button_program_image4)

    button_program4 = Button(wednesday_tab,
                             image=photo_button_program4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program4.pack(pady=15)
elif sheet['F4'].value == 'АМО':
    button_AMO_image4 = button_AMO_image4.resize(new_size_button_wednesday_image)

    photo_button_AMO4 = ImageTk.PhotoImage(button_AMO_image4)

    button_AMO4 = Button(wednesday_tab,
                         image=photo_button_AMO4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO4.pack(pady=15)
elif sheet['F4'].value == 'БЖД':
    button_BZHD_image4 = button_BZHD_image3.resize(new_size_button_wednesday_image)

    photo_button_BZHD4 = ImageTk.PhotoImage(button_BZHD_image4)

    button_BZHD4 = Button(wednesday_tab,
                          image=photo_button_BZHD4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD4.pack(pady=15)
# КОНЕЦ 3 ПАРЫ СРЕДЫ

# НАЧАЛО 4 ПАРЫ СРЕДЫ
if sheet['F5'].value == 'Укр Мова':
    button_ukr_mova_image4 = button_ukr_mova_image4.resize(new_size_button_wednesday_image)

    photo_button_ukr_mova4 = ImageTk.PhotoImage(button_ukr_mova_image4)

    button_ukr_mova4 = Button(wednesday_tab,
                              image=photo_button_ukr_mova4,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova4.pack(pady=0)
elif sheet['F5'].value == 'Укр Літ':
    button_ukr_lit_image4 = button_ukr_lit_image4.resize(new_size_button_wednesday_image)

    photo_button_ukr_lit4 = ImageTk.PhotoImage(button_ukr_lit_image4)

    button_ukr_lit4 = Button(wednesday_tab,
                             image=photo_button_ukr_lit4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit4.pack(pady=0)
elif sheet['F5'].value == 'Англійська':
    button_english_image4 = button_english_image4.resize(new_size_button_wednesday_image)

    photo_button_english4 = ImageTk.PhotoImage(button_english_image4)

    button_english4 = Button(wednesday_tab,
                             image=photo_button_english4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english4.pack(pady=0)
elif sheet['F5'].value == 'Історія':
    button_history_image4 = button_history_image4.resize(new_size_button_wednesday_image)

    photo_button_history4 = ImageTk.PhotoImage(button_history_image4)

    button_history4 = Button(wednesday_tab,
                             image=photo_button_history4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history4.pack(pady=0)
elif sheet['F5'].value == 'Економіка':
    button_economy_image4 = button_economy_image4.resize(new_size_button_wednesday_image)

    photo_button_economy4 = ImageTk.PhotoImage(button_economy_image4)

    button_economy4 = Button(wednesday_tab,
                             image=photo_button_economy4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy4.pack(pady=0)
elif sheet['F5'].value == 'Математика':
    button_math_image4 = button_math_image3.resize(new_size_button_wednesday_image)

    photo_button_math4 = ImageTk.PhotoImage(button_math_image4)

    button_math4 = Button(wednesday_tab,
                          image=photo_button_math4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math4.pack(pady=0)
elif sheet['F5'].value == 'Фізика':
    button_physics_image4 = button_physics_image3.resize(new_size_button_wednesday_image)

    photo_button_physics4 = ImageTk.PhotoImage(button_physics_image4)

    button_physics4 = Button(wednesday_tab,
                             image=photo_button_physics4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics4.pack(pady=0)
elif sheet['F5'].value == 'Астрономія':
    button_astronomy_image4 = button_astronomy_image4.resize(new_size_button_wednesday_image)

    photo_button_astronomy4 = ImageTk.PhotoImage(button_astronomy_image4)

    button_astronomy4 = Button(wednesday_tab,
                               image=photo_button_astronomy4,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy4.pack(pady=0)
elif sheet['F5'].value == 'Біологія':
    button_biology_image4 = button_biology_image3.resize(new_size_button_wednesday_image)

    photo_button_biology4 = ImageTk.PhotoImage(button_biology_image3)

    button_biology4 = Button(wednesday_tab,
                             image=photo_button_biology4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology4.pack(pady=0)
elif sheet['F5'].value == 'ФКЗ':
    button_PKZ_image4 = button_PKZ_image4.resize(new_size_button_wednesday_image)

    photo_button_PKZ4 = ImageTk.PhotoImage(button_PKZ_image4)

    button_PKZ4 = Button(wednesday_tab,
                         image=photo_button_PKZ4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ4.pack(pady=0)
elif sheet['F5'].value == 'IT':
    button_IT_image4 = button_IT_image4.resize(new_size_button_wednesday_image)

    photo_button_IT4 = ImageTk.PhotoImage(button_IT_image4)

    button_IT4 = Button(wednesday_tab,
                        image=photo_button_IT4,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT4.pack(pady=0)
elif sheet['F5'].value == 'Програмування':
    button_program_image4 = button_program_image4.resize(new_size_button_wednesday_image)

    photo_button_program4 = ImageTk.PhotoImage(button_program_image4)

    button_program4 = Button(wednesday_tab,
                             image=photo_button_program4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program4.pack(pady=0)
elif sheet['F5'].value == 'АМО':
    button_AMO_image4 = button_AMO_image4.resize(new_size_button_wednesday_image)

    photo_button_AMO4 = ImageTk.PhotoImage(button_AMO_image4)

    button_AMO4 = Button(wednesday_tab,
                         image=photo_button_AMO4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO4.pack(pady=0)
elif sheet['F5'].value == 'БЖД':
    button_BZHD_image4 = button_BZHD_image4.resize(new_size_button_wednesday_image)

    photo_button_BZHD4 = ImageTk.PhotoImage(button_BZHD_image4)

    button_BZHD4 = Button(wednesday_tab,
                          image=photo_button_BZHD4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD4.pack(pady=0)
# КОНЕЦ 4 ПАРЫ СРЕДЫ


# НАЧАЛО 1 ПАРЫ ЧЕТВЕРГА
new_size_button_thursday_image = (380, 106)
if sheet['H2'].value == 'Укр Мова':
    button_ukr_mova_image4 = button_ukr_mova_image4.resize(new_size_button_thursday_image)

    photo_button_ukr_mova4 = ImageTk.PhotoImage(button_ukr_mova_image4)

    button_ukr_mova4 = Button(thursday_tab,
                              image=photo_button_ukr_mova4,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova4.pack(pady=15)
elif sheet['H2'].value == 'Укр Літ':
    button_ukr_lit_image4 = button_ukr_lit_image4.resize(new_size_button_thursday_image)

    photo_button_ukr_lit4 = ImageTk.PhotoImage(button_ukr_lit_image4)

    button_ukr_lit4 = Button(thursday_tab,
                             image=photo_button_ukr_lit4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                              command=show_ukrainian_literature_tab)
    button_ukr_lit4.pack(pady=15)
elif sheet['H2'].value == 'Англійська':
    button_english_image4 = button_english_image4.resize(new_size_button_thursday_image)

    photo_button_english4 = ImageTk.PhotoImage(button_english_image4)

    button_english4 = Button(thursday_tab,
                             image=photo_button_english4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english4.pack(pady=15)
elif sheet['H2'].value == 'Історія':
    button_history_image4 = button_history_image4.resize(new_size_button_thursday_image)

    photo_button_history4 = ImageTk.PhotoImage(button_history_image4)

    button_history4 = Button(thursday_tab,
                             image=photo_button_history4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history4.pack(pady=15)
elif sheet['H2'].value == 'Економіка':
    button_economy_image4 = button_economy_image4.resize(new_size_button_thursday_image)

    photo_button_economy4 = ImageTk.PhotoImage(button_economy_image4)

    button_economy4 = Button(thursday_tab,
                             image=photo_button_economy4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy4.pack(pady=15)
elif sheet['H2'].value == 'Математика':
    button_math_image4 = button_math_image4.resize(new_size_button_thursday_image)

    photo_button_math4 = ImageTk.PhotoImage(button_math_image4)

    button_math4 = Button(thursday_tab,
                          image=photo_button_math4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math4.pack(pady=15)
elif sheet['H2'].value == 'Фізика':
    button_physics_image4 = button_physics_image4.resize(new_size_button_thursday_image)

    photo_button_physics4 = ImageTk.PhotoImage(button_physics_image4)

    button_physics4 = Button(thursday_tab,
                             image=photo_button_physics4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics4.pack(pady=15)
elif sheet['H2'].value == 'Астрономія':
    button_astronomy_image4 = button_astronomy_image4.resize(new_size_button_thursday_image)

    photo_button_astronomy4 = ImageTk.PhotoImage(button_astronomy_image4)

    button_astronomy4 = Button(thursday_tab,
                               image=photo_button_astronomy4,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy4.pack(pady=15)
elif sheet['H2'].value == 'Біологія':
    button_biology_image4 = button_biology_image4.resize(new_size_button_thursday_image)

    photo_button_biology4 = ImageTk.PhotoImage(button_biology_image4)

    button_biology4 = Button(thursday_tab,
                             image=photo_button_biology4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology4.pack(pady=15)
elif sheet['H2'].value == 'ФКЗ':
    button_PKZ_image4 = button_PKZ_image4.resize(new_size_button_thursday_image)

    photo_button_PKZ4 = ImageTk.PhotoImage(button_PKZ_image4)

    button_PKZ4 = Button(thursday_tab,
                         image=photo_button_PKZ4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ4.pack(pady=15)
elif sheet['H2'].value == 'IT':
    button_IT_image4 = button_IT_image4.resize(new_size_button_thursday_image)

    photo_button_IT4 = ImageTk.PhotoImage(button_IT_image4)

    button_IT4 = Button(thursday_tab,
                        image=photo_button_IT4,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT4.pack(pady=15)
elif sheet['H2'].value == 'Програмування':
    button_program_image4 = button_program_image4.resize(new_size_button_thursday_image)

    photo_button_program4 = ImageTk.PhotoImage(button_program_image4)

    button_program4 = Button(thursday_tab,
                             image=photo_button_program4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program4.pack(pady=15)
elif sheet['H2'].value == 'АМО':
    button_AMO_image4 = button_AMO_image4.resize(new_size_button_thursday_image)

    photo_button_AMO4 = ImageTk.PhotoImage(button_AMO_image4)

    button_AMO4 = Button(thursday_tab,
                         image=photo_button_AMO4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO4.pack(pady=15)
elif sheet['H2'].value == 'БЖД':
    button_BZHD_image4 = button_BZHD_image4.resize(new_size_button_thursday_image)

    photo_button_BZHD4 = ImageTk.PhotoImage(button_BZHD_image4)

    button_BZHD4 = Button(thursday_tab,
                          image=photo_button_BZHD4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD4.pack(pady=15)
# КОНЕЦ 1 ПАРЫ ЧЕТВЕРГА

# НАЧАЛО 2 ПАРЫ ЧЕТВЕРГА
if sheet['H3'].value == 'Укр Мова':
    button_ukr_mova_image4 = button_ukr_mova_image4.resize(new_size_button_thursday_image)

    photo_button_ukr_mova4 = ImageTk.PhotoImage(button_ukr_mova_image4)

    button_ukr_mova4 = Button(thursday_tab,
                              image=photo_button_ukr_mova4,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova4.pack(pady=0)
elif sheet['H3'].value == 'Укр Літ':
    button_ukr_lit_image4 = button_ukr_lit_image4.resize(new_size_button_thursday_image)

    photo_button_ukr_lit4 = ImageTk.PhotoImage(button_ukr_lit_image4)

    button_ukr_lit4 = Button(thursday_tab,
                             image=photo_button_ukr_lit4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                              command=show_ukrainian_literature_tab)
    button_ukr_lit4.pack(pady=0)
elif sheet['H3'].value == 'Англійська':
    button_english_image4 = button_english_image4.resize(new_size_button_thursday_image)

    photo_button_english4 = ImageTk.PhotoImage(button_english_image4)

    button_english4 = Button(thursday_tab,
                             image=photo_button_english4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english4.pack(pady=0)
elif sheet['H3'].value == 'Історія':
    button_history_image4 = button_history_image4.resize(new_size_button_thursday_image)

    photo_button_history4 = ImageTk.PhotoImage(button_history_image4)

    button_history4 = Button(thursday_tab,
                             image=photo_button_history4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history4.pack(pady=0)
elif sheet['H3'].value == 'Економіка':
    button_economy_image4 = button_economy_image4.resize(new_size_button_thursday_image)

    photo_button_economy4 = ImageTk.PhotoImage(button_economy_image4)

    button_economy4 = Button(thursday_tab,
                             image=photo_button_economy4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy4.pack(pady=0)
elif sheet['H3'].value == 'Математика':
    button_math_image4 = button_math_image4.resize(new_size_button_thursday_image)

    photo_button_math4 = ImageTk.PhotoImage(button_math_image4)

    button_math4 = Button(thursday_tab,
                          image=photo_button_math4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math4.pack(pady=0)
elif sheet['H3'].value == 'Фізика':
    button_physics_image4 = button_physics_image4.resize(new_size_button_thursday_image)

    photo_button_physics4 = ImageTk.PhotoImage(button_physics_image4)

    button_physics4 = Button(thursday_tab,
                             image=photo_button_physics4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics4.pack(pady=0)
elif sheet['H3'].value == 'Астрономія':
    button_astronomy_image4 = button_astronomy_image4.resize(new_size_button_thursday_image)

    photo_button_astronomy4 = ImageTk.PhotoImage(button_astronomy_image4)

    button_astronomy4 = Button(thursday_tab,
                               image=photo_button_astronomy4,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy4.pack(pady=0)
elif sheet['H3'].value == 'Біологія':
    button_biology_image4 = button_biology_image4.resize(new_size_button_thursday_image)

    photo_button_biology4 = ImageTk.PhotoImage(button_biology_image4)

    button_biology4 = Button(thursday_tab,
                             image=photo_button_biology4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology4.pack(pady=0)
elif sheet['H3'].value == 'ФКЗ':
    button_PKZ_image4 = button_PKZ_image4.resize(new_size_button_thursday_image)

    photo_button_PKZ4 = ImageTk.PhotoImage(button_PKZ_image4)

    button_PKZ4 = Button(thursday_tab,
                         image=photo_button_PKZ4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ4.pack(pady=0)
elif sheet['H3'].value == 'IT':
    button_IT_image4 = button_IT_image4.resize(new_size_button_thursday_image)

    photo_button_IT4 = ImageTk.PhotoImage(button_IT_image4)

    button_IT4 = Button(thursday_tab,
                        image=photo_button_IT4,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT4.pack(pady=0)
elif sheet['H3'].value == 'Програмування':
    button_program_image4 = button_program_image4.resize(new_size_button_thursday_image)

    photo_button_program4 = ImageTk.PhotoImage(button_program_image4)

    button_program4 = Button(thursday_tab,
                             image=photo_button_program4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                        command=show_programming_tab)
    button_program4.pack(pady=0)
elif sheet['H3'].value == 'АМО':
    button_AMO_image4 = button_AMO_image4.resize(new_size_button_thursday_image)

    photo_button_AMO4 = ImageTk.PhotoImage(button_AMO_image4)

    button_AMO4 = Button(thursday_tab,
                         image=photo_button_AMO4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO4.pack(pady=0)
elif sheet['H3'].value == 'БЖД':
    button_BZHD_image4 = button_BZHD_image4.resize(new_size_button_thursday_image)

    photo_button_BZHD4 = ImageTk.PhotoImage(button_BZHD_image4)

    button_BZHD4 = Button(thursday_tab,
                          image=photo_button_BZHD4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD4.pack(pady=0)
# КОНЕЦ 2 ПАРЫ ЧЕТВЕРГА

# НАЧАЛО 3 ПАРЫ ЧЕТВЕРГА
if sheet['H4'].value == 'Укр Мова':
    button_ukr_mova_image4 = button_ukr_mova_image4.resize(new_size_button_thursday_image)

    photo_button_ukr_mova4 = ImageTk.PhotoImage(button_ukr_mova_image4)

    button_ukr_mova4 = Button(thursday_tab,
                              image=photo_button_ukr_mova4,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova4.pack(pady=15)
elif sheet['H4'].value == 'Укр Літ':
    button_ukr_lit_image4 = button_ukr_lit_image4.resize(new_size_button_thursday_image)

    photo_button_ukr_lit4 = ImageTk.PhotoImage(button_ukr_lit_image4)

    button_ukr_lit4 = Button(thursday_tab,
                             image=photo_button_ukr_lit4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit4.pack(pady=15)
elif sheet['H4'].value == 'Англійська':
    button_english_image4 = button_english_image4.resize(new_size_button_thursday_image)

    photo_button_english4 = ImageTk.PhotoImage(button_english_image4)

    button_english4 = Button(thursday_tab,
                             image=photo_button_english4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english4.pack(pady=15)
elif sheet['H4'].value == 'Історія':
    button_history_image4 = button_history_image4.resize(new_size_button_wednesday_image)

    photo_button_history4 = ImageTk.PhotoImage(button_history_image4)

    button_history4 = Button(thursday_tab,
                             image=photo_button_history4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history4.pack(pady=15)
elif sheet['H4'].value == 'Економіка':
    button_economy_image4 = button_economy_image4.resize(new_size_button_thursday_image)

    photo_button_economy4 = ImageTk.PhotoImage(button_economy_image4)

    button_economy4 = Button(thursday_tab,
                             image=photo_button_economy4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy4.pack(pady=15)
elif sheet['H4'].value == 'Математика':
    button_math_image4 = button_math_image4.resize(new_size_button_thursday_image)

    photo_button_math4 = ImageTk.PhotoImage(button_math_image4)

    button_math4 = Button(thursday_tab,
                          image=photo_button_math4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math4.pack(pady=15)
elif sheet['H4'].value == 'Фізика':
    button_physics_image4 = button_physics_image4.resize(new_size_button_thursday_image)

    photo_button_physics4 = ImageTk.PhotoImage(button_physics_image4)

    button_physics4 = Button(thursday_tab,
                             image=photo_button_physics4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics4.pack(pady=15)
elif sheet['H4'].value == 'Астрономія':
    button_astronomy_image = button_astronomy_image4.resize(new_size_button_thursday_image)

    photo_button_astronomy4 = ImageTk.PhotoImage(button_astronomy_image4)

    button_astronomy4 = Button(thursday_tab,
                               image=photo_button_astronomy4,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy4.pack(pady=15)
elif sheet['H4'].value == 'Біологія':
    button_biology_image4 = button_biology_image4.resize(new_size_button_thursday_image)

    photo_button_biology4 = ImageTk.PhotoImage(button_biology_image4)

    button_biology4 = Button(thursday_tab,
                             image=photo_button_biology4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology4.pack(pady=15)
elif sheet['H4'].value == 'ФКЗ':
    button_PKZ_image4 = button_PKZ_image4.resize(new_size_button_thursday_image)

    photo_button_PKZ4 = ImageTk.PhotoImage(button_PKZ_image4)

    button_PKZ4 = Button(thursday_tab,
                         image=photo_button_PKZ4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ4.pack(pady=15)
elif sheet['H4'].value == 'IT':
    button_IT_image4 = button_IT_image4.resize(new_size_button_thursday_image)

    photo_button_IT4 = ImageTk.PhotoImage(button_IT_image4)

    button_IT4 = Button(thursday_tab,
                        image=photo_button_IT4,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT4.pack(pady=15)
elif sheet['H4'].value == 'Програмування':
    button_program_image4 = button_program_image4.resize(new_size_button_thursday_image)

    photo_button_program4 = ImageTk.PhotoImage(button_program_image4)

    button_program4 = Button(thursday_tab,
                             image=photo_button_program4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_programming_tab)
    button_program4.pack(pady=15)
elif sheet['H4'].value == 'АМО':
    button_AMO_image4 = button_AMO_image4.resize(new_size_button_thursday_image)

    photo_button_AMO4 = ImageTk.PhotoImage(button_AMO_image4)

    button_AMO4 = Button(thursday_tab,
                         image=photo_button_AMO4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO4.pack(pady=15)
elif sheet['H4'].value == 'БЖД':
    button_BZHD_image4 = button_BZHD_image4.resize(new_size_button_thursday_image)

    photo_button_BZHD4 = ImageTk.PhotoImage(button_BZHD_image4)

    button_BZHD4 = Button(thursday_tab,
                          image=photo_button_BZHD4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD4.pack(pady=15)
# КОНЕЦ 3 ПАРЫ ЧЕТВЕРГА

# НАЧАЛО 4 ПАРЫ ЧЕТВЕРГА
if sheet['H5'].value == 'Укр Мова':
    button_ukr_mova_image4 = button_ukr_mova_image4.resize(new_size_button_thursday_image)

    photo_button_ukr_mova4 = ImageTk.PhotoImage(button_ukr_mova_image4)

    button_ukr_mova4 = Button(thursday_tab,
                              image=photo_button_ukr_mova4,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova4.pack(pady=0)
elif sheet['H5'].value == 'Укр Літ':
    button_ukr_lit_image4 = button_ukr_lit_image4.resize(new_size_button_thursday_image)

    photo_button_ukr_lit4 = ImageTk.PhotoImage(button_ukr_lit_image4)

    button_ukr_lit4 = Button(thursday_tab,
                             image=photo_button_ukr_lit4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit4.pack(pady=0)
elif sheet['H5'].value == 'Англійська':
    button_english_image4 = button_english_image4.resize(new_size_button_thursday_image)

    photo_button_english4 = ImageTk.PhotoImage(button_english_image4)

    button_english4 = Button(thursday_tab,
                             image=photo_button_english4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english4.pack(pady=0)
elif sheet['H5'].value == 'Історія':
    button_history_image4 = button_history_image4.resize(new_size_button_thursday_image)

    photo_button_history4 = ImageTk.PhotoImage(button_history_image4)

    button_history4 = Button(thursday_tab,
                             image=photo_button_history4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history4.pack(pady=0)
elif sheet['H5'].value == 'Економіка':
    button_economy_image4 = button_economy_image4.resize(new_size_button_thursday_image)

    photo_button_economy4 = ImageTk.PhotoImage(button_economy_image4)

    button_economy4 = Button(thursday_tab,
                             image=photo_button_economy4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy4.pack(pady=0)
elif sheet['H5'].value == 'Математика':
    button_math_image4 = button_math_image4.resize(new_size_button_thursday_image)

    photo_button_math4 = ImageTk.PhotoImage(button_math_image4)

    button_math4 = Button(thursday_tab,
                          image=photo_button_math4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math4.pack(pady=0)
elif sheet['H5'].value == 'Фізика':
    button_physics_image4 = button_physics_image4.resize(new_size_button_thursday_image)

    photo_button_physics4 = ImageTk.PhotoImage(button_physics_image4)

    button_physics4 = Button(thursday_tab,
                             image=photo_button_physics4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics4.pack(pady=0)
elif sheet['H5'].value == 'Астрономія':
    button_astronomy_image4 = button_astronomy_image4.resize(new_size_button_thursday_image)

    photo_button_astronomy4 = ImageTk.PhotoImage(button_astronomy_image4)

    button_astronomy4 = Button(thursday_tab,
                               image=photo_button_astronomy4,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy4.pack(pady=0)
elif sheet['H5'].value == 'Біологія':
    button_biology_image4 = button_biology_image4.resize(new_size_button_thursday_image)

    photo_button_biology4 = ImageTk.PhotoImage(button_biology_image4)

    button_biology4 = Button(thursday_tab,
                             image=photo_button_biology4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology4.pack(pady=0)
elif sheet['H5'].value == 'ФКЗ':
    button_PKZ_image4 = button_PKZ_image4.resize(new_size_button_thursday_image)

    photo_button_PKZ4 = ImageTk.PhotoImage(button_PKZ_image4)

    button_PKZ4 = Button(thursday_tab,
                         image=photo_button_PKZ4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ4.pack(pady=0)
elif sheet['H5'].value == 'IT':
    button_IT_image4 = button_IT_image4.resize(new_size_button_thursday_image)

    photo_button_IT4 = ImageTk.PhotoImage(button_IT_image4)

    button_IT4 = Button(thursday_tab,
                        image=photo_button_IT4,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT4.pack(pady=0)
elif sheet['H5'].value == 'Програмування':
    button_program_image4 = button_program_image4.resize(new_size_button_thursday_image)

    photo_button_program4 = ImageTk.PhotoImage(button_program_image4)

    button_program4 = Button(thursday_tab,
                             image=photo_button_program4,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_programming_tab)
    button_program4.pack(pady=0)
elif sheet['H5'].value == 'АМО':
    button_AMO_image4 = button_AMO_image4.resize(new_size_button_thursday_image)

    photo_button_AMO4 = ImageTk.PhotoImage(button_AMO_image4)

    button_AMO4 = Button(thursday_tab,
                         image=photo_button_AMO4,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO4.pack(pady=0)
elif sheet['H5'].value == 'БЖД':
    button_BZHD_image4 = button_BZHD_image4.resize(new_size_button_thursday_image)

    photo_button_BZHD4 = ImageTk.PhotoImage(button_BZHD_image4)

    button_BZHD4 = Button(thursday_tab,
                          image=photo_button_BZHD4,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD4.pack(pady=0)
# КОНЕЦ 4 ПАРЫ ЧЕТВЕРГА


# НАЧАЛО 1 ПАРЫ ПЯТНИЦЫ
if sheet['J2'].value == 'Укр Мова':
    button_ukr_mova_image5 = button_ukr_mova_image5.resize(new_size_button_thursday_image)

    photo_button_ukr_mova5 = ImageTk.PhotoImage(button_ukr_mova_image5)

    button_ukr_mova5 = Button(friday_tab,
                              image=photo_button_ukr_mova5,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova5.pack(pady=15)
elif sheet['J2'].value == 'Укр Літ':
    button_ukr_lit_image5 = button_ukr_lit_image5.resize(new_size_button_thursday_image)

    photo_button_ukr_lit5 = ImageTk.PhotoImage(button_ukr_lit_image5)

    button_ukr_lit5 = Button(friday_tab,
                             image=photo_button_ukr_lit5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_ukrainian_literature_tab)
    button_ukr_lit5.pack(pady=15)
elif sheet['J2'].value == 'Англійська':
    button_english_image5 = button_english_image5.resize(new_size_button_thursday_image)

    photo_button_english5 = ImageTk.PhotoImage(button_english_image5)

    button_english5 = Button(friday_tab,
                             image=photo_button_english5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english5.pack(pady=15)
elif sheet['J2'].value == 'Історія':
    button_history_image5 = button_history_image5.resize(new_size_button_thursday_image)

    photo_button_history5 = ImageTk.PhotoImage(button_history_image5)

    button_history5 = Button(friday_tab,
                             image=photo_button_history5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history5.pack(pady=15)
elif sheet['J2'].value == 'Економіка':
    button_economy_image5 = button_economy_image5.resize(new_size_button_thursday_image)

    photo_button_economy5 = ImageTk.PhotoImage(button_economy_image5)

    button_economy5 = Button(friday_tab,
                             image=photo_button_economy5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy5.pack(pady=15)
elif sheet['J2'].value == 'Математика':
    button_math_image5 = button_math_image5.resize(new_size_button_thursday_image)

    photo_button_math5 = ImageTk.PhotoImage(button_math_image5)

    button_math5 = Button(friday_tab,
                          image=photo_button_math5,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math5.pack(pady=15)
elif sheet['J2'].value == 'Фізика':
    button_physics_image5 = button_physics_image5.resize(new_size_button_thursday_image)

    photo_button_physics5 = ImageTk.PhotoImage(button_physics_image5)

    button_physics5 = Button(friday_tab,
                             image=photo_button_physics5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics5.pack(pady=15)
elif sheet['J2'].value == 'Астрономія':
    button_astronomy_image5 = button_astronomy_image5.resize(new_size_button_thursday_image)

    photo_button_astronomy5 = ImageTk.PhotoImage(button_astronomy_image5)

    button_astronomy5 = Button(friday_tab,
                               image=photo_button_astronomy5,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy5.pack(pady=15)
elif sheet['J2'].value == 'Біологія':
    button_biology_image5 = button_biology_image5.resize(new_size_button_thursday_image)

    photo_button_biology5 = ImageTk.PhotoImage(button_biology_image5)

    button_biology5 = Button(friday_tab,
                             image=photo_button_biology5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology5.pack(pady=15)
elif sheet['J2'].value == 'ФКЗ':
    button_PKZ_image5 = button_PKZ_image5.resize(new_size_button_thursday_image)

    photo_button_PKZ5 = ImageTk.PhotoImage(button_PKZ_image5)

    button_PKZ5 = Button(friday_tab,
                         image=photo_button_PKZ5,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ5.pack(pady=15)
elif sheet['J2'].value == 'IT':
    button_IT_image5 = button_IT_image5.resize(new_size_button_thursday_image)

    photo_button_IT5 = ImageTk.PhotoImage(button_IT_image5)

    button_IT5 = Button(friday_tab,
                        image=photo_button_IT5,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT5.pack(pady=15)
elif sheet['J2'].value == 'Програмування':
    button_program_image5 = button_program_image5.resize(new_size_button_thursday_image)

    photo_button_program5 = ImageTk.PhotoImage(button_program_image5)

    button_program5 = Button(friday_tab,
                             image=photo_button_program5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_programming_tab)
    button_program5.pack(pady=15)
elif sheet['J2'].value == 'АМО':
    button_AMO_image5 = button_AMO_image5.resize(new_size_button_thursday_image)

    photo_button_AMO5 = ImageTk.PhotoImage(button_AMO_image5)

    button_AMO5 = Button(friday_tab,
                         image=photo_button_AMO5,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO5.pack(pady=15)
elif sheet['J2'].value == 'БЖД':
    button_BZHD_image5 = button_BZHD_image5.resize(new_size_button_thursday_image)

    photo_button_BZHD5 = ImageTk.PhotoImage(button_BZHD_image5)

    button_BZHD5 = Button(friday_tab,
                          image=photo_button_BZHD5,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD5.pack(pady=15)
# КОНЕЦ 1 ПАРЫ ПЯТНИЦЫ

# НАЧАЛО 2 ПАРЫ ПЯТНИЦЫ
if sheet['J3'].value == 'Укр Мова':
    button_ukr_mova_image5 = button_ukr_mova_image5.resize(new_size_button_thursday_image)

    photo_button_ukr_mova5 = ImageTk.PhotoImage(button_ukr_mova_image5)

    button_ukr_mova5 = Button(friday_tab,
                              image=photo_button_ukr_mova5,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova5.pack(pady=0)
elif sheet['J3'].value == 'Укр Літ':
    button_ukr_lit_image5 = button_ukr_lit_image5.resize(new_size_button_thursday_image)

    photo_button_ukr_lit5 = ImageTk.PhotoImage(button_ukr_lit_image5)

    button_ukr_lit5 = Button(friday_tab,
                             image=photo_button_ukr_lit5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                              command=show_ukrainian_literature_tab)
    button_ukr_lit5.pack(pady=0)
elif sheet['J3'].value == 'Англійська':
    button_english_image5 = button_english_image5.resize(new_size_button_thursday_image)

    photo_button_english5 = ImageTk.PhotoImage(button_english_image5)

    button_english5 = Button(friday_tab,
                             image=photo_button_english5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english5.pack(pady=0)
elif sheet['J3'].value == 'Історія':
    button_history_image5 = button_history_image5.resize(new_size_button_thursday_image)

    photo_button_history5 = ImageTk.PhotoImage(button_history_image5)

    button_history5 = Button(friday_tab,
                             image=photo_button_history5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history5.pack(pady=0)
elif sheet['J3'].value == 'Економіка':
    button_economy_image5 = button_economy_image5.resize(new_size_button_thursday_image)

    photo_button_economy5 = ImageTk.PhotoImage(button_economy_image5)

    button_economy5 = Button(friday_tab,
                             image=photo_button_economy5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy5.pack(pady=0)
elif sheet['J3'].value == 'Математика':
    button_math_image5 = button_math_image5.resize(new_size_button_thursday_image)

    photo_button_math5 = ImageTk.PhotoImage(button_math_image5)

    button_math5 = Button(friday_tab,
                          image=photo_button_math5,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math5.pack(pady=0)
elif sheet['J3'].value == 'Фізика':
    button_physics_image5 = button_physics_image5.resize(new_size_button_thursday_image)

    photo_button_physics5 = ImageTk.PhotoImage(button_physics_image5)

    button_physics5 = Button(friday_tab,
                             image=photo_button_physics5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics5.pack(pady=0)
elif sheet['J3'].value == 'Астрономія':
    button_astronomy_image5 = button_astronomy_image5.resize(new_size_button_thursday_image)

    photo_button_astronomy5 = ImageTk.PhotoImage(button_astronomy_image5)

    button_astronomy5 = Button(friday_tab,
                               image=photo_button_astronomy5,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy5.pack(pady=0)
elif sheet['J3'].value == 'Біологія':
    button_biology_image5 = button_biology_image5.resize(new_size_button_thursday_image)

    photo_button_biology5 = ImageTk.PhotoImage(button_biology_image5)

    button_biology5 = Button(friday_tab,
                             image=photo_button_biology5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology5.pack(pady=0)
elif sheet['J3'].value == 'ФКЗ':
    button_PKZ_image5 = button_PKZ_image5.resize(new_size_button_thursday_image)

    photo_button_PKZ5 = ImageTk.PhotoImage(button_PKZ_image5)

    button_PKZ5 = Button(friday_tab,
                         image=photo_button_PKZ5,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ5.pack(pady=0)
elif sheet['J3'].value == 'IT':
    button_IT_image5 = button_IT_image5.resize(new_size_button_thursday_image)

    photo_button_IT5 = ImageTk.PhotoImage(button_IT_image5)

    button_IT5 = Button(friday_tab,
                        image=photo_button_IT5,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT5.pack(pady=0)
elif sheet['J3'].value == 'Програмування':
    button_program_image5 = button_program_image5.resize(new_size_button_thursday_image)

    photo_button_program5 = ImageTk.PhotoImage(button_program_image5)

    button_program5 = Button(friday_tab,
                             image=photo_button_program5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_programming_tab)
    button_program5.pack(pady=0)
elif sheet['J3'].value == 'АМО':
    button_AMO_image5 = button_AMO_image5.resize(new_size_button_thursday_image)

    photo_button_AMO5 = ImageTk.PhotoImage(button_AMO_image5)

    button_AMO5 = Button(friday_tab,
                         image=photo_button_AMO5,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO5.pack(pady=0)
elif sheet['J3'].value == 'БЖД':
    button_BZHD_image5 = button_BZHD_image5.resize(new_size_button_thursday_image)

    photo_button_BZHD5 = ImageTk.PhotoImage(button_BZHD_image5)

    button_BZHD5 = Button(friday_tab,
                          image=photo_button_BZHD5,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD5.pack(pady=0)
# КОНЕЦ 2 ПАРЫ ПЯТНИЦЫ

# НАЧАЛО 3 ПАРЫ ПЯТНИЦЫ
if sheet['J4'].value == 'Укр Мова':
    button_ukr_mova_image5 = button_ukr_mova_image5.resize(new_size_button_thursday_image)

    photo_button_ukr_mova5 = ImageTk.PhotoImage(button_ukr_mova_image5)

    button_ukr_mova5 = Button(friday_tab,
                              image=photo_button_ukr_mova5,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova5.pack(pady=15)
elif sheet['J4'].value == 'Укр Літ':
    button_ukr_lit_image5 = button_ukr_lit_image5.resize(new_size_button_thursday_image)

    photo_button_ukr_lit5 = ImageTk.PhotoImage(button_ukr_lit_image5)

    button_ukr_lit5 = Button(friday_tab,
                             image=photo_button_ukr_lit5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                              command=show_ukrainian_literature_tab)
    button_ukr_lit5.pack(pady=15)
elif sheet['J4'].value == 'Англійська':
    button_english_image5 = button_english_image5.resize(new_size_button_thursday_image)

    photo_button_english5 = ImageTk.PhotoImage(button_english_image5)

    button_english5 = Button(friday_tab,
                             image=photo_button_english5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english5.pack(pady=15)
elif sheet['J4'].value == 'Історія':
    button_history_image5 = button_history_image5.resize(new_size_button_wednesday_image)

    photo_button_history5 = ImageTk.PhotoImage(button_history_image5)

    button_history5 = Button(friday_tab,
                             image=photo_button_history5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history5.pack(pady=15)
elif sheet['J4'].value == 'Економіка':
    button_economy_image5 = button_economy_image5.resize(new_size_button_thursday_image)

    photo_button_economy5 = ImageTk.PhotoImage(button_economy_image5)

    button_economy5 = Button(friday_tab,
                             image=photo_button_economy5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy5.pack(pady=15)
elif sheet['J4'].value == 'Математика':
    button_math_image5 = button_math_image5.resize(new_size_button_thursday_image)

    photo_button_math5 = ImageTk.PhotoImage(button_math_image5)

    button_math5 = Button(friday_tab,
                          image=photo_button_math5,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math5.pack(pady=15)
elif sheet['J4'].value == 'Фізика':
    button_physics_image5 = button_physics_image5.resize(new_size_button_thursday_image)

    photo_button_physics5 = ImageTk.PhotoImage(button_physics_image5)

    button_physics5 = Button(friday_tab,
                             image=photo_button_physics5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics5.pack(pady=15)
elif sheet['J4'].value == 'Астрономія':
    button_astronomy_image = button_astronomy_image5.resize(new_size_button_thursday_image)

    photo_button_astronomy5 = ImageTk.PhotoImage(button_astronomy_image5)

    button_astronomy5 = Button(friday_tab,
                               image=photo_button_astronomy5,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy5.pack(pady=15)
elif sheet['J4'].value == 'Біологія':
    button_biology_image5 = button_biology_image5.resize(new_size_button_thursday_image)

    photo_button_biology5 = ImageTk.PhotoImage(button_biology_image5)

    button_biology5 = Button(friday_tab,
                             image=photo_button_biology5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology5.pack(pady=15)
elif sheet['J4'].value == 'ФКЗ':
    button_PKZ_image5 = button_PKZ_image5.resize(new_size_button_thursday_image)

    photo_button_PKZ5 = ImageTk.PhotoImage(button_PKZ_image5)

    button_PKZ5 = Button(friday_tab,
                         image=photo_button_PKZ5,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ5.pack(pady=15)
elif sheet['J4'].value == 'IT':
    button_IT_image5 = button_IT_image5.resize(new_size_button_thursday_image)

    photo_button_IT5 = ImageTk.PhotoImage(button_IT_image5)

    button_IT5 = Button(friday_tab,
                        image=photo_button_IT5,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT5.pack(pady=15)
elif sheet['J4'].value == 'Програмування':
    button_program_image5 = button_program_image5.resize(new_size_button_thursday_image)

    photo_button_program5 = ImageTk.PhotoImage(button_program_image5)

    button_program5 = Button(friday_tab,
                             image=photo_button_program5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_programming_tab)
    button_program5.pack(pady=15)
elif sheet['J4'].value == 'АМО':
    button_AMO_image5 = button_AMO_image5.resize(new_size_button_thursday_image)

    photo_button_AMO5 = ImageTk.PhotoImage(button_AMO_image5)

    button_AMO5 = Button(friday_tab,
                         image=photo_button_AMO5,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO5.pack(pady=15)
elif sheet['J4'].value == 'БЖД':
    button_BZHD_image5 = button_BZHD_image5.resize(new_size_button_thursday_image)

    photo_button_BZHD5 = ImageTk.PhotoImage(button_BZHD_image5)

    button_BZHD5 = Button(friday_tab,
                          image=photo_button_BZHD5,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD5.pack(pady=15)
# КОНЕЦ 3 ПАРЫ ПЯТНИЦЫ

# НАЧАЛО 4 ПАРЫ ПЯТНИЦЫ
if sheet['J5'].value == 'Укр Мова':
    button_ukr_mova_image5 = button_ukr_mova_image5.resize(new_size_button_thursday_image)

    photo_button_ukr_mova5 = ImageTk.PhotoImage(button_ukr_mova_image4)

    button_ukr_mova5 = Button(friday_tab,
                              image=photo_button_ukr_mova5,
                              borderwidth=0,
                              activebackground="#fee698",
                              activeforeground="#fee698",
                              relief="flat",
                              highlightthickness=0,
                              command=show_ukrainian_language_tab)
    button_ukr_mova5.pack(pady=0)
elif sheet['J5'].value == 'Укр Літ':
    button_ukr_lit_image5 = button_ukr_lit_image5.resize(new_size_button_thursday_image)

    photo_button_ukr_lit5 = ImageTk.PhotoImage(button_ukr_lit_image5)

    button_ukr_lit5 = Button(friday_tab,
                             image=photo_button_ukr_lit5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                              command=show_ukrainian_literature_tab)
    button_ukr_lit5.pack(pady=0)
elif sheet['J5'].value == 'Англійська':
    button_english_image5 = button_english_image5.resize(new_size_button_thursday_image)

    photo_button_english5 = ImageTk.PhotoImage(button_english_image5)

    button_english5 = Button(friday_tab,
                             image=photo_button_english5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_english_tab)
    button_english5.pack(pady=0)
elif sheet['J5'].value == 'Історія':
    button_history_image5 = button_history_image5.resize(new_size_button_thursday_image)

    photo_button_history5 = ImageTk.PhotoImage(button_history_image5)

    button_history5 = Button(friday_tab,
                             image=photo_button_history5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_history_tab)
    button_history5.pack(pady=0)
elif sheet['J5'].value == 'Економіка':
    button_economy_image5 = button_economy_image5.resize(new_size_button_thursday_image)

    photo_button_economy5 = ImageTk.PhotoImage(button_economy_image5)

    button_economy5 = Button(friday_tab,
                             image=photo_button_economy5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_economy_tab)
    button_economy5.pack(pady=0)
elif sheet['J5'].value == 'Математика':
    button_math_image5 = button_math_image5.resize(new_size_button_thursday_image)

    photo_button_math5 = ImageTk.PhotoImage(button_math_image5)

    button_math5 = Button(friday_tab,
                          image=photo_button_math5,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_mathematics_tab)
    button_math5.pack(pady=0)
elif sheet['J5'].value == 'Фізика':
    button_physics_image5 = button_physics_image5.resize(new_size_button_thursday_image)

    photo_button_physics5 = ImageTk.PhotoImage(button_physics_image5)

    button_physics5 = Button(friday_tab,
                             image=photo_button_physics5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_physics_tab)
    button_physics5.pack(pady=0)
elif sheet['J5'].value == 'Астрономія':
    button_astronomy_image5 = button_astronomy_image5.resize(new_size_button_thursday_image)

    photo_button_astronomy5 = ImageTk.PhotoImage(button_astronomy_image5)

    button_astronomy5 = Button(friday_tab,
                               image=photo_button_astronomy5,
                               borderwidth=0,
                               activebackground="#fee698",
                               activeforeground="#fee698",
                               relief="flat",
                               highlightthickness=0,
                               command=show_astronomy_tab)
    button_astronomy5.pack(pady=0)
elif sheet['J5'].value == 'Біологія':
    button_biology_image5 = button_biology_image5.resize(new_size_button_thursday_image)

    photo_button_biology5 = ImageTk.PhotoImage(button_biology_image5)

    button_biology5 = Button(friday_tab,
                             image=photo_button_biology5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_biology_tab)
    button_biology5.pack(pady=0)
elif sheet['J5'].value == 'ФКЗ':
    button_PKZ_image5 = button_PKZ_image5.resize(new_size_button_thursday_image)

    photo_button_PKZ5 = ImageTk.PhotoImage(button_PKZ_image5)

    button_PKZ5 = Button(friday_tab,
                         image=photo_button_PKZ5,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_pt_tab)
    button_PKZ5.pack(pady=0)
elif sheet['J5'].value == 'IT':
    button_IT_image5 = button_IT_image5.resize(new_size_button_thursday_image)

    photo_button_IT5 = ImageTk.PhotoImage(button_IT_image5)

    button_IT5 = Button(friday_tab,
                        image=photo_button_IT5,
                        borderwidth=0,
                        activebackground="#fee698",
                        activeforeground="#fee698",
                        relief="flat",
                        highlightthickness=0,
                        command=show_it_tab)
    button_IT5.pack(pady=0)
elif sheet['J5'].value == 'Програмування':
    button_program_image5 = button_program_image5.resize(new_size_button_thursday_image)

    photo_button_program5 = ImageTk.PhotoImage(button_program_image5)

    button_program5 = Button(friday_tab,
                             image=photo_button_program5,
                             borderwidth=0,
                             activebackground="#fee698",
                             activeforeground="#fee698",
                             relief="flat",
                             highlightthickness=0,
                             command=show_programming_tab)
    button_program5.pack(pady=0)
elif sheet['J5'].value == 'АМО':
    button_AMO_image5 = button_AMO_image5.resize(new_size_button_thursday_image)

    photo_button_AMO5 = ImageTk.PhotoImage(button_AMO_image5)

    button_AMO5 = Button(friday_tab,
                         image=photo_button_AMO5,
                         borderwidth=0,
                         activebackground="#fee698",
                         activeforeground="#fee698",
                         relief="flat",
                         highlightthickness=0,
                         command=show_amo_tab)
    button_AMO5.pack(pady=0)
elif sheet['J5'].value == 'БЖД':
    button_BZHD_image5 = button_BZHD_image5.resize(new_size_button_thursday_image)

    photo_button_BZHD5 = ImageTk.PhotoImage(button_BZHD_image5)

    button_BZHD5 = Button(friday_tab,
                          image=photo_button_BZHD5,
                          borderwidth=0,
                          activebackground="#fee698",
                          activeforeground="#fee698",
                          relief="flat",
                          highlightthickness=0,
                          command=show_ls_tab)
    button_BZHD5.pack(pady=0)
# КОНЕЦ 4 ПАРЫ ПЯТНИЦЫ



root.after(10000, check_class)
root.mainloop()
workbook.close()
