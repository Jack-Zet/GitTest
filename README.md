import telebot
import webbrowser

bot = telebot.TeleBot('6818647852:AAEtLa_J5YtdZyyJrz3IJKj4M6ZbrqGDGZA')

# Открываем сайт через webbrowser
@bot.message_handler(commands=['site','website'])
def site(message):
	webbrowser.open('https://angrad.pythonanywhere.com/about_alliance/')


# Стандартный хук как стартовая команда
@bot.message_handler(commands = ['start'])
def main(message):
	bot.send_message(message.chat.id, f'Привет,{message.from_user.first_name}')


# Хук с использованием тега parse_mode=html
@bot.message_handler(commands=['help'])
def main(message):
	bot.send_message(message.chat.id, '<b>Help</b> <em><u>information</u></em>', parse_mode='html')


# Обработка всех сообщений
@bot.message_handler()
def info(message):
	if message.text.lower() == 'привет':
		bot.send_message(message.chat.id,f"Привет, {message.from_user.first_name}")
	elif message.text.lower() == 'id':
		bot.reply_to(message,f'ID: {message.from_user.id}')

bot.polling(none_stop=True) # Команда предотращающая завершение кода,делая его бесконечным.
