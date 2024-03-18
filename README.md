import telebot
import webbrowser
from telebot import types

#токен для бота
bot = telebot.TeleBot('6933413892:AAFAwcODrABYpWnG00_20zuo5QD7Fd91WYI')

#кнопки для рпг
@bot.message_handler(commands=['check'])
def main(message):
    markup = types.InlineKeyboardMarkup()
    btn1 = types.InlineKeyboardButton('Сон', url='https://www.youtube.com')
    btn2 = types.InlineKeyboardButton('Планирование', url='https://www.vk.com')
    btn3 = types.InlineKeyboardButton('Бюджет', url='https://www.whoscored.com')
    markup.row(btn1, btn2, btn3)
    btn4 = types.InlineKeyboardButton('Спорт', url='https://www.whoscored.com')
    btn5 = types.InlineKeyboardButton('Духовные практии', url='https://www.whoscored.com')
    btn6 = types.InlineKeyboardButton('Питание', url='https://www.whoscored.com')
    markup.row(btn4, btn5, btn6)
    btn7 = types.InlineKeyboardButton('Монетизация', url='https://www.whoscored.com')
    btn8 = types.InlineKeyboardButton('Обучение', url='https://www.whoscored.com')
    btn9 = types.InlineKeyboardButton('Домашнее', url='https://www.whoscored.com')
    markup.row(btn7, btn8, btn9)
    btn10 = types.InlineKeyboardButton('Развлечения', url='https://www.whoscored.com')
    btn11 = types.InlineKeyboardButton('Привычки', url='https://www.whoscored.com')
    btn12= types.InlineKeyboardButton('Ужасное', url='https://www.whoscored.com')
    markup.row(btn10, btn11, btn12)
    bot.send_message(message.chat.id, 'Выберите пункт', reply_markup=markup)


#при скидывании фото - открывает кнопки
@bot.message_handler(content_types=['photo'])
def get_photo(message):
    markup = types.InlineKeyboardMarkup()
    btn1 = types.InlineKeyboardButton('Перейти на сайт', url='https://www.youtube.com')
    markup.row(btn1)
    btn2 = types.InlineKeyboardButton('Удалить фото', callback_data='delete')
    btn3 = types.InlineKeyboardButton('Изменить текст', callback_data='edit')
    markup.row(btn2, btn3)
    bot.reply_to(message, 'Какое красивое фото!', reply_markup=markup)

#команда рпг - открывает гиперкноки
@bot.message_handler(commands=['rpg'])
def main(message):
    markup = types.InlineKeyboardMarkup()
    btn1 = types.InlineKeyboardButton('Перейти на ютуб', url='https://www.youtube.com')
    markup.row(btn1)
    btn2 = types.InlineKeyboardButton('Перейти ВК', url='https://www.vk.com' )
    btn3 = types.InlineKeyboardButton('Whoscored', url='https://www.whoscored.com')
    markup.row(btn2, btn3)
    bot.send_message(message.chat.id, 'Да начнется игра!', reply_markup = markup)

#команда старт - текст привет
@bot.message_handler(commands=['start'])
def main(message):
    bot.send_message(message.chat.id, 'Привет')


#команда сайт\вебсайт - открывает ссылку на сайт
@bot.message_handler(commands=['site', 'website'])
def site(message):
    webbrowser.open('https://www.youtube.com')

#бот работает без перерыва
bot.polling(none_stop=True)
