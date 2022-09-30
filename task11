from telegram.ext import Updater, CommandHandler, CallbackContext, MessageHandler, Filters
from telegram import Update

smiles = False


def start(update=Update, context=CallbackContext):
    update.message.reply_text("Hi, " + update.effective_user.first_name)


def echo(update=Update, context=CallbackContext):
    update.message.reply_text(update.message.text)


def smile(update=Update, context=CallbackContext):
    global smiles
    smiles = True
    update.message.reply_text("-_-")


def calc(update=Update, context=CallbackContext):
    global smiles

    if context.args:
        text = ' '.join(context.args)

        if smiles == False:
            result = eval(text)
        else:
            result = "-_-"

        update.message.reply_text(result)


def main():
    updater = Updater("*:*-*")
    dispatcher = updater.dispatcher
    dispatcher.add_handler(CommandHandler("start", start))
    dispatcher.add_handler(CommandHandler("smile", smile))
    dispatcher.add_handler(CommandHandler("calc", calc))
    dispatcher.add_handler(MessageHandler(Filters.text & ~Filters.command, echo))
    updater.start_polling()
    updater.idle()


main()
