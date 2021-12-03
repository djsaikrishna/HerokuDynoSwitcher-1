# Heroku Dyno Switcher
## What is this?
A little python project to make your heroku app alive forever without being concerned about dyno hours.

## Mechanism
The main idea is to use two accs (yeah, you need 2 of them to make this work) with two same apps and shift the dyno every 1st and 15th of a month.
Every 10 mins, the script will check if today is either 1st or 15th of a month. If it's true, then it'll switch the dyno based on the heroku app name, heroku API key, and the process type vars you have entered.
This will make your app restart once more in those days though besides the usual 24h restart in heroku free tier. And of course, you need to deploy them first 

## How?
I am dumb. I'm not good at python, but I'll try to make this done as a challenge. See `script.py` for the progress. Ah btw, this script will need to run continuously to work, so the platform to use is Railway (since it's free and the limits are pretty good actually, if you're hosting a legal thing, that is)
```
THIS FREAKING THING IS STILL IN WIP AND I HAVEN'T EVEN TESTED THIS FULLY, SO IT MAY NOT WORK PROPERLY.
SO PLEASE CHECK MY CODE, MY PRO BRO!
```

- Make sure you have deployed two same things to two apps in two different heroku accounts. Only enable dyno in one of the app, not both.
- Fork this repo.
- Make a blank app in Railway.
- Add these vars:

<b>REQUIRED</b> <br>
`FIRST_PROCESSTYPE` is the process type of your app, you can use `web`, `worker` or something else. Check it in the Resources tab of your heroku app.<br>
`FIRST_A_APPNAME` is the app name of your primary app.<br>
`FIRST_A_APIKEY` is the API key of the heroku account your primary app is in. Check it in your heroku settings, in the last of the page.<br>
`FIRST_B_APPNAME` is the app name of your secondary app.<br>
`FIRST_B_APIKEY` is the API key of the heroku account your secondary app is in. Check it in your heroku settings, in the last of the page.<br><br>
<b>OPTIONAL</b> <br>
The script supports up to 3 pair of apps simultaneously. You may add these vars if you need it.<br>
`SECOND_PROCESSTYPE`, `SECOND_A_APPNAME`, `SECOND_A_APIKEY`, `SECOND_B_APPNAME`, `SECOND_B_APIKEY`<br>
`THIRD_PROCESSTYPE`, `THIRD_A_APPNAME`, `THIRD_A_APIKEY`, `THIRD_B_APPNAME`, `THIRD_B_APIKEY`<br>
- Deploy this repo to that blank app in Railway via GitHub.
