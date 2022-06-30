import telebot;
import time
import schedule
import json
import csv
from tempfile import NamedTemporaryFile
import shutil
import datetime
from pyowm.owm import OWM
import pandas as pd
import logging
from aiogram.types import ReplyKeyboardRemove, \
    ReplyKeyboardMarkup, KeyboardButton, \
    InlineKeyboardMarkup, InlineKeyboardButton
from telebot import types
from aiogram.dispatcher.filters import Text
from matplotlib import pyplot as plt
from matplotlib import style
from dateutil import parser as dt_parser
import numpy
import tokens
bot = telebot.TeleBot(tokens.bot);
@bot.message_handler(commands=['start'])
def start_message(message):
	keyboard = telebot.types.ReplyKeyboardMarkup(True)
	keyboard.row('Прислать мне отчет', 'Ввести данные')
	keyboard.row('Сделать таблицу пустой', 'Инструкция')
	fname=message.from_user.id
	idname = str(fname) + '.csv'
	newtable(idname)
	bot.send_message(message.chat.id, 'Ура!', reply_markup=keyboard)
@bot.message_handler(commands=['menu'])
def menu_new(message):
	keyboard = telebot.types.ReplyKeyboardMarkup(True)
	keyboard.row('Прислать мне отчет', 'Ввести данные')
	keyboard.row('Сделать таблицу пустой', 'Инструкция')
	bot.send_message(message.chat.id, 'Надеюсь появилось)', reply_markup=keyboard)
@bot.message_handler(content_types=["text"])
def any_msg(message):
	fname=message.from_user.id
	global idname
	idname = str(fname) + '.csv'
	idname_photo = str(fname) + '.png'
	global b
	if message.text == 'Привет':
		bot.send_message(message.from_user.id, "Привет, " + str(message.from_user.first_name))
	elif message.text == 'Спасибо':
		bot.send_message(message.from_user.id, "Пожалуйста))))")
	elif message.text == '/help':
		bot.send_message(message.from_user.id, 'Этот бот создан для того, чтобы отслеживать твое состояние в течении дня, месяца, года.😊')
		bot.send_message(message.from_user.id,'Пункт 1.❗️\nЕсли ты в основном меню выберешь кнопку "Прислать мне отчет", то бот отправит тебе таблицу в формате .csv, которую ты заполнял за время пользования ботом и графики зависимости твоего самочувствия от температуры и погоды.🚀')
		bot.send_message(message.from_user.id,'Пункт 2.❗️\nЕсли ты в основном меню выберешь кнопку "Ввести данные", то ты сможешь отправить боту данные о своем самочувствии.😜')
		bot.send_message(message.from_user.id,'Пункт 3.❗️\nЕсли ты в основном меню выберешь кнопку "Сделать таблицу пустой", то все данные из таблицы, которые ты вносил до этого, пропадут.😀')
		bot.send_message(message.from_user.id,'Пункт 4.❗️\nЕсли ты в основном меню выберешь пункт "Инструкция", то тебе придут эти же сообщения.😂')
		bot.send_message(message.from_user.id,'Пункт 5.❗️\nЕсли хочешь начать с нуля все, то выбери /start')
		bot.send_message(message.from_user.id,'Пункт 6.❗️\nЕсли вдруг у вас пропало основное меню нажмите /menu' )
	elif message.text == 'Инструкция':
		bot.send_message(message.from_user.id, 'Этот бот создан для того, чтобы отслеживать твое состояние в течении дня, месяца, года.😊')
		bot.send_message(message.from_user.id,'Пункт 1.❗️\nЕсли ты в основном меню выберешь кнопку "Прислать мне отчет", то бот отправит тебе таблицу в формате .csv, которую ты заполнял за время пользования ботом и графики зависимости твоего самочувствия от температуры и погоды.🚀')
		bot.send_message(message.from_user.id,'Пункт 2.❗️\nЕсли ты в основном меню выберешь кнопку "Ввести данные", то ты сможешь отправить боту данные о своем самочувствии.😜')
		bot.send_message(message.from_user.id,'Пункт 3.❗️\nЕсли ты в основном меню выберешь кнопку "Сделать таблицу пустой", то все данные из таблицы, которые ты вносил до этого, пропадут.😀')
		bot.send_message(message.from_user.id,'Пункт 4.❗️\nЕсли ты в основном меню выберешь пункт "Инструкция", то тебе придут эти же сообщения.😂')
		bot.send_message(message.from_user.id,'Пункт 5.❗️\nЕсли хочешь начать с нуля все, то выбери /start')
		bot.send_message(message.from_user.id,'Пункт 6.❗️\nЕсли вдруг у вас пропало основное меню нажмите /menu' )
	elif message.text == 'Ввести данные': 
		keyboard = create_number(message)
		bot.send_message(message.from_user.id, "Если у Вас возникают какие-то вопросы, отправьте боту команду /help",reply_markup=keyboard)
	elif message.text == 'Сделать таблицу пустой':
		newtable(idname)
		bot.send_message(message.from_user.id, "Таблица стала пустой!")
	elif message.text == 'Прислать мне отчет':
		bot.send_message(message.from_user.id,'Таблица в формате .csv:')
		f = open("C:\\telegrambot\\Fails\\" + idname, "rb")
		bot.send_document(message.chat.id, f)
		schedule(idname, idname_photo)
		bot.send_message(message.from_user.id,'Зависимость самочувствия от температуры:')
		bot.send_photo(message.from_user.id, photo=open('C:\\telegrambot\\Pictures_temp\\' + idname_photo, 'rb'))
		bot.send_message(message.from_user.id,'Зависимость самочувствия от атмосферного давления:')
		bot.send_photo(message.from_user.id, photo=open('C:\\telegrambot\\Pictures_Atm.davl\\' + idname_photo, 'rb'))
	else:
		bot.send_message(message.from_user.id, 'Что-то не понятное, если есть вопросы, выбери "Инструкция" в основном меню или выбери /help')
@bot.callback_query_handler(func=lambda call: True)
def i_can(call):
	if call.message:
		global b
		fname=call.from_user.id
		idname = str(fname) + '.csv'
		if call.data == "test7":
			b = "Golova"
			create_batton(call)
		if call.data == "test8":
			b = "Bodrost"
			create_batton(call)
		if call.data == "test9":
			b = "Prodyktivnost"
			create_batton(call)
		if call.data == "test1":
			a = 1
			resh(a, b, idname)
			bot.edit_message_text(chat_id=call.message.chat.id, message_id=call.message.message_id, text="Спасибо, принято!")
		elif call.data == "test2":
			a = 2
			resh(a, b, idname)
			bot.edit_message_text(chat_id=call.message.chat.id, message_id=call.message.message_id, text="Спасибо, принято!")
		elif call.data == "test3":
			a = 3
			resh(a, b, idname)
			bot.edit_message_text(chat_id=call.message.chat.id, message_id=call.message.message_id, text="Спасибо, принято!")
		elif call.data == "test4":
			a = 4
			resh(a, b, idname)
			bot.edit_message_text(chat_id=call.message.chat.id, message_id=call.message.message_id, text="Спасибо, принято!")
		elif call.data == "test5":
			a = 5
			resh(a, b, idname)
			bot.edit_message_text(chat_id=call.message.chat.id, message_id=call.message.message_id, text="Спасибо, принято!")
def test(i, name):
	if str(df.loc[i, name]) != str("nan"):
		return True
	else:
		return False
def resh(a, b, idname):
	global df
	try:
		df = pd.read_csv('C:\\telegrambot\\Fails\\' + idname)
	except:
		logging.error('файл не обнаружен')
	if len(df) == 0:
		i = 0
		p = datetime.date.today()
	else:
		i = len(df)-1
		p = df.loc[i, "Data"]#откуда он находит это значение, если изначально там пусто
	if str(p) != str(datetime.date.today()):
		p = datetime.date.today()
		i = i + 1
	df.loc[i, b] = float(a)
	df.loc[i, "Data"] = datetime.date.today()
	df.loc[i, "Time"] = datetime.datetime.today().strftime("%H:%M:%S")
	df.loc[i, "City"] = 'Saint Petersburg,rus'
	df.loc[i, "Atm.davl"] = pressure()
	df.loc[i, "Temperatyra"] = float(weather())
	print('Именно значения:', df.loc[i, "Golova"], df.loc[i, "Prodyktivnost"], df.loc[i, "Bodrost"])
	print('Именно типы:', type(df.loc[i, "Golova"]), type(df.loc[i, "Prodyktivnost"]), type(df.loc[i, "Bodrost"]))
	if test(i, "Golova") and not test(i, "Prodyktivnost") and  not test(i, "Bodrost"):
		df.loc[i, "Samochyvstvie"] = df.loc[i, "Golova"]
	if not test(i, "Golova") and test(i, "Prodyktivnost") and  not test(i, "Bodrost"):
		df.loc[i, "Samochyvstvie"] = df.loc[i, "Prodyktivnost"]
	if not test(i, "Golova") and not test(i, "Prodyktivnost") and  test(i, "Bodrost"):
		df.loc[i, "Samochyvstvie"] = df.loc[i, "Bodrost"]
	if test(i, "Golova") and test(i, "Prodyktivnost") and  not test(i, "Bodrost"):
		df.loc[i, "Samochyvstvie"] = round(((df.loc[i, "Golova"]) + (df.loc[i, "Prodyktivnost"])/2),1)
	if test(i, "Golova") and not test(i, "Prodyktivnost") and  test(i, "Bodrost"):
		df.loc[i, "Samochyvstvie"] = round(((df.loc[i, "Golova"] + df.loc[i, "Bodrost"])/2),1)
	if not test(i, "Golova") and test(i, "Prodyktivnost") and  test(i, "Bodrost"):
		df.loc[i, "Samochyvstvie"] = round(((df.loc[i, "Prodyktivnost"] + df.loc[i, "Bodrost"])/2),1)
	if test(i, "Golova") and test(i, "Prodyktivnost") and  test(i, "Bodrost"):
		df.loc[i, "Samochyvstvie"] = round((((df.loc[i, "Prodyktivnost"]) + (df.loc[i, "Golova"]) + (df.loc[i, "Bodrost"]))/3),1)
	df.to_csv('C:\\telegrambot\\Fails\\' + idname, index=False)
def weather():
	owm = OWM(tokens.weather)
	mgr = owm.weather_manager()
	weather = mgr.weather_at_place('Saint Petersburg,rus').weather
	temp_dict_kelvin = weather.temperature()   
	w = ((temp_dict_kelvin['temp_min']+temp_dict_kelvin['temp_max'])/2)-273.15
	return int(w)
def pressure():
	owm = OWM(tokens.weather)
	mgr = owm.weather_manager()
	pressure_dict = mgr.weather_at_place('Saint Petersburg,rus').weather.pressure  # 'weather', not 'observation'
	return int(pressure_dict['press']*100/133.3-13)
def newtable(idname):
	with open("C:\\telegrambot\\Fails\\" + idname,"w",newline="") as file_writer:
		fields=['Data', 'Time', 'City', 'Samochyvstvie','Golova','Bodrost','Prodyktivnost','Atm.davl','Temperatyra']
		writer=csv.DictWriter(file_writer,fieldnames=fields)
		writer.writeheader()
def create_batton(message):
	keyboard = types.InlineKeyboardMarkup()
	keyboard.add(types.InlineKeyboardButton(text="Очень плохо", callback_data="test1"))
	keyboard.add(types.InlineKeyboardButton(text="Плохо", callback_data="test2"))
	keyboard.add(types.InlineKeyboardButton(text="Нормально", callback_data="test3"))
	keyboard.add(types.InlineKeyboardButton(text="Хорошо", callback_data="test4"))
	keyboard.add(types.InlineKeyboardButton(text="Отлично", callback_data="test5"))
	bot.send_message(message.from_user.id, "Выбирайте", reply_markup=keyboard)
def create_number(message):
	keyboard = types.InlineKeyboardMarkup()
	keyboard.add(types.InlineKeyboardButton(text="Состояние головы 🧠", callback_data="test7"))
	keyboard.add(types.InlineKeyboardButton(text="Состояние бодрости🦵", callback_data="test8"))
	keyboard.add(types.InlineKeyboardButton(text="Состояние продуктивности🖊️", callback_data="test9"))
	return keyboard
def schedule(idname, idname_photo):
	data = pd.read_csv('C:\\telegrambot\\Fails\\' + idname,sep=r'\s*,\s*', header=0, encoding='utf8', engine='python')
	data = data.sort_values('Temperatyra',ascending=True)
	data.plot(kind='scatter', x = 'Temperatyra', y = 'Samochyvstvie')
	plt.xlabel('Температура')
	plt.ylabel('Самочувствие')
	plt.title('Зависимость самочувствия от температуры')
	plt.savefig('C:\\telegrambot\\Pictures_temp\\' + idname_photo)
	data = data.sort_values('Atm.davl',ascending=True)
	data.plot(kind='scatter', x = 'Atm.davl', y = 'Samochyvstvie')
	plt.xlabel('Атмосферное давление')
	plt.ylabel('Самочувствие')
	plt.title('Зависимость самочувствия от атмосферного давления')
	plt.savefig('C:\\telegrambot\\Pictures_Atm.davl\\' + idname_photo)
bot.polling(none_stop = True, interval = 0)
