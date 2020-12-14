# The Music Theory Behind the Product
Music Theory is the study of This project required extensive research into music theory topics covered in courses such as WIRED.

### Pitch Tuning Algorithm 

### Chord Selection 

The chord selection is randomized so that the generated music does not sound repetitive. This design decision was made only after experimenting with the chord selection being attached to other variables such as the note of the y axis or z axis; we found that when there was little movement around either axis the generated music played the same three notes repeatedly. 

It selects between four chords: a major chord, a minor chord, a minor chord from the perfect 4th of the base note, and a major chord from the perfect 4th of the base note. After its selection, it will return a vector of three integers to add to the starting index of the selection of piano note frequencies. These three integers correspond to the notes needed to produce the selected chord in a modulo 12 Western music system. 

Here is what each chord sounds like with a concert A4 (440 Hz): 
- Major chord: 
<audio controls src="/media/cc0-audio/t-rex-roar.mp3"></audio>
- Minor chord:
<audio controls src="/media/cc0-audio/t-rex-roar.mp3"></audio>
- Minor chord from the perfect 4th interval (inverted such that the base note remains the lowest frequency): 
<audio controls src="/media/cc0-audio/t-rex-roar.mp3"></audio>
- Major chord from the perfect 4th interval (inverted such that the base note remains the lowest frequency): 
<audio controls src="/media/cc0-audio/t-rex-roar.mp3"></audio>

The reason why the model is limited to these four chords is because other chords (augmented chords, devil's triad) sounded objectively painful when tested on two human ears. Since it is hard to quantify what sounds 'good' or 'bad' with a sample size of two people, our group found research conducted by Pennsylvania State University that showed the majority of people prefer chords that are found in the harmonic series of the base note \[[5]\](https://sites.psu.edu/siowfa15/2015/09/16/what-makes-chords-sound-good/)

Note that the perfect 4th is a misleading yet common term in music theory as it is technically 2.5 'whole tones' above the base frequency. Since 12-tone music (Western music) is a modulo 12 arithmetic system based on 'half tones', perfect 4ths are represented as 5 'half tones'. 
