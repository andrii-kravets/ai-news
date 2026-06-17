---
title: "The Best Air Sensor is One You Can Make Yourself"
source: "https://www.youtube.com/watch?v=DqiMmY5ppnE"
author:
  - "[[FEATURE.]]"
published: 2026-06-11
created: 2026-06-17
description: "Every breath you take, every move you make, I'll be tracking you. —————————————————————————————————Discover Easy, Affordable, and Reliable PCB manufacturing with JLCPCB! Register to get $123 New cus"
tags:
  - "clippings"
processed: true
wiki_notes:
  - Knowledge/Fix&Tips/Датчик якості повітря DIY.md
---
![](https://www.youtube.com/watch?v=DqiMmY5ppnE)

Every breath you take, every move you make, I'll be tracking you.  
—————————————————————————————————  
Discover Easy, Affordable, and Reliable PCB manufacturing with JLCPCB! Register to get $123 New customer coupons: https://jlcpcb.com/?from=FEATURE  
  
Using an ESP32 and the Sensirion SEN66 to make the Ultimate Smart Home Air Quality Sensor. Even better, ESPHome means you can get going without any programming knowledge - you can even use the device standalone, no Home Assistant required.  
  
First I show you how to set the absolute easiest way to get the sensor to make readings, then I show the process of adding all the frills like using an ePaper/eInk display, connecting it to your smart home, and setting up an awesome dashboard so you have a beautiful UI to interact with this device.  
  
Support the channel so I can keep making videos!  
Patreon: https://www.patreon.com/FEATURE418  
  
Corrections:  
None yet!  
  
3D Files:  
Makerworld : https://makerworld.com/en/models/2918992-smart-desktop-air-quality-monitor-esp32-sen66  
Printables : https://www.printables.com/model/1751003-smart-desktop-air-quality-monitor-esp32-sen66  
  
All project design files can be found on github:  
https://github.com/FeatureNAB/air-sensor  
  
Links for stuff I mentioned:  
Home Assistant: https://www.home-assistant.io/  
ESPHome: https://esphome.io/  
Lapoka Embedded Display Graphics Editor: https://lopaka.app/  
Beautiful UI Card for Air Quality: https://github.com/KadenThomp36/air-quality-card  
HACS Installation tutorial: https://www.youtube.com/watch?v=TL2eqsjhmTE  
  
Affiliate links for stuff I use: (you get a 2% discount and help support the channel)  
2.13" e-ink Monochrome Display : https://www.seeedstudio.com/2-13-Monochrome-ePaper-Display-with-122x250-Pixels-p-5778.html?sensecap\_affiliate=dzMqXsY&referring\_service=link  
XIAO ESP32-C6 (3-pack - $3.45 per unit) : https://www.seeedstudio.com/Seeed-StudioXIAO-ESP32C6-3PCS-p-5918.html?sensecap\_affiliate=dzMqXsY&referring\_service=link  
XIAO ESP32-C6 (1-pack - $5.20 per unit) : https://www.seeedstudio.com/Seeed-Studio-XIAO-ESP32C6-p-5884.html?sensecap\_affiliate=dzMqXsY&referring\_service=link  
XIAO nRF52840 : https://www.seeedstudio.com/Seeed-XIAO-BLE-nRF52840-p-5201.html?sensecap\_affiliate=dzMqXsY&referring\_service=link  
  
Other Hardware (not affiliate links)  
Sensirion SEN66 (Sensor used in the video): https://mou.sr/44c63Ji  
  
Seeed studio store coupons (https://www.seeedstudio.com/):  
FANFS7ZV - Discounts on XIAO boards  
R7GOC1C1 - Site-wide discount coupon  
  
—————————————————————————————————  
  
"PM and a human hair" by Environmental Protection Agency is Public Domain.  
Source: https://www.epa.gov/pm-pollution/particulate-matter-pm-basics  
File:PM and a human hair.jpg  
License: Public Domain  
  
"GEOS Aerosols" by NASA's Scientific Visualization Studio is Public Domain.  
Source: https://svs.gsfc.nasa.gov/5572  
File:GEOS Aerosols (SVS5572 - AnnotationsLabel 9600x3240 30p).webm  
License: Public Domain  
  
"Pet rock" by Owner of Pet Rock Net is licensed under CC-BY 3.0.  
Source: https://commons.wikimedia.org/wiki/File:Pet\_rock.jpg  
File:Pet rock.jpg  
License: https://creativecommons.org/licenses/by/3.0/deed.en  
Image briefly cropped from original.

## Transcript

**0:00** · This is a little desktop air quality sensor I created to give me a better understanding of the air inside my living space. It's got a screen on the front telling me at a glance how my air quality is doing. And it connects wirelessly to my smart home where I can see in much greater detail all the data it streams back. It also clearly tells me what I need to do if I need to do something. Bad air, open a window. Good air, don't.

**0:23** · I packed a bunch more features into this little thing and I had a blast putting it together. So, if you want to know how it works and how to build one for yourself, stick around. So, this whole project basically came about because I discovered this awesome new release from Sensoron. It's a tiny all-in-one sensor that measures nine different air quality metrics. And if you're anything like me when I started this project, you're probably kind of surprised there's even that many things to measure. So, let's break down what all this stuff is and why it matters. First is particulate matter. This measures the microscopic floaty dirt in the air.

**0:53** · The different numbers correspond to different particle sizes with the smaller ones generally being worse because they can get deeper into the lungs and into the bloodstream.

**1:02** · It's stuff like dust, smoke from wildfires, exhaust fumes, brake and tire emissions from cars. Next is volatile organic compounds. These are types of gases that are emitted from things like paints, hairsprays, cleaning products, furniture. Relevant for us, 3D printing and soldering. They're kind of everywhere. Even humans themselves emit some amount of these. A significant portion of them though are harmful to health and it's generally advised to ventilate if they get too high. Carbon dioxide is created when we breathe.

**1:30** · In fact, it's created when anything breathes, including pets and spouses.

**1:38** · It's not lethal, but too much of it can make a room feel stuffy, and levels higher again can cause poor sleep, headaches, and difficulty concentrating.

**1:47** · It's also used to indicate the risk of catching infections like COVID or the flu. Then we've got nitrogen oxides. If you have a gas stove or if you live near a busy road, this might spike. I don't have either, so it's been pretty flatline for me. And then lastly, you've also got temperature and humidity.

**2:03** · Now, all this functionality comes at a cost. Like literally, compared to most of the sensors I've used to date, which are usually in the 5 to€10 range, this one is a steep ask. I paid €60 plus shipping. But the thing is, if you actually tried to buy all these sensors separately that this thing uses, you'd immediately be paying more than you would if you just used this one. Plus, it's super compact and having just one sensor means the hardware side of this project is less jumper spaghetti and more seti and foretti. So, it's pricey, but you're getting a decent amount of highquality kit.

**2:33** · Sensor is an established brand, and amazingly, this thing has a rated lifetime of over 10 years, which I don't think I've ever seen on a sensor like this. So, subscribe now and get notified of my 10ear review in 2036. Okay, enough theory. How do we get it to work hardware-wise? This is just the sensor.

**2:51** · To do something with it, we need to attach it to something that can read and interpret the data. I'm going to start with this ESP32 from Seed because they're cheap and I have some of them lying around, but you can use pretty much any microcontroller or single board computer as long as you can access its GPIO pins. Thankfully, this sensor communicates over I squared C, so connecting to it requires just four wires. 3 volts, ground, the serial data pin, and the serial clock pin. The sensor uses a kind of a weird connector.

**3:19** · I made my own cable using parts I had on hand, but you can get pre-made ones online. The connector on the sensor has six pins, but you only actually need to connect four of them to get this thing to work. That's because the pins on both ends of the connector are 3 volts and ground and they're connected internally.

**3:37** · So you just need to connect to one of them each. Now you might be asking why did sensor on use a six pin connector on a device that only needs four pins.

**3:49** · Anyway, once everything is connected, the easiest way to get this sensor up and running is to use ESP Home. This is an awesome open- source project whose entire purpose is to make life easier for schmucks like us who just want to use ESP32s to make cheap or highly customized smart home stuff without the pain of writing a bunch of code.

**4:07** · Instead, you write small config files almost like a shopping list and ESP takes care of the rest. Here, let me show you what I mean. Here's a super minimal but functional setup. We pick a device name, write down our ESP32 model, in my case the C6, and add that we want a web server. This tells the ESP32 to serve us a web page with our readings when we connect to it later via Wi-Fi.

**4:31** · Then we tell it which sensor we have, the SEN66, and which properties we want that sensor to measure. So, temperature, humidity, particulate matter, etc., and which physical pins the sensor is connected to. And that's pretty much it for the config. All that's left to do now is to give this to ESP home and have it compile into a binary that we can run on our board. Option number one is best for power users. You install the CLI tool directly on your computer. You do all of your development there.

**5:00** · This gives you the most flexibility and it lets you do really cool things that you couldn't do otherwise. We'll see some more of this later. This is what I've been doing and it's awesome for rapid prototyping. Option number two is to install ESP Home Builder within Home Assistant. I think most people watching either know of or already use Home Assistant. If that's you, installing ESP Home Builder is as easy as installing the add-on. And from there, you can write YAML and it will compile and install directly to your microcontroller.

**5:28** · I covered this in detail in my first video, so you could check that out for more. And then the bonus option for those of you who just want to dip your toes in and don't have anything fancy like Home Assistant yet.

**5:41** · I went ahead and pre-ompiled some binaries for you guys and uploaded them to GitHub. They're specific to each ESP32 board type. So download the one that matches your board. Then you can flash it directly to your board from Chrome by using this website. Once it's flashed, the board will boot up automatically and spin up an access point that you connect to with your phone or your laptop. Connect using the Wi-Fi password you set. Go to your web browser and type the device name.local.

**6:09** · I named the device air. So I go to air.local.

**6:13** · From here you can view the readings in real time. Everything here is served from the ESP32 directly. So it's quite basic but it's entirely functional. And considering the technical limitations of the ESP32, this is very impressive.

**6:28** · Now, if you want a similarly minimal setup, but you want it to show up in Home Assistant, all you have to do is add your Wi-Fi credentials and the API component, which is how Home Assistant interacts with the sensor. Install the ESP Home integration in Home Assistant if you haven't already, and it should autodiscover the device once it connects to your network. And honestly, if you just want to get readings from this sensor, you can absolutely call it here and use it like this. This works just fine as it is.

**6:53** · But seeing as we've come this far, it might be nice to add a few quality of life improvements so we can take this device from a neat demo to something that would fit quite nicely in a real living space. Having the information on your phone is cool, but it would be even better if you could just check with a glance, so you don't have to go rooting around within your phone. And it would be great to have clear, actionable insights without having to understand all the details of each measurement like PM10 densities and CO2 parts per million.

**7:20** · Most of the time, I just want to know if I should open the window or not. So, we can meet these design goals by adding a screen to display what the air is doing and to tell us if we need to do something. And we'll also connect it to Home Assistant to get access to things like fancy dashboards and home automations.

**7:39** · Screen-wise, ESP Home has a massive catalog of compatible displays to choose from, but I'm most interested in trying e- in displays for this project. They're often praised for their low power consumption, making them a perfect fit for e-readers like the Kindle. But what I'm most interested in is their almost polite impression in a space. They're not self-lit. Instead, they rely on ambient light acting more like the page of a book than the screen of an electronic device.

**8:04** · And for something that I intend to be always on and in my eyline, that's exactly the kind of low-key but functional presence I'm going for. To actually use an e-aper screen, however, we can't just plug it in to the ESP32.

**8:18** · We'll need a special driver board, and this comes down to how the technology works. Each pixel in an e- screen is actually a little bubble of oil with charged pigment particles inside. When you apply a voltage across the pixel, the particles float in one direction or another depending on their charge, making the surface appear black or white. In this way, by applying a voltage, we can force black particles to the top, making a black pixel, or we can force white particles to the top, making a white pixel. This explains why these screens use so little power.

**8:51** · It takes energy to apply a voltage and move the colored particles around. But once they're in place, you can remove the voltage and the particles will stay where they are because the oil is so viscous and the particles are so light.

**9:05** · So, it only consumes power when the image is changing.

**9:08** · The reason then that we need a special board is because physically shuttling those particles around requires a relatively high voltage, much higher than our microcontroller natively supplies. To move around the particles in an e- in display, we need something more like 15 to 20 volts. This is enough to overcome the resistance of forcing the particles through the viscous oily liquid they're submersed in. And to change the pixel quickly enough for the display to be reasonably real time.

**9:33** · So, to learn a bit more about the tech, I set about designing a circuit board that would let me drive E- in displays of various sizes. I designed this board so that it could be used in other e-ink projects in the future. And I also wanted a wide variety of options for attaching things like buttons and sensors. If you want to make one of these boards for yourself, I'll leave a link in the description with everything you'll need to get started. Start by downloading the FAB folder, then head over to jlcpcb.com.

**10:02** · Upload your Gerber file and JLCPCB will instantly fill in most of the details for you. Start by picking your PCB color. Green is fastest and others add some flare. I went with white this time.

**10:13** · Then select the ENIG finish for gold contacts. If you're going to solder the components to this board yourself, just add a stencil and you're good to go.

**10:20** · Easy, affordable PCBs, as easy as online shopping. You can have your boards produced in as little as 24 hours and boards can be got for as little as $2 with 1 to eight layers. I don't have an SMD soldering setup at home, so PCBA opens a whole world of custom engineering builds that I just couldn't achieve without a company like JLCPCB.

**10:41** · If you're using PCBA like I am, follow the steps mentioned, but enable PCBA.

**10:46** · Optionally, add board cleaning and deping if you want the boards to arrive already separated. Then upload the bill of materials and the component locations from the folder we got from GitHub earlier. If any parts are out of stock, JLCPCB will suggest replacements. Then hit order and sit back while a vast and complex manufacturing process is set into motion to create tiny boards to your exact specifications. You can track their progress in detail directly from your account, including a wide array of electrical and quality checks.

**11:14** · In my first revision of this board, I accidentally used a resistor of the wrong size. JLCPCB employees caught it immediately and helped me correct it.

**11:25** · Between automated testing and human verification, JLCPCB ensure reliability that you can count on. JLC are currently giving away $123 in coupons for new users upon registration. You can find out more with the link in the description.

**11:41** · With the boards delivered, let's take a look at what we've got.

**11:46** · There's a connector at the front for connecting our display, like so.

**11:52** · These components here are all responsible for driving the e-paper display like we mentioned earlier, creating the voltages required to push the little particles around. Besides that, I've added some convenience connections. This one here is for I squared C devices, and it uses the same stemma quick connector that Adafruit and Sparkfund use. At the bottom here are a pair of three pin connectors. These are meant for connecting things like buttons, and they're just power and a single GPIO pin.

**12:19** · In the end, I didn't actually use these in this project because the device just doesn't really need that much interaction. The idea was to press a button to trigger a new reading or to cycle through UI screens, but I figured both of these functions are better done through automations anyway. So, I ultimately left them out for this one, but they're available for other projects and use cases. At the rear, I've got all those same connections we just covered, but designed for headers and jumper cables in case you don't have these convenience cables handy.

**12:50** · Then on top and bottom, every pin on the MCU is broken out as headers, too. So, you can use this board with basically any peripheral you want.

**13:00** · So, it's not just limited to the air quality use case was originally intended for. This is also why I prefer not to integrate an ESP32 chip directly onto the PCB for lots of my projects. Rapid prototyping sometimes requires you to quickly pivot or to handle unexpected situations. Soldering the MCU directly to the board limits that flexibility considerably. So, I like to use a removable MCU instead. Using this header system means I can quickly grab an ESP32 from one board and use it in another.

**13:30** · Or I can swap out the MCU entirely, like from this powerful but high consumption S3 board down to this much more power efficient nrf52.

**13:43** · I also considered adding battery circuitry to this board, but besides increasing cost and complexity, the SEN66 we're using draws a considerable amount of power because it has a little fan that's always on. Because of this, battery power just isn't practical for this one. So, I'll be powering everything off the USB port on the ESP32 board instead.

**14:04** · Lastly, I added a few mounting slots to keep the board mechanically secure in the housing. Using full mounting holes was taking up more space than I wanted to afford, so I added a single half slot and a pair of quarter slots. And in the end, I only needed one of these to keep everything secure. Oh, and I almost forgot. I added two pull-up resistors on the I squared C lines. these tiny specs here, that's them. So, now that we have our driver board and display, we need a way to render something on it.

**14:30** · As before, the software for this thing is all written using ESP Home, which takes the sting out of getting these ESP devices to do what we want. Still, even with the help of ESP Home, the final config for this thing is over 250 lines.

**14:44** · But the beauty of ESP Home is that like before, this just boils down to a kind of shopping list. The basic stuff is all mostly the same as before, but this time we'll add a few bells and whistles. I wanted to connect to Home Assistant, so I'll activate the API. And I'll add an optional encryption key to make that more secure. I also know that the microcontroller itself can get warm, which could mess with our temperature readings. So, I'm going to manually underclock it so it runs cooler. We keep going like this, adding all the bits of functionality we need bit by bit.

**15:15** · And for the most part, ESP Home has you covered. But if you ever find that you need something extra unique, you can actually write your own code and have ESP Home use that too. In my case, there were two parts that I wrote myself. The display layout and the air quality algorithm. For the display layout, you can use these helper functions to move things along relatively quickly. This one draws a line. This one prints text.

**15:42** · Placement of all this is down to the pixel, though. There are two great ways to reduce the time that that process will take. The first is best if you're using ESP Home's CLI tool on Mac, Linux, or WSL. Add host to your config. So, ESP Home compiles for your computer and not a microcontroller. Then set the display platform to SDL with the same dimensions as the screen you're designing for. Now, when you hit compile, a screen preview will pop up showing you where everything is.

**16:13** · Once you're happy with how it looks, just remove the host and SDL changes and upload it to your board as normal, and everything should look the same as your digital preview. But if you're just dipping your toes into all this for the first time, there's a great alternative, Loka. La poka is an open- source project that you can either self-host at home or you can use the free version on their website. Using a graphical interface with the exact dimensions of the screen you're developing for, you can drag around your text, shapes, and images until you have something you like.

**16:44** · Then you copy the code that it gives you at the bottom and you can just paste it into ESP home. So if you're building something custom, I would strongly recommend using one of these two methods. For our project here though, I ultimately went with a two-creen design.

**16:59** · The main screen shows me at a glance how my air is doing. If I need to open a window, the image instantly communicates that. And if I want to know why, I can check the text below it. Then the second screen simply shows everything in a big list so I can get all the details.

**17:14** · Taking things one step further, if you provide this device with outdoor air quality data through Home Assistant, it'll actually compare indoor and outdoor to make even better recommendations. If it notices that particulate matter is high indoors, for example, but outdoor air is worse because of, say, traffic or wildfires, then it'll tell you that and advise you to turn on your air purifier instead of opening a window. So, we basically have our device working. Now, we just need something to hold it all together.

**17:43** · Firstly, I wanted the footprint to be relatively compact. And because this device needs to accurately know the temperature, I need to limit any heating that the MCU might cause to the sensor.

**17:53** · So, the controller should be above the sensor, and I'll add a baffle between the two for good measure. Sensoron also have a step file on their website for a clip that holds the sensor in place. So, I'll use that to speed up the design process quite a bit. And I'll also add some holes at the top so heat can escape. With the technical drawing finalized, I took it to my computer and meticulously copied it into CAD. Just a few short weeks later, I had my box.

**18:18** · With all of that said and done, it was time to fabricate this thing. So, I got out my chisels, a drill, some blocks of wood, and no, I I 3D printed it. I have a printer now. Is 3D printed.

**18:30** · I'm still learning a lot about printing, and there is a lot. But so far, with basically no effort on my part, the prints are easily hitting 90 to 95% of what I'd like from these sensor boxes.

**18:42** · For the remaining 5%, maybe you veteran printers out there can help me here, but things like these edges are not quite right. I originally wanted them to be circular, but then the overhang was too much and I got these nasty artifacts. So instead, I tried a chamfer, but that wasn't quite right either. It'll do for now, but I'd love to hear what people out there do to clean this stuff up a bit. Most of it prints okay, though, and once it's together, it looks honestly pretty cool.

**19:09** · I really dig the honeycomb, which started as a simple temperature control, but then I realized it could be the key to my second problem of keeping the board in place. I went through a bunch of designs trying to figure out a way that I could keep the board secure while attaching or removing the USB cable while everything was together, which ended up being a lot harder than I expected because there wasn't much room to fit tools in the top compartment. I tried a few different toolless designs that all ultimately failed in one way or another.

**19:40** · Then I realized that by just widening the hexagon structure and centering one of them above the mounting hole, I could feed through a screwdriver and use an M3 bolt like a pin. This makes the device rock solid, and inserting a USB cable has genuinely never felt so satisfying.

**20:00** · The screen looks exactly as I'd hoped.

**20:03** · It's clearly readable with ambient lighting, but it blends into the background without being distracting when you're not looking at it. It also doesn't blast your retinas in a dark room like a regular IoT screen might. To attach the front, I used these heat set inserts, which are pretty neat. You basically heat them up with your soldering iron, and they melt down into the housing, so your bolts have something to bite into without stripping out the plastic like it might if you just screwed straight into the housing.

**20:30** · Because the MCU and the E- in board take up some vertical space up top, we're limited with the screen size we can use on the front. But this top compartment has the potential to serve one more killer feature.

**20:44** · This is a 24 ghahertz radar module. It works by sending out pulseed radio waves and listening for the echo that they make in a space. And with some very clever algorithms, it can detect if someone is present or not. The more advanced modules like this one can even track multiple people at once and give you their coordinates and how fast they're moving. Fortunately for us, these devices work through plastics like this PLA housing here.

**21:10** · So, the plan is to use this space at the top and use it to trigger presence-based automations like lighting or switching off the TV if everyone has left the room and forgot to turn it off. I plan to cover presence sensing in a future video, but I figured it was worth mentioning here. Once you've got your air quality monitor connected to Home Assistant, there are practically infinite ways that you can choose to display the data, but I really like this dashboard layout in particular. This is the air quality card from Hacks.

**21:38** · I like this one so much because it supports a huge number of sensors like all the particulates and gases supported by RSN66 and also a host of others like carbon monoxide, radon, and formaldahhide. if you have sensors for these. It takes all those readings and it displays them with color-coded graphs so you can easily tell if something isn't quite right. And a little action card will appear at the top if anything in particular needs your attention. Clear, actionable insights.

**22:08** · In terms of automations, you could set up notifications or voice alerts if your living spaces pass a threshold that you set, or you could trigger a smart plug to turn on an air purifier if the particulate matter gets too high. The beauty of Home Assistant is that you can do basically anything you want with all of its data and devices. So, by all means, get creative. I'd love to hear other suggestions for this device if you have them down below. If you have any questions, let me know in the comments.

**22:33** · No doubt I've forgotten something essential in my last video. I added a whole battery level detection feature and somehow forgot to mention it in the entire video. So, let me know if something's missing.

**22:44** · This thing is by far the most advanced sensor I've added to my smart home with just the sheer number of things it measures in such a tiny package. Sensron really knocked it out of the park with this one and I'm honestly delighted with how it turned out. If you like this kind of content, consider checking out my Patreon. Otherwise, I'll catch you in the next one.