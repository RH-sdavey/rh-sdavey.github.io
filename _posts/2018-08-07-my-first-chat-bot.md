---
layout: post
title: "My useless chat bot ( and not so useless github webhook )"
author: "Endless"
categories: journal
tags: [python, discord]
image: chatbot.png
---
[1]  [https://github.com/RH-sdavey/octo-pancake/tree/master/Endless/HitchBot](https://github.com/RH-sdavey/octo-pancake/tree/master/Endless/HitchBot)

Today  I learned how to make my very own chatbot [1], that will react only when he is called by name in the chatroom ( other ways to do this are by calling it with a special prefix, such as "." or "@" ) and provides you with an _hilarious_ quote, time permitting I would like to develop this further but the minute I have very little use for it. Cool ~1 hour project though, I would reccomend it. 

[https://www.codementor.io/garethdwyer/building-a-discord-bot-with-python-and-repl-it-miblcwejz](https://www.codementor.io/garethdwyer/building-a-discord-bot-with-python-and-repl-it-miblcwejz)

Essentially the point is to create a Discord account, and using this account create a bot. The bot has no logic and no "brain" to work with, but can be reached and controlled via its 'secret key'. 
The next stage is to create a [repl.it](repl.it) account, Ive just discovered repl, but its a truly awesome piece of work, which allows developers to create projects and code in any language and run the builds and functionality of that code directly from the cloud. 
Heres the code for my "bots brain".

[https://repl.it/@RH_sdavey/mychatbot](https://repl.it/@RH_sdavey/mychatbot)

as you can see, very simple project, easily created in under 1 hour. 

``` python 
# main.py
import discord                                                          # Import modules needed 
import os
import random
from discord.utils import find
from keep_alive import keep_alive
from data.responses import quotes


client = discord.Client()                                               # Instantiate discord client

@client.event
async def on_ready():                                                   # Tell us when its ready
    print("I'm in")
    print(client.user)

@client.event                                                           # Not my code, thanks to zk
async def on_message(message):
                                                                        # check if client is in mentions
       if not find(lambda m: m.name == client.user.name, message.mentions):
        return                                                                 
       if message.author == client.user:                                # check if client is not talking to himself
        return


    response = random.choice(quotes)                                   # Get a randomn quote
    await client.send_message(message.channel, response)               #reply with randomn quote
    # print(f'{message.author}@{message.channel}: {message.content}')


keep_alive()                                                           # keep bot alive
token = os.environ.get("DISCORD_BOT_SECRET")                           
client.run(token)                                                      # run the bot with discord secret env token
```

Pretty straightforward huh?  The bot is pretty useless at the moment and will reply to his name by returning a Christopher Hitchens quote to you, let see it in action, 
To start the bot we click the green button on the top of the repl.it link I posted above, output is shown..
```
Python 3.6.1 (default, Dec 2015, 13:05:11)
[GCC 4.8.2] on linux
   
 * Tip: There are .env files present. Do "pip install python-dotenv" to use them.
 * Serving Flask app "" (lazy loading)
 * Environment: production
   WARNING: Do not use the development server in a production environment.
   Use a production WSGI server instead.
 * Debug mode: off
 * Running on http://0.0.0.0:8080/ (Press CTRL+C to quit)
172.18.0.1 - - [25/Aug/2018 11:30:54] "GET / HTTP/1.1" 200 -
I'm in
My First Bot#4210
```

then in our discord chat room set up with the bot, I call him by name, and he spits some wisdom...

```
sdavey Today at 1:33 PM
@My First Bot

My First BotBOT Today at 1:33 PM
Human decency is not derived from religion. It precedes it.
```

Nothing useful at all, but cool learning experience. 

##### Bonus section

While looking around discord and learning more about all the bots available, I discovered a very cool section about "webhooks" and within a few minutes managed to set up a webhook that posted to the chatroom every time and changes were made to my personal github repos. I know this has been a feature of Slack/ Discord etc for many years, but Ive only just learned it myself, and its very cool. 

```
GitHubBOT Today at 1:03 PM

RH-sdavey
[rh-sdavey.github.io:master] 1 new commit
d048b4a Add files via upload - RH-sdavey
```
with a link to the commit directly. 



