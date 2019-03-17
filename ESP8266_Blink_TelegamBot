
#include "CTBot.h"
CTBot myBot;

String ssid  = "******"; // your SSID or name your wifi
String pass  = "$$$$$$"; // your Password Wifi
String token = "*********:****************************-******"; // your Token Bot 

void setup()
{
  Serial.begin(115200);

  myBot.wifiConnect(ssid, pass);
  myBot.setTelegramToken(token);

  delay(5000);
  
  // Check if all things are ok
  if (myBot.testConnection()) {
    Serial.print("Telegram Bot Ready\n");
    pinMode(LED_BUILTIN, OUTPUT);
    digitalWrite(LED_BUILTIN, HIGH);
  }
  else {
    Serial.print("Connection problem\n");
  }
}

void loop()
{
  TBMessage msg;

  // If there is an incoming message...
  if (myBot.getNewMessage(msg)) {
    if (msg.text == "/start") {
      Serial.print("Client ");
      Serial.print(msg.sender.id);
      Serial.write('\n');
      String welcome = "Welcome to LED Bot Controler,\n";
      welcome += "This is Flash Led Bot example.\n\n";
      welcome += "/ledon : to switch the Led ON\n";
      welcome += "/ledoff : to switch the Led OFF\n";
      welcome += "/ledblink : to switch the Led blink\n";
      myBot.sendMessage(msg.sender.id, welcome);
    }
    else if(msg.text == "/ledon"){
      Serial.print(msg.text);
      digitalWrite(LED_BUILTIN, LOW);
      Serial.write('\n');
      myBot.sendMessage(msg.sender.id, "Lampu Sudah Hidup Juragan");
      }
    else if(msg.text == "/ledoff"){
      Serial.print(msg.text);
      digitalWrite(LED_BUILTIN, HIGH);
      Serial.write('\n');
      myBot.sendMessage(msg.sender.id, "Lampu Sudah MATI Juragan");
      }
    else if(msg.text == "/ledblink"){
      Serial.print(msg.text);
      digitalWrite(LED_BUILTIN, LOW);
      delay(500);
      Serial.write('\n');
      myBot.sendMessage(msg.sender.id, "Lampu Sudah Genit (*_-) Juragan");
      digitalWrite(LED_BUILTIN, HIGH);
      delay(500);
      digitalWrite(LED_BUILTIN, LOW);
      delay(500);
      digitalWrite(LED_BUILTIN, HIGH);
      delay(500);
      digitalWrite(LED_BUILTIN, LOW);
      delay(500);
      digitalWrite(LED_BUILTIN, HIGH);
      }
    else {
      Serial.print(msg.text);
      Serial.write('\n');
      myBot.sendMessage(msg.sender.id, "Saya Tidak Mengerti Tuan (TT)");
    }
  }

  delay(500);
}
