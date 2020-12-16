# Algorithm Development 

## Signal Manipulation and Fourier Analysis

## Selecting Peak Frequencies via Filtering in the Frequency Domain

Insert Figure with subplots A-F Here
A) <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca X axis fft.png">  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Y axis fft.png"> <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Z axis fft.png">


For each axis:
-	Selecting start and stop index for duration of dance, and taking an FFT via Matlab's fft function (A). 
-	Increasing sampling rate to allow potential frequency range occupation of pleasant auditory reception (B).
-	Identify peak positive frequencies using local max positive selection (C), selecting the greatest values (D), and calculating distance from zero, broadening the range of tones and shifting the frequencies into the audible domain, then employing a horizontal reflection (E). 
-	Standardizing the magnitude of the frequency for proper translation of frequency range during audio file writing (F). 


## Pitch Tuning Algorithm / Chord Selection Process

### Pitch Tuning Algorithm

For the purpose of making specific music chords that sound 'pleasing' to the human ear, the x axis has been set up to be the 'base' or the 'root' note. The y and z axes are tuned accordingly to the 'root' note and a randomly selected chord based on some aspect of the root note. This selection produces chords that sound pleasing to the human ear according to a study done at Penn State's Department of Music \[[5](https://sites.psu.edu/siowfa15/2015/09/16/what-makes-chords-sound-good/)\]. On the other hand this also allows for some flexibility in pitch for the y and z axes, as our project goal is to inspire users to create their own unique sounds from experimentation with movement. Regardless, an increase in acceleration in any axis will result in an increase in frequency in the respective axis of movement. In music terms, this will increase the pitch of the notes being played. Likewise, a decrease in acceleration will result in a decrease in frequency in the respective axes of movement. To add variance to the pitch of the chords, the user should move frequently and move around in all three directions of motion.

To tune each frequency from movement to a respective piano note, the pitch tuning algorithm finds the lowest distance between each frequency of movement and the piano frequencies and replaces the frequency from movement with the respective piano note. The lowest distance can be impacted for the y and z axes depending on the chord selected. When these restrictions apply, the piano frequencies that do not line up with the selected chord (e.g notes that are not present in that chord) are not considered when finding the lowest distance between the frequencies from movement and the piano frequencies. 

If you want to look more at the music theory behind the frequencies of Western music and the pitch tuning algorithm, please read more [here](https://caitlincoffey.github.io/Movement-Synthesizer/musictheory).

### Chord Selection Process

The process of selecting a chord is randomized so that the generated music does not sound repetitive. This design decision was made only after experimenting with the chord selection being attached to other variables such as the note of the y axis or z axis; we found that when there was little movement around either axis the generated music played the same three notes repeatedly, even if the movement pattern was similar to a person walking.

If you want to look more at the music theory behind what a chord is and the chord selection process, please read more [here](https://caitlincoffey.github.io/Movement-Synthesizer/musictheory).


## Playing Back the Music 

Add Frequency Plot Here
Add Music Here
-  We then play the frequencies in order of initial magnitude before standardization, one chord created from the combination of one note from each axis at a time.



