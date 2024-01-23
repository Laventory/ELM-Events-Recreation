# ELM-Events-Recreation
A very rough recreation of the FMOD event folders as a project for the Pizza Tower mod [**Egg's Lap Mod**](https://gamebanana.com/mods/464912) for those who want to use custom music and sounds with their own Pizza Tower [FMOD](https://github.com/Raltyro/PT-FSPRO-Recreation) [recreations](https://github.com/Laventory/CheesedUP-FMOD).

# How it works
The FMOD Project included here merely contains the folder structure and events that ELM reads for, in order for you to make it work with your own FMOD project all you must do is the following steps.


1. Open the FMOD project and copy the folders with the events inside into your own FMOD project.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1175285747125850202/image.png)

2. Create two new banks in the "Banks" tab, these banks respectfully should be named `ELMmusic` and `ELMsfx`, alongside these rename `Master` to `ELMMaster`

![](https://cdn.discordapp.com/attachments/1140611242411700297/1175289796025909369/image.png)

3. Assign the folders to their respective banks.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1175291221120397352/image.png)

4. Assign the events in the mixer
  - You can open the mixer tab with CTRL+5, assign the music and sfx to their respective mixer folders.
   
![](https://cdn.discordapp.com/attachments/1140611242411700297/1175461476635525120/image.png)

5. Modify to your hearts content or build and put them in `Pizza Tower\sound\Desktop\_` and `Desktop\EggsLapMod\_` for the respective ELM and normal bank files.
  - You need not worry about creating a `Master.bank` or `Master.strings.bank` as ELM only reads the `ELMMaster.bank` and `ELMMaster.strings.bank` files that are in the EggsLapMod folder.

# Alternate Lap 4 tracks.
So within the FMOD project you might notice the folder at the bottom labeled "Alternate Tracks".

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199400273253240863/image.png)

Within the folder it contains alternate tracks to replace Absolute AbsurZiti V2 in the `pizzatime` even with.

1. Inside the FMOD Project navigate to the event for the track you want to replace the current Lap 4 track with.  For example I am going to replace AbsurZiti with Funiculi Freakout V2.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199400981960597654/image.png)

2. Select the contents inside the event, that being the track, its magnet region and loop region.  Copy these.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199401436828676176/image.png)

3. Inside your `pizzatime` event, delete the section of the track containing the current Lap 4 track.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199402143644393542/image.png)
![](https://cdn.discordapp.com/attachments/1140611242411700297/1199402179648290826/image.png)

4. Paste in the tracks you copied.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199403483703550124/image.png)

5. Click on the now empty transition marker at the beginning, set the destination to the magnet region that you pasted in alongside the loop region and music track.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199404144432254996/image.png)

And viola! Now when you build your custom ELM banks, the track you inserted from here will now play instead of Absolute AbsurZiti V2.

# Changing Pizza Mayhem's Lyrics.
So lets say that within your project, you want a COMPLETELY different song to play instead of Pizza Mayhem during The Final Lap, and the song in question, lets go over this.

So the way that Egg's Lap Mod does the lyrics for Pizza Mayhem is interesting, the first thing to note is that the lyrics are stored in the english.txt file in the `lang\` folder inside Pizza Tower's directory.
The lyrics are stored at the bottom, by default the lyrics for Pizza Mayhem go up to a count of 14 but you can actually insert as many as you need.
For example.  In the alternate "Example" branch of this repo, I have replaced Pizza Mayhem with Live and Learn from Sonic Adventure 2.  That song contains 27 unique lyrics.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199411393775014128/image.png)

Meanwhile on the FMOD's end, to actually call up the lyrics it references the parameter `pmlyric`.  This parameter has a range of 0-14 by default.
If you resize the parameter to whatever your lyrics need, make sure you make it not scale.

To make the lyrics get called as the song is going, refer to the `Lyrics` and `Stops` lanes in the `finalescape` event.
These lanes have **command instruments** that will change the value of `pmlyric`.  When set to 0 they will remove the lyrics off the screen.  1 onwards represent the Lyrics (lyric<N> = " ") established in your english.txt

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199413033391357962/image.png)

It's a very time consuming process but it's definitely worth the effort.

# Music Credits
Vozaxhi - [Pillar John's Revenge](https://www.youtube.com/watch?v=MSzReOhnxXg)
Inceptradom - [Absolute AbsurZiti](https://www.youtube.com/watch?v=Tj6sN5GNBPA)
LAAAAE - [Funicula Freakout](https://www.youtube.com/watch?v=NuDjZB65ViA)