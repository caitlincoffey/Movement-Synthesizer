# Algorithm Development 

We have created an innovative approach towards making our music. First, we select the top peak frequencies, and manipulate them to allow for proper matching to tuned music notes. Then the frequencies along the x, y, and z axes are matched to notes, the selection of which is limited by our custom algorithm. Then, we play the frequencies in order of initial magnitude before standardization, one chord created from the combination of one note from each axis at a time; this was a direct way of implementing interesting music in MATLAB.

This sets the basis for our future directions, where we hope to temporally synchronise the movement inputs with the music outputs.

Below, these algorithms are explained in greater detail, while visualizing the process through the Macarena dance.

## Signal Manipulation and Fourier Analysis

## Selecting Peak Frequencies via Filtering in the Frequency Domain

First, the number of chords needed to create a song that lasts approximately as long as the dance is calculated. Each chord is created by using MATLAB's inverse fast Fourier transform `ifft()` function, and will return a signal with the same N number of points as there were used to create the original fast Fourier transform (FFT). Therefore, the length of one full chord would be N divided by the sampling rate (Fs), or `N / Fs`. However, that tends to produce tones that were longer than we wanted. So, when creating our final music, we only use the first fourth of the signal produced by MATLAB's `ifft()` function. As a result, the length of a single chord would be `4 * N / Fs`. In summary, to create a song approximately the length of the dance (max_time), the number of chords (Nc) would be `Nc = floor(4 * N /(Fs))`, `floor()` rounding down to the nearest integer, as one cannot have part of a chord.

For the initial filtering of all 3 axes, a similar pattern is followed: first, we take the FFT of the signal using MATLAB's `fft()` function.

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca X axis fft.png" height="204" width="259.333333">  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Y axis fft.png" height="204" width="259.333333"> <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Z axis fft.png" height="204" width="259.333333">

<i>A) FFTs of accelerometer data for the x (left), y (middle), and z (right) axes. </i>
<br>
<br>
<br>
We then set the sampling rate (Fs) to be 2,000 Hz, as this allows for a frequency range of -1,000 to 1,000 Hz, as the `max_frequency = Fs/2`. This allows for a broad selection of tones, while avoiding some higher, harsher tones, that some listeners have found unpleasant during the development of this product. 

<br>

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca X axis fft fs.png" height="204" width="259.333333">  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Y axis fft fs.png" height="204" width="259.333333"> <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Z axis fft fs.png" height="204" width="259.333333">

<i>B) FFTs of accelerometer data plotted with the new frequencies corresponding to the increased sampling rate for all 3 axes</i>
<br>
<br>
<br>
Then, all the peak frequencies are found, defined as a local maxima preceded by a value at least 1 unit less than itself (C). 
<br>

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca X axis fft max.png" height="204" width="259.333333">  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Y axis fft max.png" height="204" width="259.333333"> <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Z axis fft max.png" height="204" width="259.333333">

<i>C) Filtered FFTs showing only the local maximum frequencies for all 3 axes. </i>
<br>
<br>
<br>
The top Nc positive peak frequencies are selected, and then mirrored horizontally, to avoid clashing phase shifts caused by not perfectly symmetric FFTs.

<br>

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca X axis fft max selected.png" height="204" width="259.333333">  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Y axis fft max selected.png" height="204" width="259.333333"> <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Z axis fft max selected.png" height="204" width="259.333333">

<i>D) Filtered FFTs showing only the range of highest frequencies selected for music making purposes for all 3 axes.</i>
<br>
<br>
<br>
Then we spread out and shift the frequencies to broaden the range of possible tones, as well as to ensure all of them are in the audible domain. This is done by finding each frequencies' index's distance from the 0 frequency and multiplying the distance by 2 (if the max peak frequency is less than half the max potential frequency) to increase the range of tones. We then increase the distance by 10; which would shift all signals over 25 Hz, 5 Hz above the lower limit of humans' audible range \[[3](www.jstor.org/stable/10.1086/665048)\].
<br>
<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca X axis fft max selected shifted.png" height="204" width="259.333333">  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Y axis fft max selected shifted.png" height="204" width="259.333333"> <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Z axis fft max selected shifted.png" height="204" width="259.333333">

<i>E) Filtered and Shifted FFTs with a broader range of tones, frequencies all in the audible range, and the frequencies symmetric for all 3 axes.</i>
<br>
<br>
<br>
Lastly, all the magnitudes are standardized, set to 100 unit lengths to enable proper translation of frequency range during audio file writing.
<br>
<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca X axis fft max selected shifted standardized.png" height="204" width="259.333333">  <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Y axis fft max selected shifted standardized.png" height="204" width="259.333333"> <img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Z axis fft max selected shifted standardized.png" height="204" width="259.333333">

<i>F) Final FFTs before Pitch Tuning Algorithm, where the magnitudes of the frequencies are all set to 100 units for all 3 axes.</i>


## Pitch Tuning Algorithm / Chord Selection Process

### Pitch Tuning Algorithm

For the purpose of making specific music chords that sound 'pleasing' to the human ear, the x axis has been set up to be the 'base' or the 'root' note. The y and z axes are tuned accordingly to the 'root' note and a randomly selected chord based on some aspect of the root note. This selection produces chords that sound pleasing to the human ear according to a study done at Penn State's Department of Music \[[5](https://sites.psu.edu/siowfa15/2015/09/16/what-makes-chords-sound-good/)\]. On the other hand, this also allows for some flexibility in pitch for the y and z axes, as our project goal is to inspire users to create their own unique sounds from experimentation with movement. Regardless, an increase in acceleration in any axis will result in an increase in frequency in the respective axis of movement. In music terms, this will increase the pitch of the notes being played. Likewise, a decrease in acceleration will result in a decrease in frequency in the respective axes of movement. To add variance to the pitch of the chords, the user should move frequently and move around in all three directions of motion.

To tune each frequency from movement to a respective piano note, the pitch tuning algorithm finds the lowest distance between each frequency of movement and the piano frequencies and replaces the frequency from movement with the respective piano note. The lowest distance can be impacted for the y and z axes depending on the chord selected. When these restrictions apply, the piano frequencies that do not line up with the selected chord (i.e. notes that are not present in that chord) are not considered when finding the lowest distance between the frequencies from movement and the piano frequencies. 

For the X axis, the base note is determined by finding the remainder of the index selected for the music note divided by 12 (`mod(music_note_index, 12)`), and setting all values where the base note is 0 to 12, to ensure compatibility with MATLAB's indexing. After an initial base note has been selected, the next frequency is selected by first matching the frequency to the closest octave value of the base note, then allowing it to either remain as is, increase by 5 notes, or decrease by 5 notes.

For the y and z axes, the frequencies are matched to the closest value for all octaves of three different notes. Those are determined by the chord selection process below and are based off of the corresponding x base note.

If you want to look more at the music theory behind the frequencies of Western music and the pitch tuning algorithm, please read more [here](https://caitlincoffey.github.io/Movement-Synthesizer/musictheory).


### Chord Selection Process

There are six chords that can be selected at any given time. The process of selecting a chord is randomized so that the generated music does not sound repetitive. This design decision was made only after experimenting with the chord selection being attached to other variables such as the note of the y axis or z axis; we found that when there was little movement around either axis the generated music played the same three notes repeatedly. 

 <table style="width:100%">
  <tr>
    <th>First Option (Base Note)</th>
    <th>Second Option (Major/Minor 3rd)</th>
    <th>Third Option (Perfect 5th)</th>
 </tr>
 <tr>
   <td>base_note</td>
   <td>base_note+4</td>
   <td>base_note+7</td>
  </tr>
  <tr>
   <td>base_note</td>
   <td>base_note+4</td>
   <td>base_note+9</td>
  </tr>
  <tr>
   <td>base_note</td>
   <td>base_note+5</td>
   <td>base_note+9</td>
  </tr>
 <tr>
  <td>base_note+2</td>
  <td>base_note+5</td>
  <td>base_note+9</td>
 </tr>
 <tr>
  <td>base_note+2</td>
  <td>base_note+7</td>
  <td>base_note+11</td>
  </tr>
 <tr>
  <td>base_note+4</td>
  <td>base_note+7</td>
  <td>base_note+11</td>
 </tr>
</table> 

<i>Table of All Possible Chords</i>

Based off the chord selected at random and the incoming frequency from the x axis, there are three possible note choices (integers) to select for both the y and z axes. These three integers correspond to the notes needed to produce the selected chord in the 12-tone Western music scale. 

If you want to look more at the music theory behind what a chord is and the chord selection process, please read more [here](https://caitlincoffey.github.io/Movement-Synthesizer/musictheory).


## Playing Back the Music 

<img src="https://caitlincoffey.github.io/Movement-Synthesizer/media/Maca Music.png" height="306" width="377.5">
<br>
<i>The three frequencies played over each time step in the music created by movement during the Macarena dance.</i>

<br>
<audio controls> 
  
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/macarena_all.mp3" type="audio/mpeg"></audio>
The final music with all three axes combined from the Macarena.
<br>
<br>

<audio controls> 
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/macarena_x_only.mp3" type="audio/mpeg"></audio> The music along the x axis for the Macarena.
<br>
<br>

<audio controls> <source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/macarena_y_only.mp3" type="audio/mpeg"></audio> The music along the y axis for the Macarena.
<br>
<br>

<audio controls>
<source src="https://caitlincoffey.github.io/Movement-Synthesizer/audio/macarena_z_only.mp3" type="audio/mpeg"></audio> The music along the z axis for the Macarena.
<br>
<br>

We played the frequencies in the order of decreasing initial magnitude before standardization, one chord created from the combination of one note from each axis at a time. To create this, for each frequency we ran MATLAB's `ifft()` algorithm, where the symmetric FFT only had a value of 100 for the sole frequency that was to be converted into music. To make the music higher tempo, only  the first quarter of the each note being played was strung together into one longer progression of notes. The resulting music from all three axes was then combined in a .wav audio file, with each axis being a different channel.
