# Kontakt KSP - Signal vector synchroniser

Please note that the script has been written by using Nojanath's KSP plug-in for Sublime.

https://github.com/nojanath/SublimeKSP

This script aims to synchronise "while NOTE_HELD" loops with the audio flow of SIGNAL VECTORS (SV). This allows the script to access to up-to-date , consistent reading positions of the audio buffers / files being played by the Kontakt instrument, as the return value of the KSP function get_event_par(#noteID#,EVENT_PAR_PLAY_POS) is updated only the istant when the SIGNAL VECTOR is refreshed. 
This synchronisation allows commands/events to be triggered at a scale of accuracy of an audio sample. Some typical applications of this syncing feature are the ability to trigger an audio file/buffer on phase with another one already being played, or to dynamically synchronise two notes attack in order to merge them into a single acoustic event.

You can see this script in action in the Kontakt 6 demo instrument titled "Notes synchroniser / phase aligner by Alessandro Quaranta", which is included in this repository.
Instructions:
- load the instrument on a DAW (audio output must be stereo). The instrument is set to work at an audio sample rate of 96Khz. To try it on a different sample rate, edit the variable CONFIG.SR accordingly.
- trigger a note within the midi range (A3/A4). This note is the MASTER note. All the following notes triggered while the MASTER note is still playing will be synced to it.
- trigger another note withing the same range. This is the SLAVE note and as such it will be triggered by the script at the beginning of the next SV (a smaller SV size means shorter latency) 
- as all the notes within the available midi range purpoely activate the same audio buffer (the Kontakt group's "tracking" feature is disabled, meaning that the Sample playbacks are NOT transposed according to the MIDI parameter of the note on ) , you will notice that the audio signal from the right channel (SLAVE note) in on phase with the one from the left channel (MASTER note) 
 

 
