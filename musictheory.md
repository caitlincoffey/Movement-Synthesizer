# The Music Theory Behind the Project

This project required extensive research into music theory topics covered in courses such as WIRED. In the United States and Europe, music is largely based off of a 12-tone scale, where each tone corresponds to a note and either an accidental (sharp or flat) that can slightly change the frequency of the note or no accidental (e.g. a natural note). Since this is the type of music the project is creating and referring to, we will explain some of the concepts of 12-tone music and how it relates to the project.

## The Applications of Music Theory for the Pitch Tuning Algorithm 

The pitch tuning algorithm, as mentioned before, finds the lowest distance between each frequency of movement and the piano frequencies and replaces the frequency from movement with the respective piano note. 

To first understand the music theory underlying the algorithm, one must understand the concept of key signatures. Key signatures are a way of determining which notes can be played together out of the 12 possible notes. Key signatures correspond to each note; for example C has a key signature called C major. There are 7 notes in a C major scale. There are key signatures that are similar to C major such as F major or G major which share all but 1 of these notes. Going into these key signatures, for simplicity's sake, will be called 'moving up' or 'moving down' a key signature. Moving up is replacing one note out of the seven with a higher frequency (a sharp/natural), and moving down is replacing one note out of the seven with a lower frequency (a flat/natural).  

Each piano note is aligned with the 12-tone music scale. For the x axis, the algorithm always selects between the full range of notes to match the first frequency. From there, the frequencies on the x axis are matched by either the note of the tuned frequency before it (the same key signature), the key signature 1 step up of the tuned frequency before it, or the key signature one step down from the frequency before it. This is to prevent key signatures wildly shifting around, preventing most of the possible dissonance that could happen between key signature changes. Dissonance happens between groups of notes that, for a lack of a better term, do not sound good together to most people. This is why our team avoids producing dissonant music.

The lowest distance can be impacted for the y and z axes depending on the chord selected in the chord selection process. When these restrictions apply, the piano frequencies that do not line up with the selected chord (e.g notes that are not present in that chord) are not considered when finding the lowest distance between the frequencies from movement and the piano frequencies. Without the restriction, all chords would never be guaranteed to be produced as the notes would vary too much to produce them every time. It also prevents the possibility of making dissonant chords. 


## The Applications of Music Theory for the Chord Selection Process

The chord selection is randomized so that the generated music does not sound repetitive. This design decision was made only after experimenting with the chord selection being attached to other variables such as the note of the y axis or z axis; we found that when there was little movement around either axis the generated music played the same three notes repeatedly. 

It selects between six chords: a major chord in the same key signature, a minor chord in the same key signature, a minor chord in the key signature above, a major chord in the key signature above, a minor chord in the key signature below, and a major chord the key signature below. This helps mitigate most dissonant chords, while it also provides some room for the key signature to move around.

Based off the chord selection and the incoming note from the x axis (the base note), there are three possible note choices (integers) to select for both the z and y axes. These three integers correspond to the notes needed to produce the selected chord in the 12-tone Western music scale. Here is an example of three possible note choices to form a major chord in the same key signature: `musicnote_limits = [base_note, base_note+4, base_note+7];`

Major chords have three notes: the root, the major third, and the perfect 5th. The root in this case is the base note selected from the x axis. Since 12-tone music is a modulo 12 arithmetic system based on 'half tones', major 3rds are represented as 4 'half tones' above the base note, and perfect 5ths are represented as 7 'half tones' above the base note.

The reason why the model is limited to major and minor chords within 1 key signature difference is because other chords (augmented chords, devil's triad) sounded objectively painful when tested on two human ears. Since it is hard to quantify what sounds 'good' or 'bad' with a sample size of two people, our group found research conducted by Pennsylvania State University that showed the majority of people prefer chords that are found in the harmonic series of the base note \[[6](https://sites.psu.edu/siowfa15/2015/09/16/what-makes-chords-sound-good/)\].
