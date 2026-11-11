
      **Вивід з відео про моніторинг JK BMS за допомогою Meshtastic + Home Assistant:**

      Відео демонструє **DIY-проєкт**, який дозволяє **безперервний моніторинг стану батареї JK BMS** на **кілометровій дистанції без інтернету** за допомогою **мережі Meshtastic** та **Home Assistant**.

      **Основні етапи:**
      1. **ESP32** використовується для **прямого зв’язку з батареєю** без WiFi, за допомогою **I/Q семплів** (перехоплення сигналу з FR частини).
      2. **Створення вузлів Meshtastic** (DIY-ноди) для **міжвузлової комунікації** без інтернету.
      3. **Міст Meshtastic для Home Assistant** для **інтеграції даних** у домашню автоматизацію.
      4. **Налаштування Home Assistant** для відображення показників (напруга, струм, заряд) у вебінтерфейсі.

      **Технологія:**
      - **ESP32** як **SDR-пристрій** для читання I/Q семплів без WiFi.
      - **Meshtastic** для **міжвузлової передачі даних** на великі відстані.
      - **Home Assistant** для **обробки та відображення** даних у реальному часі.

      **Плюси:**
      - **Безперервний моніторинг** навіть без інтернету.
      - **Низька витрата енергії** завдяки Meshtastic.
      - **Гнучка інтеграція** з Home Assistant для автоматизації.

      **Технічні деталі:**
      - Використання **LR30 модулів** та **ESP32** для комунікації.
      - Приклад коду та конфігурацій для **ESPHome** та **Home Assistant** наведено в описі.
      - **DIY-комплектування** для самозбудження вузла.
    
![](https://www.youtube.com/watch?v=4DMolMjcxDE)

💬Канал в Telegram - https://t.me/rio\_diy  
  
🫙Підтримати канал:  
https://www.youtube.com/@rio\_diy/join  
  
📌Інструкція по збиранню вузла ➡ https://github.com/brad112358/easy\_E22  
  
⚙️Комплектючі:  
📌Модель корпусу ➡ https://thingiverse.com/thing:7408482  
📌Дешеві LORA модулі LR30 ➡ https://fas.st/Vu84Gn  
📌EBYTE E22-400M30S ➡ https://fas.st/akLa5  
📌NRF52840 Promicro ➡ https://fas.st/oP4mh  
📌ESP32 ➡ https://fas.st/37LQV  
📌Антена 433МГц Gizont 40cm ➡ https://fas.st/SrSQWS  
📌Антена 433МГц Gizont 20cm ➡ https://fas.st/pwbOB  
  
📺Відео про Meshtastic:  
📌https://www.youtube.com/watch?v=gaQT17Xxedg  
📌https://www.youtube.com/watch?v=TCA2lhjquZ0  
  
💻Приклади коду:  
📌Конфіг ESPHome для JK BMS ➡ https://github.com/syssi/esphome-jk-bms  
📌Мій конфіг ESPHome для JK BMS ➡ https://gist.github.com/ivan-rio/529b878106f65b45f24ec84f94e0c897  
📌Приклад MQTT конфігурації ➡ https://gist.github.com/ivan-rio/47aaf2d42dd4b5f33680e43559d869e1  
  
ℹ️Ресурси про Meshtastic:  
📌Сайт проекту ➡ https://meshtastic.org  
📌WikiMESH ➡ https://wikimesh.in.ua  
📌Meshtastic Ukaraine TG ➡ https://t.me/meshtastic\_ua  
  
  
📩Співпраця ➡️ rioprod.78@gmail.com  
  
  
Зміст:  
00:00 Початок  
00:19 Що таке Meshtastic  
01:45 Мій DIY вузол Meshtastic  
03:50 Meshtastic міст для Home Assistant  
04:29 Перша нода Meshtastic  
04:54 ESP32 для комунікації з батареєю  
05:32 Налаштування першої ноди (відправника)  
05:49 Друга нода Meshtastic (отримувач)  
06:27 Налаштування Home Assistant  
07:03 Результат

## Transcript

### Початок

**0:00** · Welcome to my channel, and today I will share my interesting experience with Meshtastic. I see no point in repeating myself and making a video about what it is and how it works, since channels like Noc Make or Ctrl D—apologies if I got the names wrong—have several informative videos on this topic. I will leave links to them in the description. But in short, it is a project that allows us to assemble a node using a simple microcontroller like an ESP32 and a LoRa radio module.

### Що таке Meshtastic

**0:30** · Meshtastic is a kind of virtual pager that allows you to send text messages without the internet or mobile service.

**0:39** · And all because every node in this network acts not only as a client but also as a repeater. For example, I send a text message from my pager. It flies into the radio spectrum as an encrypted packet. And, for instance, my neighbor with the same pager receives this packet. Each packet has a sort of hop counter, or "hops" in English. And let's say there were five of them.

**1:05** · After my neighbor sends this packet back into the air, there will be four left. And in this way, the packet will travel through the network until it reaches the recipient or the hop counter runs out. And this is the main feature of such a network. You don't need any large stationary repeaters. It is enough for the network to have a sufficiently large number of users. And if we talk about Kyiv, in just one day, my node saw over 100 other nodes.

**1:32** · And sending a message from one end of Kyiv to the other is not a problem at all.

**1:41** · So, this thing is pretty cool. It's a pity I didn't know about it back in 2022. Let me tell you a little about my device. I had known about this story for a long time and wanted to try it out. That's why the components had been sitting on my shelf for several months.

### Мій DIY вузол Meshtastic

**1:56** · I had a board with an NRF52840 microcontroller and an Ebyte E 22-400 M 30 S radio module. This radio module operates on the 433 MHz frequency. And this is important, as the Ukrainian Meshtastic network uses exactly this frequency. You can find this and a lot of other useful and important information on the meshtastic.ua wiki or in the Meshtastic Ukraine Telegram community.

**2:22** · So, I had these components, but I didn't have the inspiration to look for a board to solder them onto or figure out how to connect them.

**2:32** · Suddenly, on GitHub, I found a very interesting guide on how to solder these boards literally to each other and get a quite compact node. And then, well, I had to model a case for it. I also added an OLED display, as Meshtastic supports it, and an encoder, which Meshtastic also supports.

**2:50** · And honestly, in this configuration, I would look for a ready-made board, because connecting an encoder and a display is tricky; it’s an extra four to eight wires, too much soldering, and it’s very hard to fit it all into one case. But if you’re building it without a display and encoder, the guide is top-notch, and I’ll definitely leave a link to it. As for the inside, as you can see, it’s a bit of a mess, but there’s room for a battery.

**3:19** · It might be hard to see, but at the bottom, there’s a sandwich of two boards. Of course, there is a Type-C port at the bottom. That is actually the port for the NRF 52840 board. About the micro. It can charge the battery, so in its assembled form, it is, well, I would say, a fully functional device you can use. And on top, there is a switch to turn off the node if you want. So, I will also leave links to my 3 D-printed case models in the description of this video.

**3:48** · And as soon as I learned about Meshtastic, one idea stuck in my head for a long time.

### Meshtastic міст для Home Assistant

**3:56** · What if I organized a radio bridge between a Home Assistant server and, for example, a battery with a smart BMS located at a summer house or a garage a few kilometers away from your apartment , especially if your apartment is on the 10th floor or higher? Getting ahead of myself, I’ll say that the experiment was a success. And now I will tell you step-by-step what and how you need to configure and connect to make such a radio bridge work for you.

**4:27** · Obviously, we need two Meshtastic nodes . My first one is this node based on the NRF 52840. This is a microcontroller that has very low power consumption. It is efficient and generally the best option for a battery-powered Meshtastic node, meaning for a portable one, but it has a downside: it doesn't have Wi-Fi. But in this case, that’s not a problem because its only task is to transmit information from the BMS into the radio space.

### Перша нода Meshtastic

**4:53** · However, it cannot connect to the BMS directly, so an ESP32-C3 is also used here, programmed using ESPHome. With the familiar configuration, I’ll leave the link in the description of this video with a small addition. I added an interval block there, which forms a single message from the voltage, current, and battery charge level. It separates these three values with colons and sends them via UART, over the yellow and green wires, to the Meshtastic node . The blue wire is the ground.

### ESP32 для комунікації з батареєю

**5:24** · It is also necessary for communication. This node is, in general, an absolutely standard Meshtastic node. The only difference is that in the settings, under components, you need to enable the serial port. And, of course, specify the pins to which you will connect the ESP via UART. And to avoid flooding the public chat, I set up my own separate channel with my own encryption key.

### Налаштування першої ноди (відправника)

**5:48** · I built the other node using the same radio module, but the microcontroller here is an ESP32 because it has Wi-Fi, which is very important for us. Obviously, the main channel in Meshtastic is configured the same way as on the first node. Also, connection to the home Wi-Fi network is configured in Meshtastic, and MQTT is set up in the modules. I already have an MQTT broker installed on my Home Assistant server, so it was enough to enter its IP address, port, login, and password.

### Друга нода Meshtastic (отримувач)

**6:18** · And be sure to turn on the JSON switch, thanks to which we will receive readable information in MQTT in JSON format. Well, as for the Home Assistant server itself, as I already said, you must have an MQTT broker. On the screen, you see an example of what information from a Meshtastic node looks like in MQTT. And from there, using the following MQTT configuration in Home Assistant, we extract the information. Let me remind you that my test message consists of three values separated by a colon.

### Налаштування Home Assistant

**6:48** · Accordingly, we extract them into three sensors. Two additional sensors are also defined, which display the RSSI signal level and the SNR signal-to-noise ratio. And what was the result? The ESP32 receives information from the battery via Bluetooth. It sends a message via UART to the Meshtastic node, which broadcasts this message over the air.

### Результат

**7:16** · Another Meshtastic node, located, for example, 2-3 km away, catches this message and publishes it to MQTT, from where the Home Assistant smart home server pulls this information and updates its sensors. Home Assistant received five entities, one of which is the RSSI signal level, and there is also SNR. And, of course, the battery voltage from the JK BMS, the state of charge, and the current seen by the BMS . Let me remind you that this data was updated every minute.

**7:46** · If you open the detailed history, it is clearly visible , but there is no point on the graph for every minute, because Home Assistant does not create new points if the sensor value is the same. Of course , one minute is a bit frequent. In order not to clutter the radio spectrum , it makes sense to set the data transmission interval to about 5 minutes, or even 10. So, as I said, the experiment was a success. I satisfied my curiosity.

**8:12** · Let me remind you again that I have left links to all the components and all configuration examples in the description for this video. And I will end on that note. If you liked this video, don't forget to rate it. Also, subscribe to my channel so you don't miss future videos. Well, and with you was me, Ivan. See you later.