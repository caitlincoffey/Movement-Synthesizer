# Algorithm Development 

We have created an innovative approach towards making our music. First, we select the top peak frequencies, and manipulate them so as to allow for proper matching to tuned music notes. Then the frequencies along the X, Y, and Z axis are matched to notes, the selection of which is limited by our custom algorithm. After the matching of notes, we play the frequencies in order of initial magnitude before standardization, one chord created from the combination of one note from each axis at a time.


## Signal Manipulation and Fourier Analysis

## Selecting Peak Frequencies via Filtering in the Frequency Domain

For each axis:

 


<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca X axis fft.png" height="244.8" width="311.2" >  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Y axis fft.png" height="244.8" width="311.2"> <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Z axis fft.png" hheight="244.8" width="311.2">

A) FFTs of acclerometer data for the X (left), Y (middle), and Z (right) axes. 
## 


<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca X axis fft fs.png" height="244.8" width="311.2" >  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Y axis fft fs.png" height="244.8" width="311.2" > <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Z axis fft fs.png" height="244.8" width="311.2">

B) FFTs of accelerometer data plotted with the new frequencies corresponding to the increased sampling rate for all 3 axes
## 

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca X axis fft max.png" height="244.8" width="311.2" >  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Y axis fft max.png" height="244.8" width="311.2" > <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Z axis fft max.png" height="244.8" width="311.2">

C) Filtered FFTs showing only the local maximum frequencies for all 3 axes. 
##

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca X axis fft max selected.png" height="244.8" width="311.2" >  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Y axis fft max selected.png" height="244.8" width="311.2" > <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Z axis fft max selected.png" height="244.8" width="311.2">

D) Filtered FFTs showing only the range of highest frequencies selected for music making purposes for all 3 axes.
##

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca X axis fft max selected shifted.png" height="244.8" width="311.2">  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Y axis fft max selected shifted.png" height="244.8" width="311.2" > <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Z axis fft max selected shifted.png" height="244.8" width="311.2">

E) Filtered and Shifted FFTs with a broader range of tones, frequencies all in the audible range, and the frequencies symmetric for all 3 axes.
##

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca X axis fft max selected shifted standardized.png" height="244.8" width="311.2" >  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Y axis fft max selected shifted standardized.png" height="244.8" width="311.2" > <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Z axis fft max selected shifted standardized.png" height="244.8" width="311.2">

F) Final FFTs before Pitch Tuning Algorithm, where the magnitudes of the frequencies are all set to 100 units for all 3 axes.
##

First, the number of chords needed to create a song that lasts approximately as long as the dance was is determined. Each chord is created by using Matlab's inverse fast fourier transform `ifft()` function, and will return a signal with the same N number of points as there were used to create the original fast fourier transform (FFT). So the length of one full chord would be N divided by the sampling rate (Fs), or `N / Fs`. However, that tends to produce tones that were longer than we wanted. So, when creating our final music, we only use the first fourth of the signal produced by Matlab's `ifft()` function. As a result, the length of a single chord would be `4 * N / Fs`. As a result, to create a song approximately the length of the dance (max_time), the number of chords(Nc) would be `Nc = floor(4 * N /(Fs))`, `floor()` rounding down to the nearsest integer, as one cannot have part of a chord.

For the initial filtering of all 3 axis, a similar pattern is followed: first, we take the FFT of the signal using Matlab's `fft()` function (A). We then set the sampling rate (Fs) to be 2,000 Hz (B), as this allows for a frequency range of -1,000 to 1,000 Hz, as the `max_frequency = Fs/2`. This allows for a broad selection of tones, while avoiding some higher, harsher tones, that some listeners have found unpleasant during the development of this product. 

Then, all the peak frequencies are found, defined as a local maxima preceded by a value at least 1 unit less than itself (C). The top Nc positive peak frequencies are selected, and then mirrored horizontally, to avoid clashing phaseshifts caused by not perfectly symmetric FFTs(D).

Then we spread out and shift the frequencies to broaden the range of possible tones, as well as to ensure all of them are in the audible domain. This is done by finding each frequencies' index's distance from the 0 frequency, multiplying the distance by 2 (if the max peak frequency is less than half the max potential frequency), and increasing the distance by 20(E). Lastly, all the magnitudes are standardized, set to 100 unit lengths to enable proper translation of frequency range during audiofile writing(F).


## Pitch Tuning Algorithm / Chord Selection Process

### Pitch Tuning Algorithm

For the purpose of making specific music chords that sound 'pleasing' to the human ear, the x axis has been set up to be the 'base' or the 'root' note. The y and z axes are tuned accordingly to the 'root' note and a randomly selected chord based on some aspect of the root note. This selection produces chords that sound pleasing to the human ear according to a study done at Penn State's Department of Music \[[5](https://sites.psu.edu/siowfa15/2015/09/16/what-makes-chords-sound-good/)\]. On the other hand this also allows for some flexibility in pitch for the y and z axes, as our project goal is to inspire users to create their own unique sounds from experimentation with movement. Regardless, an increase in acceleration in any axis will result in an increase in frequency in the respective axis of movement. In music terms, this will increase the pitch of the notes being played. Likewise, a decrease in acceleration will result in a decrease in frequency in the respective axes of movement. To add variance to the pitch of the chords, the user should move frequently and move around in all three directions of motion.

To tune each frequency from movement to a respective piano note, the pitch tuning algorithm finds the lowest distance between each frequency of movement and the piano frequencies and replaces the frequency from movement with the respective piano note. The lowest distance can be impacted for the y and z axes depending on the chord selected. When these restrictions apply, the piano frequencies that do not line up with the selected chord (e.g notes that are not present in that chord) are not considered when finding the lowest distance between the frequencies from movement and the piano frequencies. 

If you want to look more at the music theory behind the frequencies of Western music and the pitch tuning algorithm, please read more [here](https://caitlincoffey.github.io/Movement-Synthesizer/musictheory).


### Chord Selection Process

There are six chords that can be selected at any given time. The process of selecting a chord is randomized so that the generated music does not sound repetitive. This design decision was made only after experimenting with the chord selection being attached to other variables such as the note of the y axis or z axis; we found that when there was little movement around either axis the generated music played the same three notes repeatedly, even if the movement pattern was similar to a person walking. 

 <table style="width:100%">
  <tr>
    <th>First Option (Base Note)</th>
    <th>base_note</th>
    <th>base_note</th>
    <th>base_note</th>
    <td>base_note+2</td>
    <td>base_note+2</td>
    <td>base_note+4</td>
  </tr>
  <tr>
    <td>Second Option (Major/Minor 3rd)</td>
    <th>base_note+4</th>
    <th>base_note+4</th>
    <th>base_note+5</th>
    <td>base_note+5</td>
    <td>base_note+7</td>
    <td>base_note+7</td>
  </tr>
  <tr>
    <td>Third Option (Perfect 5th)</td>
    <th>base_note+7</th>
    <th>base_note+9</th>
    <th>base_note+9</th>
    <td>base_note+9</td>
    <td>base_note+11</td>
    <td>base_note+11</td>
  </tr>
</table> 

<i>Table of All Possible Chords</i>

Based off the chord selected at random and the incoming frequency from the x axis, there are three possible note choices (integers) to select for both the y and z axes. These three integers correspond to the notes needed to produce the selected chord in the 12-tone Western music scale. 

If you want to look more at the music theory behind what a chord is and the chord selection process, please read more [here](https://caitlincoffey.github.io/Movement-Synthesizer/musictheory).


## Playing Back the Music 

Add Frequency Plot Here
Add Music Here
-  We then play the frequencies in order of initial magnitude before standardization, one chord created from the combination of one note from each axis at a time.



