# Simple C++ Telegram BotApi Wrapper
This C++ simple header-only library implements wrapper around Telegram bot api. There are methods for sending text, images and files. No handler is implemented, only a method to get last message. The main purpose of this library is providing a simple way of communication from pc program to user's mobile device and not creating an actual telegram bot.

## Usage and requirements
To use this library just place "TelegramBotApi.hpp" in project directory. <br> [Cpr library](https://github.com/libcpr/cpr)  is required to run.

## Example
This lib is really simple and short, this one block of code explains all there is to know.
```cpp
#include <iostream>
#include <string>

#include "TelegramBotApi.hpp"

std::string token = "token";
std::string chatId = "chatid";

int main(){
	tba::TelegramBotApi bot(token);

    // Every send method returns true or false depending if data was sent sucessfully
    // You can set the chatId this way or pass it as argument everytime you send data
	bot.chatId = chatId;  
	bot.sendText("Hello World!");
    bot.sendPhoto("C:/users/user/desktop/img.jpg");

    // Second way of passing chatId
    bot.sendText("Hello World!", "-69420")
    bot.sendFile("C:/users/user/abc.txt", "-69420");

    // Returns last message (std::string) in json format. All data like chat_id or date included
	std::cout << bot.getLastMessage() << std::endl;
}

```