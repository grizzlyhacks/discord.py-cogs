# setting up your bot

this is a step-by-step guide for setting up a discord bot using this repo.

## install python

python comes pre-installed on mac and most linux distributions, but the
pre-installed version is often somewhat dated. it's recommended to ensure you're
running an up-to-date version of python

### windows | mac

go to [python.org/downloads](https://www.python.org/downloads/) and download
the version for your system. use the default settings save for one exception:
on windows, be sure to check the *Add Python to PATH* option during
installation  
![image](https://user-images.githubusercontent.com/621412/142649557-c534cc2a-96d6-497c-9cbc-54e9ff1ae5c6.png)


### *nix

```shell
# debian / ubuntu / linux mint
sudo apt install python3

# fedora
sudo dnf install python3

# redhat / rhel / centos
sudo yum install python
```

## install pycord

[`pycord`](https://github.com/Pycord-Development/pycord) is the most recent,
actively updated python discord library. install it with pip:

```shell
pip install py-cord
```

or for voice channel support:

```shell
pip install py-cord[voice]
```

## download the code

on the main repo page, click the `Code` button and select "Download ZIP". once
the download completes, unzip the archive

![image](https://user-images.githubusercontent.com/621412/142582301-08e7a1aa-8000-4465-a7e4-029939b4d0e0.png)

## alternative: replit

replit.com is essentially a cloud based IDE. through it, you can copy the
project, edit it, and run the code all from your webbrowser. if you'd prefer to
run the bot on your own computer, feel free to skip this section. to use replit,
follow these steps:

1. follow the below instructions to get a bot token
2. create a replit account
3. visit the [bot's replit](https://replit.com/@shitchell/discord-bot)
4. click the `Fork repl` button  
![image](https://user-images.githubusercontent.com/621412/142602403-34bcabe6-4b66-42b4-ab65-091d5cfbe7bb.png)
5. on the left side of your new replit, go to the *Secrets* tab  
![image](https://user-images.githubusercontent.com/621412/142602690-86ef8a6b-b82e-48db-8906-7c9e8eb22349.png)
6. add a new "secret" with the name `BOT_TOKEN` and paste your bot token for the value  
![image](https://user-images.githubusercontent.com/621412/142602892-62da47aa-77f5-4eaa-ab75-1cb8a0788e55.png)
7. click `Run`!

### caveat

--------------------------------------------------------------------------------

replit.com doesn't allow you to run programs long-term without a paid
subscription. if you want to leave the bot running, you'll have to set up python
and run it on your personal computer

## get a bot token

### 1. go to the discord developer portal

visit the discord developer portal:  
[https://discordapp.com/developers/applications/](discordapp.com/devs/apps)

this portal shows you all of your apps and bots. if you've already created a
bot, click it in the list and skip to [step 4](#4-retrieve-your-token). if you
don't have one yet, click the `New Application` button

![image](https://user-images.githubusercontent.com/621412/142582807-f9dd09fe-9a5f-4e55-ac62-a6c082c4b5dd.png)

### 2. name your bot

after clicking the `New Application` button, you'll be asked to create a name
for your bot. once you've entered the name, click `Create`

![image](https://user-images.githubusercontent.com/621412/142583193-0b0d3e90-fb6f-443f-b101-37f6a4e8832a.png)

### 3. icon and description

all that's left is to create an icon and description! the recommended size is
1024x1024, but you can use lower resolution images and still achieve good
quality results

iconfinder has a huge collection of *free* awesome icons:  
[iconfinder.com/free_icons](https://www.iconfinder.com/free_icons)

once you've added an icon and added a description, click `Save Changes`!

![image](https://user-images.githubusercontent.com/621412/142584424-5e84e1dc-8831-487a-99d9-3dd716f8fd50.png)

the remaining options can be ignored unless you intend to post your bot on
a website like [discordbotlist.com](https://discordbotlist.com/) for the
general public to use

### 4. retrieve your token

next we need to get a token that we can use in our code to login as our bot.
NEVER share this token with anyone. it's not only against the discord terms;
they can use it to log in to your bot's account and destroy the world.

head over to the **Bot** section in the left menu bar and then click the
`Add Bot` button

![image](https://user-images.githubusercontent.com/621412/142585310-567f9fe0-ea60-4a0e-bf33-1968e3b069ed.png)

if it was successful, you'll see the message *"A wild bot has appeared!"*

![image](https://user-images.githubusercontent.com/621412/142585491-e63018a9-8b5f-46ed-a34a-4c666a4c74c8.png)

you can now grab your bot token! under the **Build-A-Bot** section, click the
link that reads *"Click to Reveal Token"*

![image](https://user-images.githubusercontent.com/621412/142585916-fca3b764-63de-4e22-9aac-38fc1a58b807.png)

## add the token to your code

copy the token and then head to your code. in the root folder, you should see
a file named *settings-example.py*. rename this file to *settings.py* and open
it in the editor of your choice. you should see a line that reads:

```py
#token = 'YOUR BOT TOKEN HERE'
```

uncomment the line by deleting the `#` in the beginning and then replace the
text with your bot token, e.g.:

```py
token = 'abc123def456'
```

the *settings.py* file is listed in the gitignore, so you can safely add your
token to this file and share your code with others via github 🙂

#### token environment variable

optionally, you can also set your bot token using the `BOT_TOKEN` *environment
variable*. many IDE's will allow you to set specific environment variables when
running code, replit allows you to set environment variables in the *Secrets*
tab in the left hand menu bar, and on mac/linux you can set an environment
variable when running a program like so:

```shell
BOT_TOKEN="abc123def456" python bot.py
```

this is the preferred method over using the *settings.py* file if you're running
the bot on replit.com or if you're using a shared computer where you don't feel
comfortable saving the token in a file

## set your bot prefix

in the *settings.py*, you should see the line:

```py
prefix = ['BOT PREFIX']
```

edit the line and add your bot prefix in the strings:

```py
prefix = ['!']
```

optionally, you can add multiple prefixes if you want multiple options with how
you run commands:

```py
prefix = ['!', ':', '.']
```

## run the bot!

you're ready to run it! at this point, you can open up a command prompt (*cmd*
on windows, *terminal* on mac) and run:

```shell
cd path/to/bot/folder/
python3 bot.py
```

if you don't know what to put for `path/to/bot/folder/`, you can just drag and
drop the bot folder from your desktop onto the terminal after typing `cd `
(with a space after `cd`)

## add some commands

and be sure to add some commands 🙂 this bot implementation uses *cogs*, a
method of writing commands that involves separating them into separate files in
a specific folder. in this project, that's the `cogs/` folder. each *cog*
follows the following structure:

```py
import discord
from discord.ext import commands

# You can change 'Fun' to anything.
class Fun(commands.Cog):
    def __init__(self, client):
        self.client = client

    @commands.command()
    async def hello(self, ctx):
        """make the bot say hello"""
        await ctx.send("hello")

def setup(client):
    client.add_cog(Fun(client))
```
`Fun` can be anything you choose but should describe the category of commands
included in the file. for each command itself, the function name (in this case
`def hello()` defines the command name. the text inside of the`"""triple
quotes"""` is the syntax python uses for documenting functions & classes, and
it's used to set the help text for your bot's commands.

--------------------------------------------------------------------------------
there are several example cogs provided, and there are a plethora of cogs you
can find on google and github! search `discord.py bot cogs` to find more
examples for inspiration and guidance with your own bot commands. happy coding!

### resources

`py-cord` python discord library:  
https://docs.pycord.dev/en/master/api.html  
https://github.com/Pycord-Development/pycord

more example cogs:  
[advanced help command: gist/1c7060a14a9d94e7929aa2ef14c41bc2](https://gist.github.com/nonchris/1c7060a14a9d94e7929aa2ef14c41bc2)  
[miscellaneous cogs: gist/d78c061a4798ae81be9825468fe146be](https://gist.github.com/EvieePy/d78c061a4798ae81be9825468fe146be)
