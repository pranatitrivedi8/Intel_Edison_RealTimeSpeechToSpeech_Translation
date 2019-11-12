# Intel_Edison_RealTimeSpeechToSpeech_Translation
Real time Speech to Speech translation using Intel Edison The environment we live and work is becoming a multilingual. 
Learning  new languages is a good thing but  If you don't have timethen you will have to typically depends on apps to  bridge a 
communication gap. For next level intra-language conversations inreal-time, though,  you might need some extra translation power.
Aim is to effective communication without language barrier and one of the  solution for  that is  created by us which is " EDItalk ".
The key components we are using in this device are:
Intel edison board as a processing device , usb microphone , usb sound card with earphone for audio input,
bluetooth headset as a speaker.
Intel edison board's gpio is connected to buttons. Earphone is connected to otg port using soundcard.
we interface three buttons . Red button is for language acquisition device. Green button is for language translation.
Blue button is for wireless music player.
The main application of the device is language translation and in that for a speech to text and text to speech conversion
we used ibm watson's API. and for language translation we used what'smate API.
As we press this green button it will wait for the word to speak and then it will translate the spoken phrase in respective language .
In future we will try to modify our project with following feature:
Touch screen display , wifi free feature and try to make a gadget that's small enough to fit in your pocket.

 feature 1 : english language understanding for rural people and children
 feature 2 : language translation : self study for new language learner & for conversation (calling) purpose & for travelling purpose
               ---  speech to speech : english to spanish
               ---  speech to speech : spanish to english
               ---  speech to speech  : hindi to  english
               --- ( trying for other whatsmate language ) : other  to english  --(for number purpose)
               --- (trying) speech to speech : english to hindi
               ---   speech to text : english to hindi (use for deaf people - no need to use sign language)
               -----    ( trying for other whatsmate language ) speech to  text :(use for deaf people- no need to use sign language) -- (for number purpose)
feature 3 : wireless music listen  --  (wifi direct file transfering between two edison )  -- long distance communication
                               ---  bluetooth as a speaker set command
                              --- use this device as a music player : learn with fun
feature 4: final product display : compact module ( EDITalk + software code )

