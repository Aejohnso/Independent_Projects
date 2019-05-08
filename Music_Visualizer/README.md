# Homemade Music Visualizer with Homemade Music

This repository hosts all files related to my development of music visualizers, inspired by [this](https://github.com/Hvass-Labs/TensorFlow-Tutorials/blob/master/14_DeepDream.ipynb) code.

Beta version of my code [here](https://github.com/Aejohnso/Independent_Projects/blob/master/Music_Visualizer/DeepDreamViz.ipynb).

## Summary

The goal was to create a music visualizer that has deep dream distortions that respond to the music. If you are unfamiliar with deep dream, it can create transformations like this:

![jpg](DeepDreamCompare.jpg)

My code does the following steps:
1) Imports a song and creates a spectogram of the song using the package pylab. This fourier transform gives us the intensity (volume) of each frequency at each timestep in the song.
2) The spectogram is analyzed to find the intensity of the song between the frequency range 0-120Hz. This range corresponds to the kick drum. This intensity, which has a value for each of the 30 frames per second, is converted to an integer, expG, between 1 and 20. Note that the bass also exists in this frequency range, but the intensity of the kick drum exceeds that of the bass. If the previous timestep's intensity is less than the current timestep, the value of expG is set to 93% of the previous. This reduces the amount that the distortions change between timesteps, making it more enjoyable to watch.
3) The integer is used as input into the [deep dream algorithm](https://github.com/Hvass-Labs/TensorFlow-Tutorials/blob/master/14_DeepDream.ipynb). The higher the integer, the deeper the image transcends into deep dream space. Depending on which layer of the neural network is chosen, you can get qualitatively very different image distortions. For this first video, I used the 8th layer because of personal preference. Note that the algorithm doesn't redo the calculation if it has already done it for a given integer; it simply copies the image from previously. At the end of this loop, I have a folder with thousands of images (30 images per second of the song). 
4) The images are compiled using FFMEG in the terminal, creating a video that appears to move in response to the beat of the song. Each time you hear the kick drum, the distortions from the deep dream algorithm are maximized.

### Click the image below to watch the video! (I made the music too) 

[![Watch the video](https://github.com/Aejohnso/Independent_Projects/blob/master/Music_Visualizer/DeepDream.png)](https://youtu.be/madgMBmzsOs)

## Second Iteration
Here's another go with different music and visuals. Code [here](https://github.com/Aejohnso/Independent_Projects/blob/master/Music_Visualizer/DeepDreamViz_v2.ipynb). Again, click the image below to watch the video.

[![Watch the video](https://github.com/Aejohnso/Independent_Projects/blob/master/Music_Visualizer/DeepDreamBlazing.png){:height="200px" width="200px"}](https://www.facebook.com/trazermusic/videos/452995825472775/)


[<img src="https://github.com/Aejohnso/Independent_Projects/blob/master/Music_Visualizer/DeepDreamBlazing.png" width="400" height="400">](https://www.facebook.com/trazermusic/videos/452995825472775/)




