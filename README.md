# Kontakt KSP - Signal vector synchroniser

Please note that the script has been written by using Nojanath's KSP plug-in for Sublime.

https://github.com/nojanath/SublimeKSP

The main function of this script is to synchronise a NOTE_HELD while loop within a note on event with the audio SIGNAL VECTOR (SV). This allows to retrieve up-to-date , consistent reading positions the audio buffers / files being played, as the return value of the KSP function get_event_par(#noteID#,EVENT_PAR_PLAY_POS) is updated only when the SIGNAL VECTOR is refreshed. 
This, in turn, allows a to trigger commands with a high degree of precision relative to a note playing position. As shown by this script's extra feature, one of the most basic application of this synchronisation to the SV is the ability to synchronise notes being played together to a single audio sample level of precision, which allows to dynamically play audio signals on phase, or merge two audio pulses into one. 

This script has been configured to work with a Kontakt 6 demo instrument titled "Notes synchroniser / phase aligner by Alessandro Quaranta". 
Instructions:
- load the instrument on a DAW (audio output must be stereo). The instrument is set to work at an audio sample rate of 96Khz. To try it on a different sample rate, edit the variable CONFIG.SR accordingly.
- trigger a note within the midi range (A3/A4). This note is the MASTER note. All the following notes triggered while the MASTER note is still playing will be synced to it.
- trigger another note withing the same range. This is the SLAVE note and as such it will be triggered by the script at the beginning of the next SV (a smaller SV size means shorter latency) 
- as all the notes within the available midi range purpoely activate the same audio buffer (the Kontakt group's "tracking" feature is disabled, meaning that the Sample playbacks are NOT transposed according to the MIDI parameter of the note on ) , you will notice that the audio signal from the right channel (SLAVE note) in on phase with the one from the left channel (MASTER note) 
 

 
