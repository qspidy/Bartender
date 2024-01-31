# Bartender

This is a chatbot for Rocket.Chat that uses OpenAI endpoints to respond to user input. Written in Go, this bot can engage in natural and meaningful conversations with users. With customizable prompts and responses, it can be tailored to fit the needs of a variety of use cases.

## Install

1. Start by creating a user with the bot role in your Rocket.Chat server. Make sure to invite the bot user to the channels where you want it to be active.
2. Collect the user ID for the bot user and set a secure password for it.
3. Download the appropriate version of the bot from the GitHub releases page.
4. Rename the [config.yaml.default](config.yaml.default) file to config.yaml.
5. Open the config.yaml file in a text editor and fill it out with the appropriate values. You will need to provide URLs, API tokens, the bot ID, and the bot password for your Rocket.Chat instance. There are comments in the default configuration file to help you understand what each setting does.
6. If you want to use a different location for the config.yaml file, set the BARTENDER_CONFIG environmental variable to the full path of the file (e.g. BARTENDER_CONFIG=/etc/bartender/config.yaml).
7. Start the bot by running the binary file. If everything is set up correctly, the bot's status in Rocket.Chat should change to "available" and it will be ready to respond to user input in the specified channels. (This might not work on 5.x and 6.x, see known issues)

## Build

```bash
git clone https://github.com/qspidy/Bartender
cd Bartender
go biuld
```

#### Known issues
 - The bot is always shown as offline on RocketChat 5.x and 6.x even when it successfully connects (Rocket.Chat bug?)
 - The bot cannot guarantee that the history will not grow bigger than 4k/8k/32k tokens which will trigger an error. To prevent this, do not send very long messages to the bot and do not set the history size too big.
 - The bot does not retry if an API call fails which can result in more frequent errors when the OpenAI API endpoints are experiencing issues.

#### Thanks

Thanks to [MilesBreslin](https://github.com/MilesBreslin) for the [boilerplate code](https://github.com/MilesBreslin/rocket-bot-go).

#### License

This project is licensed under the MIT License. See the `LICENSE` file for more details.
