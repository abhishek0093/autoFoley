# Introduction 
Ever Wondered about background soundtrack added to the movies, those "dhichkyoon" sound of pistols, those footsteps sound, those car racing sounds? You need to hire sound artists to generate those kinds of sounds, and the art is called Foley.But what if you don't have that much money to pay to artist or to pay for copyright usage? Well, then there is some good news for you. You can use a Deep Learning Model to generate a never-before music for your video, and that too almost free!! 
In this project we would explore the possibility of automating the process of Foley with the help of Deep Learning, and hence the name AutoFoley. 

# Flow ...
To Generate the music for a video scene, we must first recognize what's happening in the video. Then only a sound that is relevant to the video scene can be generated(think of playing horror music during party scene).
So the project would be splitted in three parts : 
1) Recognizing the activity in video 
2) Generating Music
3) Stitching generated music to the video 

## PART1- Recognizing Activity(LRCN Model):
Object detection through image is quite straightforward as there is only spatial information to deal with, but for video activity recognisition we also have time dependent temporal information. CNNs are great at extracting out spatial information, while LSTMs are great to deal with sequential data, so why not to use combination of them to detect activity in the video, and call it out as LRCN (Long-term Recurrent Convolutional Network).
### Approach 
The video is nothing but collection of various frames. If we have computation power we can process each frames, but otherwise splitting the entire video equally in {SEQUENCE_LENGTH} of frames will also give the gist of activity happening in the video. To train the model, we will split each video in eqidistant {SEQUENCE_LENGTH} frames and the corresponding target label would be the activity. The frames would be fed out to CNN layers which will extract out spatial features, and those extracted features would be fed to a LSTM model to train the model on the embedded time information in the video. Currently the model has been trained to recognize {PlayingPiano,HorseRace, Swing, Tai-chi} classes, trained on subset on UCF-50 Dataset.  

### Plots 
<p align="center">
  <img src="https://user-images.githubusercontent.com/111701999/185924337-1f6be0e4-a6ba-4878-939b-1f79c57a9f44.png">
</p>
 
<p align= "center">
  <img src="https://user-images.githubusercontent.com/111701999/185924343-ef0b9d69-da77-4720-a07d-c3c79accf6eb.png" align="center">
</p>

### Results

https://user-images.githubusercontent.com/111701999/185932993-e5b141ef-9b02-4daa-ac28-27b97e72fd6a.mp4


## PART2- Generating Music 
 Music is composed of notes and chords, and the entire music can be represented with a midi file which contain all the details of various notes played, their location and time duration. 
### Approach : 
We choose a SEQ_LEN, a window size at which we will be looking to make prediction for the next note. We split our midi files into notes of length of SEQ_LEN and the corresponding target note would be the actual next note in the music. The relationship between given set of notes of SEQ_LEN and targetted output would be learnt by our model during training.
At Music generation time, we would randomly select a starting point(of SEQ_LEN from train data), and model will make the prediction of next note. We will include the made prediction in our Window while excluding the element that came first and this will continue for desired amount of time. 
Note : I have trained the model to generate classical Piano tunes, and it can be changed as per needs by adding the relevant training data.

### Results: 

<video src="https://user-images.githubusercontent.com/111701999/185937460-eed4cbb9-c66d-40db-99c6-2f4f014f7af2.mp4"  width="330" height="250">
</video> 


## PART3- Adding Music to Video
We have saved both the lrcn_model and the music_model in google drive, and we can use those saved model to make the final AutoFoley. User will give a `unknown` video as input, we will first run our `lrcn_model` to detect activity happening inside the video. Once activity has been detected, we will call the relevant `music_model` saved in drive to generate a music for the video. We will add the generated music to the video using the music21 library. 

And guess what, You have now become a sound artist too(Okay Okay, not you but your laptop)!!.

### Results: 
https://user-images.githubusercontent.com/111701999/185940112-5690d445-4311-48f6-bdf9-f771a2896ac4.mp4

YES! We only gave it a silent video. And that music is copyright free !!


# Table of Content 

* <h4> autofoley_lrcn.ipynb </h4> 
  Google Colab file to train the LRCN Model. Can also be used solo to detect the activity happening in a video(see attached video in the outputs file). 
* #### autofoley_music_generator.ipynb : 
  Google Colab file to train the music_model. Can also be used solo to generate only the music(see attached audio in the file). 
* #### autofoley_final.ipynb :
  Google Colab file that uses above trained models to make final AutoFoley(see outputs folder). 
* #### Project : 
  Folder that you should add to your google drive to use the project. Contains saved models, saved helper values, test_videos etc.
* #### Outputs :
  Outputs obtained in project. 
* #### Plots :
  Various plots for the model . 

# Further Improvements and Futute Planning : 
* More Classes can be included for both lrcn_model and music_model to make it more general purpose. 
* API can be written to provide better experience to non-technical users. 

# References : 
https://learnopencv.com/introduction-to-video-classification-and-human-activity-recognition/

https://towardsdatascience.com/how-to-generate-music-using-a-lstm-neural-network-in-keras-68786834d4c5

And some youtube videos :). 



