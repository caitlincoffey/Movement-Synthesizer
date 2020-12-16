# The Music Theory Behind the Product

This project required extensive research into music theory topics covered in courses such as WIRED. **Music theory** is the study of the standards and practices behind both modern and historical music. In the United States and Europe, music is largely based off of a 12-tone scale, where each tone corresponds to a note and either an accidental (sharp or flat) that can slightly change the frequency of the note or no accidental (e.g. a natural note). Since this is the type of music the project is creating and referring to, we will explain some of the concepts of 12-tone music and how it relates to the project.

## Referring to Notes

There are seven natural notes in Western music, and each one is based off of a letter in the latin alphabet: A, B, C, D, E, F, and G. These notes, combined with accidentals, can map to every single note in Western music by the use of **octaves**. An **octave** is the interval between one musical pitch and another with double its frequency. To denote what octave a note is in, one should use the natural note letter followed by a number (e.g. A4 = 440Hz). 

If the note contains an accidental (either a sharp or flat), one should include those as well when referring to the note. A sharp note is referred to by a sign similar to the pound sign, /#. One can refer to a flat note with the flat sign, ♭. If this character does not show on the browser, one can substitute the sign with a lowercase b. For example, a G sharp note in the same octave as A4 can be referred to as G\#4. 

It is important to keep accidentals in mind, as they come up when talking about **key signatures**.

## Key Signatures 



## Pitch Tuning Algorithm 



## Chord Selection  Process

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
