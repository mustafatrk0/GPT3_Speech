import pyttsx3
import os
import speech_recognition as sr
import webbrowser
import random
from datetime import datetime
import time
import openai
import sys

r = sr.Recognizer()

# You should get your GPT3 API from https://platform.openai.com/account/api-keys site and paste it in this field
openai.api_key = "YOUR-API"

engine = pyttsx3.init()
engine.setProperty("rate", 200)  # speech rate
voices = engine.getProperty('voices')
engine.setProperty("volume", 2.0)
engine.setProperty('voice', voices[2].id)  # Choose Turkısh Language

# speech function
def speak(text):
    engine.say(text)
    engine.runAndWait()

# microphone function
def record(ask=False):
    with sr.Microphone() as source:
        if ask:
            speak(ask)
        audio = r.listen(source)
        voice = ''
        try:
            voice = r.recognize_google(audio, language='tr-Tr')
        except sr.UnknownValueError:
            return voice
        except sr.Recognizer:
            speak('sistem çalışmıyor')
        return voice

# task function
def response(voice):
    if 'merhaba' in voice:
        speak('Merhaba efendim')
    elif 'saat kaç' in voice:
        speak(datetime.now().strftime('%H:%M'))
    elif 'arama yap' in voice:
        search = record('ne aramak istiyorsunuz')
        url = 'https://www.google.com/search?q=' + search
        webbrowser.get().open(url)
        speak(search + 'için bulduklarım')
    elif 'kapan' in voice:
        speak('görüşürüz başkan')
        exit()
    elif 'bilgisayarı kapat' in voice:
        speak('bilgisayarını 10dan geriye doğru sayıp kapatacağım')
        os.system("shutdown /s /t 8")
        for i in range(10, 0, -1):
            speak(i)
    elif 'ayarları aç' in voice:
        os.system("start ms-setting")
    elif "hangi gündeyiz" in voice:
        today = time.strftime("%A")
        today.capitalize()
        if today == "Monday":
            today = "Pazartesi"

        elif today == "Tuesday":
            today = "Salı"

        elif today == "Wednesday":
            today = "Çarşamba"

        elif today == "Thursday":
            today = "Perşembe"

        elif today == "Friday":
            today = "Cuma"

        elif today == "Saturday":
            today = "Cumartesi"

        elif today == "Sunday":
            today = "Pazar"

        speak(today)
    else:
        # GPT3 engine response condition
        respon = openai.Completion.create(
            engine="text-davinci-003",
            max_tokens=4000,
            prompt=voice
        )
        gpt = respon["choices"][0]["text"]
        speak(gpt)

while True:
    voice = record()
    if voice != "":
        voice = voice.lower()
        response(voice)
