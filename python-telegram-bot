import os
from telegram import Update, ReplyKeyboardMarkup
from telegram.ext import (
    ApplicationBuilder,
    CommandHandler,
    MessageHandler,
    ContextTypes,
    filters,
)

TOKEN = os.getenv("BOT_TOKEN")

keyboard = [
    ["🔥 Lazer gravirovka", "💰 Narxlar"],
    ["🪵 Materiallar", "📏 Lazer turlari"],
    ["📱 Instagram", "▶️ YouTube"],
    ["📢 Telegram kanal", "ℹ️ Yordam"],
]

MENU = ReplyKeyboardMarkup(
    keyboard,
    resize_keyboard=True
)


async def start(update: Update, context: ContextTypes.DEFAULT_TYPE):
    text = (
        "👋 Assalomu alaykum!\n\n"
        "🤖 Men Lazer AI botman.\n"
        "Lazer gravirovkasi haqida ma'lumot, "
        "materiallar va taxminiy narxlar bo'yicha yordam beraman.\n\n"
        "👇 Kerakli bo'limni tanlang:"
    )

    await update.message.reply_text(
        text,
        reply_markup=MENU
    )


async def help_command(update: Update, context: ContextTypes.DEFAULT_TYPE):
    await update.message.reply_text(
        "ℹ️ Yordam\n\n"
        "/start — asosiy menyu\n"
        "/help — yordam\n\n"
        "Savolingizni yozishingiz yoki menyudagi "
        "tugmalardan foydalanishingiz mumkin."
    )


async def message_handler(update: Update, context: ContextTypes.DEFAULT_TYPE):
    message = update.message.text

    if message == "🔥 Lazer gravirovka":
        text = (
            "🔥 LAZER GRAVIROVKA\n\n"
            "Lazer gravirovka — yog'och, fanera, "
            "akril, teri va boshqa materiallarga "
            "rasm yoki yozuv tushirish usuli.\n\n"
            "📌 Qo'llanilishi:\n"
            "• Ism va yozuvlar\n"
            "• Logotiplar\n"
            "• Sovg'a buyumlari\n"
            "• Reklama mahsulotlari\n"
            "• Yog'och va fanera bezaklari"
        )

    elif message == "💰 Narxlar":
        text = (
            "💰 LAZER GRAVIROVKA NARXLARI\n\n"
            "Narx ishning hajmi, materiali va "
            "dizayniga qarab o'zgaradi.\n\n"
            "📌 Narxga ta'sir qiluvchi omillar:\n"
            "• Material turi\n"
            "• O'lchami\n"
            "• Gravirovka maydoni\n"
            "• Dizayn murakkabligi\n"
            "• Buyurtma soni\n\n"
            "📩 Aniq narx uchun material va "
            "o'lchamni yozib yuboring."
        )

    elif message == "🪵 Materiallar":
        text = (
            "🪵 LAZER UCHUN MATERIALlar\n\n"
            "Ko'p ishlatiladigan materiallar:\n"
            "• 🪵 Yog'och\n"
            "• 📦 Fanera\n"
            "• 🟦 Akril\n"
            "• 👜 Teri\n"
            "• 📄 Karton\n"
            "• 🪧 Ayrim plastik turlari\n\n"
            "⚠️ Har bir material lazer uchun mos "
            "bo'lavermaydi."
        )

    elif message == "📏 Lazer turlari":
        text = (
            "📏 LAZER TURLARI\n\n"
            "🔴 CO₂ lazer — yog'och, akril, fanera "
            "va boshqa materiallar uchun.\n\n"
            "🔵 Diode lazer — ayrim yog'och, fanera "
            "va gravirovka ishlarida ishlatiladi.\n\n"
            "⚙️ Fiber lazer — asosan metall "
            "markirovka va gravirovka uchun."
        )

    elif message == "📱 Instagram":
        text = (
            "📱 Instagram\n\n"
            "Instagram sahifangiz manzilini shu yerga "
            "keyin qo'shishingiz mumkin."
        )

    elif message == "▶️ YouTube":
        text = (
            "▶️ YouTube\n\n"
            "Lazer gravirovkasi bo'yicha videolar "
            "va darslar uchun YouTube kanal havolasini "
            "shu yerga qo'shishingiz mumkin."
        )

    elif message == "📢 Telegram kanal":
        text = (
            "📢 Telegram kanal\n\n"
            "Lazer gravirovkasi bo'yicha yangiliklar, "
            "narxlar va foydali ma'lumotlarni shu "
            "kanalda berishingiz mumkin."
        )

    elif message == "ℹ️ Yordam":
        text = (
            "ℹ️ YORDAM\n\n"
            "Masalan, quyidagicha savol yozing:\n\n"
            "👉 Yog'ochga gravirovka qancha turadi?\n"
            "👉 Qaysi lazer metallga ishlaydi?\n"
            "👉 Faneraga rasm tushirish mumkinmi?\n"
            "👉 Lazer stanogi narxi qancha?"
        )

    else:
        text = (
            "🤖 Savolingizni tushundim.\n\n"
            "Lazer gravirovkasi, materiallar yoki "
            "narxlar haqida savol bering.\n\n"
            "👇 Yoki menyudan bo'lim tanlang."
        )

    await update.message.reply_text(
        text,
        reply_markup=MENU
    )


def main():
    if not TOKEN:
        raise ValueError(
            "BOT_TOKEN topilmadi. Bot tokenini environment variable "
            "orqali BOT_TOKEN nomi bilan kiriting."
        )

    app = ApplicationBuilder().token(TOKEN).build()

    app.add_handler(CommandHandler("start", start))
    app.add_handler(CommandHandler("help", help_command))
    app.add_handler(
        MessageHandler(filters.TEXT & ~filters.COMMAND, message_handler)
    )

    print("🤖 Lazer AI bot ishga tushdi...")
    app.run_polling()


if __name__ == "__main__":
    main()
