- 👋 Hi, I’m @amirmohamadgamerr
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
amirmohamadgamerr/amirmohamadgamerr is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
#tarkib
import cv2
import pyttsx3
import speech_recognition as sr
import random
import datetime
r = sr.Recognizer()
def saytime():
    now=datetime.datetime.now()
    return f"The current time is {now.strftime('%H:%M:%S')}"

def isfunction(inp):
    return callable(inp)
commands={
    "hello": ['hello', "hey", "welcome to app"],
    "hey": ['hello', "hey", "welcome to app"],
    "hi": ['hello', "hey", "welcome to app"],
    "pc": ['hello', "hey", "welcome to app"],
    "bye": ['bye', 'have a nice day', "goodbye"],
    "goodbye": ['bye', 'have a nice day', "goodbye"],
    "time":saytime
}
name='mamad'
def listen():
    try:
        with sr.Microphone() as source:
            r.adjust_for_ambient_noise(source, duration=0.2)
            audio = r.listen(source)
            MyText = r.recognize_google(audio).lower()
            print(MyText)
            detected_key = detect(MyText)
            response = text_p(detected_key)
            speeck_text(response)
    except sr.RequestError as e:
        print(f"Could not request results; {e}")
    except sr.UnknownValueError:
        print("unknown error occurred")

def learn(inp):
    try:
        SpeekText(f"I don't know what '{inp}' means. Can you teach me?")
        with sr.Microphone() as source:
            response=r.adjust_for_ambient_noise(source, duration=0.2)
            audio = r.listen(source)
            print("Did you say",response)
            response=response.replace("say","")
            commands[inp]=[response]
            print("update command",commands)
    except sr.RequestError as e:
        print(f"Could not request results; {e}")
    except sr.UnknownValueError:
        print("unknown error occurred")

def textprocess(inp):
    for key,value in commands.items():
        if key in inp:
            if isiteafunction(value):
                return value()
            else:
                return random.choice(value)
    learn(inp)
