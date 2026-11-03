
      **Виклад відео про K-Plex 0.3.0 для Obsidian:**

      **Основні нововведення:**
      - **Інтерактивний Mindmap View**: Живий безмежний канвас для візуалізації знань.
      - **Фацети (Visual Buckets)**: Налаштовувані візуальні контейнери для організації нотаток за метаданними та правилами.
      - **Двоканальна перетяжка (Dual-Canvas Drag & Drop)**: Зв’язування нотаток між двома вікнами за допомогою перетягування.
      - **Темна/світла теми Obsidian**: Підтримка стилів для зручності роботи.
      - **\"My Footprints\"**: Візуальні сліди нависання для відстеження подорожей у знанні.
      - **AI-підтримка**: Автоматичне генерування промптів для створення фацетів.
      - **Налаштування для навчання**: Графічні лінзи та правила для навчальних сценаріїв.

      **Практичні функції:**
      - Компас для орієнтації в нотатах.
      - Sidecar для інспекції нотаток.
      - Експорт слідів нависання для аналізу пошуку знань.

      **Розділи відео:**
      1. Вступ до K-Plex.
      2. Завантаження зразкового допоміжного файлу.
      3. Компас та орієнтація.
      4. Редагування нотаток з Markdown.
      5. Sidecar для інспекції.
      6. Mindmap View.
      7. Фацети та їх робота.
      8. Навчальні сценарії.
      9. Двоканальна перетяжка.
      10. \"My Footprints\".
      11. AI-підтримка для фацетів.
      12. Наступні функції (CLI, агентні графічні з’єднання).

      **Цільова аудиторія**: Учні PKM, розробники Obsidian, дослідники знань.
    
![](https://www.youtube.com/watch?v=oRUXDwe-x3Q)

🔗 RESOURCES & LINKS:  
🤔 K-Plex Help Vault on GitHub: https://github.com/zsviczian/kplex-help  
(Download/clone the vault to test out these exact graphs and facet configurations!)  
⚙️ Obsidian Community Plugins: https://community.obsidian.md/plugins/k-plex  
🎨 K-Plex on GitHub: https://github.com/zsviczian/kplex  
📝 Obsidian: https://obsidian.md  
  
JOIN THE COMMUNITY & COURSES  
📕 Read Sketch Your Mind: https://community.sketch-your-mind.com/sym  
Join the Sketch Your Mind Community: https://community.sketch-your-mind.com/welcome  
✏️ Sign up for the Visual Thinking Workshop: https://community.sketch-your-mind.com/vtw  
🎨 Master Obsidian-Excalidraw: https://community.sketch-your-mind.com/em  
📨 Join the Sketch Your Mind Newsletter: https://sketch-your-mind.com/newsletter  
  
📱 CONNECT WITH ME  
🥰 Support the plugin, buy me a coffee: https://ko-fi.com/zsolt  
📩 @zsviczian on the Obsidian Members Group (OMG) Discord  
🐦 Twitter: https://twitter.com/zsviczian  
💬 Meet on Mastodon: https://pkm.social/@zsviczian  
  
\---  
  
In this video, I walk you through the latest 0.3.0 update to K-Plex (Knowledge Plex)—an ontology-driven, interactive graph view and visual thinking tool for Obsidian.  
  
We explore brand new features, including the dynamic Mindmap View, customizable Facets (board/bucket views based on frontmatter metadata & rules), native Obsidian light/dark theme support, split-canvas drag-and-drop linking, Footprints (visual breadcrumb trails), and built-in AI prompt generation to build custom facets effortlessly.  
  
\---  
  
⏱️ TIMESTAMPS:  
0:00 - Introduction to K-Plex for Obsidian  
0:46 - Downloading the Sample Help Vault  
1:44 - The Core Compass View & Directional Navigation  
2:40 - Embedded Markdown Editor & Note Properties  
4:02 - Using the Sidecar for Note Inspection  
5:14 - Mindmap View: Live Infinite Canvas Exploration  
7:13 - Introducing Facets: Visual Buckets for Your Notes  
8:37 - How Facets Work (Workshop Stage Example)  
9:48 - Advanced Rules & Graph Lenses (Learning Mode Example)  
11:53 - Nick Milo's Local Map Roles Facet  
12:47 - Obsidian Light & Dark Theme Support  
13:23 - Dual-Canvas Drag & Drop Relationship Linking  
15:32 - "My Footprints" Breadcrumb Navigation History  
16:47 - AI-Powered Facet Builder Prompt Generator  
17:43 - What's Next: CLI & Agentic AI Graph Access  
  
\---  
  
🍿 Watch next:  
K-Plex Walkthrough with Andy: https://youtu.be/XIq8uf8OaNI  
K-Plex 0.1.3 Release Notes on the Sketch Your Mind Community: https://community.sketch-your-mind.com/t/12443  
K-Plex on GitHub: https://github.com/zsviczian/kplex  
  
https://youtu.be/7rnsULzez-g  
https://youtu.be/pQbv5jSaW9Q  
https://youtu.be/O-7JHDj5d7Y  
  
\---  
  
#Obsidian #ObsidianMD #PKM #PersonalKnowledgeManagement #NoteTaking #Productivity #GraphView #Zettelkasten #KPlex #VisualThinking #PKM #MapOfContent

## Transcript

### Introduction to K-Plex for Obsidian

**0:00** · Hey everyone, it's Zsolt here.

**0:03** · I want you to take a few minutes to show you what's new in K-PLEX.

**0:08** · And those of you who are not familiar with K-PLEX, K-PLEX is my new Obsidian plugin.

**0:14** · K-PLEX stands for Knowledge Plex.

**0:18** · And Plex is a suffix that comes from Latin and it stands for Weaving or Braiding.

**0:26** · So this is your knowledge interwoven.

**0:30** · K-PLEX is a graph view for Obsidian that allows you many different ways to organize your notes and look at them.

**0:41** · It's an ontology-driven graph view that allows you to create new connections, that allows you to do drag and drop.

### Downloading the Sample Help Vault

**0:50** · There are different type of views.

**0:53** · So I'm going to show you because there are many new features in that space.

**0:57** · I'm also going to show you a few of the existing features so you understand it if this is your first video seeing K-PLEX in action.

**1:07** · The graph that we are looking at here right now is available on GitHub.

**1:12** · It's the K-PLEX Help repository.

**1:15** · I'm going to include it in the video description below.

**1:19** · So I encourage you to clone this repository and explore K-PLEX like this.

**1:26** · The repository is a full Obsidian vault.

**1:29** · If you open it in Obsidian, you allow the plugins, then K-PLEX will come to life like this as you see it right here.

**1:39** · And I try to keep this up to date so that the new features are always available.

### The Core Compass View & Directional Navigation

**1:44** · So let me show you how you navigate K-PLEX.

**1:46** · This is the default view of K-PLEX.

**1:50** · It's called the Compass view and I'm going to explain why a compass in a second.

**1:56** · Navigation is very simple.

**1:59** · If I click on a node, then that node is going to come to the center and around it, I'm going to see all the other nodes.

**2:09** · Now what you can see here is you can see that you have parent nodes, you have children nodes, you have right hand side and left hand side nodes.

**2:21** · And the right and the left or the east and the west has different meaning.

**2:27** · The east are the challengers and the next items and the left are the friends and the previous items if you're looking at navigating like this.

### Embedded Markdown Editor & Note Properties

**2:40** · Now each of the nodes can be expanded into an editor mode.

**2:46** · If I click here, then the markdown node is open.

**2:50** · Right now in Obsidian, I have the document properties set up to show in source mode.

**2:59** · That's my preference.

**3:00** · I'm old fashioned.

**3:02** · I know.

**3:03** · Of course, you can use the Obsidian Properties view as well.

**3:07** · So if I open file properties like this, then you can see the same node.

**3:14** · Actually, you can see the same properties here in the Obsidian Properties editor as well.

**3:21** · But for some cases, I like it better like this.

**3:24** · Of course, you can change the setting.

**3:27** · It's simple setting, you can come here to document properties and you can, for example, hide those properties.

**3:35** · I'm going to keep them visible because I do want to show you something later on.

**3:40** · So I just wanted to mention that.

**3:41** · But this is a proper markdown editor that you can use to explore your nodes.

**3:47** · And by the way, Obsidian Canvas, Exclidraw and other plugins can also open in this view here as well.

**3:57** · Now, there's another way to look at your nodes and then we'll jump into the new features.

### Using the Sidecar for Note Inspection

**4:02** · I just wanted to show you the sidecar here.

**4:05** · So if I open the sidecar, then as I navigate, then always the relevant sidecar, the page that's in the center appears here in the sidecar.

**4:17** · And you can move the sidecar to whichever side of the node you want that can be helpful.

**4:23** · And you also have this button that you can actually come here and make this full screen or you can push this out like this.

**4:32** · Or you can also do this if you hold down the control button, then you can, that's the command button on the Mac, you can extend it in one step or close it in one step.

**4:46** · And by the way, that's something to remember.

**4:49** · I am going to come back and improve on the shortcuts and the modifier keys.

**4:54** · But often the alt or option and control or command keys have special meanings as you navigate the graph.

**5:04** · By the way, you can also use the keyboard to navigate the graph and then you can use the enter to activate nodes and many other things.

### Mindmap View: Live Infinite Canvas Exploration

**5:15** · But what I wanted to show you first today is the different type of views available in this next update or actually this is the current version of of K-plex.

**5:29** · And here you can see the mind map view.

**5:33** · And I want to show you this that if I come here to the views and the lenses menu, then I can click here to open a mind map.

**5:43** · And this way I can view this note in a mind map type of setup.

**5:50** · And here I can start to navigate my notes as a mind map.

**5:55** · Now what's fun here is this mind map can be expanded pretty much infinitely, not infinitely because I have a limitation of maximum 2000 notes in a canvas and that's already I think a performance challenge.

**6:14** · But yeah, so here if I click on this node, I can continue to expand this now, sometimes you will read this that you no longer have the expansion node and that's because you've reached a cyclical reference reference in this case, this node is already here so it would become an infinite expansion.

**6:38** · But you can see this how I can start to expand my mind map like that.

**6:46** · And this is your live obsidian notes that you're expanding into the mind map.

**6:53** · This is a bit of a well, maybe unconventional mind map because you can also expand here the parents.

**7:01** · This might not has several different layers there, it can start to expand and you can view your obsidian graph like this.

**7:11** · I think this is pretty nice.

### Introducing Facets: Visual Buckets for Your Notes

**7:13** · But what I wanted to show you as well is the facets view because I think that is a very powerful feature of the new cape like version.

**7:26** · And I have a couple of demonstrations of facets.

**7:29** · I wanted to show you a few of them that you get a better understanding.

**7:34** · So, for example, I can create a workshop board facet.

**7:40** · So if I click on this, then at first, if you look at this encompass view, then nothing special happens, you've already seen my map and you can imagine how that will look like.

**7:53** · But here I can also come to select facets and I can look at the workshop stage.

**8:01** · And now this view has changed.

**8:04** · So you can see here that I have the collect shape and the share and notes are distributed in different buckets, but you can still see the basic logic of the friends, the children, the parents, etc.

**8:23** · But these are distributed to these buckets and the buckets can also have some relational logic as well.

**8:31** · Now, I'm going to show you a couple of different facets.

**8:34** · So you get an understanding of how these can work.

### How Facets Work (Workshop Stage Example)

**8:38** · You can define these and I'm going to click here to open the workshop stage settings.

**8:45** · And in this case, you can see that this facet is based on a markdown property and indeed the property name is Workshop Stage.

**8:57** · And if I scroll down, then I can see that if the Workshop Stage is shape, then it's going to be green background.

**9:12** · Yeah, you can see here that if it's the stage is collect, then it's going to be blue background, etc.

**9:21** · So you can see all of that right here that these are the shape, these are the collect.

**9:26** · And by the way, these items and if I move my mouse and hold down the Alt key or option on the Mac, I can I can redefine the size of these as I want.

**9:37** · I can also make this double big.

**9:40** · And of course, the facet is going to remember that so you have this organization opportunity here.

**9:47** · But if you look at a different type of review here, let's look at now let's go up here.

### Advanced Rules & Graph Lenses (Learning Mode Example)

**9:55** · Let's look at our workbench questions example.

**10:00** · So in this case, I'm going to click here to facets.

**10:04** · And we're going to select a workbench questions.

**10:09** · And what I want to show you here is that this one is based on a category rule that gives you much more flexibility in how you define this because in this case, what you will see here is I have also the lenses.

**10:28** · So you can see here I have different graph lenses defined and graph lenses can hide notes, or they can also color different nodes based on their content and they follow an obsidian basis like syntax.

**10:46** · So here you can see if the notes learning mode, tag is read and session size is short.

**10:56** · That means it's read briefly item.

**11:00** · So learning mode and session size.

**11:03** · Let me show you how this looks like.

**11:05** · So if we zoom in here, and I open this node right here, then you will see that this is learning mode read session size short.

**11:18** · And for example, if I come to read deeply, then this is going to look different, because this is again going to be learning mode read.

**11:28** · But in this case, session size is going to be longer.

**11:33** · And that's why it was categorized into another category.

**11:37** · So if your notes are categorized, then you can split your view into these buckets.

**11:44** · And these buckets can help you organize and understand your notes better.

**11:50** · Just to show you one last example of the facets.

### Nick Milo's Local Map Roles Facet

**11:54** · I also implemented the local map roles example.

**12:02** · So I'm taking this from Nick Milo's work.

**12:06** · And essentially what this shows you is it shows you the relative role of the file or the note because you have reference notes, you have concepts, you have supporting maps, and you have major maps.

**12:24** · And of course, you have the note right here.

**12:26** · And you can divide the note the notes.

**12:30** · Of course, in the test database, you have single notes for each of them, but you can you can do, you can have multiple nodes in each of these categories.

**12:43** · And I think finally, what I wanted to show you, of course, you can see that already, but just wanting to call it out.

### Obsidian Light & Dark Theme Support

**12:50** · So you're aware that Capelax now follows the obsidian theme settings.

**12:57** · So if I come here, and I change my obsidian theme to light, then you will see that Capelax follows that.

**13:08** · So now Capelax is fully integrated into how you like your obsidian.

**13:15** · And let me turn this back to dark note because it's the evening for me.

**13:20** · So I want to burn my eyes with that.

### Dual-Canvas Drag & Drop Relationship Linking

**13:23** · And maybe just to show you one last thing before I close the video today.

**13:31** · If you click here, you can create a second canvas.

**13:35** · And of course, this canvas can have maybe a different view.

**13:40** · So this one is now a mind map view.

**13:42** · But I want to show you the following is if I come here, like that, I can pick a note here.

**13:50** · So I'm going to pick this model and I'm going to show you the image and edit relationships, I can just click on this drag, and I can move it here and maybe I'm going to move it here as a right side item I can drop it in here.

**14:06** · And so this is now a challenger I can choose which challenger ontology I want.

**14:12** · I'm going to say this is a watch out.

**14:15** · And I'm going to just click link.

**14:17** · And voila, I created a new link here.

**14:20** · And of course, if now I open this, then we should actually see here the challenger now of course this is there you go.

**14:30** · The example local map roles has now appeared as a node linked to here because we just created that connection.

**14:42** · And of course, I can also come here and I can unlink it if I don't want this link, I can remove the link and then it is removed, of course on both graphs.

**14:53** · This is good because maybe on one side you have your facets and you have your containers.

**15:00** · And you can logically select your notes on the other side you might have your compass view.

**15:07** · Maybe you're working on a topic and you're looking for different items and perspectives to sort around the note.

**15:14** · And you can just drag and drop.

**15:16** · And of course you can drag and drop from obsidian bases you can drag and drop from the file menu you can create a link from here to either the pins or the history and lots of other stuff.

### "My Footprints" Breadcrumb Navigation History

**15:33** · And then you see I cannot stop because there are so many fun feature, just the real very very very last feature I want to show you here.

**15:41** · My footprints, which is your breadcrumbs.

**15:45** · This gives you a full navigation history of your session on this graph so it's different from the history at the bottom because the history

**16:25** · around your notes copying that can be helpful.

**16:29** · So I hope you found this video helpful.

**16:33** · I'm still working very actively to build additional features.

**16:38** · The next one I'm working on is to give you CLI access so that you can have Claude do all sorts of fun things with this.

### AI-Powered Facet Builder Prompt Generator

**16:48** · By the way that reminds me so I really cannot stop here.

**16:53** · But what I wanted to show you is if we come to facets, then here you have this copy AI authoring prompt.

**17:03** · And the value of this is you don't really need to understand how to set up facets you copy this prompt, you give it to your favorite agent, you explain what you want to do, it should return you a meaningful JSON object, you can also import your JSON here.

**17:24** · So you can create these different facets with the help of your favorite AI tool you don't really need to understand all of the logic.

**17:35** · Of course, it's not black magic, it's understandable but yeah if you want the shortcut that's already available and I was saying I'm working on next features and one of the important next features I want to implement is give your AI agent access to the graph stored in K-Plax and that should give you lots of flexibility in how you interrogate your notes and how you can navigate your notes.

### What's Next: CLI & Agentic AI Graph Access

**18:07** · Thank you.

**18:08** · I hope you enjoyed this and let's stay in contact.