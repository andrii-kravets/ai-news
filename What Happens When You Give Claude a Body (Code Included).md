The page is a YouTube video titled **"What Happens When You Give Claude a Body? (Code Included)"** by **Tech With Anant**. 

- **Content**: The video demonstrates the creation of **Saras 2.0**, an autonomous AI-powered robot using **Anthropic's Claude** for decision-making. It covers hardware assembly, LiDAR integration, and a "zero-coding" software stack enabling the robot to navigate the real world dynamically.
- **Key Topics**: AI robotics, agentic AI, Claude API, LLM agents, Python robotics, LiDAR navigation, and AGI hardware.
- **Views/Date**: 16.4K views, uploaded on **June 19, 2026**.
- **Links**: GitHub code ([Saras AI Robot v2](https://github.com/techwithanant/saras_ai_robot_v2)), Discord community, and a previous video on Saras 1.0.
- **Chapters**: Intro, hardware/software build, live demo, challenges, and future plans (Saras 3.0).
- **Hashtags**: #Saras #Anthropic #Claude #LLM.

The page also includes YouTube's sidebar with recommended videos, Shorts, and gaming content.
![](https://www.youtube.com/watch?v=zrvFgxxDrIU)

Meet #Saras 2.0: Giving an AI a Physical Body  
  
What if your robot didn’t just follow hardcoded commands, but actually thought through what to do next? After a year of rebuilding, I transitioned Saras from a basic script-following machine into an autonomous agentic robot powered by #Anthropic #Claude. This video covers the entire journey—from hardware assembly and LiDAR integration to building a "zero-coding" software brain that allows an #LLM to navigate the real world.  
  
🔗 Important Links  
💻 Get the Code (GitHub): https://github.com/techwithanant/saras\_ai\_robot\_v2  
👾 Join the Community (Discord): https://discord.gg/dXTat44y9y  
⏪ Watch the Original Saras 1.0 Build: https://youtu.be/e-nbSGRFP4Q  
  
⏱️ Video Chapters  
00:00 - Intro to Saras 2.0  
01:16 - The Journey So Far  
01:59 - Building the Body (Hardware & Assembly)  
06:58 - Building the Brain (Claude & Software Stack)  
10:34 - Live Demo (Real-World Test & Recoveries)  
22:29 - The Gaps  
23:28 - Saras 3.0  
  
🤖 About This Build  
In this project, we explore what happens when you give Large Language Models (LLMs), like Claude Code, physical agency. Unlike Saras 1.0, which relied on rigid logic, Saras 2.0 uses an agentic AI approach. We dive deep into the software architecture, showing how Claude evaluates its environment, processes voice commands, and dynamically generates paths.  
  
We also break down real-world robotics challenges, like tuning 2D LiDAR for obstacle detection and the critical trade-offs between latency and reasoning depth. I demonstrate why running a smaller model (like Claude Haiku) makes the robot react much faster, but why complex navigation still requires the sharper, multi-step thinking of larger models (like Claude Sonnet).  
  
Topics covered: AI robotics, DIY autonomous robots, Claude API, Anthropic, LLM agents, Agentic AI, robot building, Python robotics, LiDAR navigation, and artificial general intelligence (AGI) hardware.

## Transcript

### Intro to Saras 2.0

**0:00** · I gave Claude a body.

**0:05** · And I don't mean that metaphorically. I mean I built a real robot, connected its sensors and motors, give it a voice, and took a very different approach with Sorus 2.0. Almost zero coding and a lot more letting the AI figure things out for itself. Hey Sarus, greet my YouTube audience.

**0:22** · Hey, I'm Saras, a robot car running on a Raspberry Pi and apparently a YouTube star. Let's do this.

**0:34** · And this is Sus 2.0.

**0:37** · Hey everyone, welcome back. A lot of you have been asking about the Sora software video, and honestly, that's fair. I didn't want to rush it because over the last year, cloud code and AI in general moved fast enough that I could rethink the whole software approach instead of just iterating on the old one. If you haven't watched the earlier video, I'll leave the link in the description. But this video still covers everything you need from hardware upgrades to the AI site. So, you won't be lost either way.

**1:02** · So, this version is not just an upgrade.

**1:04** · It's a different idea entirely. And the real question I wanted to answer was what happens when you give Claude a robot body, give it the tools to use that body, and then let it decides what to do. And that's what this video is about.

### The Journey So Far

**1:19** · So Sarus didn't started here. Version 1.0 was my first ever hardware project, and I have never built a robot before.

**1:25** · Never worked with motors or sensors or physical components. But I wanted a robot that could respond to commands, navigate its environment, and actually think.

**1:35** · So, I just started building and it worked. SAS 1.0 could move, talk, see, detect obstacles, and respond to voice commands.

**1:44** · But building it taught me exactly how fragile that version was. 1.0 wasn't broken. It just had a ceiling I kept bumping into. And at some point, patching it stopped making sense. And hence, I had to rebuild it from scratch.

**1:56** · That's 2.0. And the rest of this video is how.

### Building the Body (Hardware & Assembly)

**2:02** · So, the first thing I did with 2.0 was to throw out the chases entirely. 1.0 was three separate layers stacked on top of each other. Motors at the bottom, pie in the middle, everything else piled on top. Wires everywhere and open on all sides. It looked exactly like what it was, a prototype. Functional, but barely held together visually. For 2.0, I went back to Fusion 360 and designed from scratch. single enclosed body, thicker walls, heat inserts for the screws, a bumper at the front, and a window panel.

**2:35** · When I finished printing it, I remember thinking it finally looked like a robot and not a science fair project. Sharp edges, clean lines, someone call it a cybert truck, and honestly, I'll take that. The body change wasn't just aesthetic. The enclosed design gave me a proper place to mount everything. The bumper holds the TF sensor and the camera. The front panel holds the screen and upper camera. With a better body came the question of what goes inside it. The motors in 1.0 were the cheapest DC motors I could find. They were fine for moving in a straight line but the moment you ask them to turn against any resistance they give up.

**3:06** · Hence the scotch tape 2.0 uses JGA25 motors with encoders. The encoders matter because they give feedback. That means the motor tells you exactly how far it's turned, which means movement becomes precise instead of approximate. But better motors needed a smarter way to control them. In 1.0, the L298 driver connected directly to the Pi. In 2.0, I added a dual channel edge bridge rated up to 30 ampere, which connects to all four motors.

**3:37** · The SP32 sits between the driver and the Pi running a C++ program, which I flashed via Arduino ID.

**3:47** · The Pi sends highle commands and reads the encoder data back. The Pi stays focused on the AI side. The ESP32 handles the physical side.

**3:57** · Cleaner separation and more reliable overall. Now, the part that genuinely stressed me out was the power. 1.0 ran on two separate systems because I couldn't get a single source to power both the Pi and the motors together cleanly. It worked, but it was messy and I always knew it was a problem waiting to happen.

**4:15** · For 2.0, I decided to build my own battery pack. A 3S2P configuration using 18650 cells, six cells wired in a combination of series and parallel to get the voltage and current I needed with a BMS to protect against overcharge and over drain. I'm generally not very comfortable in soldering anything in my life. I was generally terrified working with the lithium cells for the very first time. These RNA batteries done wrong, they can vent, catch fire, or worse.

**4:44** · I did a lot of research, watched a lot of videos, and eventually found a spot welder, which made the nickel strip connection significantly less scary than trying to solder directly onto cell terminals.

**4:55** · With movement sorted, the next problem was 1.0 had three ultrasonic sensors, one forward, one left, one right. They worked, but the coverage was terrible.

**5:05** · Anything behind surus, anything at an unusual angle, anything low to the ground, it was completely invisible. 2.0 has two dedicated sensors for this. The first is an LT06 lighter, a spinning laser that does a full 360° scan and divides the room into 36 directional buckets. Sus always knows what's around it in every direction, which is updated continuously. This alone changed what navigation could look like. The second is a time offlight sensor mounted on the bumper.

**5:33** · It produces an 8x8 grid of distance reading at floor level aimed slightly downward. Ladder sits high and misses low obstacles, a cable on the floor, a shoe, anything under about 20 cm, which is where the TF sensor comes handy. Together, they cover almost every blind spot. The display is something which I kept from the older version. The 7-in HDMI screen from 1.0 still does exactly what it needs to do. It's surah's face and it works.

**6:01** · The camera are the last piece and they have their own story. I started 2.0 with a single Raspberry Pi camera mounted above the screen.

**6:09** · Angled slightly up to capture the room ahead. And then I noticed something. It kept bumping into things at floor level.

**6:14** · Objects below the camera's field of view, cables, small items, low furniture simply weren't in the frame. The camera was seeing the room but not the floor in front of it. The fix was obvious. Add a second camera pointed at the floor. So I stripped the webcam down to just lens and PCB. No housing, no stand, no casing, just a small round lens on a tiny board. When Sus captures an image now, it could grabs both cameras and stitches them into a single frame. Top half is the horizon level cam and the bottom half is the flow directly in front.

**6:48** · Now I haven't gone step by step through the full assembly here and the hardware alone deserves its own dedicated video.

**6:54** · If you want a full walkthrough every component, every wire, let me know in the comments.

### Building the Brain (Claude & Software Stack)

**7:01** · With the hardware done and every component in place, it was time to figure out what was actually going to run inside this thing. I SSH into the Raspberry Pi and started from scratch.

**7:11** · The first thing I installed was Cloud Code.

**7:14** · If you haven't come across it, Cloud Code is anthropic agentic coding tool.

**7:18** · You run it from the terminal, give it access to your project, and it can read files, write code, run commands, and reason about what to do next. It's not a chatbot you paste questions into. It's an agent that works inside your actual development environment, and that's what's running on the Pi. Before writing any software, I needed to verify the Pi could actually see everything. I fired a set of commands to check each peripheral, the ESP32, the Pi camera, the lighter, the TF sensor, the speaker, and the microphone. All of it showing up, all of it responding. I'll put the exact commands in the description.

**7:48** · This sounds like a small thing, but it saves hours of debugging later when something isn't responding and you have no idea if the problem is in the hardware or the code. Now, the real question, how do you give an AI clean, reliable access to all of this? The answer is MCP, which is model context protocol. It's an open standard from enthropic for exposing tools to an AI model in a structured way. Instead of clot firing raw terminal commands every time it wants a lighter you wrap each of hardware in a proper tool definition.

**8:19** · The AI sees the tool knows what it does calls it with parameters gets a clean result back. It doesn't have to rediscover how to talk to the hardware every single session. And here's the part I didn't expect. I didn't write those servers. I asked cloud code to write them. I described each peripheral what it does, what input it takes, and what it should return. and clot code wrote the tool definitions, the server structure, and the integration code. The AI wrote the code that lets it control its own body. You can see it happening on the screen here.

**8:49** · Claude reading the hardware description, writing the move tool, the lighter reader, the camera capture, catching its own mistake, and fixing them. I found that genuinely strange to watch, but in a good way.

**9:01** · Once the servers were running, Sarus has a body, but it still needed a personality. And that's claw.md. This file is the entire operating manual for Sorus written in plain English, not Python. It describes what the sensors do, what actions are available, what the safety rules are, how to navigate, how to express itself through the face display, when to speak, and what to say.

**9:22** · Sarah's character lives in this file and it's also shared in the GitHub project.

**9:26** · I have a link in the description for that. And that's genuinely how I build most of it. What I found is that this file is powerful in a way that feels almost unreasonable. Early on, Sarus was completely silent, navigating, avoiding obstacles, completing task, saying almost nothing. I added a few lines about narrating decisions out loud, and it suddenly wouldn't stop talking.

**9:46** · Changing a sentence in a text file changed the robot's entire personality.

**9:50** · And amazingly, no code touched. That's the clot. MD effect, and it works in both direction. And this is really the core difference between 1.0 and 2.0.

**9:58** · Version 1.0 was components stitched together. every behavior patched in manually. But 2.0 is much cleaner, more intentional and AIdriven from the ground up.

**10:13** · For logging, every sensor reading, every movement decision, every reasoning steps gets written to a log. I'm rooting that to Snowflake because I want to run proper analysis on the decisions data over time. But you essentially can do something similar with a local Postgress database or even a flat file on the Pi itself. The point is having a record of what the robot did and why.

### Live Demo (Real-World Test & Recoveries)

**10:37** · Now let me just show you how SURS perform in the real world. I'm going to run four demos. Basic operations, object detection, navigating to our target, and the last one is the most interesting one I have done with Sus yet. I'll save what it is. Just stay tuned. Hey Sus, who are you?

**11:04** · I'm Saras, a physical AI robot car running on a Raspberry Pi 4. I can see, move, speak, and explore the world around me. Nice to meet you.

**11:21** · Hey, Saras, what do you see?

**11:26** · As Sus describes the room on the right, you can see the logs in real time. It accessed both cameras to answer that question.

**11:34** · I can see you. A bearded person in a flannel shirt sitting at a desk with a monitor. On the floor, there's a small tripod right in front of me and a standing desk with cables and blue lighting underneath.

**11:46** · Hey Sus, can you turn to your left by 90°?

**11:56** · Turning left 90°.

**12:06** · Hey Sus, I want you to find the couch in this room.

**12:16** · On it. Let me do a full 360 sweep first to see if I can spot the couch from here. You can see in the log mapping everything around in 360° then reasoning about where the couch is likely to be based on what it sees.

**12:45** · Hold on. I can see something beige and upholstered on my right. That could be the couch. Horizon cam for the room. Flow cam for what's directly in front of it. One image, full picture.

**12:58** · Found it. The couch is right here. It's a gray sofa with a blanket and a fluffy white pillow on it.

**13:07** · Hey Sus, I want you to find the window in this room and move towards that. on it. Let me sweep the room first to find the window. Got it. Window spotted on my right. Lots of natural light coming through. Orienting towards it now.

**13:57** · Watch the logs. It checked lighter before moving. Confirm the path that looked clear. Then send the move command through to the ESP32.

**14:05** · Window is right ahead. I can see the sky and houses outside. Moving in. What it didn't account for was how close the window wall actually was.

**14:26** · Hey Sus, do you know you have bumped into the window?

**14:33** · Oops. Yeah, got a little too enthusiastic there. Backing up. I didn't write any recovery behavior there. Claude decided to back up on its own.

**14:50** · So, that happened. And I want to be honest, the first time I saw that, I actually laughed. The decision was right. It found the window. It just didn't stop in time. In 1.0, I would have opened a Python file and written a fix. But in 2.0, I described the problem differently by changing a few lines in cloudMD. And I'm going to show you what that change actually did.

**15:09** · Hey Sus, I want you to go forward this time, but do not bump into the window. Heads up, I'm still facing the window, so going in carefully.

**15:36** · Now carefully watch the locks. Ladder reading dropped below the safety threshold midmovement and it stopped itself. That's the interrupt I built into the MCP server. It can't override it even if the original instruction said to keep going. One description change and it went from bumping the wall to stopping few centimeters before it. But now a different question arises. Can it do the same when there are real objects in its path? It's time to make this harder.

**16:00** · Hey Sus, I want you to go to the window without bumping into anything.

**16:06** · Let me help you navigate through that window safely. I can see the window ahead, but there's a traffic cone blocking my direct path. I'll need to go around it.

**16:18** · Here it sees the cone, check slider, decides to route right.

**16:24** · Good clearance this way. Moving forward to get past the cone. I'm right in front of the window now, but it looks closed and there's a baseboard heater on the floor blocking the last bit of approach. Hey Sus, you are still far from the window. There is a cone in front of you.

**17:04** · Still got that cone in my face. Backing up and going around properly this time.

**17:09** · So Sorus reach a second cone, but it bumps into it. Also, it just told me it reached the window. It saw something in the target direction and concluded it was done.

**17:18** · The cone is right on my bumper. I'll turn in place to angle away from it first. And I think the problem here is in the TR sensor that should have caught that cone at flow level which I think it was taking too long to report back.

**17:34** · What you just saw was a very reasonable mistake. And this is where I did something I think is the most interesting part of this whole build. I didn't open a code editor. I opened a cloud code terminal session and just told it what was wrong. First I asked it to verify the sensor is actually working. It fires the check, reads the output, confirms it's responding. I told it the sensor wasn't working from the main program.

**18:01** · Watch this. It goes into the code, reads it, find the issue, and fixes it without me touching a file. And those are real edits to real files. I just reviewed them, and accepted the changes. Before asking it to move, I did something slightly different this time. I asked Sus if it was safe to move forward. So this time TF sensor caught that.

**18:23** · Nope. Forward is blocked. There's something on the floor right in front of me and true clearance is only 49 mm. Not safe to move forward.

**18:33** · Then I asked how it would navigate if it had to.

**18:39** · I turn right to go around the floor obstacle. Rescan after each move, then curve back toward the original direction once it's cleared.

**18:50** · And only then I told it to go.

**18:54** · What you are about to see is it planning before acting and stopping the moment it detects its first obstacle.

**19:01** · Got it. There's a red cone right in front to my right. I'll go left to get around it. turned left. Got some clearance ahead.

**19:23** · Moving forward carefully.

**19:42** · Wall ahead. Turning right to get back on course.

**19:46** · My leg is showing up as a wall on the sensor. You can see it in the log as well. It stopped without any instruction from me.

**19:59** · Path looks clear. Over a meter ahead.

**20:01** · Going for it.

**20:14** · It is the lighter this time. It saw couch on the left. It stopped, made a slight right turn, and it kept going. And there's the wall. Emergency stop triggered and this time even after several obstacles nothing bumped. That's what a few minute of conversation with clot code did. Same robot same room same task no Python file opened and the robot debugged itself. I just told it what was wrong. And now one last demo.

**20:49** · Hey Sus, I want you to move towards the window following the traffic light rules. Here I'm using a toy traffic lights to see how much of the real world Saras already understands without me ever explaining it.

**21:09** · Hey, I'll find the window and head toward it using traffic light rules to stay safe. Green means go, yellow means slow down, red means stop.

**21:20** · It took an image, identified the red light, and pulled up what it already knows about traffic rules. not hardcoded, not something I taught it. It already knew. Now it's checking the image, seeing red, and deciding to hold.

**21:36** · Window spotted straight ahead, but the traffic light is red, so I'm stopping and waiting.

**21:46** · Face vent to alert, which means it's waiting. Green light moving forward toward the window.

**22:02** · And this time it sees green light. It noticed, confirmed it's safe, and started moving. So you can see that I gave it a traffic light and it followed the rules. I didn't write what red means or what green means. It already knew. That's the difference between programming a behavior and giving an AI the tools to act on what it already understands.

### The Gaps

**22:33** · Throughout every demo you just watched, one thing which was impossible to ignore is the latency. That pause between a command and the first movement is because Claude reasoning through the situation, deciding what to call and in what order. That's real and it's the most honest limitation of this version.

**22:48** · When you watch Boston Dynamics or Tesla Optimus, the motion looks fluid because those systems run dedicated real-time control loops hundred of times per second. Sus doesn't work that way. It's deliberate rather than reactive. For what it is, that's fine, but it's the honest gap between an LLMdriven robot and a purpose-built robotic system. And the gap is the thing I most want to close in the next version. I could swap to a faster model like Claude Haiku and the response time would drop noticeably.

**23:17** · But you would be trading the speed for decision quality. Haiku thinks faster, Sonnet thinks better. On a moving robot making real navigation decisions, that trade-off matters more than you would expect. So what's next? The biggest one on my list is Ross 2. It's the industry standard middleware for robotics.

### Saras 3.0

**23:37** · real-time sensor fusion, continuous control loops, and proper navigation stacks. Integrating SRUS with ROSS 2 would directly address the discrete step. It's a significant undertaking, but the highest leverage upgrade I can make. I'll keep building and keep documenting. And if you want a full step-by-step assembly tutorial, drop a comment below. I'll make that video if there is enough interest. And again, everything from this video, the hardware component list, clotmpt file, all the prompts is on GitHub. And the SURS 1.0 video is there too if you want to see how far this has come. There is also a discord link in the description.

**24:06** · If you are building something similar or want to go deeper on any part of this, come join. It's a good place to ask questions and share what you have been working on. All right, that's it for this video. Hey Saras, say goodbye to my YouTube audience.

**24:21** · Goodbye everyone and thanks for watching. Don't forget to like and subscribe. See you in the next one.