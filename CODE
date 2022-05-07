import speech_recognition as sr
from gtts import gTTS
from playsound import playsound
import os
import datetime as dt
import pywhatkit as pk
import webbrowser

listener= sr.Recognizer()

def speak(cmd):
    tts = gTTS(cmd, lang="te")
    tts.save("audio.mp3")
    playsound("audio.mp3")
    os.remove("audio.mp3")

va_name="సాయి"
speak(" నమస్కారము నేను మీ పర్సనల్ వాయిస్ అసిస్టెంట్ మీకు ఏ విధంగా సహాయ పడగలను")
def take_cmd(check):
    command=""
    try:
        with sr.Microphone() as source:
            print("listening")
            audio=listener.listen(source)

            if check:
                command = listener.recognize_google(audio, language="te")

                if va_name in command:
                  command=command.replace("సాయి","")
                  print(command)
                  # speak(command)
                else:
                      command=""
            else:
                command = listener.recognize_google(audio, language="en-US")

    except:
        print("check your mic")
    return command
while True:
    final_cmd=take_cmd(True)
    if final_cmd!="":
        if " టైం" in final_cmd:
            current_time=dt.datetime.now().strftime("%I:%M %p")
            speak(current_time)
        if "యూట్యూబ్" in final_cmd:
            speak(" ఏ వీడియో ప్లే చేయాలో చెప్పండి")
            final_cmd=take_cmd(False)
            pk.playonyt(final_cmd)
            speak("ఆనందించండి ")
        if "గూగుల్" in final_cmd:
            speak("ఏమి వెతకాలో చెప్పండి")
            final_cmd=take_cmd(False)
            pk.search(final_cmd)
