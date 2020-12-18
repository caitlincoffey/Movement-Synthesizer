## Table of Contents
> We have consolidated our other pages here for ease of access.
> - [Algorithm Development](/Movement-Synthesizer/algorithms)
  >   - The algorithms and methods used to get our final output from our input data
 
> - [The Music Theory Behind the Pitch Selection and Chord Selection Algorithms](/Movement-Synthesizer/musictheory)
 >    - More detail about the music theory applications of two of our algorithms
  
> - [References](/Movement-Synthesizer/references)
 >    - A list of resources our team referenced when creating this project
 
> - [About the Team](/Movement-Synthesizer/about)
 >    - More information about the team behind the project (Ale and Caitlin)


# About The Project

Imagine having a new musical instrument easily acessible from your phone that encourages movement, different dance moves, and a love for experimentation. Our project idea aims to fulfill this part of people’s lives by taking accelerometer data from a smartphone and manipulating these incoming signals to produce vibrant, unique music relative to the person’s movement.

# Why Create Music from Movement?

For people who are indoors most or all of the day (either working at home or isolating), one might have heard of the term 'Quarantine Fatigue'. Quarantine fatigue is caused by a reduction in physical activity which affects one's mind \[[1](/Movement-Synthesizer/references)\]. According to the American Heart Association even small bursts of movement are beneficial to one’s health \[[2](/Movement-Synthesizer/references)\]. By having the collection of the information be tied to a smartphone, it allows flexibility on the user’s behalf. End users can collect the data while running, walking, or even standing. To encourage movement, the longer someone moves, the longer the song will be!

In addition, even if the music isn’t a Mozart worthy masterpiece, having a low level of background music can help boost creativity in one’s endeavors \[[3](/Movement-Synthesizer/references)\]. According to the Harvard Medical School, “music can enhance the function of neural networks, slow the heart rate, lower blood pressure, and reduce levels of stress hormones, appealing to end users who might be stressed due to their environment or other factors" \[[4](/Movement-Synthesizer/references)\]. Our team aims to combat stress whilst enhancing creativity by producing quality music that a user can listen to at any time.

Inspired by the benefits of both these exercises, our project combines them into an easily accessible smartphone program targeted towards people who are spending more time than usual indoors and sitting down (e.g. students, remote workers).

# How it Works

The Movement-Synthesizer captures acceleration from the x, y, and z axes of smartphone accelerometer data. It does so using Matlab's Sensor Data Collection App and by loading that data into a livescript on Matlab's Desktop version. In the future, this could be made into a smartphone app. 
<br>
<center>
<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/accelerometer.png" height="300" width="300">
<br>
<i>The 3 Axes of Motion Captured on the Accelerometer <a href="/Movement-Synthesizer/references">[5]</a></i>
</center>
<br>

After capturing the accelerometer data, it translates signals from the three axes into a .wav file of frequencies audible to the human ear that sound like music. This process involves some signal amplifying, frequency 'tuning', and filtering using concepts learned in class related to Fourier Transforms. We cover this process in greater detail on our [algorithms page](https://caitlincoffey.github.io/Movement-Synthesizer/algorithms). There are other topics covered as well such as music theory concepts from WIRED, a first-year Olin College course. To learn more about the music theory behind our project, click [here](https://caitlincoffey.github.io/Movement-Synthesizer/musictheory).

One of the main methods we use to do our analysis is a Fourier Transform. A Fourier Transform separates individual frequencies found in the incoming, complex signal of movement. It does so by using a series of matrix operations to transform a signal in the time domain to the frequency domain, allowing individual frequencies to be recognized. Without the use of this method, we would have been unable to manipulate and tune individual frequencies to create our music.

We use acceleration from movement along all three axes to encourage users to move their body as much as they can. The more one accelerates in each axis, the more the frequencies will vary over time. By moving frequently in all three directions, one can produce songs with more variability in sounds than by sitting still or only using one axis of movement. Our project looks at all frequencies and all possible types of motion in order to produce songs that capture the amount of variability in motion that is present.

Our project tracks acceleration, the first derivative of velocity, as one of our goals is to have users variate the way that they move. Our original project used the velocity of the person's movement (the first derivative of position), but it produced music in a less cohesive form than using acceleration. Our team recognizes that this could lead to less variation in pitch for movement that has little change in velocity yet a significant change in position, like running. When making this decision, we determined that we should emphasize using movement like dancing which usually changes in velocity frequently and requires more creativity on the user's end. Our team also made the assumption that most people in quarantine (our user group) are not getting most of their daily exercise/movement from activities like running. 

To encourage variations of movement even further, the same movement along different axes will sound different depending on the axis used. This is because of the way the incoming signals are tuned in the pitch tuning algorithm, which is explained more in detail on this [page](https://caitlincoffey.github.io/Movement-Synthesizer/algorithms). One can look at video and audio files of the shuffling (side-to-side), bumping (front-back), and jumping (up-down) movements to see/hear the difference of each axis of movement!

Additionally, to encourage greater periods of movement, we based our total number selection of frequencies so the length of the final song would approximate the length of time spent dancing. 

<br>
<center><img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/x-axissidetoside.gif" alt="Side to side movement" height="332" width="589">
<br>
<i>Side to Side Movement Captured from Smartphone Accelerometer Data</i>
<br>
<br>
<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/SidetoSide X axis fft.png" height="204" width="259.333333">  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/SidetoSide Y axis fft.png" height="204" width="259.333333"> <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/SidetoSide Z axis fft.png" height="204" width="259.333333">

<i>FFTs of Unfiltered Accelerometer Data for the X (left), Y (middle), and Z (right) Axes.</i>
<br>
<br>
<audio controls>
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/x-axissidetoside.mp3" type="audio/mpeg">Oh no! Your browser does not support the <code>audio</code> code element! </audio> 
<br>
<i>Music Generated from Side to Side Movement</i>

<br>
<br>
Most of this movement is captured on the x axis of the accelerometer. As one can hear, the pitch of the x axis changes over time to allow for a variety of chords in different octaves.

<br>
<br>
---
<br>

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/y-axisupdown.gif" alt="Up and down movement" height="332" width="589">
<br>
<i>Up and Down Movement Captured from Smartphone Accelerometer Data</i>
<br>
<br>
<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/UpDown X axis fft.png" height="204" width="259.333333">  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/UpDown Y axis fft.png" height="204" width="259.333333"> <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/UpDown Z axis fft.png" height="204" width="259.333333">

<i>FFTs of Unfiltered Accelerometer Data for the X (left), Y (middle), and Z (right) Axes.</i>
<br>
<br>
<audio controls>
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/y-axisupdown.mp3" type="audio/mpeg">Oh no! Your browser does not support the <code>audio</code> code element! </audio> 
<br>
<i>Music Generated from Up and Down Movement</i>
<br>
<br>

Most of this movement is captured on the y axis of the accelerometer. As one accelerates up and down, the pitch of the y axis changes significantly over time, allowing more of a variety of frequencies to be heard in comparison to the standing example down below. The pitch here is different from the x axis, which could be attributed to the constant 9.8 m/s^2 experienced from the normal force.

<br>
<br>
---
<br>

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/z-axisfrontback.gif" alt="Front to back movement" height="332" width="589">

<br>
<i>Front and Back Movement Captured from Smartphone Accelerometer Data</i>
<br>
<br>
<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/FrontBack X axis fft.png" height="204" width="259.333333">  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/FrontBack Y axis fft.png" height="204" width="259.333333"> <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/FrontBack Z axis fft.png" height="204" width="259.333333">

<i>FFTs of Unfiltered Accelerometer Data for the X (left), Y (middle), and Z (right) Axes.</i>
<br>
<br>
<audio controls>
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/z-axisfrontback.mp3" type="audio/mpeg">Oh no! Your browser does not support the <code>audio</code> code element! </audio> 
<br>

<i>Music Generated from Front to Back Movement</i>
<br>
<br>

Most of this movement is captured on the z axis of the accelerometer. Similar to the other examples, the pitch of the z axis variates over time. 

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

An example of a classic dance is The Macarena Dance which involves movement around all three axes. As a result of the combined movement in all three axes, there is a significant amount of variation in pitch in the generated music. This is because we are changing in velocity (e.g. direction) significantly as we are moving and the algorithm plays the frequencies in order of magnitude. You can listen to the music generated below!

<center>
<audio controls>
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/macarena_all.mp3" type="audio/mpeg">Oh no! Your browser does not support the <code>audio</code> code element! </audio> 
<br>

<i>Music Generated from the Macarena</i>
<br>
</center>

## Example 2: Standing

<br>
<center><img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/standing.jpg" height="612" width="332.8">
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
- Add more complexity to the chord selection process (for example, by using Machine Learning to select chords versus random selection)
  - Improving the current design of the chord selection algorithm would help make the music more unique and entertaining than it is right now. As of now, the chords are selected randomly. Modern music does not do this; chords are carefully selected based on at least the 5-10 previous chords. Making a complex algorithm to select the chords (rather than doing so at random) would allow the music to have more rhythm and make more sense.
  - On the other hand, randomly generated music could have some unintended benefits for artists and creators. Artists could use this random generation of music for inspiration for making contemporary/modern music rather than using the traditional approach of carefully selecting chords. We're open to any thoughts, suggestions, or ideas about this!
 
Our code is available on Github and is available for use under the MIT License. We have also put in some .mat files of data so you can start creating music right away.

# References
Our references are listed [here](https://caitlincoffey.github.io/Movement-Synthesizer/references). This is not mentioned in our references, but we would like to thank the QEA teaching team for their help and support throughout this project!

<!--- Thoughts from the lecture:
- How to make equations: [stackoverflow](https://stackoverflow.com/questions/26275645/how-to-support-latex-in-github-pages)
- For graphs, choose distinguishing colors, different line thicknesses.
- https://docs.google.com/presentation/d/1ZrCd_3JE7x1tYL_IcSek4cTsEc63TjfPzzRDT7T8hRs/edit#slide=id.gb06d338265_0_42
--->

