## Table of Contents
> Here is a consolidation of pages on our website for ease of access.
> - [Algorithm Development](/Movement-Synthesizer/algorithms)
  >   - The algorithms and methods used to get our final output from our input data
 
> - [The Music Theory Behind the Pitch Selection and Chord Selection Algorithms](/Movement-Synthesizer/musictheory)
 >  - More detail about the music theory applications of two of our algorithms
  
> - [References](/Movement-Synthesizer/references)
 >  - A list of resources our team referenced when creating this project


# About The Project

Imagine having a new musical instrument from your phone that encourages movement, different dance moves, and a love for experimentation. Our project idea aims to fill this potential hole in people’s lives by taking accelerometer data from a smartphone and manipulating these incoming signals to produce vibrant, unique music relative to the person's movement.

# Why Create Music from Movement?

For people who are indoors most or all of the day (either working at home or isolating), one might have heard of the term 'Quarantine Fatigue'. Quarantine fatigue is caused by a reduction in physical activity which affects one's mind \[[1](/Movement-Synthesizer/references)\]. According to the American Heart Association even small bursts of movement are beneficial to one’s health \[[2](/Movement-Synthesizer/references)\]. By having the collection of the information be tied to a smartphone, it allows flexibility on the user’s behalf. End users can collect the data while running, walking, or even standing. To encourage movement, the longer someone moves, the longer the song will be!

In addition, even if the music isn’t a Mozart worthy masterpiece, having a low level of background music can help boost creativity in one’s endeavors \[[3](/Movement-Synthesizer/references)\]. According to the Harvard Medical School, “music can enhance the function of neural networks, slow the heart rate, lower blood pressure, and reduce levels of stress hormones, appealing to end users who might be stressed due to their environment or other factors" \[[4](/Movement-Synthesizer/references)\]. Our team aims to combat stress and enhance creativity by producing quality music that a user can listen to at any time.

Inspired by the benefits of both these exercises, our project combines them into an easily accessible smartphone program targetted towards people who are spending more time than usual indoors and sitting down (e.g. students, remote workers).

# How it Works

The Movement-Synthesizer captures acceleration from the x, y, and z axes of smartphone accelerometer data. In return, it translates signals from those three axes into a .wav file of frequencies audible to the human ear that sound like music. This process involves some signal amplifying, frequency 'tuning', and filtering using concepts learned in class related to Fourier Transforms. There are other topics covered as well such as music theory concepts from WIRED, a first-year Olin College course. To learn more about the music theory behind our project, click [here](https://caitlincoffey.github.io/Movement-Synthesizer/musictheory).

We incorportate information from movement along all three axes to encourage users to move their body as much as they can. To encourage variations of movement even further, the same movement along different axes will sound different depending on the axis. This is because of __________. One can look at video and audio files of the shuffling (side-to-side), bumping (front-back), and jumping (up-down) movements to see/hear the difference of each axis of movement!

Additionally, to encourage greater periods of movement, we based our total number selection of frequencies so the length of the final song would approximate the length of time spent dancing. 

<br>
<center><img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/x-axissidetoside.gif" alt="Side to side movement" height="332" width="589">
<br>
<i>Side to Side Movement Captured from Smartphone Accelerometer Data</i>

<br>
<audio controls>
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/side_to_side_all.mp3" type="audio/mpeg">Oh no! Your browser does not support the <code>audio</code> code element! </audio> 
<br>

<i>Music Generated from Side to Side Movement</i>

Most of this movement is captured on the x axis of the accelerometer. As one can hear, the pitch of the x axis changes over time to allow for a variety of chords in different octaves.

<br>
---
<br>

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/y-axisupdown.gif" alt="Up and down movement" height="332" width="589">
<br>
<i>Up and Down Movement Captured from Smartphone Accelerometer Data</i>

Most of this movement is captured on the y axis of the accelerometer. As one accelerates up and down, the pitch of the y axis changes significantly over time, allowing more of a variety of frequencies to be heard in comparison to the standing example down below. The pitch here is different from the x axis, which could be attributed to the constant 9.8 m/s^2 experienced from the normal force.

<br>
<audio controls> 
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/up_down_all.mp3" type="audio/mpeg"></audio> 
<br>

<i>Music Generated from Side to Side Movement</i>

<br>
---
<br>

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/z-axisfrontback.gif" alt="Front to back movement" height="332" width="589">

<br>
<i>Front and Back Movement Captured from Smartphone Accelerometer Data</i>

Most of this movement is captured on the z axis of the accelerometer. Similar to the other examples, the pitch of the z axis variates over time. 

<br>
<audio controls> 
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/front_back_all.mp3" type="audio/mpeg"></audio>
<br>

<i>Music Generated from Side to Side Movement</i>

<br>
</center>


# Examples of Movement

## Example 1: The Macarena 

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/macarena.gif">

- Add graphs of accelerometer data, FFTs, music

This dance involves a lot of movement around all three axes. As a result of the combined movement in all three axes, there is a significant amount of variation in pitch in the generated music. You can listen to the music generated below!

- Add music

## Example 2: Standing

- Add graphs of acccelerometer data, FFTs, music, add video of movement

Although it might appear to be silly to use this example, standing is technically considered movement. Standing, as mentioned earlier, does provide some benefits to one's health \[[2](/Movement-Synthesizer/references)\]. Standing requires relatively little movement in comparison to the previous example. You can listen to the music generated below!

- Add music

# References
Our references are listed [here](https://caitlincoffey.github.io/Movement-Synthesizer/references). This is not mentioned in our references, but we would like to thank the QEA teaching team for their help and support throughout this project!

<!--- Thoughts from the lecture:
- How to make equations: [stackoverflow](https://stackoverflow.com/questions/26275645/how-to-support-latex-in-github-pages)
- For graphs, choose distinguishing colors, different line thicknesses.
- https://docs.google.com/presentation/d/1ZrCd_3JE7x1tYL_IcSek4cTsEc63TjfPzzRDT7T8hRs/edit#slide=id.gb06d338265_0_42
--->

