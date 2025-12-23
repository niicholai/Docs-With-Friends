---
Version: 1.0.0
---


# AI Obsidian Gold 
---


## 1. Plugins for Obsidian
 
**Obsidian Plugins** (Settings -> Community Plugins -> Browse):
- `Templater` by SilentVoid
- `Dataview` by Michael Brenan
- `DataCards` by Sophokles187
- `Dataview Serializer` by Sebastien Dubois
- `Smart Connections` by Brian Petro
- `Style Settings` by mgmeyers
 
Don't forget to click `Enable` after you click `Install` and they get done. Obsidian doesn't auto-enable community plugins.
 
There are others, but they are more niche, and I'm looking to get you started with minimal easy steps that do the most for you.
 
---


## 2. Themes for Obsidian
 
`ITS Theme` is a gorgeous, flat, matte theme with black, grays, and deep reds that are easy on the eyes with an amazing font. Images of mine attached for your viewing.
 
**Obsidian Themes:** (Settings -> Appearance -> Themes -> Manage)
- `ITS Theme` by SIRvb - is the one I use, I can't recommend it enough.
- `Minimal` by kepano - is recommend by a lot of power users.
- `AnuPpuccin` by Anubis - Looks fantastic, but it has a TON of color pallets to choose from.
- `Obsidianite` by Benny Guo - is gorgeous, it's a dark one with black, purples, shades of blue, and a icy blue font color.
 
 
---


## 3. Local AI & Embedding
 
We need to get you a local AI setup going to handle embedding. Embedding is... well, who better to explain a concept/tool/method we'll use AI for, than an AI itself? I'll let GPT handle this one.

Feel free to skip the quoted `What is Embedding` section, it's only here just in case you want to know what it is, and how it works, so you understand why people (and AI) love it and add it.
 
### What is Embedding? (A RAG concept)
> Imagine your notes and documents are a giant library—tons of pages, topics, thoughts, ideas. Now imagine you have a friend who’s really good at finding things, even if you don't describe them perfectly or remember the exact wording. You say:
> 
> `"Find something about how I fixed my server issue last month"`
> 
> and instead of searching only for those exact words, this friend understands what you're asking and pulls up the right information—even if you actually wrote `resolved nginx timeout` instead. That friend is an `Embedding model`.
> 
> At its core, an Embedding is a way of converting text into numbers. But not random numbers—numbers arranged so that similar ideas end up close together.
> 
> **Input:** Words, sentences, documents. Any text, including formats like markdown, HTML, etc.
> **Embedding:** Turns those into points in a 3D-like map that is thousands of dimensions. It's called a `vector map`.
> **Embedded Numbers:** Cause the AI to understand that, similar meaning = close together, different meaning = far apart. If `dinosaur` is 0.8765091, then `lizard` might be 0.8765008, and `cloud` might be 0.2144313.
> **This Allows:** The AI you talk to, to go from comparing text as raw letters, to actually comparing meaning.
> 
> **What does this mean for Obsidian?**
> 
> If you have 2,000 notes, traditional searching only finds matches if the words are exact. If you search for Dinosaur, you get the word Dinosaur, that's it. But asking AI to search after embedding, now you get a list of all the dinosaurs you wrote about, that snippet of how raptors became chickens that you saved, and that reminder you set to wear your T-Rex costume to your friends party. The more context you give the AI when asking to search for you, the better results you will get after embedding, normal searches do not come close to this.
> 
> **Final Example:**
> 
> You tell your AI chat in Obsidian: `Show me my notes about troubleshooting network errors.`
> 
> But you only wrote this in the note: `I fixed connectivity issues with my router by adjusting DNS.`
> 
> A normal search might miss that and come back with 0 results. But with embeddings your AI sees:
> - `network errors`
> - `connectivity issues`
> - `router DNS problem`
> 
> All 3 of those live next to each other in the embedding space so the AI says `"These ideas are related, I will pull this information for the user."`
> 
> **Final Summary of Embedding:**
> Embeddings turn your notes into meaning-based search, so you can find things even when you don't remember the exact words you used.


**ollama + Qwen3:**
1. Go to `ollama.com/download` and download then install the Windows version. This allows you to run open AI models locally. This will hit your GPU/CPU/RAM a bit, but only when the model is actively doing things and not sitting idle.
2. Open PowerShell (Preferably Windows Terminal with PowerShell 7 as your console, cause we're big boy IT guys now), type `ollama` and send, it should print a list of help commands if it installed and is running.
3. Same terminal run `ollama pull qwen3-embedding:8b` and ollama will download the 8 billion parameter embedding model by Qwen3 (Google but open source).
4. Make sure ollama desktop is running, if it is just minimize it, don't close it. When minimized it should "close" the window and still be running in the task bar with your other little icons.
 
---


## 4. Smart Connections Chat-Bot + Open Router API (The Big Brain) + Embedding with Ollama
 
Now you're cooking, you're so close to having an amazing AI setup in your Obsidian which is going to help a LOT, trust. But, how is embedding going to help if you can't actually talk to the AI that handles it? That's right, embedding AI models aren't meant for chatting and normal tasks, they are very specialized and trained to do one thing, and do it very well. Now we need an actual LLM model. Not only are we getting a big boy LLM your PC can't even handle, we're going to do it **for free**.
 
We need to setup an Open Router account for you, then edit the Smart Connections plugin setting in Obsidian. There's other settings you can tweak in it, but for now we're going to just get your AI's up and running.
 
**OpenRouter:**
1. Go to `https://openrouter.ai/` and make a free account. Make yourself an API key, name it what you want, I'd recommend `Obsidian Chat` just so you know what it is. Copy the API key and slap it into Notepad or something for now. Pretty sure it's gone as soon as you close the little API window, you'll most likely have to make another if you lose it before using it.
 
**Smart Connections:**
2. Go back to Obsidian and go to Settings -> Smart Chat -> Scroll down to the Model section.
3. **Chat Model Platform:** Select `Open Router`
4. **API Key:** Put in the Open Router API key you generated earlier with your Open Router Account.
5. **Refresh Models:** Click the Refresh Models button.
 
Now we need a sick nasty big boy LLM that is good at chatting, reasoning, taking instruction, and general use

**OpenRouter, again:**
1. Go to the `models` page or just use my link: `https://openrouter.ai/models`
2. On the left side panel expand `Prompt pricing` and drag the right circle all the way to the left circle. This should only show free models, which is what we want. Be sure to double check each one, sometimes they accidentally add paid ones in.
3. On the left side panel expand `Context length` While we can use smaller models, I would say use one with at least 128K context. So move the circle for the slider up to the first line past `64K` and take a look at the models.
4. `Note:` Unfortunately at some point to do this efficiently you will need to learn about models to some extent, take your time reading them as different models are designed for different things. For example, `TNG: R1T Chimera` is mostly used for roleplaying, whereas `Mistral: Devstral 2 2512` is used for coding and dev work.
5. `My Recommendations:` At this time, 12/10/2025, I would say choose `Amazon: Nova 2 Lite (free)`, `Tongyi DeepResearch 30B A3B (free)`, `OpenAI: gpt-oss-120b (free)`, `TNG: DeepSeek R1T2 Chimera (free)`, or `Qwen: Qwen3 235B A22B (free)`. Out of those 5, I would probably try DeepSeek R1T2, Qwen3 235B, and gpt-oss-120b first, in that order.
6. Once you know what model you want, head back into Smart Connections Settings.


**Smart Connections again:**
1. Go to `Chat Model` and click the empty box. Scroll down and find the one you want, click it.
2. Go down to `Smart Environment` and click on `Show Environment Settings`.
3. Scroll down to `Smart Sources`.
4. Find `Embedding model platform` and click the box beside it. Choose `Ollama (Local)`.
5. Under that you should see `Embedding Model`, click the box beside it and choose `qwen3-embedding:8b`.


## 5. Success!


That is it! You should now have a fully functioning embedding system that works automatically any time you make changes to a note. If you have a lot of notes you might hear your GPU spin up for a while as the embedding model we're running locally uses your GPU to do everything. So don't do this initially if you're fixing to play a game and you have a bunch of notes.

To actually talk to the AI, look on your left side bar in Obsidian and find the icon that looks like a conversation box from a comic with a smile face in it.  If you hover over it you should get a text popup that shows `Open: Smart Chat`. Click that and a new tab will open. You can expand here, name your chats, start a new fresh one, check your chat history, open chat settings, and more. But that's another topic for another time.

You did it, this guide was a lot to read, but I went step-by-step, and together our efforts should have you a gorgeous theme, full AI with powerful LLM's backing them up, and a full local embedding system up and running.


## 6. What's Next?


I will have more guides coming soon, such as how to write better notes, different ways to make use of the AI, how to use the plugins we installed earlier, and more! So look forward to it and I hope you enjoy your new Obsidian setup friends.