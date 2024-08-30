# ELM-Events-Recreation
A recreation of the FMOD events for the Pizza Tower mod [**Egg's Lap Mod**](https://gamebanana.com/mods/464912) (And any fanmade Noise Update ports) as an FSPRO containing only those events/folders for those who want to use custom music and sounds with their own [Pizza Tower FMOD FSPRO recreations](https://github.com/Raltyro/PT-FSPRO-Recreation).

# How it works
The FMOD Project included here merely contains the folder structure and events that ELM reads for, in order for you to make it work with your own FMOD project all you must do is the following steps.


1. Open the FMOD project and copy the folders with the events inside into your own FMOD project.

![](https://i.postimg.cc/P5LvndG6/1.png)

2. Create two new banks in the "Banks" tab, these banks respectfully should be named `ELMmusic` and `ELMsfx`, alongside these rename `Master` to `ELMMaster`

![](https://i.postimg.cc/Kvp3WRWk/2.png)

3. Assign the folders to their respective banks.

![](https://i.postimg.cc/cJwK6TLw/3.png)

4. Assign the events in the mixer
  - You can open the mixer tab with CTRL+5, assign the music and sfx to their respective mixer folders.
   
![](https://i.postimg.cc/2SPbzgrC/4.png)

5. Set the state parameter to be "Exposed recursively via event instruments"
  - This allows the pizzatime event to actually reference the main Pizza Tower one and still function as it should, instead of needing to recreate the original event.

![](https://i.postimg.cc/pV4pQg5z/state.png)

6. If you are choosing to build for The Noise Update and you want Noise to have unique music, port over the `pizzatimenoise` event instead, and rename it to `pizzatime`.

7. Modify to your hearts content or build and put them in `Pizza Tower\sound\Desktop\_` and `Desktop\EggsLapMod\_` for the respective normal and ELM bank files.
  - You need not worry about creating a `Master.bank` or `Master.strings.bank` as ELM only reads the `ELMMaster.bank` and `ELMMaster.strings.bank` files that are in the EggsLapMod folder.
  
# How does the pizzatime event work?
So with the introduction of Swap Mode within V1.1.0 of Pizza Tower, they needed a way to have it so the music switches seemlessly between Peppino's tracks and Noise's tracks.

The formatting is as follows:

![](https://i.postimg.cc/cCpCsnGX/Magnet.png)

- The Magnet regions are used to transition between Peppino and Noise's music tracks.
- Both songs must have the same length to them, you can sync this up by using transition regions at the ends of the tracks to both ensure there's padding for smooth transitions on the timeline, and to also make sure that if you swap character right as it loops, it doesn't leak into the next song by mistake.

![](https://i.postimg.cc/brmrKwzw/Lap2.png)
An example using the Lap 2 songs

= Transition markers =

![](https://i.postimg.cc/tgDg1gxt/markers.png)

- Incase you are confused about the transition markers at the top left of the logic tracks.  These are so that the event can start from the Lap 3 or 4 songs after respawning.  The character specific ones are overlayed on each other.

# Alternate Lap 4 tracks.
So within the FMOD project you might notice the folder at the top labeled "Alternate Tracks".

![](https://i.postimg.cc/Mp2HNNwR/folders.png)

Within the folder it contains alternate tracks to replace the Lap 4 song in the `pizzatime`/`pizzatimenoise` event with.

1. Inside the FMOD Project navigate to the event for the track you want to replace the current Lap 4 track with.  For example I am going to replace Memento Morinara with Funiculi Freakout V1 REDUX, for Noise specifically.

![](https://i.postimg.cc/VkGTdQN0/redux.png)

2. Select the contents inside the event, that being the audio track and its logic tracks.  Copy these.

![](https://i.postimg.cc/ZqXMx8pT/selected.png)

3. Inside the `pizzatimenoise` event, delete the section of the track containing the current Lap 4 track, then delete the transition region and marker for Noise's Lap 4 specifically.

![](https://i.postimg.cc/vB6CJqbg/Deletion.gif)

4. Paste in the tracks you copied.

![](https://i.postimg.cc/bN2d687p/pasted.png)

5. Since we're doing this with the Noise Update pizzatime event, stretch out Peppino's Lap 4 magnet region.  Make sure that it's the same length as Noise's.

![](https://i.postimg.cc/NGn57LPd/Stretched-Pep.png)

6. You're now gonna want to stretch out the song for Peppino, then adjust the loop region accordingly.  I'd recommend copying the first loop and putting the duplicated one after it. This might take some fiddling around to get right but with Memento Morinara it's not too hard.

![](https://i.postimg.cc/mrSPQw09/Loop.png)

7. Select the imported Magnet Region, Transition Region and Transition Marker for Funiculi Freakout, and make sure that the `isnoise` parameter on them is set to `1`.  This makes it so that they will only activate if you're playing as Noise. Setting it to `0` will make it so it plays as Peppino instead.

![](https://i.postimg.cc/QCvCXnW2/noise.gif)

8. Move the transition marker to the beginning and stretch out the transition region so it covers up to the end of the Lap 3 tracks.

![](https://i.postimg.cc/k4XBwSmp/stretched-and-moved.png)

And viola! Now when you build your custom ELM banks, Funiculi Freakout will now play instead of Memento Morinara as Noise.

# Changing Pizza Mayhem's Lyrics.
So lets say that within your project, you want a COMPLETELY different song to play instead of Pizza Mayhem during The Final Lap, and the song in question, lets go over this.

So the way that Egg's Lap Mod does the lyrics for Pizza Mayhem is interesting, the first thing to note is that the lyrics are stored in the english.txt file in the `lang\` folder inside Pizza Tower's directory.
The lyrics are stored at the bottom, by default the lyrics for Pizza Mayhem go up to a count of 14 but you can actually insert as many as you need.
For example.  Lets say that I wanted to replace Pizza Mayhem with Live and Learn from Sonic Adventure 2.  That song contains 27 unique lyrics, so the parameter would be increased to 27.

![](https://i.postimg.cc/kM2xd00h/live-and-learn.png)

Meanwhile on the FMOD's end, to actually call up the lyrics it references the parameter `pmlyric`.  This parameter has a range of 0-14 by default.
If you resize the parameter to whatever your lyrics need, make sure you make it not scale.

To make the lyrics get called as the song is going, refer to the `Lyrics` and `Stops` lanes in the `finalescape` event.
These lanes have **command instruments** that will change the value of `pmlyric`.  When set to 0 they will remove the lyrics off the screen.  1 onwards represent the Lyrics (lyric# = "") established in your english.txt.
I have colour coded these command instruments, so that the lyrics are blue and any that set pmlyric to 0 are purple.

![](https://i.postimg.cc/MXkZkMCx/pmlyric.png)
![](https://i.postimg.cc/wxnDxWHx/pmlyric-lanes.png)

It's a very time consuming process but it's definitely worth the effort.

# Music Credits
- Vozaxhi - [Pillar John's Revenge](https://www.youtube.com/watch?v=MSzReOhnxXg)
- Inceptradom - Absolute AbsurZiti [V1 REDUX](https://www.youtube.com/watch?v=_x3RvXH7sdo) / [V2](https://www.youtube.com/watch?v=Tj6sN5GNBPA)
- LAAAAE - Funiculi Freakout [V1](https://www.youtube.com/watch?v=cr0Y_DkL05w) / [V1 REDUX](https://www.youtube.com/watch?v=vPA3co_iesA) / [V2](https://www.youtube.com/watch?v=NuDjZB65ViA)
- DimWiddy - [Memento Morinara](https://soundcloud.com/dimwiddy/memento-morinara)
