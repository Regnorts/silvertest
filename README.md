import telebot
from telebot import types
bot = telebot.TeleBot("5594734576:AAEae3VdLF-jwxoOlxctXeIExegfJVNZfvA")


@bot.message_handler(commands=['start'])
def start(message):
    mess = f'Здарова, <b>{message.from_user.first_name} </b> -чувачилоо'
    bot.send_message(message.chat.id, mess, parse_mode='html')


#@bot.message_handler()
#def get_user_text(message):
    userMessage = message.text
    userMessage = userMessage.lower()
    if "как" in userMessage:
        bot.send_message(message.chat.id, "збс")
    elif userMessage == "ништяг" or userMessage == "каеф" or userMessage == "норм":
        bot.send_message(message.chat.id, "Сам знаю чувак")
    elif userMessage == 'красава':
        bot.send_message(message.chat.id, 'че по кайфу')
    elif userMessage == "photo":
        photo = open('1.jpg', 'rb')
        bot.send_photo(message.chat.id, photo)
    elif userMessage == 'отмена' or userMessage == 'стоп' or userMessage == 'stop':
        bot.send_message(message.chat.id, 'Отмена')
        #Как прерывать процесс
    else:
        bot.send_message(message.chat.id, 'Не понял, что ты хотел сказать')

@bot.message_handler(commands=["website"])
def website(message):
    markup = types.InlineKeyboardMarkup()
    markup.add(types.InlineKeyboardButton("Посетить Веб сайт", url="http://oasis-light.ru/" ))
    bot.send_message(message.chat.id, "Перейти на сайт", reply_markup=markup)


bot.polling(none_stop=True)
