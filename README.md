# Introduction 
Ever Wondered about background soundtrack added to the movies, those dhikyon sound of pistols, those footsteps sound, those car racing sounds? You need to hire sound artists to generate those kinds of sounds, and that art is called Foley.But what if you don't have that much money to pay to artist or for copyright usage, but instead have a computer and some knowledge of deep Learning. Well, then there is some good news for you. You can use a Deep Learning Model to generate a never-before music to your video without worrying about copyright issues with existing sounds. 
In this project we would explore the possibility of automating the process of Foley with the help of Deep Learning, and hence the name AutoFoley. 

# Flow ...
To Generate the music for a video, we must first recognize what's happening in the video, and then only we can generate the relevant music(not liked this, think what it would be to play funny music over a sad scene). 
So the project would be splitted in three parts : 
1) Recognizing the activity in video 
2) Generating Music
3) Stitching generated music to the video 

# PART1- Recognizing Activity(LRCN Model):


# PART2- Generating Music 

# PART3- Adding Music to Video

# Table of Content 

* #### autofoley_lrcn.ipynb #### : Google Colab file to train the LRCN Model. Can also be used solo to detect the activity happening in a video. 
* #### autofoley_music_generator.ipynb #### : Google Colab file to train the music_model. Can also be used solo to generate only the music. 
* #### autofoley_final.ipynb #### : Google Colab file that uses above trained models to make final AutoFoley. 
* #### Project #### : Folder that you should add to your google drive to use the project. Contains saved models, saved helper values, test_videos etc.
* #### Outputs #### : Outputs obtained in project. 
* #### Plots #### : Various plots for the model . 

# Further Improvements : 
More Classes can be included for both lrcn_model and music_model to make it more general.

# References : 
https://learnopencv.com/introduction-to-video-classification-and-human-activity-recognition/
https://towardsdatascience.com/how-to-generate-music-using-a-lstm-neural-network-in-keras-68786834d4c5

And some youtube videos :). 
