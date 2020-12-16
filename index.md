# About The Project

Imagine having a new musical instrument from your phone that encourages movement, different dance moves, and a love for experimentation. Our project idea aims to fill this potential hole in people’s lives by taking accelerometer data from a smartphone and manipulating these incoming signals to produce vibrant, unique music relative to the person's movement.

# Why Create Music from Movement?

For people who are indoors most or all of the day (either working at home or isolating), one might have heard of the term 'Quarantine Fatigue'. Quarantine fatigue is caused by a reduction in physical activity which affects one's mind \[[1](/Movement-Synthesizer/references)\]. According to the American Heart Association even small bursts of movement are beneficial to one’s health \[[2](/Movement-Synthesizer/references)\]. By having the collection of the information be tied to a smartphone, it allows flexibility on the user’s behalf. End users can collect the data while running, walking, or even standing. To encourage movement, the longer someone moves, the longer the song will be!

In addition, even if the music isn’t a Mozart worthy masterpiece, having a low level of background music can help boost creativity in one’s endeavors \[[3](/Movement-Synthesizer/references)\]. According to the Harvard Medical School, “music can enhance the function of neural networks, slow the heart rate, lower blood pressure, and reduce levels of stress hormones, appealing to end users who might be stressed due to their environment or other factors \[[4](/Movement-Synthesizer/references)\]. 

Inspired by the benefits of both these exercises, our project combines them into an easily accessible smartphone program targetted towards people who are spending more time than usual indoors and sitting down (e.g. students, remote workers).

# How it Works

The Movement-Synthesizer captures motion from the x, y, and z coordinates of smartphone accelerometer data. In return, it translates signals from those three axes into a .wav file of frequencies audible to the human ear that sound like tuned music chords. This process involves some signal amplifying, frequency 'tuning', and filtering using concepts learned in class related to Fourier Transforms. There are other topics covered as well such as music theory from WIRED, a first-year Olin Music course. 

We looked at three primary movements to encourage users to move their body as much as they can: shuffling (side-to-side), bumping (front-back), and jumping (up-down).

<center><img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/x-axissidetoside.gif" alt="Side to side movement" height="332" width="589">

<i>Side to Side Movement on the X Axis Captured from Smartphone Accelerometer Data</i>

<audio controls>
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/x-axissidetoside.mp3" type="audio/mpeg">Oh no! Your browser does not support the <code>audio</code> code element! </audio> 
  
<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/y-axisupdown.gif" alt="Up and down movement" height="332" width="589">

<i>Up and Down Movement on the Y Axis Captured from Smartphone Accelerometer Data</i>

<audio controls> 
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/y-axisupdown.mp3" type="audio/mpeg"></audio> 

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/z-axisfrontback.gif" alt="Front to back movement" height="332" width="589">

<i>Front and Back Movement on the Z Axis Captured from Smartphone Accelerometer Data</i>

<audio controls> 
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/z-axisfrontback.mp3" type="audio/mpeg"></audio>
</center>

For the purpose of making specific music chords that sound 'pleasing' to the human ear, the x axis has been set up to be the 'base' or the 'root' note. The y and z axes are tuned accordingly to the 'root' note and a randomly selected chord based on some aspect of the root note. This selection produces chords that sound pleasing to the human ear according to a study done at Penn State's Department of Music \[[5](https://sites.psu.edu/siowfa15/2015/09/16/what-makes-chords-sound-good/)\]. On the other hand this also allows for some flexibility in pitch for the y and z axes, as our project goal is to inspire users to create their own unique sounds from experimentation with movement. Regardless, an increase in acceleration in any axis will result in an increase in frequency in the respective axis of movement. In music terms, this will increase the pitch of the notes being played. Likewise, a decrease in acceleration will result in a decrease in frequency in the respective axes of movement. To add variance to the pitch of the chords, the user should move frequently and move around in all three directions of motion.



- Talk about motion model 
- Talk about sound, separate x, y, and z axes into different sound files

### Signal Manipulation and Fourier Analysis

Selecting Peak Frequencies via Filtering in the Frequency Domain
•	Selecting start and stop index for duration of dance
•	Increasing sampling rate to allow potential frequency range occupation of pleasant auditory reception.
•	Identify peak positive frequencies using max positive selection and calculating distance from zero, broadening the range of tones and shifting the frequencies into the audible domain, then employing a horizontal reflection. 
•	Standardizing the magnitude of the frequency for proper translation of frequency range during audio file writing. 


### Pitch Tuning Algorithm / Chord Selection Algorithm 

To tune each frequency from movement to a respective piano note, the Pitch Tuning algorithm finds the lowest distance between each frequency of movement and the piano frequencies and replaces the frequency from movement with the respective piano note. The lowest distance can be impacted for the y and z axes depending on the chord selected. When these restrictions apply, the piano frequencies that do not line up with the selected chord (e.g the note is not present in that chord) are not considered when finding the lowest distance between the frequencies from movement and the piano frequencies. 

The chord selection is randomized so that the generated music does not sound repetitive. This design decision was made only after experimenting with the chord selection being attached to other variables such as the note of the y axis or z axis; we found that when there was little movement around either axis the generated music played the same three notes repeatedly, even if the movement pattern was similar to a person walking.

If you want to look more at the music theory behind the Pitch Tuning algorithm and the Chord Selection algorithm, please read more [here](https://caitlincoffey.github.io/Movement-Synthesizer/musictheory).


### Playing Back the Music 


## Example 1: The Renegade Dance (from Tiktok)

- Add graphs, add video of movement

This dance involves a lot of movement around all three axes. Notably, however, there are repeated movements in _ directions. There are notable variations in pitch in these directions with a slight variation in pitch in the other direction because of this pattern of movement. You can listen to the music generated below!

## Example 2: Standing

- Add graphs, add video of movement

Although it might appear to be silly to use this example, standing is technically considered movement. Standing, as mentioned earlier, does provide some benefits to one's health \[[2](/Movement-Synthesizer/references)\]. 

# References
Our references are listed [here](https://caitlincoffey.github.io/Movement-Synthesizer/references). This is not mentioned in our references, but we would like to thank the QEA teaching team for their help and support throughout this project!

<!--- Thoughts from the lecture:
- Do MLA citations and have perhaps a separate references page. 
- [1] inline citations, whenever you're taking information from a reference you should use it. Note that inline citations should be at the end of the sentence, like this [1].
- How to make equations: [stackoverflow](https://stackoverflow.com/questions/26275645/how-to-support-latex-in-github-pages)
- For graphs, choose distinguishing colors, different line thicknesses.
- https://docs.google.com/presentation/d/1ZrCd_3JE7x1tYL_IcSek4cTsEc63TjfPzzRDT7T8hRs/edit#slide=id.gb06d338265_0_42
Value Creation
The proof-of-concept supports a specific user group(s) in clearly defined ways. The connection between the proof-of-concept and the user group is clear, and based on existing research and/or a strong understanding of particular areas of opportunity.
This criterion is linked to a Learning Outcome Motion Model
Your motion model should demonstrated a clear understanding of the dynamics of your motion, the degrees of freedom and their time derivatives, and the important frequencies. You should explain how your model informed your data collection, and what, if any, modifications were made to the model following experimentation.
This criterion is linked to a Learning Outcome Proof-of-Concept
The proof-of-concept should include a selection of sensors that are appropriate for the specific application. The experiment(s) should demonstrate some aspect of how the product would work in reality. Next steps for the proof-of-concept (e.g. additional experiments, changes to the design) should be well articulated.
This criterion is linked to a Learning Outcome Algorithm Development
The algorithm(s) for data analysis should demonstrate a clear understanding of Fourier analysis, frequency and time domains, and motion model dynamics. The project website should clearly explain the application of the algorithm to the experimental data through the use of appropriate equations and graphics.
This criterion is linked to a Learning Outcome Overall Presentation and Delivery of Information
The website is professional and well-organized. The information is clear, easy to understand, and appropriate for the intended audience.
--->
