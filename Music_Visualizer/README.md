# Homemade Music Visualizer

This repository hosts all files related to my development of music visualizers, inspired by [this](https://github.com/Hvass-Labs/TensorFlow-Tutorials/blob/master/14_DeepDream.ipynb) code.

Beta version of my code [here](https://github.com/Aejohnso/Independent_Projects/blob/master/Music_Visualizer/DeepDreamViz.ipynb).

## Progress

I have created a code that does the following steps:
1) Imports a song and creates a spectogram of the song using the package pylab. This fourier transform gives us the intensity (volume) of each frequency at each timestep in the song.
2) The spectogram is analyzed to find the intensity of the song between the frequency range 0-120Hz. This range corresponds to the kick drum. This intensity, which has a value for each of the 30 frames per second, is converted to an integer between 1 and 20.
3) The integer is used as input into the [deep dream algorithm](https://github.com/Hvass-Labs/TensorFlow-Tutorials/blob/master/14_DeepDream.ipynb). The higher the integer, the deeper the image transcends into deep dream space. Depending on which layer of the neural network is chosen, you can get qualitatively very different image distortions. For this first video, I used the 8th layer because of personal preference. Note that the algorithm doesn't redo the calculation if it has already done it for a given integer; it simply copies the image from previously. At the end of this loop, I have a folder with thousands of images (30 images per second of the song).
4) The images are compiled using FFMEG in the terminal, creating a final video.

