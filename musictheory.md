# The Music Theory Behind the Project

This project required extensive research into music theory topics covered in courses such as WIRED. **Music theory** is the study of the standards and practices behind both modern and historical music. In the United States and Europe, music is largely based off of a 12-tone scale, where each tone corresponds to a note and either an accidental (sharp or flat) that can slightly change the frequency of the note or no accidental (e.g. a natural note). Since this is the type of music the project is creating and referring to, we will explain some of the concepts of 12-tone music and how it relates to the project.

## Referring to Notes

There are seven natural notes in Western music, and each one is based off of a letter in the latin alphabet: A, B, C, D, E, F, and G. These notes, combined with accidentals, can map to every single note in Western music by the use of **octaves**. An **octave** is the interval between one musical pitch and another with double its frequency. To denote what octave a note is in, one should use the natural note letter followed by a number (e.g. A4 = 440Hz). 

If the note contains an accidental (either a sharp or flat), one should include those as well when referring to the note. A sharp note is referred to by a sign similar to the pound sign, /#. One can refer to a flat note with the flat sign, ♭. If this character does not show on the browser, one can substitute the sign with a lowercase b. For example, a G sharp note in the same octave as A4 can be referred to as G\#4. 

It is important to keep accidentals in mind, as they come up when talking about **key signatures**.

## Key Signatures 

A **key signature** is the 7 distinct notes that can be played at any given time. In music, the key signature is a vital part of the music and one is always declared at the beginning of the piece. Without a key signature, musicians would have a harder time knowing which notes are assumed to be 'sharp' or 'flat'. 

<center>
<img src="https://raw.githubusercontent.com/caitlincoffey/Movement-Synthesizer/gh-pages/media/fmajorkye.png" height="400" width="400">
 <br>
<i>The F Major Key Signature</i>
 </center>

It shows that there is one note that should always be assumed to be flat, unless otherwise stated via an accidental; this note is B. The key signature tells us that if B ever comes up in the piece, one should always play it flat. The other notes should be treated as natural notes.

The number of notes that should be played flat or sharp depends on the key signature, as is the number of notes that should be played as natural notes. This is important to remember as certain sharp, flat, and natural notes played together produce not-so-good clashing tones. This means certain key signature combinations are more likely clash if played together, like F major and E major.

### Key Signatures and Chords 
If clashing key signatures are present, clashing chords will also be present (and these do not sound good!). 

To prevent clashing chords, the only room of movement for chords is between two points: one step down or one step up. One step 'up' means that the key signature is becoming sharper, so either a flat will be removed or a sharp will be added. One step down is going in the other direction; one flat will be added or a sharp will be removed. This helps mitigate most of the clashing chords, while it also provides some room for the key signature to expand as staying in one key signature for the entire piece can sound boring at times. The process of selecting between going 'up', 'down', or staying in the same key signature is determined randomly. 


## Pitch Tuning Algorithm 

The pitch tuning algorithm, as mentioned before, finds the lowest distance between each frequency of movement and the piano frequencies and replaces the frequency from movement with the respective piano note. 

Each piano note is aligned with the 12-tone music scale. For the x axis, the algorithm always selects between the full range of notes to match the first frequency. From there, the frequencies on the x axis are matched by either the note of the tuned frequency before it (the same key signature), the key signature 1 step up of the tuned frequency before it, or the key signature one step down from the frequency before it. This is to prevent key signatures widly shifting around, preventing most dissonant chords from happening between shifts. Dissonant chords do not sound pleasant to most people according to Pennsylvania State's School of Music study \[[5](https://sites.psu.edu/siowfa15/2015/09/16/what-makes-chords-sound-good/)\], which is why we are avoiding producing dissonant chords.

The lowest distance can be impacted for the y and z axes depending on the chord selected in the chord selection process. When these restrictions apply, the piano frequencies that do not line up with the selected chord (e.g notes that are not present in that chord) are not considered when finding the lowest distance between the frequencies from movement and the piano frequencies. Without the restriction, all chords would never be guaranteed to be produced as the notes would vary too much to produce them every time. It also prevents the possibility of making dissonant chords. 


## Chord Selection Process

The chord selection is randomized so that the generated music does not sound repetitive. This design decision was made only after experimenting with the chord selection being attached to other variables such as the note of the y axis or z axis; we found that when there was little movement around either axis the generated music played the same three notes repeatedly. 

It selects between six chords: a major chord in the same key signature, a minor chord in the same key signature, a minor chord in the key signature above, a major chord in the key signature above, a minor chord in the key signature below, and a major chord the key signature below. From there, it creates three possible note choices (integers) to select for both the x and y axes. These three integers correspond to the notes needed to produce the selected chord in a modulo 12 Western music system. Here is an example of three possible note choices to form a major chord in the same key signature: `musicnote_limits = [base_note, base_note+4, base_note+7];`

Major chords have three notes: the root, the major third, and the perfect 5th. The root in this case is the base note selected from the x axis. Since 12-tone music (Western music) is a modulo 12 arithmetic system based on 'half tones', major 3rds are represented as 4 'half tones' above the base note, and perfect 5ths are represented as 5 'half tones'. 

The reason why the model is limited to major and minor chords within 1 key signature difference is because other chords (augmented chords, devil's triad) sounded objectively painful when tested on two human ears. Since it is hard to quantify what sounds 'good' or 'bad' with a sample size of two people, our group found research conducted by Pennsylvania State University that showed the majority of people prefer chords that are found in the harmonic series of the base note \[[5](https://sites.psu.edu/siowfa15/2015/09/16/what-makes-chords-sound-good/)\]
