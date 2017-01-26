#Audio

## Audio Clips
These are files that you imported. AIFF, WAV, MP3, and Ogg. Music can also be .xm, .mod, .it, and .s3m files. For iOS and Android, these will be converted to either Vorbis/MP3 to use hardware decompression. On Xbox One and PS Vita, they are compressed with HEVAG/XMA.

## [Audio Sources](http://docs.unity3d.com/Manual/class-AudioSource.html)
Use this to play a sound in your scene. 

## [Audio Listeners](http://docs.unity3d.com/Manual/class-AudioListener.html)
Usually attached to the main camera, acts like your ears in the Unity game world. In order for you to hear any sound in your Unity project, you'll have to have one of these in your project. By default, it is added to the Main Camera in the project. You can only have 1 in your scene for sound to work properly, so sometimes when you import a character controller, it may have one attached to it and you will need to disable or delete one of the listeners.

## [Audio Mixer](http://docs.unity3d.com/Manual/AudioMixer.html)
This allows you to adjust the sound in your project. There's is quite a bit that can be accomplished with Audio Mixer, so invest some time in looking through the Unity manual for details.

## [Audio Filters](http://docs.unity3d.com/Manual/class-AudioEffect.html)
Can be applied to either the Audio Source or Audio Listener components. While they are optimized, some of the filters may caise a lot of CPU usage.

## [Reverb Zone](http://docs.unity3d.com/Manual/class-AudioReverbZone.html)
This allows you to mimic an area where you will want to distort sound, like you are entering a cavern. 

## Audio Settings
This is a class give you information on the game's host sound system.
