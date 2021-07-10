# MuseScore_General_HQ.sf2

**Version 0.1.9**

---

Please see **MuseScore_General_HQ_License.md** for authorship and license information.

The purpose of this README is to provide useful information on instruments contained within MuseScore_General_HQ. It is currently a work-in-progress.

## About

This is a fork of FluidR3Mono_GM.sf2, with many samples (eventually) being replaced and/or reprogrammed. The SoundFont is currently a work-in-progress. Detailed information on presets and sample sources used can be found in "MuseScore_General_HQ_Sample_Sources.csv". All instruments without attribution are still using samples from FluidR3Mono.

## SoundFont Compatibility

**MuseScore_General_HQ** makes full use of SoundFont 2.01 specification modulators (particularly in the newer instruments) and requires a player/sampler with robust support for the standard. To my knowledge, the only SoundFont players that can accurately play this SoundFont are:

* [MuseScore](https://musescore.org)
* [FluidSynth](http://www.fluidsynth.org/)
* [Sobanth VSTi](https://blog.rosseaux.net/page/e5ca75d98990e33b31dadc78a8df1333/Sobanth)
* Sound Blaster Audigy/Audigy2 hardware SoundFont synth (probably X-Fi as well)

The only SoundFont editors that can play this SoundFont correctly are:

* Creative Vienna SoundFont Studio (requires Sound Blaster or E-MU hardware synth with SoundFont 2.01 modulator support)
* [SWAMI](http://www.swamiproject.org/) (uses FluidSynth)

## Presets

### General MIDI Presets

**MuseScore_General_HQ** is compatible with the [General MIDI standard](https://en.wikipedia.org/wiki/General_MIDI) with some additional presets from the [Roland GS standard](https://en.wikipedia.org/wiki/Roland_GS) as well.

### Fluid r3 Additional Drum Kits

Additional drum kits have been inherited from **Fluid r3**, beyond the kits specified in the [Roland GS standard](https://en.wikipedia.org/wiki/Roland_GS). It is possible that some of these kits will be removed in the future when new drum samples are added.

### Instrument Variations

In addition to the General MIDI presets, further instrument variations can be found on banks 20 and above, utilizing identical preset numbers so that General MIDI preset fallback can occur if ever the instrument becomes no longer available on the higher bank number. In other words, if you have a track assigned to bank #40, preset #48 "Celli Fast", then try to play it using a different General MIDI device or SoundFont, the preset will fall back to bank #0, preset #48 "Fast Strings" instead, and playback will at least sound somewhat correct.

### MuseScore Marching Percussion

The following marching percussion presets exist in the percussion bank (bank 128):
* 56: Marching Snare
* 57: OldMarchingBass
* 58: Marching Cymbals
* 59: Marching Bass
* 95: OldMarchingTenor
* 96: Marching Tenor

These presets are used for marching percussion support in MuseScore and do not conform to GM layout.

### Expressive Presets

As of version 0.1.5, **MuseScore_General_HQ** features expressive variants of all sustained presets, indicated by "Expr." at the end of the preset name. The dynamics of these presets are controlled using MIDI Control Change #2 (CC2), allowing fluid crescendos and diminuendos while a note is being held. This makes for much more realistic expression of strings, brass, woodwinds, etc. Note velocity no longer controls dynamics in these presets, but in some instruments, velocity will have some effect on the speed of the note attack. In MuseScore, the default (and ideal) behavior is for expressive instruments to have their dynamics controlled by sending identical values to both CC2 and note velocity (the latter only during note-on, naturally).

The expressive presets exist on higher bank numbers but use the same preset number as their non-expressive defaults. You can see what bank numbers the expressive presets use in column #2 ("Expr. Bank #") of the included **MuseScore_General_HQ_Sample_Sources.csv** file. The general rule is as follows:

* Bank 0 expressive presets are on Bank 17
* Bank 8 expressive presets are on Bank 18
* Bank 20-126 expressive presets are one bank higher (e.g., Bank 20 Expr. presets are on Bank 21)

### VSCO2 Ensemble Strings

**MuseScore_General_HQ** features an ensemble strings library based on samples from [VSCO 2.1.1 Community Edition](http://vis.versilstudios.net/vsco-community.html). This library includes unique sections for Violins, Violins 2, Violas, Celli and Basses, the presets for which can be found on banks 20-32. The bank:preset arrangement is such that proper GM fallback can occur (e.g., if a user selects "020:048 Violins Fast" for a staff but plays the score back later using a different SoundFont, they will hear the fallback preset "000:048 Strings Fast" instead). The default GM strings presets on bank 0 offer a more homogenized sound, with the Violins, Violas, Celli and Basses spread across the entire key range.

Each instrument section contains the following articulations:

* **Fast:** Sustained notes with fast attack
* **Slow:** Sustained notes with slow attack
* **Tremolo:** Tremolo, sustained notes
* **Pizzicato:** Plucked strings

The default sustained articulation for use in MuseScore should be "Fast", so that notes in fast passages will be audible. "Slow" can be used where a more lyrical tone is desired.

Some additional articulations have been created, but are not yet included in **MuseScore_General_HQ**:

* **CC2:** Sustained with note volume & tone controlled by CC2, and note attack controlled by key velocity
* **Staccato:** Short bowstrokes
* **Trem CC2:** Tremolo, sustained with note volume & tone controlled by CC2

The Staccato presets will only be added if there are enough SoundFont instrument generators left after upgrading all of the other instrument samples, potentially along with second viola and cello sections as well. The "CC2" presets cannot currently be used by MuseScore, but future versions may be able to incorporate a fluid expression mode (e.g., crescendo on a single note). I am designing all of the new expressive instruments to be able to support this feature. See: https://www.youtube.com/watch?v=TlhB6RBWIJA. Any developers wishing to implement such support in MuseScore should contact me, [S. Christian Collins](mailto:s_chriscollins@hotmail.com), for details.

#### Preset List (bank:preset)

- 000:044 - Strings Tremolo
- 000:045 - Strings Pizzicato
- 000:048 - Strings Fast
- 000:049 - Strings Slow
- 020:044 - Violins Tremolo
- 020:045 - Violins Pizzicato
- 020:048 - Violins Fast
- 020:049 - Violins Slow
- 025:044 - Violins2 Tremolo
- 025:045 - Violins2 Pizzicato
- 025:048 - Violins2 Fast
- 025:049 - Violins2 Slow
- 030:044 - Violas Tremolo
- 030:045 - Violas Pizzicato
- 030:048 - Violas Fast
- 030:049 - Violas Slow
- 040:044 - Celli Tremolo
- 040:045 - Celli Pizzicato
- 040:048 - Celli Fast
- 040:049 - Celli Slow
- 050:044 - Basses Tremolo
- 050:045 - Basses Pizzicato
- 050:048 - Basses Fast
- 050:049 - Basses Slow

#### Additional Details

* Each instrument's tone changes gradually across the entire velocity range. VSCO2 only provides samples at two dynamic levels (in some cases only one), so the samples use pseudo-crossfading to provide a smooth transition from PP to FF.
* The second violin section ("Violins2") uses the same samples as the first, but they are manipulated using sample offset and other tricks so that they can play in unison with the first section without the usual sample doubling effect.
* Realtime sample manipulation is performed to achieve variable note attacks for each instrument group. The violin samples, for example, all have a slow attack, so I used sample offset and layering of the staccato samples to create a faster attack for the "Violins Fast" preset. Doing this without sounding artificial is *extremely* difficult, but I think I have it about as realistic as possible using these samples. As with any orchestral sample library, a good reverb plugin will help everything sound more natural.
* I have made many changes to the original VSCO2 samples, including:
  * All samples were normalized.
  * Loops were created for all sustained and tremolo samples.
  * Created new timestretched samples to extend the upper range of all instruments (particularly needed for the violins).
  * There was no bass section in the VSCO 2 samples (only solo contrabass), so I combined solo bass samples to create a small section.
  * Many noises have been removed/reduced (scrapes, bangs, notes from instrument in neighboring room).
  * Pitch drift on some samples has been fixed.
