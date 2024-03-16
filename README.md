# ELM-Events-Recreation
A very rough recreation of the FMOD event folders as a project for the Pizza Tower mod [**Egg's Lap Mod**](https://gamebanana.com/mods/464912) for those who want to use custom music and sounds with their own Pizza Tower [FMOD](https://github.com/Raltyro/PT-FSPRO-Recreation) [recreations](https://github.com/Laventory/CheesedUP-FMOD).


# !! NOISE UPDATE !!


![](https://cdn.discordapp.com/attachments/1201874990635696169/1218458718241558538/EXT.png?ex=6607bd1c&is=65f5481c&hm=9fd8940c6b71226d47c1122b17c129777594258b07dddc3882dee3f7c3c14238&)

I'm going to kill John Pizza Tower.

# How it works
The FMOD Project included here merely contains the folder structure and events that ELM reads for, in order for you to make it work with your own FMOD project all you must do is the following steps.


1. Open the FMOD project and copy the folders with the events inside into your own FMOD project.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1175285747125850202/image.png?ex=66078fa5&is=65f51aa5&hm=c402efcaba4e314b3e5e1e49dc757c784caa223b16c0c368860cede65bae6c7c&)

2. Create two new banks in the "Banks" tab, these banks respectfully should be named `ELMmusic` and `ELMsfx`, alongside these rename `Master` to `ELMMaster`

![](https://cdn.discordapp.com/attachments/1140611242411700297/1175289796025909369/image.png?ex=6607936b&is=65f51e6b&hm=f026ffc7a4ae4c485a0cf0a229c23da53fb2cc66dc8adee05043a88b15549a8a&)

3. Assign the folders to their respective banks.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1175291221120397352/image.png?ex=660794be&is=65f51fbe&hm=9286f425cb6a6f1c4731e2eef16668780001122b153b6ffb0b04a3d868af17e5&)

4. Assign the events in the mixer
  - You can open the mixer tab with CTRL+5, assign the music and sfx to their respective mixer folders.
   
![](https://cdn.discordapp.com/attachments/1140611242411700297/1175461476635525120/image.png?ex=6608334f&is=65f5be4f&hm=03674b6d2cb539225f58481adc445d07bb0ad6e1e3279bc374067fe4455c4616&)

5. Modify to your hearts content or build and put them in `Pizza Tower\sound\Desktop\_` and `Desktop\EggsLapMod\_` for the respective ELM and normal bank files.
  - You need not worry about creating a `Master.bank` or `Master.strings.bank` as ELM only reads the `ELMMaster.bank` and `ELMMaster.strings.bank` files that are in the EggsLapMod folder.

# Alternate Lap 4 tracks.
## WARNING:  These haven't been reformatted for the Noise Update banks, I'll get on them later but you'll understand if you even just GLANCE at the pizzatime event now.
So within the FMOD project you might notice the folder at the bottom labeled "Alternate Tracks".

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199400273253240863/image.png?ex=6603010c&is=65f08c0c&hm=0eab6c353c947bd3b60c5020fcd5264e06e171297b33c1d6ea2132a093bd7fca&)

Within the folder it contains alternate tracks to replace Absolute AbsurZiti V2 in the `pizzatime` even with.

1. Inside the FMOD Project navigate to the event for the track you want to replace the current Lap 4 track with.  For example I am going to replace AbsurZiti with Funiculi Freakout V2.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199400981960597654/image.png?ex=660301b5&is=65f08cb5&hm=901eeda110d578d300f52d2b67a76dace0bd0600cfb5a00ccf6b5a5426d264c3&)

2. Select the contents inside the event, that being the track, its magnet region and loop region.  Copy these.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199401436828676176/image.png?ex=66030222&is=65f08d22&hm=b6f0dc2d73500330a7f6ff3d02b7f4e68311d73a11b224ea7a03ab8185eba0fb&)

3. Inside your `pizzatime` event, delete the section of the track containing the current Lap 4 track.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199402143644393542/image.png?ex=660302ca&is=65f08dca&hm=b6b67937c759bc33716a5710e30f7fc1bc4b561f6d9fa800e17f805a75f1a6b5&)
![](https://cdn.discordapp.com/attachments/1140611242411700297/1199402179648290826/image.png?ex=660302d3&is=65f08dd3&hm=1f624e2d56061dbe7e8ae688455042af0afab96b5367891ff0332c4320ca7fb1&)

4. Paste in the tracks you copied.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199403483703550124/image.png?ex=6603040a&is=65f08f0a&hm=54f54ea9a0c538eb155267125f85823ce113c6e09ea985bac261bba1d5467903&)

5. Click on the now empty transition marker at the beginning, set the destination to the magnet region that you pasted in alongside the loop region and music track.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199404144432254996/image.png?ex=660304a7&is=65f08fa7&hm=a602a08f40551a46d6c8e8723ead086dbbea52dca4a0de983bf450342c715811&)

And viola! Now when you build your custom ELM banks, the track you inserted from here will now play instead of Absolute AbsurZiti V2.

# Changing Pizza Mayhem's Lyrics.
So lets say that within your project, you want a COMPLETELY different song to play instead of Pizza Mayhem during The Final Lap, and the song in question, lets go over this.

So the way that Egg's Lap Mod does the lyrics for Pizza Mayhem is interesting, the first thing to note is that the lyrics are stored in the english.txt file in the `lang\` folder inside Pizza Tower's directory.
The lyrics are stored at the bottom, by default the lyrics for Pizza Mayhem go up to a count of 14 but you can actually insert as many as you need.
For example.  In the alternate "Example" branch of this repo, I have replaced Pizza Mayhem with Live and Learn from Sonic Adventure 2.  That song contains 27 unique lyrics.

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199411393775014128/image.png?ex=66030b68&is=65f09668&hm=85346455932a5af7276f662ef46927c934ff9e4a4ff9e22fdc7a114d035c206b&)

Meanwhile on the FMOD's end, to actually call up the lyrics it references the parameter `pmlyric`.  This parameter has a range of 0-14 by default.
If you resize the parameter to whatever your lyrics need, make sure you make it not scale.

To make the lyrics get called as the song is going, refer to the `Lyrics` and `Stops` lanes in the `finalescape` event.
These lanes have **command instruments** that will change the value of `pmlyric`.  When set to 0 they will remove the lyrics off the screen.  1 onwards represent the Lyrics (lyric<N> = " ") established in your english.txt

![](https://cdn.discordapp.com/attachments/1140611242411700297/1199411956113735802/image.png?ex=66030bee&is=65f096ee&hm=5c2c9fea654aa2f7eb59ca07d50248db33dc69c8dc7309c0d0dc26e365853b59&)
![](https://cdn.discordapp.com/attachments/1140611242411700297/1199413033391357962/image.png?ex=66030cef&is=65f097ef&hm=6ae635f9be379433e86545a29035f03b264274f7538358624c9a18f2f5bbe933&)

It's a very time consuming process but it's definitely worth the effort.

# Music Credits
Vozaxhi - [Pillar John's Revenge](https://www.youtube.com/watch?v=MSzReOhnxXg)
Inceptradom - [Absolute AbsurZiti](https://www.youtube.com/watch?v=Tj6sN5GNBPA)
LAAAAE - [Funicula Freakout](https://www.youtube.com/watch?v=NuDjZB65ViA)
