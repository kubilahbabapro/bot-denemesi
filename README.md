# bot-denemesi
import discord
from discord.ext import commands
intents = discord.Intents.default()  
intents.message_content = True
intents = discord.Intents.default()  
intents.message_content = True
# Botun komut öneki
bot = commands.Bot(command_prefix='.', intents=intents)

# Botun başlatılma durumu
@bot.event
async def on_ready():
    print(f'Bot {bot.user.name} olarak giriş yaptı!')
    await bot.change_presence(activity=discord.Game(name="Atık Ayrımı Yardımcısı"))
@bot.command()
async def hello(ctx):
    await ctx.send(f'Merhaba {bot.user}! Ben bir botum!')
# Atık kategorilerine göre rehberlik eden bir komut
@bot.command()
async def atik(ctx, *, atik_turu):
    atik_turu = atik_turu.lower()

    if "plastik" in atik_turu:
        await ctx.send(
            "eee bunu bende bilmiyom şaka bea  geri dönüşüm kutusuna atabilirsiniz. Ancak plastik poşetler, ince plastikler ve plastik oyuncaklar genellikle geri dönüştürülemez. "
            "Lütfen geri dönüştürülebilir sembolüne dikkat edin!"
        )
    elif "cam" in atik_turu:
        await ctx.send(
            "Cam şişeleri ve kavanozları geri dönüşüm kutusuna atabilirsiniz. Fakat kırık camlar, ampuller ve aynalar geri dönüştürülemez."
        )
    elif "kağıt" in atik_turu:
        await ctx.send(
            "Kağıt ve karton atıklarını geri dönüşüm kutusuna atabilirsiniz. Islanmış veya yağlanmış kağıtlar geri dönüştürülemez."
        )
    elif "organik" in atik_turu or "yemek" in atik_turu:
        await ctx.send(
            "Organik atıkları kompost yapabilirsiniz. Sebze, meyve kabukları, kahve telvesi gibi atıklar komposta uygundur. "
            "Ancak et ve süt ürünlerini komposta eklememelisiniz."
        )
    elif "metal" in atik_turu:
        await ctx.send(
            "Alüminyum kutular, teneke kutular gibi metal atıkları geri dönüşüm kutusuna atabilirsiniz. "
            "Ancak boya kutuları ve kimyasal içeren metaller geri dönüştürülemez."
        )
    else:
        await ctx.send("Bu atık türü için henüz bir bilgi yok. Lütfen yaygın atık türlerini kullanın: plastik, cam, kağıt, organik, metal.")
