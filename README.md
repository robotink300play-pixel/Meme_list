import os
import discord
from discord.ext import commands

intents = discord.Intents.default()
intents.message_content = True  # actívalo también en el Developer Portal

bot = commands.Bot(command_prefix="!", intents=intents)

@bot.event
async def on_ready():
    print(f"Bot conectado como {bot.user}")

@bot.command()
async def saludo(ctx):
    await ctx.send(f"¡Hola, {ctx.author.display_name}! 👋")

bot.run(os.getenv("DISCORD_TOKEN"))
