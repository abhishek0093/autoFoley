# Introduction 
Ever Wondered about background soundtrack added to the movies, those "dhichkyoon" sound of pistols, those footsteps sound, those car racing sounds? You need to hire sound artists to generate those kinds of sounds, and the art is called Foley.But what if you don't have that much money to pay to artist or to pay for copyright usage? Well, then there is some good news for you. You can use a Deep Learning Model to generate a never-before music for your video, and that too almost free!! 
In this project we would explore the possibility of automating the process of Foley with the help of Deep Learning, and hence the name AutoFoley. 

# Flow ...
To Generate the music for a video scene, we must first recognize what's happening in the video. Then only a sound that is relevant to the video scene can be generated(think of playing horror music during party scene).
So the project would be splitted in three parts : 
1) Recognizing the activity in video 
2) Generating Music
3) Stitching generated music to the video 

# PART1- Recognizing Activity(LRCN Model):
Object detection through image is quite straightforward as there is only spatial information to deal with, but for video activity recognisition we also have time dependent temporal information. CNNs are great at extracting out spatial information, while LSTMs are great to deal with sequential data, so why not to use combination of them to detect activity in the video, and call it out as LRCN (Long-term Recurrent Convolutional Network).
## Approach 
The video is nothing but collection of various frames. If we have computation power we can process each frames, but otherwise splitting the entire video equally in {SEQUENCE_LENGTH} of frames will also give the gist of activity happening in the video. To train the model, we will split each video in eqidistant {SEQUENCE_LENGTH} frames and the corresponding target label would be the activity. The frames would be fed out to CNN layers which will extract out spatial features, and those extracted features would be fed to a LSTM model to train the model on the embedded time information in the video.

# PART2- Generating Music 

# PART3- Adding Music to Video

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
