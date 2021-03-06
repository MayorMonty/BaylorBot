# BaylorBot

This Reddit bot requests data for Baylor University's sports games, and updates the sidebar of [/r/baylorsports](https://reddit.com/r/baylorsports)

Made for [/u/adeafblindman](https://reddit.com/u/adeafblindman)

## Installation on Debain & Raspberry Pi

*Note*: Make sure that you have Node.js and NPM installed before proceeding. [Here's](http://thisdavej.com/beginners-guide-to-installing-node-js-on-a-raspberry-pi/) a great guide.

First, clone from GitHub **into /home/pi/BaylorBot**

    git clone https://github.com/MayorMonty/BaylorBot /home/pi/BaylorBot

Fill in `credentials.json`. It should look like this:

    {
      "reddit": {
        "clientId": "<your client id>",
        "clientSecret": "<your client secret>",
        "username": "<your username>",
        "password": "<your password>",
        "userAgent": "nodejs:com.mayormonty.baylorbot:v0.0.0"
      }
    }

Then, install and register as a service:

    sudo npm i -g pm2
    sudo npm i

Now, register the bot with [PM2](https://pm2.io), a process manager for node applcations:

    sudo pm2 startup
    pm2 start main.js --name 'BaylorBot'
    pm2 save

Done. The service will restart on OS startup, and will update the sidebar every 30 seconds. You can check the status of the bot using the command:

    pm2 monit

Pay attention to the application entitled BaylorBot
