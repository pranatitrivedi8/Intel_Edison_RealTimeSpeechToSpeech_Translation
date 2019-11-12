# Intel_Edison_RealTimeSpeechToSpeech_Translation
Real time Speech to Speech translation using Intel Edison The environment we live and work is becoming a multilingual. 
Learning  new languages is a good thing but  If you don't have timethen you will have to typically depends on apps to  bridge a 
communication gap. For next level intra-language conversations inreal-time, though,  you might need some extra translation power.
Aim is to effective communication without language barrier and one of the  solution for  that is  created by us which is " EDItalk ".

### The key components we are using in this device are:
- Intel edison board as a processing device , usb microphone , usb sound card with earphone for audio input,bluetooth headset as a speaker.
- Intel edison board's gpio is connected to buttons. Earphone is connected to otg port using soundcard.I interface three buttons .Red   button is for language acquisition device. Green button is for language translation.Blue button is for wireless music player.
- The main application of the device is language translation and in that for a speech to text and text to speech conversion.We used ibm watson's API. and for language translation, used what'smate API.
- As pressing this green button it will wait for the word to speak and then it will translate the spoken phrase in respective language .
- In future I will try to modify our project with following feature:
Touch screen display , wifi free feature and try to make a gadget that's small enough to fit in your pocket.
## Features 
1. English language understanding for rural people and children
2. Language translation : self study for new language learner & for conversation (calling) purpose & for travelling purpose
               ---  speech to speech : english to spanish
               ---  speech to speech : spanish to english
               ---  speech to speech  : hindi to  english
               --- ( trying for other whatsmate language ) : other  to english  --(for number purpose)
               --- (trying) speech to speech : english to hindi
               ---   speech to text : english to hindi (use for deaf people - no need to use sign language)
               -----    ( trying for other whatsmate language ) speech to  text :(use for deaf people- no need to use sign language) -- (for number purpose)
3.  Wireless music listen  --  (wifi direct file transfering between two edison )  -- long distance communication
                               ---  bluetooth as a speaker set command
                              --- use this device as a music player : learn with fun
4.  Final product display : compact module ( EDITalk + software code )

## Video 
This project's demo is [EdiTalk](https://www.youtube.com/watch?v=Glm0kKbHLlw).


 


