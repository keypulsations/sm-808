# sm-808, Key Pulsations edition

This is a simple command line sequencer designed to make the process of trying out different combinations of rhythms and samples much faster. Instead of dragging and dropping audio samples into Ableton or another DAW and manually coding or recording different MIDI sequences, we can use the command line to quickly iterate between different combinations of provided samples and (potentially AI-generated) sequences.

`play_sequence` does the following:

* selects a random combination of a kick, snare and hihat samples from a given set of samples in `audio/*` (the included were taken from Splice's KSHMR sample set and cannot contain spaces)
* selects a random kick, snare and hihat sequence from an included set of patterns hard coded in the script (sequences could alternatively be generated automatically with machine learning tools, discussed below)
* if one sequence is longer than the others, it loops the shorter sequences until the longer sequence is finished (assumes any longer sequences have lengths that are integer multiples of the shorter sequences)
* offers the user to input a tempo and amplitude to affect the realtime display output
* plots the sequence visually, with the color spectrum deriving from the given tempo

## Dependencies/Installation
This tiny app was created and tested on Mac OS X Yosemite 10.10.5 and run on iTerm2.

The only requirement for it to run correctly is SoX, which is needed to play audio files: http://brewformulas.org/Sox

If you have homebrew installed, you can install Sox with:

`brew install sox`

## Usage
* cd into the sm-808 directory
* run `bash play_sequence` in the command line
* you'll be prompted for a tempo and amplitude, but can press enter for defaults (160 and 0.5 respectively)

## Next steps
* make it easier to output the results of any execution to Ableton or any other DAW (with MIDI and audio files ready to go)
* allow the user to alter the tempo/amplitude in real time (though quantized) while the sequencer is playing
* allow the user to change individual samples (kick, snare and hihat) in real time (though quantized) while the sequencer is playing
* allow the user to change individual sequences (kick, snare and hihat) while the sequencer is playing
* offer an option after the sequencer ends to play the same set of samples/sequences again, or to play the sample samples with different sequences and vice versa
* train TensorFlow/Magenta on MIDI data (from Splice, possibly) individually on kick, snare and hihat patterns and use the training set to generate sequences on the fly
* consider dropping audio samples entirely and use TensorFlow/Magenta to synthesize audio: https://magenta.tensorflow.org/nsynth-instrument
