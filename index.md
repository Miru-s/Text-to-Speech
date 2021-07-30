# Text to Speech Conversion

At first we have imported some important library files that are required for our project.
Tkinter- This framework provides Python users with a simple way to create GUI elements using the widgets found in the Tk toolkit. Tk widgets can be used to construct buttons, menus, data fields, etc. in a Python application.
gTTS- gTTS (Google Text-to-Speech)is a Python library and CLI tool to interface with Google Translate text-to-speech API. gTTS is a very easy to use tool which converts the text entered, into audio which can be saved as a mp3 file.
playsound - The playsound module is a cross platform module that can play audio files.
 
Then we have designed our GUI window, where we have defined it’s dimensions to be 350x300 and background colour to be black. We defined all the text along with their styling and font size.
 
Then comes the function Text_to_speech(). The function converts the text that we have entered in the GUI box (entry_field) to speech and saves it as a mp3 file in the same folder.
 
Then we have defined various buttons in our GUI box; those are “Play”, “Exit” and “Reset” buttons.


 
       
    from tkinter import *
    from gtts import gTTS
    from playsound import playsound

    root = Tk()
    root.geometry('350x300')
    root.resizable(0,0)
    root.config(bg = 'black')
    root.title('TEXT TO SPEECH')

    ##heading
    Label(root, text = 'TEXT_TO_SPEECH' , font='arial 20 bold' , bg ='white smoke').pack()
    #Label(root, text ='DataFlair' , font ='arial 15 bold', bg = 'white smoke').pack(side = BOTTOM)
    #label
    Label(root, text ='Enter Text', font ='arial 15 bold', bg ='black').place(x=20,y=60)
    #text variable
    Msg = StringVar()

    #Entry
    entry_field = Entry(root,textvariable =Msg, width ='50')
    entry_field.place(x=20 , y=100)
    def Text_to_speech():
      Message = entry_field.get()
      speech = gTTS(text = Message)
      speech.save('DataFlair.mp3')
      playsound('DataFlair.mp3')

    def Exit():
      root.destroy()

    def Reset():
      Msg.set("")

    #Button
    Button(root, text = "PLAY" , font = 'arial 15 bold', command = Text_to_speech, width =4).place(x=25, y=140)
    Button(root,text = 'EXIT',font = 'arial 15 bold' , command = Exit, bg = 'Red').place(x=100,y=140)
    Button(root, text = 'RESET', font='arial 15 bold', command = Reset).place(x=175 , y =140)


    #infinite loop to run program
    root.mainloop()

