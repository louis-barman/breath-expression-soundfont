# Breath_Expression.sf2

**Version 0.0.1**

---


This SoundFont works well with a MIDI Wind Controller (an Electronic Wind Instrument)
that uses the breath controller #2 (CC2) to set the level of the sound.

> WARNING: This soundfont will not normally work with standard MIDI keyboards
or respond to a MIDI file unless the MIDI breath controller (CC2) is used.

## Download

This soundfont is too large to be included as part of the source code in this GitHub repository
but it is provided on the GitHUb release page. see: https://github.com/louis-barman/breath-expression-soundfont/releases


## About

This soundfont is based on the **MuseScore_General_Full** SoundFont that is
provided in the **musescore-general-soundfont-lossless** package on Debian (Linux).
This soundfont uses all the expression patches that were added to support
Single-Note Dynamics available in MuseScore >3.2.
As these expression patches all use the breath controller (CC2) they also
work very well with a MIDI Wind instrument.

To reduce the size of this soundfont it has been reorganised by removing all
General MIDI patches leaving just the expression patches which have been
renumbered and moved to bank 0.

## MIDI Wind Controller setup

When using a MIDI Wind Controller it is recommended that fluidsynth 2.x
is used and that MIDI Mono (Monophonic mode) is turned on using Control Change #126
(CC126). There is a noticeable improvement in the quality of some of
the sounds with MIDI Mono On which causes the ADSR volume envelopes to be improved
when playing legato.

This soundfont has been tested using FluidSynth version 2.1.1 and the WARBL
MIDI Wind Controller. For the WARBL set Expression to "Send Pressure as CC"
using CC2 for the breath pressure sensor output.

## Expressive Presets

The dynamics of these presets are controlled using MIDI Control Change #2 (CC2),
allowing fluid crescendos and diminuendos while a note is being held. This makes
for much more realistic expression of strings, brass, woodwinds, etc. Note velocity
no longer controls dynamics in these presets, but in some instruments, velocity will
have some effect on the speed of the note attack. In MuseScore, the default (and ideal)
behaviour is for expressive instruments to have their dynamics controlled by sending
identical values to both CC2 and note velocity (the latter only during note-on, naturally).


## SoundFont Compatibility

**Breath_Expression** makes full use of SoundFont 2.01 specification modulators
(particularly in the newer instruments) and requires a player/sampler with robust
support for the standard. To my knowledge, the only SoundFont players that can
accurately play this SoundFont are:

* [MuseScore](https://musescore.org)
* [FluidSynth](http://www.fluidsynth.org/)
* [Sobanth VSTi](https://blog.rosseaux.net/page/e5ca75d98990e33b31dadc78a8df1333/Sobanth)
* Sound Blaster Audigy/Audigy2 hardware SoundFont synth (probably X-Fi as well)

The only SoundFont editors that can play this SoundFont correctly are:

* Creative Vienna SoundFont Studio (requires Sound Blaster or E-MU hardware synth with SoundFont 2.01 modulator support)
* [SWAMI](http://www.swamiproject.org/) (uses FluidSynth)


## Breath Expression Requirements

There are some different requirements when adding a new instrument or editing
an existing one when designing them to be used with a MIDI Wind Controller:

* It is much better to have sound samples without any vibrato because the player
can control the amount of vibrato using their breath.
* Be aware that a MIDI wind instrument may generate very short transient
MIDI notes. This is because the players fingers may not open or
close all the keys at exactly the same time when moving to another note.
The soundfont should be setup to handle these short transient MIDI notes without
introducing any unwanted sounds (pops or squeaks).
* When two notes are played legato on a monophonic wind instrument the
first note does not need to have a decay and the second note does not need
to have an attack so that the sound flows smoothly between the two notes.
