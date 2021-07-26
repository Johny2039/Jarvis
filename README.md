# Jarvis
AI application


import pyttsx3
import datetime
import speech_recognition as sr
import wikipedia
import webbrowser
import os 
import time

opts = {"alias": ('Jarvis', 'jarvis', 'Jarymes'),
        "tbr": ('say', 'say me', 'look me', 'how much', 'pronounce', 'as','how many','put','translate', "notches",'run','how much will'),
        "cmds":
            {"ctime": ('current time', 'time', 'what time is it'),
             'startStopwatch': ('start the stopwatch', "turn on the stopwatch", "serif time"),
             'stopStopwatch': ('stop the stopwatch', "turn off the stopwatch", "stop"),
             "stupid1": ('tell a joke', 'make me laugh', 'you know jokes', "joke"),
             "calc": ('прибавить','умножить','разделить','степень','вычесть','поделить','х','+','-','/'),
             "shutdown": ('off', 'turn off', 'shutdown of my laptop')}}

engine = pyttsx3.init()
voices = engine.getProperty('voices')
#print(voices[1].id)
engine.setProperty('voices', voices[0].id)


def speak(audio):
    engine.say(audio)
    engine.runAndWait()

def time(): 
    Time = datetime.datetime.now().strftime("%I:%M:%S")
    speak(Time)

def date():
    year = int(datetime.datetime.now().year)
    month = int(datetime.datetime.now().month)
    date = int(datetime.datetime.now().day)
    speak(date)
    speak(month)
    speak(year)

def wishme():
    speak("Welcome back sir!")
    speak("The current time is")
    time()
    speak("The current date is")
    date()
    hour = datetime.datetime.now().hour
    if hour >= 6 and hour<12:
        speak("Good morning sir!")
    elif hour >=12 and hour<18:
        soeak("Good afternon sir!")
    elif hour >=18 and hour<24:
        speak("Good evening sir!")
    else: 
        speak("Good night sir!")

    speak("JARVIS at your service. Please, tell me how can I help you?")

if __name__ == "__main__":
    speak("Hello sir?")
    speak(",")
    speak(".")
    speak("How are you sir?....")
    speak(",")
    speak(".")
    speak(",")
    speak(".")
    speak(".")
    speak(".")
    speak(".")
    speak(".")
    speak(".")
    speak(".")
    speak(".")
    speak(".")
    speak("Thank you for your interest sir, everything is fine")
    speak(",")
    speak(".")
    speak("Sir please, tell me how can I help you?")

def takeCommand():
    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("Listening...")
        r.pause_threshold = 1
        audio = r.listen(source)

    try:
        print("Recognizing...")
        query = r.recognize_google(audio, language='en-En')
        print(query)

    except Exception as e:
        print(e)
        speak("Say that again please...")

        return "None"
    return query 

query = takeCommand().lower()

if 'wikipedia' in query:
    speak('Searching Wikipedia...')
    query = query.replace("wikipedia", "")
    results = wikipedia.summary(query, sentences=2)
    speak("According to Wikipedia")
    print(results)
    speak(results)
    
   
elif 'open youtube' in query:
    webbrowser.open("youtube.com")

elif 'open whatsapp' in query:
    webbrowser.open("web.whatsapp.com")

elif 'open sliwbl' in query:
    webbrowser.open("https://sliwbl.biz/")

elif 'open telegram' in query:
    webbrowser.open("https://web.telegram.org/#/im")

elif 'open platonus' in query:
    webbrowser.open("https://edu2.aues.kz/")

elif 'open google' in query:
    webbrowser.open("google.com")

elif 'play music' in query:
    music_dir = 'C:\\Songs'
    songs = os.listdir(music_dir)
    print(songs)
    os.startfile(os.path.join(music_dir, songs[0]))
    
if 'Jarvis stop' in query:
    speak('Ok sir...')
    results = os.system('')
