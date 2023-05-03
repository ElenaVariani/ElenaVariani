from telegram.ext import Updater, CommandHandler, MessageHandler, Filters
import requests

def start(update, context):
    context.bot.send_message(chat_id=update.effective_chat.id, text="Ciao, benvenuto nel bot della Taverna di Enry! Come posso aiutarti?")
    
def help(update, context):
    context.bot.send_message(chat_id=update.effective_chat.id, text="Ecco le cose che posso fare:\n\n"
                        "1. Mostrare la disponibilità delle carte in cardmarket: https://www.cardmarket.com/it/YuGiOh/Users/Taverna-di-enry00\n"
                        "2. Aiutare con il tracciamento degli ordini")

def cardmarket(update, context):
    response = requests.get('https://www.cardmarket.com/it/YuGiOh/Users/Taverna-di-enry00')
    if response.status_code == 200:
        context.bot.send_message(chat_id=update.effective_chat.id, text="Ecco il link alla disponibilità delle carte:\n\n"
                            "https://www.cardmarket.com/it/YuGiOh/Users/Taverna-di-enry00")
    else:
        context.bot.send_message(chat_id=update.effective_chat.id, text="Spiacenti, non è possibile accedere alla disponibilità delle carte al momento.")

def track_order(update, context):
    context.bot.send_message(chat_id=update.effective_chat.id, text="Per tracciare il tuo ordine, invia il tuo numero di tracking.")

def unknown(update, context):
    context.bot.send_message(chat_id=update.effective_chat.id, text="Mi dispiace, non ho capito😭")

def main():
    updater = Updater('6026699200:AAF4n1jFOT8vYhPH4Yz66IGc_Pue3l3WjJU', use_context=True)

    dp = updater.dispatcher

    dp.add_handler(CommandHandler('start', start))
    dp.add_handler(CommandHandler('help', help))
    dp.add_handler(CommandHandler('cardmarket', cardmarket))
    dp.add_handler(CommandHandler('track_order', track_order))
    dp.add_handler(MessageHandler(Filters.command, unknown))

    updater.start_polling()
    updater.idle()

if _name_ == '_main_':
    main()
