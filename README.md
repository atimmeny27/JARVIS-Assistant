## JARVIS-Assistant

This is a spin off of JARVIS from Iron Man, also highly customizable to be an expert in stem, history, or any subject(s) you can think of. It uses an HTML/CSS/JS stack for frontend and an API key with an n8n webhook as a backend or for the logic. If you wish to add/subtract features this n8n is no-code and all you need is an API for the intended service. You can send emails, texts, set reminders, turn on and off lights in your house, have a conversation, generate images, and anything else you want to build out.

It runs locally on port 2006, you can change if you want. When the user presses the middle button, it activates an 11labs Voice Agent running with an [ollama model](https://github.com/ollama/ollama). This then uses the agent to decide which n8n process to run, completes the task, and responds using the same ollama model in whatever 11labs voice and prompt you use.

When the user presses "W", they have the option to bring up a camera and mic. Pressing the space bar after giving permissions will allow the user to speak a prompt, show an item or anything in the webcam, and interact with whatever llm they use as if it had eyes and was conversing with them. I am working on adding CAD specific features to this to make for better and more practical STEM use cases. By changing the index.html a bit, you can wire up a different camera to use if you want. I cannot provide this because it will be different based on various factors. 

## Frontend Setup
1.
```bash
git clone https://github.com/atimmeny27/JARVIS-Assistant
cd JARVIS-Assistant
```
2. If you launch it, it probably wont have functionality but should look like this. Yes most of this is just for looks, the only thing that updates is the date, time, temp, and temperature widget when you click the circle in the bottom right. I have hardcoded [this repo](https://github.com/atimmeny27/IOS-Location-Change) into the map in the top right, so when I click a location it changes my location to there, but it can slow down processing speeds and there is rarely a use-case for it.
<img width="1694" alt="Screenshot 2025-06-10 at 3 13 11 PM" src="https://github.com/user-attachments/assets/e5f8488f-b089-41d0-b1f2-d91e019e0bb9" />

3. And it has this animation when you talk to it
<img width="1695" alt="Screenshot 2025-06-10 at 3 33 52 PM" src="https://github.com/user-attachments/assets/08927344-625c-4b9b-82f3-b364cb308f42" />

4. This is all changable in the html file.

## Backend Setup
1. This backend (n8n) costs $20/month but has a free trial and is a great and easy option to update and integrate new features.
2. [This](https://www.youtube.com/watch?v=KUvSzvFeZls) YouTube video explains it well how to setup this backend and provides free templates if you want to use them.
3. Ensure you setup the proper API keys for each service you use. 99% of the time there is a free option to use.

## 11 Labs Voice Agent
1. This is what actually talks to you, you can choose a voice, and prompt engineer any characteristics you want to [here](https://elevenlabs.io/)
2. All you have to do is "add a tool", setup a post request for your active production n8n webhook, and replace all the proper API keys in the html (Search "your_API" in the file and replace)

# Run It
1. The easiest way to run this is via docker and a localhost with
```
docker build -t JARVIS-Assistant .
docker run -d --name jarvis-container -p 2006:80 --restart always JARVIS-Assistant
```
2. Launch via localhost:2006 or whatever port you choose, thats it.

3. Using a pi 4 or newer with any persistent docker alternatives via ssh is what I have changed to and currently use. 
