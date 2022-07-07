###NOTICE: In April of 2022 the code in this repo will be deprecated and we will no longer offer support for it!! For updated info on the future of the Ritabot-Project be sure to follow the (ANNOUNCEMENTS channel in our Discord Server)[https://discord.com/invite/v62WNej]

<p align="center"><a href="https://ritabot.gg/"><img src="https://media3.giphy.com/media/YO4a0qsdVX3Gq3darL/giphy.gif" data-canonical-src="https://media3.giphy.com/media/YO4a0qsdVX3Gq3darL/giphy.gif" width="175" height="175" href="https://ritabot.gg/"></a></p>
<h1 align="center">Rita</h1>
<p align="center">Breaking the language barrier for free.</p>
<p align="center">Join the Language Revolution, use RITA today.</p>
<p align="center">
</p>

------




<p align="center">An open-source, free Discord Translator Bot built using <strong>google-translate-api</strong> and <strong>Discord.js</strong>.</p>

![Rita Translator Diagram](https://storage.pixteller.com/designs/designs-images/2021-02-03/05/poster-simple-quote-1-601a17471d0b6.png)

## :book: Table of Contents

*Please note some of these links direct you towards our website*
<details>
<summary></strong>Click to expand contents</strong></summary>

* [Setting up Rita](#new-bot)
* [Setting up Rita locally](#local)
* [How to Update your Bot](#update)
* [Coming Soon](#soon)
  * [Heroku Database Support](https://ritabot.gg/dbsupport/)
  * [Setup on a Raspberry Pi](https://ritabot.gg/raspberry-pi/)
  * [Whats New with Rita](https://ritabot.gg/whats-new/)
  * [Features](https://ritabot.gg/features)
  * [Usage](https://ritabot.gg/usage/)
  * [How to Update your Database Manually](https://ritabot.gg/dbsupport/)
  * [C-3PO to RITA Bot Migration](https://ritabot.gg/migration/)
  * [Webhook Log Setup](https://ritabot.gg/troubleshooting)
  * [Common Issues](https://ritabot.gg/common-issues)
  * [Command Wiki](https://ritabot.gg/wiki)
    * [Supporters](#supporters)
    * [Credits & License](#credits-&-license)
    * [Design Team](#design-team)
    * [About Us](#history)
</details>

------

## <a name="new-bot"></a>:computer: Setting up Rita Translator on Heroku

<p align="center">
<img src="https://github-images.s3.amazonaws.com/help/bootcamp/Bootcamp-Fork.png">
</p><br/><br/>

#### 1. Fork this repository.
* If you don't yet have a Github account, [create one](https://github.com/join)! It's free and easy.
* Click [here](https://github.com/RitaBot-Project/RitaBot/fork) or use the button in the upper righthand side of this page to fork the repository so that it will be associated with your Github account.


* Please ***star our project*** if you like it using the top-right Star icon. Every star helps us! 
<p align="center">
<img src="https://ritabot.gg/assets/images/star.png" href="https://github.com/RitaBot-Project/RitaBot/stargazers">
</p><br/><br/>

#### 2. Create a new [Discord Application](https://discordapp.com/developers/applications) in the Discord Developer Portal
* Give app a friendly name and click the **Create App** button
  * I like the name **C-3PO**, but feel free to pick something different if you fear George Lucas's wrath. Maybe **C-4PO**
* Take note of the app **CLIENT ID**, you will need it later
* Scroll down to the **Bot** section
* Click the **Create a Bot User** button
* Click the **Yes, do it!** button
* Copy the bot's **TOKEN**, you will need it later

#### 3. Create a [Heroku account](https://id.heroku.com/signup/login) (It's free!)
* Create a new app. It's name must be unique and composed of all lowercase letters and dashes. Something like `yourname-discordbot` is fine
* Under **Deployment Method** select Github. Connect to your Github account and search for this repository by name.
* Scroll down to the manual deploy section, and select the **Master** branch. Click deploy branch, and wait for the successfully deployed message.

* Go to the **Resources** tab and look for the addons section. Search 'Postgres', and add a 'Hobby Dev - Free' version of Heroku Postgres. This will be automatically attached as your bot's database.
* Go to the **Settings** tab. Click to reveal Config Variables, then add then add the following:
  * **KEY:** =  DISCORD_TOKEN
    * **Value:** = Your discord bot's token that you copied earlier.
  * **KEY:** =  NODE_MODULES_CACHE
     * **Value:** = false
    * *This is to ensure that when the bot updates it does not use any old Dependencies that Heroku has stored and gets fresh ones from the package.json file*
* Go to the **Overview** tab and click configure dynos. Turn off the default `web npm start` dyno and turn on the `worker node src/bot.js` dyno. Your bot will now be up and running!


###### **Make sure that you have added the `Heroku Postgres` Addon in the Resources Tab of Heroku or else your bot shall not run!**

* *If you have any issues running your bot join our [Discord Server](https://discord.gg/invite/mgNR64R)*
#### 4. Invite your bot to your server and configure it!
* Replace the CLIENTID string in the following URL with your own apps client id from Step 2: 
    *  **https://discordapp.com/oauth2/authorize?&client_id=CLIENTID&scope=bot&permissions=8**
    
* Visit the resulting URL and add your bot to any server where you have admin privileges.
  * Once added, your bot should show in your server, **now go back to [Heroku](https://heroku.com/) and go to the "Deploy" section, scroll down to "Manual Deploy" and deploy the *master* branch. That's it your are good to go!**
    * Your bot is now setup and ready for any translation you have for it to do. Use the commands `!tr help` and `!tr help modules` to learn more about the commands Rita has!
  

* **Important Note**
 * The `!tr embed` command is changeable whenever you like. It simply decides wether you would like translations to be sent as Webhooks (more user-like, profile picture) or embed (bot sends message with anembed message contintaining user profile picture.)

------

## <a name="update"></a>:floppy_disk: How to Update to Stable Branch on Heroku
#### 1. Checklist
* You must have a bot already running on your server, if not then refer to [Setting up a New Bot](#new-bot)

#### 2. Make a Pull Request to your Fork from this Repo
* Complete a Pull Request from the master Branch of RitaBot-Project/Rita to your master branch. 
  * Detailed instructions with example can be found **[here](https://www.sitepoint.com/quick-tip-sync-your-fork-with-the-original-without-the-cli/)**


#### 3. Deploy Updated Fork in Heroku
* Log in to your Heroku account.
* Select the bot you made in Step 3 of [Setting up a New Bot](#new-bot)
* Under **Deployment Method** make sure you have Github selected, ensure **Connect to GitHub** has the correct repository selected, Scroll down to the "Manual deploY" section, and select the **master** branch. Click deploy branch, and wait for the successfully deployed message.

#### 4. Updating Database

* Once the bot has been deployed with the successfully updated fork you are all done.
------

## <a name="local"></a>:desktop_computer: Running Rita Locally

*The bot can also be run locally on a device. Please note that for the bot to continue running 24/7, the process of `node src/bot.js` should always remain online and thus your PC/hosting device must remain online too*

1. Install [node.js](https://nodejs.org/en/). It comes with [npm](https://www.npmjs.com/get-npm) which you will need.
2. Simply download this repository as a .zip, or clone it if you have git: **```git clone https://github.com/RitaBot-Project/RitaBot```**
3. In the RitaBot folder, rename the existing **.env.example** file and name it **.env**. Edit the Value of **DISCORD_TOKEN**. (If you don't have a bot account, see [Step 2 of "Setting Up a New Bot"](#new-bot))
4. Open a terminal/console in the RitaBot folder and download dependencies using **`npm install`**
5. Start the bot with **`npm start`**
6. Invite your bot to your server and configure it!

* If you don't already have a invite for your bot, you can replace the **CLIENTID** string in the following URL with your own apps client id: https://discordapp.com/oauth2/authorize?&client_id=**CLIENTID**&scope=bot&permissions=8 . Visit the resulting URL and add your bot to any server where you have admin privileges. Once added, your bot should show up as online.

* Your bot is now setup and ready for any translation you have for it to do. Use the commands `!tr help` and `!tr help modules` to learn more about the commands Rita has!

#### Alternative Database Settings
Any Database that runs with [SQL Sequelize](https://sequelize.org/master/) can be used. If you want to use an alternative DB Location other than in the default directory then you can manually set this. Example: The connection to a sqlite database with the name *`database.db`* stored at the same level of this README file would be *`./database.db`*.

Within the **.env** file from the above step, set the **DATABASE_URL** to be the path to the database file, if there is no DB file in the selected path then RITA will create the DB file upon startup.
* Example -  `DATABASE_URL` = `C:\Admin\Rita_Development\test.db`

## <a name="database"></a>Heroku Database Support
Sometimes you need to edit the Database manually, This is not something you should be playing around with unless you really know what you are doing.

#### 1. Checklist
1. Know that you are doing, if you don't then **don't** touch the DB. Simple.
2. Download and Install Postgres Admin 4, Located [Here](https://www.pgadmin.org/download/) or [Here](https://www.postgresql.org/ftp/pgadmin/pgadmin4/). *This guide will be for Windows, but it shouldn't be much different for any other OS.*
3. Locate your credentials for you Heroku Database, Log in to **Heroku** > Select your **App** > Click **Resources** > Click **Heroku Postgres** > Click **Settings** > Click **View Credentials** (*Note: Heroku rotates credentials periodically and updates applications where this database is attached.*)

#### 2. Connect
For a fresh install of pgAdmin, the dashboard likely contains only one server. This is your local server, Ignore this.
1. Right click server(s) > create > server …
2. Fill out the following:
  * **Name:** This is solely for you. Name it whatever you want, I chose ‘Heroku-Run — On’

*Under the connection tab:*
  * **Hostname/Address:** This is the host credential you located in Step 3. It should look like \*\*-\*\*-\*\*...amazonaws.com
  * **Port:** Keep the port at 5432, unless your credentials list otherwise
  * **Maintenance database** This is the database name in the credentials
  * **Username:**  This is the user field in the credentials
  * **Password:** The password field located in Step 3. I highly advise checking save password so that you don’t have to copypasta this every time you want to connect.
  * In the **SSL Tab**, mark SSL mode as require

At this point, if we were to hit ‘save’ (please don’t), something very strange would happen. You’d see hundreds if not thousands of databases appear in pgAdmin. This has to do with how Heroku configures their servers. You’ll still only have access to your specific database, not those of others. In order to avoid parsing so many databases, we have to white list only those databases we care about.

1. Go to the **Advanced** tab and under db restriction copy the database name (it’s the same value as the **Maintenance Database** field filled earlier).
2. Click Save/Connect and you are done. Edit away.
------
### <a name="soon"></a>:bulb: Coming Soon!

01. Error Message Support Section.
02. `!tr tasks #TargetChannel` Implementation.
03. Allow Bot Translation (V1.3.0)
04. Discord slash commands introduction

------


### <a name="credits-&-license"></a>:star_struck: Credits & License

This project was originally released by Aziz under the MIT license. He chose to take the project private/commercial at version 0.4.2 Beta. Bobby Johnson forked the project and renamed it Louie after his dog. AlooAkbar forked Louie and added the necessary modifications for simple and free deployment of the bot using Heroku. RitaBot-Project Picked up the fork and as part of a team fixed over 200 errors and brought it in to the modern age, All would like to thank Aziz for his hard work and making these early versions OSS so that others may learn and build on his hard work to share with the community.

------

### <a name="design-team"></a>:sunglasses: Design Team
* Zycore / [ZyC0R3](https://github.com/ZyC0R3)
* Artanis / [ArtanisTheOne](https://github.com/ArtanisTheOne)
* Jshep89 - AKA Lord Lazarus / [Jshep89](https://github.com/JShep89)
* Z3US / [cyberlooper](https://github.com/cyberlooper)
* Maddious / [MadIndex](https://github.com/MadIndex)
* defqon.1 / [wdaniel1985](https://github.com/wdaniel1985)

***Released under MIT license.***
