from pytube import YouTube
import pyperclip
import time
from tkinter import *
from tkinter import filedialog
import customtkinter

customtkinter.set_appearance_mode("dark")

def Ctheme():
    if theme.get() == "dark":
        customtkinter.set_appearance_mode('dark')
    elif theme.get() == "light":
        customtkinter.set_appearance_mode('light')

f = customtkinter.CTk()
f.geometry('600x525+575+200')
f.title("downloader youtube")
f.iconbitmap("C:\\Users\Bychette\Desktop\code\images.ico")
f.resizable(width=False, height=False)

theme = StringVar()
theme.set("dark")

CTeme1 = customtkinter.CTkRadioButton(f, text="dark", variable=theme, value="dark", command=Ctheme)
CTeme1.place(x= 220, y= 490)

CTeme2 = customtkinter.CTkRadioButton(f, text="light", variable=theme, value="light", command=Ctheme)
CTeme2.place(x= 290, y= 490)

def clearf():
    Eurl.delete(0, END)
    AUclabel= customtkinter.CTkLabel(f, text="                                                                                                                                                   ")
    AUclabel.place(x=85, y=70)
    Ticlabel = customtkinter.CTkLabel(f, text="                                                                                                                                                ")
    Ticlabel.place(x=85, y=140)
    TAclabel = customtkinter.CTkLabel(f, text="                                                                                                                                                  ")
    TAclabel.place(x=85, y=210)
    EEclabel= customtkinter.CTkLabel(f, text="                                                                                                                                                   ")
    EEclabel.place(x=190, y=350)
    Bccopy = customtkinter.CTkLabel(f, text="                                                                                                                                                          ")
    Bccopy.place(x= 35, y=100)
    Bccopy = customtkinter.CTkLabel(f, text="                                                                                                                                                          ")
    Bccopy.place(x= 35, y=170)
    Bccopy = customtkinter.CTkLabel(f, text="                                                                                                                                                             ")
    Bccopy.place(x= 35, y=240)

clearbutton = customtkinter.CTkButton(f, text="clear", command=clearf, hover_color="#099B02",  fg_color="#09CA00")
clearbutton.place(x= 10, y= 490)

Eurl = customtkinter.CTkEntry(f)
Eurl.place(x=75, y=20, width=400)

def cherche():
    try:
        youtube_video = YouTube(Eurl.get())
        titre = youtube_video.title
        chaine = youtube_video.channel_url
        aUTEUR = youtube_video.author

        def caopy():
            try:
                pyperclip.copy(aUTEUR)
            except:
                print()
        
        Bcopy = customtkinter.CTkButton(f, text="copier le nom de l'auteur", command=caopy)
        Bcopy.place(x= 35, y=100)
        try:
            AUlabel= customtkinter.CTkLabel(f, text=aUTEUR + "                                                                                                  ")
            AUlabel.place(x=85, y=70)
        except:
            print("erreur auteur")
            AUlabel= customtkinter.CTkLabel(f, text="Erreur!" + "                                                                                                    ", text_color="#FF0000")
            AUlabel.place(x=85, y=70)

        def ctopy():
            try:
                pyperclip.copy(titre)
            except:
                print()
        
        Bcopy = customtkinter.CTkButton(f, text="copier le nom de la vidéo", command=ctopy)
        Bcopy.place(x= 35, y=170)

        try:
            Tilabel = customtkinter.CTkLabel(f, text=titre + "                                                                                                  ")
            Tilabel.place(x=85, y=140)
        except:
            print()

        def ccopy():
            try:
                pyperclip.copy(chaine)
            except:
                print()
        
        Bcopy = customtkinter.CTkButton(f, text="copier l'url de la chaine", command=ccopy)
        Bcopy.place(x= 35, y=240)

        try:    
            TAlabel = customtkinter.CTkLabel(f, text=chaine+ "                                                                                                  ")
            TAlabel.place(x=85, y=210)
        except:
            TAlabel = customtkinter.CTkLabel(f, text="Erreur!"+ "                                                                                                     ", text_color="#FF0000")
            TAlabel.place(x=85, y=210)
    except:
        EElabel= customtkinter.CTkLabel(f, text="Vous devez mettre une URL youtube!", text_color="#FF0000")
        EElabel.place(x=190, y=350)
        AUclabel= customtkinter.CTkLabel(f, text="                                                                                                                                                   ")
        AUclabel.place(x=85, y=70)
        Ticlabel = customtkinter.CTkLabel(f, text="                                                                                                                                                ")
        Ticlabel.place(x=85, y=140)
        TAclabel = customtkinter.CTkLabel(f, text="                                                                                                                                                  ")
        TAclabel.place(x=85, y=210)

bcherch = customtkinter.CTkButton(f, text="shearch", command=cherche)
bcherch.place(x=420, y=20)

TTlabel = customtkinter.CTkLabel(f, text='Titre : ')
TTlabel.place(x=5, y=140)

AAlabel = customtkinter.CTkLabel(f, text='Auteur : ')
AAlabel.place(x=5, y=70)

Ttlabel = customtkinter.CTkLabel(f, text="Chaine : ")
Ttlabel.place(x=5, y=210)

UUlabel = customtkinter.CTkLabel(f, text='URL : ')
UUlabel.place(x=40, y=20)

def downloader():
    try:
        youtube_video = YouTube(Eurl.get())

        f2 = customtkinter.CTkToplevel(f)
        f2.title("Télécharger")
        f2.geometry('600x525+575+200')
        f2.iconbitmap("C:\\Users\Bychette\Desktop\code\images.ico")
        f2.resizable(width=False, height=False)

        filelabel = customtkinter.CTkLabel(f2, text="le dossier d'arriver : Vous navez choisis aucun fichier d'arriver!", text_color="#FF0000")
        filelabel.place(x= 20, y= 190)

        CTeme1 = customtkinter.CTkRadioButton(f2, text="dark", variable=theme, value="dark", command=Ctheme)
        CTeme1.place(x= 220, y= 490)

        CTeme2 = customtkinter.CTkRadioButton(f2, text="light", variable=theme, value="light", command=Ctheme)
        CTeme2.place(x= 290, y= 490)

        qualites = ['haute', 'moyen', 'bass', 'audio']

        Cqualites = customtkinter.CTkComboBox(f2, values=qualites)
        Cqualites.place(x= 15, y = 20)

        def quitter2():
            f2.destroy()

        B2quitter = customtkinter.CTkButton(f2, text="QUITTER", command=quitter2)
        B2quitter.place(x= 450, y=490)

        def chem():
            global fileredirect
            fileredirect = filedialog.askdirectory()
            filelabel = customtkinter.CTkLabel(f2, text="le dossier d'arriver : " + fileredirect + "                                             ")
            filelabel.place(x= 20, y= 190)

        Cchemain = customtkinter.CTkButton(f2, text="choisir le dossier", command=chem)
        Cchemain.place(x= 325, y= 20)
        
        def Download():
            qualite =  Cqualites.get()
            time.sleep(3)

            if qualite == 'haute':
                video = youtube_video.streams.get_highest_resolution()
                video.download(fileredirect)
                telelabel= customtkinter.CTkLabel (f2, text="Le téléchargement est finis!                                                            ", text_color="#00F028")
                telelabel.place(x=20, y=160)

            elif qualite == 'moyen':
                video = youtube_video.streams.get_by_itag(18)
                video.download(fileredirect)
                telelabel= customtkinter.CTkLabel (f2, text="Le téléchargement est finis!                                                            ", text_color="#00F028")
                telelabel.place(x=20, y=160)

            elif qualite == 'bass':
                video = youtube_video.streams.get_lowest_resolution()
                video.download(fileredirect)
                telelabel= customtkinter.CTkLabel (f2, text="Le téléchargement est finis!                                                            ", text_color="#00F028")
                telelabel.place(x=20, y=160)   

            elif qualite == 'audio':
                video = youtube_video.streams.get_audio_only()
                video.download(fileredirect)
                telelabel= customtkinter.CTkLabel (f2, text="Le téléchargement est finis!                                                            ", text_color="#00F028")
                telelabel.place(x=20, y=160)
            else:
                ETlabel= customtkinter.CTkLabel (f2, text="un problème est survenue!                                                            ", text_color="#FF0000")
                ETlabel.place(x=20, y=160)

        Btelecharger = customtkinter.CTkButton(f2, text="télécharger", command=Download)
        Btelecharger.place(x=170, y= 20)

        f2.mainloop()

    except:
        EElabel= customtkinter.CTkLabel(f, text="Vous devez mettre une URL youtube!", text_color="#FF0000")
        EElabel.place(x=190, y=350)

Bdownload = customtkinter.CTkButton (f, text="TÉLÉCHARGER", command=downloader ,hover_color="#9A0000", fg_color="#C60000")
Bdownload.place(x=225, y=290, height= 70)

def quitter():
    f.destroy()

Bquitter = customtkinter.CTkButton(f, text="QUITTER", command=quitter,hover_color="#B45700", fg_color="#DA6A00")
Bquitter.place(x= 450, y=490)

f.mainloop()

<!---
Max127832/Max127832 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
