## Table of Contents
> We have consolidated our other pages here for ease of access.
> - [Algorithm Development](/Movement-Synthesizer/algorithms)
  >   - The algorithms and methods used to get our final output from our input data
 
> - [The Music Theory Behind the Pitch Selection and Chord Selection Algorithms](/Movement-Synthesizer/musictheory)
 >    - More detail about the music theory applications of two of our algorithms
  
> - [References](/Movement-Synthesizer/references)
 >    - A list of resources our team referenced when creating this project


# About The Project

Imagine having a new musical instrument from your phone that encourages movement, different dance moves, and a love for experimentation. Our project idea aims to fill this potential hole in people’s lives by taking accelerometer data from a smartphone and manipulating these incoming signals to produce vibrant, unique music relative to the person's movement.

# Why Create Music from Movement?

For people who are indoors most or all of the day (either working at home or isolating), one might have heard of the term 'Quarantine Fatigue'. Quarantine fatigue is caused by a reduction in physical activity which affects one's mind \[[1](/Movement-Synthesizer/references)\]. According to the American Heart Association even small bursts of movement are beneficial to one’s health \[[2](/Movement-Synthesizer/references)\]. By having the collection of the information be tied to a smartphone, it allows flexibility on the user’s behalf. End users can collect the data while running, walking, or even standing. To encourage movement, the longer someone moves, the longer the song will be!

In addition, even if the music isn’t a Mozart worthy masterpiece, having a low level of background music can help boost creativity in one’s endeavors \[[3](/Movement-Synthesizer/references)\]. According to the Harvard Medical School, “music can enhance the function of neural networks, slow the heart rate, lower blood pressure, and reduce levels of stress hormones, appealing to end users who might be stressed due to their environment or other factors" \[[4](/Movement-Synthesizer/references)\]. Our team aims to combat stress and enhance creativity by producing quality music that a user can listen to at any time.

Inspired by the benefits of both these exercises, our project combines them into an easily accessible smartphone program targetted towards people who are spending more time than usual indoors and sitting down (e.g. students, remote workers).

# How it Works

The Movement-Synthesizer captures acceleration from the x, y, and z axes of smartphone accelerometer data. It does so using Matlab's Sensor Data Collection App and by loading that data into a livescript on Matlab's Desktop version. In the future, this could be made into a smartphone app. 
<br>
<center>
<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/accelerometer.png" height="300" width="300">
<br>
<i>The 3 Axes of Motion Captured on the Accelerometer <a href="/Movement-Synthesizer/references">[5]</a></i>
</center>
<br>

After capturing the accelerometer data, it translates signals from the three axes into a .wav file of frequencies audible to the human ear that sound like music. This process involves some signal amplifying, frequency 'tuning', and filtering using concepts learned in class related to Fourier Transforms. There are other topics covered as well such as music theory concepts from WIRED, a first-year Olin College course. To learn more about the music theory behind our project, click [here](https://caitlincoffey.github.io/Movement-Synthesizer/musictheory).

We use information from movement along all three axes to encourage users to move their body as much as they can. Furthermore, the more one accelerates in each axis the more the frequencies will vary over time. By moving frequently in all three directions, one can produce songs with more variability in sounds than by sitting still or only using one axis of movement. Our project looks at all frequencies and all possible types of motion in order to produce songs that capture the amount of variability in motion that is present.

To encourage variations of movement even further, the same movement along different axes will sound different depending on the axis used. This is because of the way the incoming signals are tuned in the pitch tuning algorithm, which is explained more in detail on this [page](https://caitlincoffey.github.io/Movement-Synthesizer/algorithms). One can look at video and audio files of the shuffling (side-to-side), bumping (front-back), and jumping (up-down) movements to see/hear the difference of each axis of movement!

Additionally, to encourage greater periods of movement, we based our total number selection of frequencies so the length of the final song would approximate the length of time spent dancing. 

<br>
<center><img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/x-axissidetoside.gif" alt="Side to side movement" height="332" width="589">
<br>
<i>Side to Side Movement Captured from Smartphone Accelerometer Data</i>

<br>
<audio controls>
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/side_to_side_all.mp3" type="audio/mpeg">Oh no! Your browser does not support the <code>audio</code> code element! </audio> 
<br>
<br>

<i>Music Generated from Side to Side Movement</i>

<br>
<br>
Most of this movement is captured on the x axis of the accelerometer. As one can hear, the pitch of the x axis changes over time to allow for a variety of chords in different octaves.

<br>
---
<br>

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/y-axisupdown.gif" alt="Up and down movement" height="332" width="589">
<br>
<i>Up and Down Movement Captured from Smartphone Accelerometer Data</i>
<br>
Most of this movement is captured on the y axis of the accelerometer. As one accelerates up and down, the pitch of the y axis changes significantly over time, allowing more of a variety of frequencies to be heard in comparison to the standing example down below. The pitch here is different from the x axis, which could be attributed to the constant 9.8 m/s^2 experienced from the normal force.

<br>
<audio controls> 
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/up_down_all.mp3" type="audio/mpeg"></audio> 
<br>
<br>

<i>Music Generated from Side to Side Movement</i>

<br>
<br>
---
<br>

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/z-axisfrontback.gif" alt="Front to back movement" height="332" width="589">

<br>
<i>Front and Back Movement Captured from Smartphone Accelerometer Data</i>
<br>
Most of this movement is captured on the z axis of the accelerometer. Similar to the other examples, the pitch of the z axis variates over time. 

<br>
<audio controls> 
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/front_back_all.mp3" type="audio/mpeg"></audio>
<br>
<br>

<i>Music Generated from Side to Side Movement</i>

<br>
<br>
</center>


# Examples of Movement

## Example 1: The Macarena 

<br>
<center>
<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/macarena.gif">
<br>
<i>The Macarena Dance Captured on the Accelerometer</i>
</center>

This dance involves movement around all three axes. As a result of the combined movement in all three axes, there is a significant amount of variation in pitch in the generated music. You can listen to the music generated below!

<center>
<audio controls>
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/macarena_all.mp3" type="audio/mpeg">Oh no! Your browser does not support the <code>audio</code> code element! </audio> 
<br>

<i>Music Generated from the Macarena</i>
<br>
</center>

## Example 2: Standing

<br>
<center><img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/standing.jpg">
<br>
<i>Standing Movement Captured on the Accelerometer</i>
<br>
</center>


Although it might appear to be silly to use this example, standing is technically considered movement. Standing, as mentioned earlier, does provide some benefits to one's health \[[2](/Movement-Synthesizer/references)\]. Standing requires relatively little movement in comparison to the previous example. You can listen to the music generated below here!

<center>
<audio controls>
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/standing_all.mp3" type="audio/mpeg">Oh no! Your browser does not support the <code>audio</code> code element! </audio> 
<br>

<i>Music Generated from Standing</i>
<br>
</center>
<br>

# Contributing

As of now, the Movement Synthesizer lives on a Matlab livescript, and there is not an immediate path to get the accelerometer data onto the livescript. Additionally, the livescript runs manually (e.g. it will not run automatically after receiving new data). To make this project more accessible to users, these are the next steps our team (or you!) can take: 

- Create a smartphone app (Android + IOS) that gathers accelerometer data and uses the algorithms mentioned in the [Algorithm Development](/Movement-Synthesizer/algorithms) to process the data
- Test the algorithm on specific patterns of behavior, such as marching
- Add more complexity to the chord selection process (perhaps using Machine Learning to select chords rather than at random?)
  - Improving the current design of the chord selection algorithm would help make the music more unique and entertaining than it is right now. As of now, the chords are selected randomly. Modern music does not do this; chords are carefully selected based on at least the 5-10 previous chords. Making a complex algorithm to select the chords (rather than doing so at random) would allow the music to have more rhythm and make more sense. 

# References
Our references are listed [here](https://caitlincoffey.github.io/Movement-Synthesizer/references). This is not mentioned in our references, but we would like to thank the QEA teaching team for their help and support throughout this project!

<!--- Thoughts from the lecture:
- How to make equations: [stackoverflow](https://stackoverflow.com/questions/26275645/how-to-support-latex-in-github-pages)
- For graphs, choose distinguishing colors, different line thicknesses.
- https://docs.google.com/presentation/d/1ZrCd_3JE7x1tYL_IcSek4cTsEc63TjfPzzRDT7T8hRs/edit#slide=id.gb06d338265_0_42
--->

